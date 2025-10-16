<!-- copyf059c23874764fd1a6f5dc34d5e920c9 -->

# Exposing Workloads with Istio VirtualService

Learn how to expose a workload with Istio VirtualService.



<a name="copyf059c23874764fd1a6f5dc34d5e920c9__prereq_xhb_svl_zfc"/>

## Prerequisites

-   You have the Istio module added to your Kyma runtime instance.
-   You have a deployed workload.
-   You have set up your custom domain and a custom TLS Gateway. See [Set Up a Custom Domain](https://kyma-project.io/#/api-gateway/user/tutorials/01-10-setup-custom-domain-for-workload) and [Set Up a TLS Gateway](https://kyma-project.io/#/api-gateway/user/tutorials/01-20-set-up-tls-gateway).

    Alternatively, you can use the default domain of your Kyma cluster and the default Gateway `kyma-system/kyma-gateway`. To use the default domain and Gateway, the API Gateway module must be added to your cluster.

    > ### Tip:  
    > To get the default domain of your Kyma cluster, run the following command:
    > 
    > ```
    > kubectl get gateway -n kyma-system kyma-gateway -o jsonpath='{.spec.servers[0].hosts}'
    > ```




## Context

Kyma's API Gateway module provides the APIRule custom resource \(CR\), which is the recommended solution for securely exposing workloads. To expose a workload using an APIRule `v2`, you must include the workload in the Istio service mesh. Including a workload in the mesh brings several benefits, such as secure service-to-service communication, tracing capabilities, or traffic management. For more information, see [Purpose and Benefits of Istio Sidecar Proxies](https://help.sap.com/docs/btp/sap-business-technology-platform/istio-sidecar-proxies?version=Cloud) and [The Istio service mesh](https://istio.io/latest/about/service-mesh/).

However, if you do not need the capabilities provided by the Istio service mesh, you can expose an unsecured workload using Istio VirtualService only. Such an approach might be useful in the following scenarios:

-   If you use [Unified Gateway](https://pages.github.tools.sap/unified-gateway/) as an entry point for SAP Cloud solutions. In this case, you can configure Unified Gateway to manage API exposure, JWT validation, and routing capabilities, offloading these responsibilities from the service mesh.
-   If you want to expose front-end Services that manage their own authentication mechanisms.
-   If you require certain features or want to implement specific configurations that APIRule does not support.
-   If you require full control over Istio resources and you want to manage them directly without any higher-level abstractions.

The following instructions demonstrate a simple use case where VirtualService exposes an unsecured Service, skipping the requirement to include the Service in the Istio service mesh.



## Procedure

-   Use Kyma dashbaord

    1.  Go to the namespace in which you want to create a VirtualService resource.

    2.  Go to *Istio \> Virtual Services*.

    3.  Choose *Create* and provide the following configuration details:


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
        
        `Name`
        
        </td>
        <td valign="top">
        
        The name of the VirtualService resource you're creating.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `Hosts`
        
        </td>
        <td valign="top">
        
        The address or addresses the client uses when sending requests to the destination Service. Use the fully qualified domain name \(FQDN\) constructed with the subdomain and domain name in the following format: *\{SUBDOMAIN\}.\{DOMAIN\_NAME\}*. The hosts must be defined in the referenced Gateway.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `Gateways`
        
        </td>
        <td valign="top">
        
        The name of the Gateway you want to use and the namespace in which it is created. Use the format *\{GATEWAY\_NAMESPACE\}/\{GATEWAY\_NAME\}*.
        
        </td>
        </tr>
        </table>
        
    4.  Go to *HTTP \> Matches \> Match* and provide the following configuration details:


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
        
        `URI`
        
        </td>
        <td valign="top">
        
        Add the URI prefix used to match incoming requests. This determines which requests are routed to the specified destination Service.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `Port`
        
        </td>
        <td valign="top">
        
        This is the port number on which the destination Service is listening. It specifies where the VirtualService routes the incoming traffic. If a Service exposes only a single port it is not required to explicitly select the port.
        
        </td>
        </tr>
        </table>
        
    5.  Go to *HTTP \> Routes \> Route \> Destinations \> Host* and add the name and namespace of the Service you want to expose using the following format: *\{SERVICE\_NAME\}.\{SERVICE\_NAMESPACE\}.svc.cluster.local*. The traffic is routed to this Service.

        For more configuration options, see [Virtual Service.](https://istio.io/latest/docs/reference/config/networking/virtual-service/)

        > ### Sample Code:  
        > See a sample VirtualService configuration that directs all HTTP traffic received at `httpbin.my-domain.com` through the *my-gateway* Gateway to the [HTTPBin Service](https://github.com/istio/istio/blob/master/samples/httpbin/httpbin.yaml), which is running on port *8000* in the *default* namespace.
        > 
        > ```
        > apiVersion: networking.istio.io/v1
        > kind: VirtualService
        > metadata:
        >   name: example-vs
        >   namespace: default
        > spec:
        >   hosts:
        >     - httpbin.my-domain.com
        >   gateways:
        >     - default/my-gateway
        >   http:
        >   - match:
        >     - uri:
        >         prefix: /
        >     route:
        >     - destination:
        >         port:
        >           number: 8000
        >         host: httpbin.default.svc.cluster.local
        > ```

    6.  To verify if the Service is exposed, run the following command:

        ```
        curl -s -I https://{SUBDOMAIN}.{DOMAIN_NAME}/
        ```

        If successful, you get code ***200*** in response.


-   Use kubectl

    1.  To expose a workload using VirtualService, replace the placeholders and run the following command:


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
        
        `{NAME}`
        
        </td>
        <td valign="top">
        
        The name of the VirtualService resource you're creating.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `{NAMESPACE}`
        
        </td>
        <td valign="top">
        
        The namespace in which you want to create the VirtualService resource.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `{SUBDOMAIN}.{DOMAIN_NAME}`
        
        </td>
        <td valign="top">
        
        The address or addresses the client uses when sending requests to the destination Service. Use the fully qualified domain name \(FQDN\) constructed with the subdomain and domain name in the following format: *\{SUBDOMAIN\}.\{DOMAIN\_NAME\}*. The hosts must be defined in the referenced Gateway.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `{GATEWAY_NAMESPACE}/{GATEWAY_NAME}`
        
        </td>
        <td valign="top">
        
        The name of the Gateway you want to use and the namespace in which it is created.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `{URI_PREFIX}`
        
        </td>
        <td valign="top">
        
        The URI prefix used to match incoming requests. This determines which requests are routed to the specified destination Service.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `{PORT_NUMBER}`
        
        </td>
        <td valign="top">
        
        This is the port number on which the destination Service is listening. It specifies where the VirtualService routes incoming requests. If a Service exposes only a single port it is not required to explicitly select the port.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        `{SERVICE_NAME}.{SERVICE_NAMESPACE}`
        
        </td>
        <td valign="top">
        
        The name and namespace of the Service you want to expose. The requests are routed to this Service.
        
        </td>
        </tr>
        </table>
        
        For more configuration options, see [Virtual Service.](https://istio.io/latest/docs/reference/config/networking/virtual-service/)

        ```
        cat <<EOF | kubectl apply -f -
        apiVersion: networking.istio.io/v1
        kind: VirtualService
        metadata:
          name: {VS_NAME}
          namespace: {VS_NAMESPACE}
        spec:
          hosts:
            - {SUBDOMAIN}.{DOMAIN_NAME}
          gateways:
            - {GATEWAY_NAMESPACE}/{GATEWAY_NAME}
          http:
          - match:
            - uri:
                prefix: {URI_PREFIX}
            route:
            - destination:
                port:
                  number: {PORT_NUMBER}
                host: {SERVICE_NAME}.{SERVICE_NAMESPACE}.svc.cluster.local
        ```

        > ### Sample Code:  
        > See a sample VirtualService configuration that directs all HTTP traffic received at `httpbin.my-domain.com` through the *my-gateway* Gateway to the [HTTPBin Service](https://github.com/istio/istio/blob/master/samples/httpbin/httpbin.yaml), which is running on port *8000* in the *default* namespace.
        > 
        > ```
        > apiVersion: networking.istio.io/v1
        > kind: VirtualService
        > metadata:
        >   name: example-vs
        >   namespace: default
        > spec:
        >   hosts:
        >     - httpbin.my-domain.com
        >   gateways:
        >     - default/my-gateway
        >   http:
        >   - match:
        >     - uri:
        >         prefix: /
        >     route:
        >     - destination:
        >         port:
        >           number: 8000
        >         host: httpbin.default.svc.cluster.local
        > ```

    2.  To verify if the Service is exposed, run the following command:

        ```
        curl -s -I https://{SUBDOMAIN}.{DOMAIN_NAME}/
        ```

        If successful, you get code ***200*** in response.



