<!-- loio87a874c616e04740a14235acff6597a3 -->

# Configure a TLS Gateway

Learn how to configure a TLS Gateway in SAP BTP, Kyma runtime using Gardener-managed Let's Encrypt certificates.



## Context

In this procedure, you set up a TLS Gateway that secures communication between clients and your workloads. The server certificate is automatically provisioned and managed through Gardener's Certificate custom resource \(CR\), which requests a publicly trusted certificate from Let's Encrypt.

For setting up the TLS Gateway, you must prepare the domain name available in the public DNS zone. You can either use a custom domain \(see [Custom Domain Scenario](configure-a-tls-gateway-87a874c.md#loio87a874c616e04740a14235acff6597a3__task_fc1_4rj_vhc)\) or the default domain of your Kyma cluster \(see [Default Domain Scenario](configure-an-mtls-gateway-e7c6c6a.md#loioe7c6c6a2b47744dbaa405b422e454303__task_m2p_3zl_dhc). For more information on the domain names and Gateways, see [Istio Gateways](https://help.sap.com/docs/btp/sap-business-technology-platform-internal/configuring-istio-gateways?locale=en-US&state=DRAFT&version=Internal).

<a name="task_fc1_4rj_vhc"/>

<!-- task\_fc1\_4rj\_vhc -->

## Custom Domain Scenario



## Prerequisites

-   The Istio and API Gateway modules are added to your Kyma cluster by default. See [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).
-   You have the domain name available in the public DNS zone.
-   Your DNS provider is supported by Gardener. For the list of supported providers, see [External DNS Management Guidelines](https://github.com/gardener/external-dns-management/blob/master/README.md#external-dns-management).



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
    echo "Parent Domain: ${PARENT_DOMAIN}"
    echo "Subdomain: ${SUBDOMAIN}"
    echo "Gateway Domain: ${GATEWAY_DOMAIN}"
    echo "Workload Domain: ${WORKLOAD_DOMAIN}"
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
    
    A subdomain created under the parent domain, specifically for the TLS Gateway.
    
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
    
    A wildcard domain covering all possible subdomains under the TLS subdomain. When configuring the Gateway, this allows you to expose workloads on multiple hosts \(for example, `httpbin.tls.my-own-domain.example.com`, `test.httpbin.tls.my-own-domain.example.com`\) without creating separate Gateway rules for each one.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `WORKLOAD_DOMAIN`
    
    </td>
    <td valign="top">
    
    `httpbin.tls.my-own-domain.example.com`
    
    </td>
    <td valign="top">
    
    The specific domain assigned to your workload.
    
    </td>
    </tr>
    </table>
    
3.  Create a Secret containing credentials for your DNS cloud service provider.

    The information you provide to the data field differs depending on the DNS provider you're using. The DNS provider must be supported by Gardener. To learn how to configure the Secret for a specific provider, follow [External DNS Management Guidelines](https://github.com/gardener/external-dns-management) and the [External DNS Management examples](https://github.com/gardener/external-dns-management/tree/master/examples).

    See an example Secret for AWS Route 53 DNS provider. `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` are base-64 encoded credentials.

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

    See an example Secret for AWS Route 53 DNS provider:

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
      secretName: kyma-mtls
      commonName: "${GATEWAY_DOMAIN}"
      issuerRef:
        name: garden
    EOF
    ```

    To verify that the Secret with Gateway certificates is created, run:

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
            name: https
            protocol: HTTPS
          tls:
            mode: SIMPLE
            credentialName: custom-tls-secret
          hosts:
            - "${GATEWAY_DOMAIN}"
    EOF
    
    ```

    To verify that the TLS Gateway is created, run:

    ```
    kubectl get gateway -n test custom-tls-gateway
    ```

9.  To test the TLS connection, you can deploy and expose a sample HTTPBin Service.

    1.  Deploy the HTTPBin Service.

        ```
        cat <<EOF | kubectl apply -f -
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
        EOF
        ```

    2.  Expose the HTTPBin Service.

        ```
        cat <<EOF | kubectl apply -f -
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
            - methods:
                - GET
              noAuth: true
              path: /*
              timeout: 300
          service:
            name: httpbin
            port: 8000
        EOF
        ```

    3.  Test the connection.

        ```
        curl -X GET https://${WORKLOAD_DOMAIN}/ip
        ```

        If successful, you get code `200` in response.



<a name="task_m5h_srj_vhc"/>

<!-- task\_m5h\_srj\_vhc -->

## Kyma Domain Scenario



## Prerequisites

-   The Istio and API Gateway modules are added to your Kyma cluster by default. See [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).



## Procedure

1.  Create a namespace with enabled Istio sidecar proxy injection.

    ```
    kubectl create ns test
    kubectl label namespace test istio-injection=enabled --overwrite
    ```

2.  Export the following domain names as environment variables. Replace `my-own-domain.example.com` with the name of your domain. You can adjust these values as needed.

    ```
    PARENT_DOMAIN=$(kubectl get gateway -n kyma-system kyma-gateway -o jsonpath='{.spec.servers[0].hosts[0]}' | sed 's/\*\.//')
    SUBDOMAIN="tls.${PARENT_DOMAIN}"
    GATEWAY_DOMAIN="*.${SUBDOMAIN}"
    WORKLOAD_DOMAIN="httpbin.${SUBDOMAIN}"
    echo "Parent Domain: ${PARENT_DOMAIN}"
    echo "Subdomain: ${SUBDOMAIN}"
    echo "Gateway Domain: ${GATEWAY_DOMAIN}"
    echo "Workload Domain: ${WORKLOAD_DOMAIN}"
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
    
    `my-default-domain.example.com`
    
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
    
    `tls.my-default-domain.example.com`
    
    </td>
    <td valign="top">
    
    A subdomain created under the parent domain, specifically for the TLS Gateway.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `GATEWAY_DOMAIN`
    
    </td>
    <td valign="top">
    
    `*.tls.my-default-domain.example.com`
    
    </td>
    <td valign="top">
    
    A wildcard domain covering all possible subdomains under the TLS subdomain. When configuring the Gateway, this allows you to expose workloads on multiple hosts \(for example, `httpbin.tls.my-default-domain.example.com`, `test.httpbin.tls.my-default-domain.example.com`\) without creating separate Gateway rules for each one.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `WORKLOAD_DOMAIN`
    
    </td>
    <td valign="top">
    
    `httpbin.tls.my-default-domain.example.com`
    
    </td>
    <td valign="top">
    
    The specific domain assigned to your workload.
    
    </td>
    </tr>
    </table>
    
3.  Create a TLS Gateway.

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
            name: https
            protocol: HTTPS
          tls:
            mode: SIMPLE
            credentialName: custom-tls-secret
          hosts:
            - "${GATEWAY_DOMAIN}"
    EOF
    
    ```

    To verify that the TLS Gateway is created, run:

    ```
    kubectl get gateway -n test custom-tls-gateway
    ```

4.  To test the TLS connection, you can deploy and expose a sample HTTPBin Service.

    1.  Deploy the HTTPBin Service.

        ```
        cat <<EOF | kubectl apply -f -
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
        EOF
        ```

    2.  Expose the HTTPBin Service.

        ```
        cat <<EOF | kubectl apply -f -
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
            - methods:
                - GET
              noAuth: true
              path: /*
              timeout: 300
          service:
            name: httpbin
            port: 8000
        EOF
        ```

    3.  Test the connection.

        ```
        curl -X GET https://${WORKLOAD_DOMAIN}/ip
        ```

        If successful, you get code `200` in response.



