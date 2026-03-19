<!-- loioac66329f84bd460d9e9db761983190fb -->

# Expose Multiple Workloads on the Same Host

Expose multiple backend workloads under a single host by routing traffic to different Services.

There are two primary patterns for configuring multiple workloads on the same host: [Path-Level Service Definition](expose-multiple-workloads-on-the-same-host-ac66329.md#loioac66329f84bd460d9e9db761983190fb__path-level-definition) and [Root-Level Service with Overrides](expose-multiple-workloads-on-the-same-host-ac66329.md#loioac66329f84bd460d9e9db761983190fb__root-level-definiton). Additionally, you can expose Services deployed in different namespaces. See [Cross-Namespace Service Exposure](expose-multiple-workloads-on-the-same-host-ac66329.md#loioac66329f84bd460d9e9db761983190fb__cross-namespace-service-exposure).



<a name="loioac66329f84bd460d9e9db761983190fb__path-level-definition"/>

## Path-Level Service Definition

In this pattern, each path explicitly declares which Service it routes to. You define all Service configurations at the `spec.rules` level, with no default Service defined at the root.

-   Explicit routing - each path clearly states its target Service
-   No default fallback behavior
-   Maximum clarity and predictability
-   Ideal when Services are unrelated or follow different architectural patterns

```
spec:
  rules:
    - path: /headers
      service:
        name: service-a
    - path: /get
      service:
        name: service-b

```



<a name="loioac66329f84bd460d9e9db761983190fb__root-level-definiton"/>

## Root-Level Service with Overrides

This pattern defines a default Service at the root level \(`spec.service`\), which applies to all paths unless explicitly overridden. Individual rules can specify alternative Services that take precedence over the root definition.

-   Default Service handles most traffic \(with exceptions\)
-   Selective overrides for specific paths
-   Reduces configuration verbosity when most paths use the same Service

> ### Note:  
> When both root-level and rule-level Services are defined, the rule-level Service takes precedence.

```
spec:
  service:
    name: primary-service
  rules:
    - path: /headers
    - path: /admin
      service:
        name: admin-service

```



<a name="loioac66329f84bd460d9e9db761983190fb__cross-namespace-service-exposure"/>

## Cross-Namespace Service Exposure

When exposing Services, each Service referenced in the rules can be in a different namespace. To expose a Service deployed in a different namespace from the `APIRule` resource itself, specify its namespace in the field `service.namespace`.

```
spec:
  rules:
    - path: /headers
      service:
        name: service-a
        namespace: ns-a
    - path: /get
      service:
        name: service-b
        namespace: ns-b

```



## Example

This example demonstrates all configuration patterns in a single `APIRule`, showing how to expose multiple workloads on one host.

1.  Create namespaces with enabled Istio sidecar proxy injection.

    ```
    kubectl create ns httpbin-a
    kubectl label namespace httpbin-a istio-injection=enabled --overwrite
    kubectl create ns httpbin-b
    kubectl label namespace httpbin-b istio-injection=enabled --overwrite
    kubectl create ns apirule
    kubectl label namespace apirule istio-injection=enabled --overwrite
    
    ```

2.  Get the default domain of your project "Kyma" cluster.

    ```
    PARENT_DOMAIN=$(kubectl get gateway -n kyma-system kyma-gateway -o jsonpath='{.spec.servers[0].hosts[0]}' | sed 's/\*\.//')
    
    ```

3.  Deploy two sample HTTPBin Services in different namespaces.

    ```
    kubectl apply -n httpbin-a -f https://raw.githubusercontent.com/istio/istio/master/samples/httpbin/httpbin.yaml
    kubectl apply -n httpbin-b -f https://raw.githubusercontent.com/istio/istio/master/samples/httpbin/httpbin.yaml
    
    ```

4.  Create an `APIRule`:

    > ### Caution:  
    > Exposing a workload to the outside world is always a potential security vulnerability, so be careful. In a production environment, remember to secure the workload you expose with `jwt` or `extAuth`.

    ```
    cat <<EOF | kubectl -n apirule apply -f -
    apiVersion: gateway.kyma-project.io/v2
    kind: APIRule
    metadata:
      name: multi-workload
    spec:
      hosts:
        - test.${PARENT_DOMAIN}
      gateway: kyma-system/kyma-gateway
      service:
        name: httpbin
        namespace: httpbin-a
        port: 8000
      rules:
        - path: /headers    # Default: routes to httpbin-a service
          methods: ["GET"]
          noAuth: true       
        - path: /ip     # Override: routes to httpbin-b service
          methods: ["GET"]
          noAuth: true
          service:
            name: httpbin
            namespace: httpbin-b
            port: 8000
    EOF
    
    ```

5.  Test the connection:

    -   Call default service.

        ```
        curl -ik https://test.${PARENT_DOMAIN}/headers
        
        ```

    -   Call the override service.

        ```
        curl -ik https://test.${PARENT_DOMAIN}/ip
        
        ```


    If successful, each request returns a ***200 OK*** response from its respective service.


