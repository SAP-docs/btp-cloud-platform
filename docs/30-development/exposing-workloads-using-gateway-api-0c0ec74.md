<!-- loio0c0ec74470114a6da55e44131d89e60a -->

# Exposing Workloads Using Gateway API

Use [Gateway API](https://gateway-api.sigs.k8s.io/) to expose your workload.



<a name="loio0c0ec74470114a6da55e44131d89e60a__prereq_zvp_5j4_xcc"/>

## Prerequisites

-   You have the Istio module added. See [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).
-   You have a deployed workload.

> ### Caution:  
> Exposing an unsecured workload to the outside world is a potential security vulnerability, so be careful. If you want to use this example in a production environment, make sure to secure your workload.



## Procedure

1.  Export the following values as environment variables:

    ```
    export NAMESAPCE={service-namespace}
    export BACKENDNAME={service-name}
    export PORT={service-port}
    ```


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
    
    **NAMESAPCE**
    
    </td>
    <td valign="top">
    
    The name of the backend service.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **BACKENDNAME**
    
    </td>
    <td valign="top">
    
    The name of the backend service that you want to use for routing the incoming HTTP traffic.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **PORT**
    
    </td>
    <td valign="top">
    
    The port number of the backend server to which requests should be forwarded.
    
    </td>
    </tr>
    </table>
    
2.  Install Gateway API CustomResourceDefinitions \(CRDs\) from the standard channel.

    ```
    kubectl get crd gateways.gateway.networking.k8s.io &> /dev/null || \
    { kubectl kustomize "github.com/kubernetes-sigs/gateway-api/config/crd?ref=v1.1.0" | kubectl apply -f -; }
    ```

    > ### Note:  
    > If you’ve already installed Gateway API CRDs from the experimental channel, you must delete them before installing Gateway API CRDs from the standard channel.

3.  Create a Kubernetes Gateway to deploy Istio Ingress Gateway.

    ```
    cat <<EOF | kubectl apply -f -
    apiVersion: gateway.networking.k8s.io/v1
    kind: Gateway
    metadata:
      name: gateway
      namespace: ${NAMESPACE}
    spec:
      gatewayClassName: istio
      listeners:
      - name: http
        hostname: "your-domain.kyma.example.com"
        port: 80
        protocol: HTTP
        allowedRoutes:
          namespaces:
            from: Same
    EOF
    ```

    This command deploys the Istio Ingress service in your namespace with the corresponding Kubernetes Service of type `LoadBalanced` and an assigned external IP address.

4.  Create an HTTPRoute to configure access to your workload:

    ```
    cat <<EOF | kubectl apply -f -
    apiVersion: gateway.networking.k8s.io/v1
    kind: HTTPRoute
    metadata:
      name: httproute
      namespace: ${NAMESPACE}
    spec:
      parentRefs:
      - name: gateway
      hostnames: ["your-domain.kyma.example.com"]
      rules:
      - matches:
        - path:
            type: PathPrefix
            value: /headers
        backendRefs:
        - name: ${BACKENDNAME}
          namespace: ${NAMESPACE}
          port: ${PORT}
    EOF
    ```




<a name="loio0c0ec74470114a6da55e44131d89e60a__result_tdr_3y5_xcc"/>

## Results

You've exposed your workload. To access it, follow the steps:

1.  Discover Istio Ingress Gateway’s IP and port.

    ```
    export INGRESS_HOST=$(kubectl get gtw gateway -n $NAMESPACE -o jsonpath='{.status.addresses[0].value}')
    export INGRESS_PORT=$(kubectl get gtw gateway -n $NAMESPACE -o jsonpath='{.spec.listeners[?(@.name=="http")].port}')
    ```

2.  Call the service.

    ```
    curl -s -I -HHost:your-domain.kyma.example.com "http://$INGRESS_HOST:$INGRESS_PORT/headers"
    
    ```

    > ### Note:  
    > This task assumes there’s no DNS setup for the `httpbin.kyma.example.com` host, so the call contains the host header.


