<!-- loio44bb2d3596554bf4b94ea344e40937dd -->

# Expose and Secure a Workload with a JWT Using SAP Cloud Identity Services

This procedure explains how to expose a workload on a custom domain and secure it with JSON Web Tokens \(JWTs\) issued by SAP Cloud Identity Services - Identity Authentication using the Client Credentials grant.



<a name="loio44bb2d3596554bf4b94ea344e40937dd__prereq_g4r_ybm_rsb"/>

## Prerequisites

-   You have an SAP BTP, Kyma runtime instance with the Istio and API Gateway modules added. The Istio and API Gateway modules are added to your Kyma cluster by default.
-   You have an SAP Cloud Identity Services tenant. See [Initial Setup](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/initial-setup?locale=en-US&version=Cloud&q=open+id+connect).



<a name="loio44bb2d3596554bf4b94ea344e40937dd__context_umr_nyg_y2c"/>

## Context

Use this procedure to secure your workload with a short-lived JWT. To get the JWT, you must first register an OpenID Connect \(OIDC\) application in SAP Cloud Identity Services and enable the Client Credentials grant. This generates a client ID \(public identifier\) and a client secret \(confidential credential\). A calling system sends these credentials to the OIDC token endpoint over TLS, receiving a signed JWT.

When the client calls your exposed API, it includes the token in the Authorization header using the Bearer scheme. The API Gateway module validates the token based on the configuration you include in the APIRule custom resource \(CR\). If the validation fails, the Gateway returns \`HTTP/2 403 RBAC: access denied\` without forwarding the request to the backend Service.

If the validation is successful, the request proceeds to the Service behind the Gateway. At that point, you can implement optional, deeper authorization \(examining scopes, audience, or custom claims\) inside your application code.

Follow these steps:

1.  [Configure a TLS Gateway for Your Custom Domain](expose-and-secure-a-workload-with-a-jwt-using-sap-cloud-identity-services-44bb2d3.md#loio44bb2d3596554bf4b94ea344e40937dd__task_zn2_ngt_3hc)
2.  [Create and Configure an OpenID Connect Application](expose-and-secure-a-workload-with-a-jwt-using-sap-cloud-identity-services-44bb2d3.md#loio44bb2d3596554bf4b94ea344e40937dd__task_igm_nht_3hc)
3.  [Get a JWT](expose-and-secure-a-workload-with-a-jwt-using-sap-cloud-identity-services-44bb2d3.md#loio44bb2d3596554bf4b94ea344e40937dd__task_oxs_q3t_3hc)
4.  [Configure JWT Authentication in Kyma](expose-and-secure-a-workload-with-a-jwt-using-sap-cloud-identity-services-44bb2d3.md#loio44bb2d3596554bf4b94ea344e40937dd__task_rrf_1jt_3hc)

<a name="task_zn2_ngt_3hc"/>

<!-- task\_zn2\_ngt\_3hc -->

## Configure a TLS Gateway for Your Custom Domain

To configure the flow in Kyma, you must first provide credentials for a supported DNS provider so Gardener can create and verify the necessary DNS records for your custom wildcard domain. After this, Let’s Encrypt issues a trusted TLS certificate. The issued certificate is stored in a Kubernetes Secret referenced by an Istio Gateway, which terminates HTTPS at the cluster edge, so all downstream traffic enters encrypted.



## Procedure

1.  Create a namespace with enabled Istio sidecar proxy injection.

    ```
    kubectl create ns test
    kubectl label namespace test istio-injection=enabled --overwrite
    ```

2.  Export the following domain names as environment variables. Replace `my-own-domain.example.com` with the name of your domain. You can adjust these values as needed.

    ```
    PARENT_DOMAIN="my-own-domain.example.com"
    SUBDOMAIN="tls.${PARENT_DOMAIN}"
    GATEWAY_DOMAIN="*.${SUBDOMAIN}"
    WORKLOAD_DOMAIN="httpbin.${SUBDOMAIN}"
    ```


    <table>
    <tr>
    <th valign="top">

    Placeholder
    
    </th>
    <th valign="top">

    Example domain name
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `PARENT_DOMAIN`
    
    </td>
    <td valign="top">
    
    `my-own-domain.example.com`
    
    </td>
    <td valign="top">
    
    The domain name available in your public DNS zone.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `SUBDOMAIN`
    
    </td>
    <td valign="top">
    
    `tls.my-own-domain.example.com`
    
    </td>
    <td valign="top">
    
    A subdomain created under the parent domain, specifically for the mTLS Gateway.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `GATEWAY_DOMAIN`
    
    </td>
    <td valign="top">
    
    `*.tls.my-own-domain.example.com`
    
    </td>
    <td valign="top">
    
    A wildcard domain covering all possible subdomains under the TLS subdomain. When configuring the Gateway, this allows you to expose workloads on multiple hosts \(for example, `httpbin.mtls.my-own-domain.example.com`, `test.httpbin.mtls.my-own-domain.example.com`\) without creating separate Gateway rules for each one.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `WORKLOAD_DOMAIN`
    
    </td>
    <td valign="top">
    
    `httpbin.tls.my-own-domain.example.co`
    
    </td>
    <td valign="top">
    
    The specific domain assigned to your workload.
    
    </td>
    </tr>
    </table>
    
3.  Create a Secret containing credentials for your DNS cloud service provider.

    The information you provide to the data field differs depending on the DNS provider you're using. The DNS provider must be supported by Gardener. To learn how to configure the Secret for a specific provider, follow [External DNS Management Guidelines](https://github.com/gardener/external-dns-management) and the [External DNS Management examples](https://github.com/gardener/external-dns-management/tree/master/examples).

    See an example Secret for the AWS Route 53 DNS provider. `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` are base-64 encoded credentials.

    ```
    apiVersion: v1
    kind: Secret
    metadata:
      annotations:
        dns.gardener.cloud/class: garden
      name: aws-credentials
      namespace: test
    type: Opaque
    data:
      AWS_ACCESS_KEY_ID: <your AWS access key>
      AWS_SECRET_ACCESS_KEY: <your AWS secret access key>
      # Optionally, specify the region
      #AWS_REGION: <your AWS region>
      # Optionally, specify the token
      #AWS_SESSION_TOKEN: <your AWS session token>
    ```

4.  Create a DNSProvider resource that references the Secret with your DNS provider's credentials.

    See an example Secret for the AWS Route 53 DNS provider:

    ```
    apiVersion: dns.gardener.cloud/v1alpha1
    kind: DNSProvider
    metadata:
      name: aws
      namespace: test
    spec:
      type: aws-route53
      secretRef:
        name: aws-credentials
      domains:
        include:
        - "${PARENT_DOMAIN}"
    ```

    For DNSProvider configuration for other providers, see the [External DNS Management examples](https://github.com/gardener/external-dns-management/tree/master/examples).

    To verify that the DNSProvider is ready, run:

    > ### Sample Code:  
    > ```
    > kubectl get DNSProvider -n test {DNSPROVIDER_NAME}
    > ```

5.  Get the external access point of the `istio-ingressgateway` service.

    The external access point is either stored in the ingress Gateway's `ip` field \(for example, on GCP\) or in the ingress Gateway's `hostname` field \(for example, on AWS\).

    ```
    LOAD_BALANCER_ADDRESS=$(kubectl get services --namespace istio-system istio-ingressgateway --output jsonpath='{.status.loadBalancer.ingress[0].ip}')
    if [[ -z $LOAD_BALANCER_ADDRESS ]]; then
        LOAD_BALANCER_ADDRESS=$(kubectl get services --namespace istio-system istio-ingressgateway --output jsonpath='{.status.loadBalancer.ingress[0].hostname}')
    fi
    echo "The load balancer address is ${LOAD_BALANCER_ADDRESS}"
    ```

6.  Create a DNSEntry resource.

    ```
    cat <<EOF | kubectl apply -f -
    apiVersion: dns.gardener.cloud/v1alpha1
    kind: DNSEntry
    metadata:
      name: dns-entry
      namespace: test
      annotations:
        dns.gardener.cloud/class: garden
    spec:
      dnsName: "${GATEWAY_DOMAIN}"
      ttl: 600
      targets:
        - "${LOAD_BALANCER_ADDRESS}"
    EOF
    ```

    To verify that the DNSEntry is ready, run:

    > ### Sample Code:  
    > ```
    > kubectl get DNSEntry -n test dns-entry
    > ```

7.  Create the server's certificate.

    You use a Certificate CR to request and manage Let's Encrypt certificates from your Kyma cluster. When you create a Certificate CR, one of Gardener's operators detects it and creates an [ACME](https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://letsencrypt.org/how-it-works/&ved=2ahUKEwiRhM_VrruQAxWFPxAIHbePM38QFnoECC0QAQ&usg=AOvVaw25RIWodU2kz362IWS5BbJs) request to Let's Encrypt requesting certificate for the specified domain names. The issued certificate is stored in an automatically created Kubernetes Secret, which name you specify in the Certificate's `secretName` field. For more information, see [Manage certificates with Gardener for public domain](https://gardener.cloud/docs/extensions/others/gardener-extension-shoot-cert-service/request_cert/).

    ```
    cat <<EOF | kubectl apply -f -
    apiVersion: cert.gardener.cloud/v1alpha1
    kind: Certificate
    metadata:
      name: domain-certificate
      namespace: "istio-system"
    spec:
      secretName: custom-tls-secret
      commonName: "${GATEWAY_DOMAIN}"
      issuerRef:
        name: garden
    EOF
    ```

    To verify that the Secret with Gateway certificates is ready, run:

    > ### Sample Code:  
    > ```
    > kubectl get secret -n istio-system custom-tls-secret
    > ```

8.  Create a TLS Gateway.

    ```
    cat <<EOF | kubectl apply -f -
    apiVersion: networking.istio.io/v1alpha3
    kind: Gateway
    metadata:
      name: custom-tls-gateway
      namespace: test
    spec:
      selector:
        app: istio-ingressgateway
        istio: ingressgateway
      servers:
        - port:
            number: 443
            name: tls
            protocol: HTTPS
          tls:
            mode: SIMPLE
            credentialName: custom-tls-secret
          hosts:
            - "${GATEWAY_DOMAIN}"
    EOF
    ```

    To verify that the TLS Gateway is ready, run:

    > ### Sample Code:  
    > ```
    > kubectl get gateway -n test custom-tls-gateway
    > ```


<a name="task_igm_nht_3hc"/>

<!-- task\_igm\_nht\_3hc -->

## Create and Configure an OpenID Connect Application

You need an identity provider to issue JWTs. Create an OpenID Connect application to use SAP Cloud Identity Services as your JWT issuer that manages authentication for your workloads.



## Procedure

1.  Sign in to the administration console for SAP Cloud Identity Services. See [Access Admin Console](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/accessing-administration-console?locale=en-US&version=Cloud).

2.  Create an OpenID Connect Application.

    1.  Go to *Application Resources → Application*.

    2.  Choose *Create*, provide the application name, and select the OpenID Connect radio-button.

        For more configuration options, see [Create OpenID Connect Application](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/create-openid-connect-application-299ae2f07a6646768cbc881c4d368dac?locale=en-US&version=Cloud).

    3.  Choose *\+ Create*.


3.  Configure OpenID Connect Application for the Client Credentials flow.

    1.  In the *Trust → Single Sign-On* section of your created application, choose *OpenID Connect Configuration*.

    2.  Provide the name..

    3.  In the *Grant types* section, check *Client Credentials*.

        For more configuration options, see [Configure OpenID Connect Application for Client Credentials Flow](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/client-cred-configure-openid-connect-application-for-client-credentials-flow?locale=en-US&version=Cloud).

    4.  Choose *Save*.


4.  Configure a secret for API authentication.

    1.  In the *Application API → Client Authentication* section of your created application, choose *OpenID Connect Configuration*.

    2.  In the *Secret* section, choose *Add*.

    3.  Choose the OpenID scope and provide other configuration as needed.

        For more configuration options, see [Configure Secrets for API Authentication](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/dev-configure-secrets-for-api-authentication?version=Cloud&locale=en-US).

    4.  Choose *Save*.


    Your client ID and secret appear in a pop-up window. Save the secret, as you cannot retrieve it again after closing this window.


<a name="task_oxs_q3t_3hc"/>

<!-- task\_oxs\_q3t\_3hc -->

## Get a JWT



## Procedure

1.  Export the following values as environment variables:

    ```
    CLOUD_IDENTITY_SERVICES_INSTANCE="my-example-tenant.accounts.ondemand.com"
    CLIENT_ID="{YOUR-CLIENT-ID}"
    CLIENT_SECRET="{YOUR-CLIENT-SECRET}"
    ```

2.  Export base 64 encoded client ID and client secret.

    ```
    export ENCODED_CREDENTIALS=$(echo -n "$CLIENT_ID:$CLIENT_SECRET" | base64)
    ```

3.  Get `token_endpoint`, `jwks_uri`, and `issuer` from your OpenID application, and save these values as environment variables:

    ```
    TOKEN_ENDPOINT=$(curl -s https://$CLOUD_IDENTITY_SERVICES_INSTANCE/.well-known/openid-configuration | jq -r '.token_endpoint')
    echo token_endpoint: $TOKEN_ENDPOINT
    JWKS_URI=$(curl -s https://$CLOUD_IDENTITY_SERVICES_INSTANCE/.well-known/openid-configuration | jq -r '.jwks_uri')
    echo jwks_uri: $JWKS_URI
    ISSUER=$(curl -s https://$CLOUD_IDENTITY_SERVICES_INSTANCE/.well-known/openid-configuration | jq -r '.issuer')
    echo issuer: $ISSUER
    ```

4.  Get the JWT access token:

    ```
    ACCESS_TOKEN=$(curl -s -X POST "$TOKEN_ENDPOINT" \
        -d "grant_type=client_credentials" \
        -d "client_id=$CLIENT_ID" \
        -H "Content-Type: application/x-www-form-urlencoded" \
        -H "Authorization: Basic $ENCODED_CREDENTIALS" |  jq -r '.access_token')
    echo $ACCESS_TOKEN
    ```


<a name="task_rrf_1jt_3hc"/>

<!-- task\_rrf\_1jt\_3hc -->

## Configure JWT Authentication in Kyma

To configure JWT authentication, expose your workload using APIRule custom resource \(CR\) and configure `jwt` as the access strategy. You can either use kubectl or Kyma dashboard.



## Procedure

-   Kyma dashboard

    1.  Go to *Discovery and Network → API Rules* and choose *Create*.

    2.  Provide all the required configuration details.

    3.  For each path you want to secure with a JWT, add a rule with the following configuration.


        <table>
        <tr>
        <th valign="top">

        Option
        
        </th>
        <th valign="top">

        Description
        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
        *Path*
        
        </td>
        <td valign="top">
        
        Specify the request path.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *Methods*
        
        </td>
        <td valign="top">
        
        Check the allowed access methods.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *Access Strategy*
        
        </td>
        <td valign="top">
        
        *JWT*
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *JWT → Authentications*
        
        </td>
        <td valign="top">
        
        In the *JWT* section, add an authentication with your issuer and JSON Web Key Set URIs.
        
        </td>
        </tr>
        </table>
        
        See the following example of a sample HTTPBin Deployment exposed by an APIRule with JWT authentication:

        ```
        apiVersion: v1
        kind: ServiceAccount
        metadata:
          name: httpbin
          namespace: test
        ---
        apiVersion: v1
        kind: Service
        metadata:
          name: httpbin
          namespace: test
          labels:
            app: httpbin
            service: httpbin
        spec:
          ports:
          - name: http
            port: 8000
            targetPort: 80
          selector:
            app: httpbin
        ---
        apiVersion: apps/v1
        kind: Deployment
        metadata:
          name: httpbin
          namespace: test
        spec:
          replicas: 1
          selector:
            matchLabels:
              app: httpbin
              version: v1
          template:
            metadata:
              labels:
                app: httpbin
                version: v1
            spec:
              serviceAccountName: httpbin
              containers:
              - image: docker.io/kennethreitz/httpbin
                imagePullPolicy: IfNotPresent
                name: httpbin
                ports:
                - containerPort: 80
        ```

        ```
        apiVersion: gateway.kyma-project.io/v2
        kind: APIRule
        metadata:
          name: httpbin-tls
          namespace: test
        spec:
          gateway: test/custom-tls-gateway
          hosts:
            - "${WORKLOAD_DOMAIN}"
          rules:
            - jwt:
                authentications:
                  - issuer: ${ISSUER}
                    jwksUri: ${JWKS_URI}
              methods:
                - GET
              path: /*
          service:
            name: httpbin
            port: 8000
        ```


-   kubectl

    To expose and secure your Service, create the APIRule custom resource. For each path you want to secure with a JWT, add a rule with the `jwt` field and specify the `issuer` and `jwksUri`.

    ```
    rules:
    ...
      - jwt:
          authentications:
            - issuer: ${ISSUER}
              jwksUri: ${JWKS_URI}
    ...
    ```

    See the following example of a sample HTTPBin Deployment exposed by an APIRule with JWT authentication:

    ```
    apiVersion: v1
    kind: ServiceAccount
    metadata:
      name: httpbin
      namespace: test
    ---
    apiVersion: v1
    kind: Service
    metadata:
      name: httpbin
      namespace: test
      labels:
        app: httpbin
        service: httpbin
    spec:
      ports:
      - name: http
        port: 8000
        targetPort: 80
      selector:
        app: httpbin
    ---
    apiVersion: apps/v1
    kind: Deployment
    metadata:
      name: httpbin
      namespace: test
    spec:
      replicas: 1
      selector:
        matchLabels:
          app: httpbin
          version: v1
      template:
        metadata:
          labels:
            app: httpbin
            version: v1
        spec:
          serviceAccountName: httpbin
          containers:
          - image: docker.io/kennethreitz/httpbin
            imagePullPolicy: IfNotPresent
            name: httpbin
            ports:
            - containerPort: 80
    ```

    ```
    apiVersion: gateway.kyma-project.io/v2
    kind: APIRule
    metadata:
      name: httpbin-tls
      namespace: test
    spec:
      gateway: test/custom-tls-gateway
      hosts:
        - "${WORKLOAD_DOMAIN}"
      rules:
        - jwt:
            authentications:
              - issuer: ${ISSUER}
                jwksUri: ${JWKS_URI}
          methods:
            - GET
          path: /*
      service:
        name: httpbin
        port: 8000
    ```




<a name="task_rrf_1jt_3hc__result_pxs_llt_3hc"/>

## Results

You have exposed the workload with APIRule custom resource.

1.  First, test the connection without the JWT.

    ```
    curl -ik -X GET https://${WORKLOAD_DOMAIN}/headers
    ```

    You get the error `HTTP/2 403 RBAC: access denied`.

2.  Now, access the secured workload using the correct JWT.

    ```
    curl -ik -X GET https://${WORKLOAD_DOMAIN}/headers --header "Authorization:Bearer $ACCESS_TOKEN"
    ```

    You get the `200 OK` response code.


