<!-- loioe7c6c6a2b47744dbaa405b422e454303 -->

# Configure mTLS Authentication

Learn how to configure mutual TLS \(mTLS\) in SAP BTP, Kyma runtime using Gardener-managed Let's Encrypt server certificates and client certificates that you supply.



<a name="loioe7c6c6a2b47744dbaa405b422e454303__prereq_f1d_vrf_jhc"/>

## Prerequisites

-   You have an SAP BTP, Kyma runtime instance with Istio and API Gateway modules added. The Istio and API Gateway modules are added to your Kyma cluster by default.
-   For setting up the mTLS Gateway, you must prepare the domain name available in the public DNS zone. You can use one of the following approaches:
    -   Use your custom domain.

        To use a custom domain, you must own the DNS zone and supply credentials for a provider supported by Gardener so the ACME DNS challenge can be completed. For this, you must first register this DNS provider in your Kyma runtime cluster and create a DNS entry resource.

    -   Use the default domain of your Kyma cluster.

        When you create an SAP BTP, Kyma runtime instance, your cluster receives a default wildcard domain that provides the endpoint for the Kubernetes API server. This is the primary access point for all cluster management operations, used by kubectl and other tools.

        By default, the default Ingress Gateway `kyma-gateway` is configured under this domain. To learn what the domain is, you can check the APIServer URL in your subaccount overview, or get the domain name from the default simple TLS Gateway:

        ```
        kubectl get gateway -n kyma-system kyma-gateway -o jsonpath='{.spec.servers[0].hosts[0]}'
        ```

        You can request any subdomain of the assigned default domain and use it to create a TLS or mTLS Gateway, as long as it is not used by another resource. For example, if your default domain is `*.c12345.kyma.ondemand.com` you can use such subdomains as `example.c12345.kyma.ondemand.com`, `*.example.c12345.kyma.ondemand.com`, and more. If you use the Kyma runtime default domain, Gardener’s issuer can issue certificates for subdomains of that domain without additional DNS delegation.





<a name="loioe7c6c6a2b47744dbaa405b422e454303__context_wcd_wxv_2hc"/>

## Context

In this procedure, you generate certificates using the following approach:

-   Gardener’s Certificate custom resource \(CR\) requests a publicly trusted server certificate from Let’s Encrypt and creates a Secret that stores the certificate and private key. Therefore, the clients must trust Let's Encrypt, which is the CA that signs the server's certificate. Most modern HTTP clients already trust Let's Encrypt.
-   Client certificates are self-signed. For production use, it's advised to use certificates issued by a trusted CA instead.

For setting up an mTLS Gateway, you can either use your custom domain or the default domain of your Kyma cluster. See [Custom Domain Scenario](configure-mtls-authentication-e7c6c6a.md#loioe7c6c6a2b47744dbaa405b422e454303__h5l_rnt_wgc) or [Kyma Default Domain Scenario](configure-mtls-authentication-e7c6c6a.md#loioe7c6c6a2b47744dbaa405b422e454303__task_m2p_3zl_dhc).

<a name="h5l_rnt_wgc"/>

<!-- h5l\_rnt\_wgc -->

## Custom Domain Scenario



## Procedure

1.  Create a namespace with enabled Istio sidecar proxy injection.

    ```
    kubectl create ns test
    kubectl label namespace test istio-injection=enabled --overwrite
    ```

2.  Export the following domain names as environment variables. Replace `my-own-domain.example.com` with the name of your domain. You can adjust the following values as needed.

    ```
    PARENT_DOMAIN="my-own-domain.example.com"
    SUBDOMAIN="mtls.${PARENT_DOMAIN}"
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
    
    `mtls.my-own-domain.example.co`
    
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
    
    `*.mtls.my-own-domain.example.co`
    
    </td>
    <td valign="top">
    
    A wildcard domain covering all possible subdomains under the mTLS subdomain. When configuring the Gateway, this allows you to expose workloads on multiple hosts \(for example, `httpbin.mtls.my-own-domain.example.com`, `test.httpbin.mtls.my-own-domain.example.com`\) without creating separate Gateway rules for each one.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `WORKLOAD_DOMAIN`
    
    </td>
    <td valign="top">
    
    `httpbin.mtls.my-own-domain.example.co`
    
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
    > kubectl get secret -n istio-system kyma-mtls
    > ```

8.  Prepare the client's certificates.

    > ### Caution:  
    > For production deployments, use trusted certificate authorities to ensure proper security and automatic certificate management.

    1.  Create the client's root CA.

        ```
        CLIENT_ROOT_CA_KEY_FILE="client_root_ca_cn.key"
        CLIENT_ROOT_CA_CRT_FILE="client_root_ca_cn.crt"
        openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -subj "/O=Example Client Root CA ORG/CN=Example Client Root CA CN" -keyout "${CLIENT_ROOT_CA_KEY_FILE}" -out "${CLIENT_ROOT_CA_CRT_FILE}"
        
        ```

    2.  Create the client's certificate.

        ```
        CLIENT_CERT_CRT_FILE="client_cert_cn.crt"
        CLIENT_CERT_CSR_FILE="client_cert_cn.csr"
        CLIENT_CERT_KEY_FILE="client_cert_cn.key"
        openssl req -out "${CLIENT_CERT_CSR_FILE}" -newkey rsa:2048 -nodes -keyout "${CLIENT_CERT_KEY_FILE}" -subj "/CN=Example Client Cert CN/O=Example Client Cert Org"
        ```

    3.  Sign the client's certificate.

        ```
        openssl x509 -req -days 365 -CA "${CLIENT_ROOT_CA_CRT_FILE}" -CAkey "${CLIENT_ROOT_CA_KEY_FILE}" -set_serial 0 -in "${CLIENT_CERT_CSR_FILE}" -out "${CLIENT_CERT_CRT_FILE}"
        ```


9.  Create a Secret with Client CA Cert for mTLS Gateway. For more information on the convention that the Secret must use, see [Key Convention](https://istio.io/latest/docs/tasks/traffic-management/ingress/secure-ingress/#key-formats).

    ```
    kubectl create secret generic -n istio-system "kyma-mtls-cacert" --from-file=cacert="${CLIENT_ROOT_CA_CRT_FILE}"
    ```

10. Create an mTLS Gateway.

    ```
    cat <<EOF | kubectl apply -f -
    apiVersion: networking.istio.io/v1alpha3
    kind: Gateway
    metadata:
      name: kyma-mtls-gateway
      namespace: test
    spec:
      selector:
        app: istio-ingressgateway
        istio: ingressgateway
      servers:
        - port:
            number: 443
            name: mtls
            protocol: HTTPS
          tls:
            mode: MUTUAL
            credentialName: kyma-mtls
          hosts:
            - "${GATEWAY_DOMAIN}"
    EOF
    ```

11. To expose your workload, create an APIRule custom resource.

    You can configure the APIRule to append the headers `X-CLIENT-SSL-CN: '%DOWNSTREAM_PEER_SUBJECT%'`, `X-CLIENT-SSL-ISSUER: '%DOWNSTREAM_PEER_ISSUER%'`, and `X-CLIENT-SSL-SAN: '%DOWNSTREAM_PEER_URI_SAN%'` to the request. These headers provide the upstream \(your workload\) with the downstream \(authenticated client's\) identity. This is optional configuration is commonly used in mTLS use cases. For more information about these values, see [Envoy Access logging](https://www.envoyproxy.io/docs/envoy/latest/configuration/observability/access_log/usage#access-logging).

    See an example APIRule that exposes the following sample HTTPBin Service:

    > ### Sample Code:  
    > ```
    > apiVersion: v1
    > kind: ServiceAccount
    > metadata:
    >   name: httpbin
    >   namespace: test
    > ---
    > apiVersion: v1
    > kind: Service
    > metadata:
    >   name: httpbin
    >   namespace: test
    >   labels:
    >     app: httpbin
    >     service: httpbin
    > spec:
    >   ports:
    >   - name: http
    >     port: 8000
    >     targetPort: 80
    >   selector:
    >     app: httpbin
    > ---
    > apiVersion: apps/v1
    > kind: Deployment
    > metadata:
    >   name: httpbin
    >   namespace: test
    > spec:
    >   replicas: 1
    >   selector:
    >     matchLabels:
    >       app: httpbin
    >       version: v1
    >   template:
    >     metadata:
    >       labels:
    >         app: httpbin
    >         version: v1
    >     spec:
    >       serviceAccountName: httpbin
    >       containers:
    >       - image: docker.io/kennethreitz/httpbin
    >         imagePullPolicy: IfNotPresent
    >         name: httpbin
    >         ports:
    >         - containerPort: 80
    > ```
    > 
    > ```
    > apiVersion: gateway.kyma-project.io/v2
    > kind: APIRule
    > metadata:
    >   name: httpbin-mtls
    >   namespace: test
    > spec:
    >   gateway: test/kyma-mtls-gateway
    >   hosts:
    >     - "${WORKLOAD_DOMAIN}"
    >   rules:
    >     - methods:
    >         - GET
    >       noAuth: true
    >       path: /*
    >       timeout: 300
    >       request:
    >         headers:
    >           X-CLIENT-SSL-CN: '%DOWNSTREAM_PEER_SUBJECT%'
    >           X-CLIENT-SSL-ISSUER: '%DOWNSTREAM_PEER_ISSUER%'
    >           X-CLIENT-SSL-SAN: '%DOWNSTREAM_PEER_URI_SAN%'
    >   service:
    >     name: httpbin
    >     port: 8000
    > ```

12. Test the mTLS connection.

    1.  Call the workload without providing client certificates.

        ```
        curl --fail --verbose "https://${WORKLOAD_DOMAIN}/headers?show_env=true"
        ```

        You get cURL 56 error, which indicates that a certificate is not provided by the client. See the following example:

        ```
        curl: (56) OpenSSL SSL_read: OpenSSL/3.5.2: error:0A00045C:SSL routines::tlsv13 alert certificate required, errno 0 
        
        ```

    2.  Run the following curl command, which specifies the client's certificate and public key:

        ```
        curl --fail --verbose \
          --key "${CLIENT_CERT_KEY_FILE}" \
          --cert "${CLIENT_CERT_CRT_FILE}" \
          "https://${WORKLOAD_DOMAIN}/headers?show_env=true"
        ```

        If successful, you get code `200` in response. The configured headers are also populated. See the following example:

        ```
        {
          "headers": {
            ...
            "X-Client-Ssl-Cn": "O=Example Client Cert Org,CN=Example Client Cert CN",
            "X-Client-Ssl-Issuer": "CN=Example Client Root CA CN,O=Example Client Root CA ORG",
            ...
          }
        }
        
        ```



<a name="task_m2p_3zl_dhc"/>

<!-- task\_m2p\_3zl\_dhc -->

## Default Kyma Domain Scenario



## Procedure

1.  Create a namespace with enabled Istio sidecar proxy injection.

    ```
    kubectl create ns test
    kubectl label namespace test istio-injection=enabled --overwrite
    ```

2.  Export the following domain names as environment variables. Replace `my-own-domain.example.com` with the name of your domain. You can adjust the following values as needed.

    ```
    PARENT_DOMAIN=$(kubectl get gateway -n kyma-system kyma-gateway -o jsonpath='{.spec.servers[0].hosts[0]}' | sed 's/\*\.//')
    SUBDOMAIN="mtls.${PARENT_DOMAIN}"
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
    
    `my-default-domain.kyma.ondemand.com`
    
    </td>
    <td valign="top">
    
    The default domain of your Kyma cluster retrieved from the default TLS Gateway `kyma-gateway`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `SUBDOMAIN`
    
    </td>
    <td valign="top">
    
    `mtls.my-default-domain.kyma.ondemand.com`
    
    </td>
    <td valign="top">
    
    A subdomain created under the parent domain, specifically for the mTLS Gateway. Having a separate subdomain is required if you use the default domain of your Kyma cluster, as the parent domain name is already assigned to the TLS Gateway `kyma-gateway` installed in your cluster by default.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `GATEWAY_DOMAIN`
    
    </td>
    <td valign="top">
    
    `*.mtls.my-default-domain.kyma.ondemand.com`
    
    </td>
    <td valign="top">
    
    A wildcard domain covering all possible subdomains under the mTLS subdomain. When configuring the Gateway, this allows you to expose workloads on multiple hosts \(for example, `httpbin.mtls.my-default-domain.kyma.ondemand.com`, `test.httpbin.mtls.my-default-domain.kyma.ondemand.com`\) without creating separate Gateway rules for each one.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `WORKLOAD_DOMAIN`
    
    </td>
    <td valign="top">
    
    `httpbin.mtls.my-default-domain.kyma.ondemand.com`
    
    </td>
    <td valign="top">
    
    The specific domain assigned to your workload.
    
    </td>
    </tr>
    </table>
    
3.  Create the server's certificate.

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

    ```
    kubectl get secret -n istio-system kyma-mtls
    ```

4.  Prepare the client's certificates.

    > ### Caution:  
    > For production deployments, use trusted certificate authorities to ensure proper security and automatic certificate management.

    1.  Create the client's root CA.

        ```
        CLIENT_ROOT_CA_KEY_FILE="client_root_ca_cn.key"
        CLIENT_ROOT_CA_CRT_FILE="client_root_ca_cn.crt"
        openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -subj "/O=Example Client Root CA ORG/CN=Example Client Root CA CN" -keyout "${CLIENT_ROOT_CA_KEY_FILE}" -out "${CLIENT_ROOT_CA_CRT_FILE}"
        
        ```

    2.  Create the client's certificate.

        ```
        CLIENT_CERT_CRT_FILE="client_cert_cn.crt"
        CLIENT_CERT_CSR_FILE="client_cert_cn.csr"
        CLIENT_CERT_KEY_FILE="client_cert_cn.key"
        openssl req -out "${CLIENT_CERT_CSR_FILE}" -newkey rsa:2048 -nodes -keyout "${CLIENT_CERT_KEY_FILE}" -subj "/CN=Example Client Cert CN/O=Example Client Cert Org"
        ```

    3.  Sign the client's certificate.

        ```
        openssl x509 -req -days 365 -CA "${CLIENT_ROOT_CA_CRT_FILE}" -CAkey "${CLIENT_ROOT_CA_KEY_FILE}" -set_serial 0 -in "${CLIENT_CERT_CSR_FILE}" -out "${CLIENT_CERT_CRT_FILE}"
        ```


5.  Create a Secret with Client CA Cert for mTLS Gateway. For more information on the convention that the Secret must use, see [Key Convention](https://istio.io/latest/docs/tasks/traffic-management/ingress/secure-ingress/#key-formats).

    ```
    kubectl create secret generic -n istio-system "kyma-mtls-cacert" --from-file=cacert="${CLIENT_ROOT_CA_CRT_FILE}"
    ```

6.  Create an mTLS Gateway.

    ```
    cat <<EOF | kubectl apply -f -
    apiVersion: networking.istio.io/v1alpha3
    kind: Gateway
    metadata:
      name: kyma-mtls-gateway
      namespace: test
    spec:
      selector:
        app: istio-ingressgateway
        istio: ingressgateway
      servers:
        - port:
            number: 443
            name: mtls
            protocol: HTTPS
          tls:
            mode: MUTUAL
            credentialName: kyma-mtls
          hosts:
            - "${GATEWAY_DOMAIN}"
    EOF
    ```

7.  To expose your workload, create an APIRule custom resource.

    You can cofigure the APIRule to append the headers `X-CLIENT-SSL-CN: '%DOWNSTREAM_PEER_SUBJECT%'`, `X-CLIENT-SSL-ISSUER: '%DOWNSTREAM_PEER_ISSUER%'`, and `X-CLIENT-SSL-SAN: '%DOWNSTREAM_PEER_URI_SAN%'` to the request. These headers provide the upstream \(your workload\) with the downstream \(authenticated client's\) identity. This is optional configuration is commonly used in mTLS use cases. For more information about these values, see [Envoy Access logging](https://www.envoyproxy.io/docs/envoy/latest/configuration/observability/access_log/usage#access-logging).

    See an example APIRule that exposes the following sample HTTPBin Service:

    > ### Sample Code:  
    > ```
    > apiVersion: v1
    > kind: ServiceAccount
    > metadata:
    >   name: httpbin
    >   namespace: test
    > ---
    > apiVersion: v1
    > kind: Service
    > metadata:
    >   name: httpbin
    >   namespace: test
    >   labels:
    >     app: httpbin
    >     service: httpbin
    > spec:
    >   ports:
    >   - name: http
    >     port: 8000
    >     targetPort: 80
    >   selector:
    >     app: httpbin
    > ---
    > apiVersion: apps/v1
    > kind: Deployment
    > metadata:
    >   name: httpbin
    >   namespace: test
    > spec:
    >   replicas: 1
    >   selector:
    >     matchLabels:
    >       app: httpbin
    >       version: v1
    >   template:
    >     metadata:
    >       labels:
    >         app: httpbin
    >         version: v1
    >     spec:
    >       serviceAccountName: httpbin
    >       containers:
    >       - image: docker.io/kennethreitz/httpbin
    >         imagePullPolicy: IfNotPresent
    >         name: httpbin
    >         ports:
    >         - containerPort: 80
    > ```

    ```
    apiVersion: gateway.kyma-project.io/v2
    kind: APIRule
    metadata:
      name: httpbin-mtls
      namespace: test
    spec:
      gateway: test/kyma-mtls-gateway
      hosts:
        - "${WORKLOAD_DOMAIN}"
      rules:
        - methods:
            - GET
          noAuth: true
          path: /*
          timeout: 300
          request:
            headers:
              X-CLIENT-SSL-CN: '%DOWNSTREAM_PEER_SUBJECT%'
              X-CLIENT-SSL-ISSUER: '%DOWNSTREAM_PEER_ISSUER%'
              X-CLIENT-SSL-SAN: '%DOWNSTREAM_PEER_URI_SAN%'
      service:
        name: httpbin
        port: 8000
    ```

8.  Test the mTLS connection.

    1.  Call the workload without providing client certificates.

        ```
        curl --fail --verbose "https://${WORKLOAD_DOMAIN}/headers?show_env=true"
        ```

        You get cURL 56 error, which indicates that a certificate is not provided by the client. See the following example:

        ```
        curl: (56) OpenSSL SSL_read: OpenSSL/3.5.2: error:0A00045C:SSL routines::tlsv13 alert certificate required, errno 0 
        
        ```

    2.  Run the following curl command, which specifies the client's certificate and public key:

        ```
        curl --fail --verbose \
          --key "${CLIENT_CERT_KEY_FILE}" \
          --cert "${CLIENT_CERT_CRT_FILE}" \
          "https://${WORKLOAD_DOMAIN}/headers?show_env=true"
        ```

        If successful, you get code `200` in response. The configured headers are also populated. See the following example:

        ```
        {
          "headers": {
            ...
            "X-Client-Ssl-Cn": "O=Example Client Cert Org,CN=Example Client Cert CN",
            "X-Client-Ssl-Issuer": "CN=Example Client Root CA CN,O=Example Client Root CA ORG",
            ...
          }
        }
        
        ```



