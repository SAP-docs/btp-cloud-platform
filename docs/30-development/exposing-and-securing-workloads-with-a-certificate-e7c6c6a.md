<!-- loioe7c6c6a2b47744dbaa405b422e454303 -->

# Exposing and Securing Workloads with a Certificate

Learn how to expose and secure a workload with mutual authentication using a TLS Gateway.



<a name="loioe7c6c6a2b47744dbaa405b422e454303__prereq_adk_mv3_x2c"/>

## Prerequisites

-   You have the Istio and API Gateway modules added. See [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).
-   You have access to Kyma dashboard. Alternatively, to use CLI instructions, you must install [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl) and configure it to communicate with your Kyma runtime instance. See [Access a Kyma Instance Using kubectl](access-a-kyma-instance-using-kubectl-3e25944.md).
-   You have installed [curl](https://curl.se/).
-   You have a deployed workload.
-   You have [set up your custom domain](https://kyma-project.io/#/api-gateway/user/tutorials/01-10-setup-custom-domain-for-workload). Alternatively, you can use the default domain of your Kyma cluster and the default Gateway `kyma-system/kyma-gateway`.

    > ### Note:  
    > Because the default Kyma domain is a wildcard domain, which uses a simple TLS Gateway, it is recommended that you set up your custom domain for use in a production environment.

    > ### Tip:  
    > To learn what the default domain of your Kyma cluster is, run the following command:
    > 
    > ```
    > kubectl get gateway -n kyma-system kyma-gateway -o jsonpath='{.spec.servers[0].hosts}'
    > ```

-   Optionally, you can [create your own self-signed Client Root CA and certificate](https://kyma-project.io/#/api-gateway/user/tutorials/01-60-security/01-61-mtls-selfsign-client-certicate).




<a name="loioe7c6c6a2b47744dbaa405b422e454303__context_nt4_mfw_x2c"/>

## Context

To expose your workload, create Istio `VirtualService`. Then, create an AuthorizationPolicy to verify that the name specified in it matches the client’s common name in the certificate.



## Procedure

You can use either Kyma dashboard or kubectl.

-   Use Kyma dashboard.

    1.  Go to the namespace in which you want to create a `VirtualService` and `AuthorizationPolicy`.

    2.  Go to *Istio \> Virtual Services* and select *Create*.

    3.  Provide the name of the `VirtualService` resource.

    4.  In the *HTTP* section, add a route with the destination port and a host.

    5.  Go to **HTTP \> Headers \> Request \> Set** and add the following headers:


        <table>
        <tr>
        <th valign="top">

        Key
        
        </th>
        <th valign="top">

        Value
        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
        `X-CLIENT-SSL-CN`
        
        </td>
        <td valign="top">
        
        *%DOWNSTREAM\_PEER\_SUBJECT%*
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `X-CLIENT-SSL-SAN`
        
        </td>
        <td valign="top">
        
        *%DOWNSTREAM\_PEER\_URI\_SAN%*
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `X-CLIENT-SSL-ISSUER`
        
        </td>
        <td valign="top">
        
        *%DOWNSTREAM\_PEER\_ISSUER%*
        
        </td>
        </tr>
        </table>
        
    6.  In the *Host* section, add a host.

    7.  Add a Gateway.

    8.  Go to *Istio \> Authorization Policies* and select *Create*.

    9.  Provide the name of the `AuthorizationPolicy` and select the *ALLOW* action.

    10. Go to **Rule \> To \> Operation \> Hosts** and add a host in the format `{YOUR_SUBDOMAIN}.{YOUR_DOMAIN}`.

    11. Go to *Rule \> When* and add the following values:


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
        
        `key`
        
        </td>
        <td valign="top">
        
        *request.headers\[X-Client-Ssl-Cn\]*
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `values`
        
        </td>
        <td valign="top">
        
        *\["O=\{CLIENT\_CERT\_ORG\}*, *CN=\{CLIENT\_CERT\_CN\}"\]*

        Replace *\["O=\{CLIENT\_CERT\_ORG\}* with the name of your organization and *CN=\{CLIENT\_CERT\_CN\}"\]* with the common name.
        
        </td>
        </tr>
        </table>
        
    12. To call the secured endpoints of your Service, send a `GET` with the client certificate that you used to create your Gateway:

        ```
        curl --key ${CLIENT_CERT_KEY_FILE} \
              --cert ${CLIENT_CERT_CRT_FILE} \
              --cacert ${CLIENT_ROOT_CA_CRT_FILE} \
              -ik -X GET https://httpbin-vs.$DOMAIN_TO_EXPOSE_WORKLOADS/headers
        ```

        If successful, the call returns the `200 OK` response code. If you call the Service without the proper certificates or with invalid ones, you get the error `403 Forbidden`.


-   Use kubectl.

    1.  Replace the placeholders and export the following values as environment variables:

        ```
        export CLIENT_ROOT_CA_CRT_FILE=<CLIENT_ROOT_CA_CRT_FILE>
        export CLIENT_CERT_CN=<COMMON_NAME>
        export CLIENT_CERT_ORG=<ORGANIZATION>
        export CLIENT_CERT_CRT_FILE=<CLIENT_CERT_CRT_FILE>
        export CLIENT_CERT_KEY_FILE=<CLIENT_CERT_KEY_FILE>
        export NAMESPACE=<YOUR_NAMESPACE>
        export DOMAIN_NAME=<DOMAIN_TO_EXPOSE_WORKLOADS>
        export GATEWAY=<GATEWAY_NAMESPACE>/<GATEWAY_NAME>
        ```

    2.  Create VirtualService that adds the `X-CLIENT-SSL` headers to incoming requests:

        ```
        cat <<EOF | kubectl apply -f -
        apiVersion: networking.istio.io/v1alpha3
        kind: VirtualService
        metadata:
          name: httpbin-vs
          namespace: ${NAMESPACE}
        spec:
          hosts:
          - "httpbin-vs.${DOMAIN_NAME}"
          gateways:
          - ${MTLS_GATEWAY_NAME}
          http:
          - route:
            - destination:
                port:
                  number: 8000
                host: httpbin
              headers:
                request:
                  set:
                    X-CLIENT-SSL-CN: "%DOWNSTREAM_PEER_SUBJECT%"
                    X-CLIENT-SSL-SAN: "%DOWNSTREAM_PEER_URI_SAN%"
                    X-CLIENT-SSL-ISSUER: "%DOWNSTREAM_PEER_ISSUER%"
        EOF
        ```

    3.  Create AuthorizationPolicy that verifies if the request contains a client certificate:

        ```
        cat <<EOF | kubectl apply -f -
        apiVersion: security.istio.io/v1beta1
        kind: AuthorizationPolicy
        metadata:
          name: test-authz-policy
          namespace: ${NAMESPACE}
        spec:
          action: ALLOW
          rules:
          - to:
            - operation:
                hosts: ["httpbin-vs.${DOMAIN_NAME}"]
            when:
            - key: request.headers[X-Client-Ssl-Cn]
              values: ["O=${CLIENT_CERT_ORG},CN=${CLIENT_CERT_CN}"]
        EOF
        ```

    4.  To call the secured endpoints of your Service, send a `GET` with the client certificate that you used to create your Gateway:

        ```
        curl --key ${CLIENT_CERT_KEY_FILE} \
              --cert ${CLIENT_CERT_CRT_FILE} \
              --cacert ${CLIENT_ROOT_CA_CRT_FILE} \
              -ik -X GET https://httpbin-vs.$DOMAIN_TO_EXPOSE_WORKLOADS/headers
        ```

        If successful, the call returns the `200 OK` response code. If you call the Service without the proper certificates or with invalid ones, you get the error `403 Forbidden`.



