<!-- loioe7c6c6a2b47744dbaa405b422e454303 -->

# Exposing and Securing Workloads with a Certificate

Learn how to expose and secure a workload with mutual authentication using a TLS Gateway.



<a name="loioe7c6c6a2b47744dbaa405b422e454303__prereq_adk_mv3_x2c"/>

## Prerequisites

-   You have the Istio and API Gateway modules added. See [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).
-   You have access to Kyma dashboard. Alternatively, to use CLI instructions, you must install [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl) and configure it to communicate with your Kyma runtime instance. See [Access a Kyma Instance Using kubectl](access-a-kyma-instance-using-kubectl-3e25944.md).
-   You have installed [curl](https://curl.se/).
-   You have a deployed workload.

    > ### Note:  
    > To expose a workload using APIRule in version `v2`, the workload must be a part of the Istio service mesh. See [Enabling Istio Sidecar Proxy Injection](enabling-istio-sidecar-proxy-injection-b3c6f1d.md).

-   You have [set up your custom domain](https://kyma-project.io/#/api-gateway/user/tutorials/01-10-setup-custom-domain-for-workload).
-   You have set up an mTLS Gateway. See  <?sap-ot O2O class="- topic/xref " href="de2755f7b9d243b69af817836697955c.xml" text="" desc="" xtrc="xref:8" xtrf="file:/home/builder/src/dita-all/jjq1673438782153/loio2080d0faf9d84ce6aa14caa4caa32935_en-US/src/content/localization/en-us/e7c6c6a2b47744dbaa405b422e454303.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> .



<a name="loioe7c6c6a2b47744dbaa405b422e454303__context_nt4_mfw_x2c"/>

## Context

To expose and secure a workload with mutual authentication using TLS Gateway, you must create an APIRule custom resource \(CR\) that adds the `X-CLIENT-SSL` headers to incoming requests. Follow the procedure to learn how to do this.



## Procedure

You can use either Kyma dashboard or kubectl.

-   Use Kyma dashboard.

    1.  Go to *Discovery and Network \> APIRule* and select *Create*.

    2.  Add a name for your APIRule CR.

    3.  Add the name and namespace of the Gateway you want to use.

    4.  Specify the host.

    5.  Add a Rule with the following configuration:

        ****


        <table>
        <tr>
        <th valign="top">

        Parameter
        
        </th>
        <th valign="top">

        Option
        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
        `Path`
        
        </td>
        <td valign="top">
        
        */\**
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `Methods`
        
        </td>
        <td valign="top">
        
        *GET*
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `Access Strategy`
        
        </td>
        <td valign="top">
        
        *No Auth*
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `Request > Headers`
        
        </td>
        <td valign="top">
        
        Add the following key-value pairs:

        -   `X-CLIENT-SSL-CN`: *%DOWNSTREAM\_PEER\_SUBJECT%*
        -   `X-CLIENT-SSL-SAN`: *%DOWNSTREAM\_PEER\_URI\_SAN%*
        -   `X-CLIENT-SSL-ISSUER`: *%DOWNSTREAM\_PEER\_ISSUER%*


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `Service`
        
        </td>
        <td valign="top">
        
        Add the name and port of the Service you want to expose.
        
        </td>
        </tr>
        </table>
        
    6.  Choose *Create*.


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

    2.  Create APIRule CR that adds the `X-CLIENT-SSL` headers to incoming requests:

        ```
        cat <<EOF | kubectl apply -f -
        apiVersion: gateway.kyma-project.io/v2
        kind: APIRule
        metadata:
          name: {APIRULE_NAME}
          namespace: {APIRULE_NAMESPACE}
        spec:
          gateway: {GATEWAY_NAMESPACE}/{GATEWAY_NAME}
          hosts:
            - {SUBDOMAIN}.{DOMAIN}
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
            name: {SERVICE_NAME}
            port: {SERVICE_PORT}
        EOF
        ```





<a name="loioe7c6c6a2b47744dbaa405b422e454303__result_own_sc5_rfc"/>

## Results

To call the secured endpoints of your Service, send a `GET` with the client certificate that you used to create your Gateway

```
curl --key ${CLIENT_CERT_KEY_FILE} \
      --cert ${CLIENT_CERT_CRT_FILE} \
      --cacert ${CLIENT_ROOT_CA_CRT_FILE} \
      -ik -X GET https://httpbin-vs.$DOMAIN_TO_EXPOSE_WORKLOADS/headers
```

If successful, the call returns the `200 OK` response code. If you call the Service without the proper certificates or with invalid ones, you get the error `403 Forbidden`.

