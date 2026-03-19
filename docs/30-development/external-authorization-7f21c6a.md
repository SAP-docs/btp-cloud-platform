<!-- loio7f21c6ac78be4a45a9e9a528ca3df7d3 -->

# External Authorization

Configure the `extAuth` access strategy in the `APIRule` custom resource \(CR\) to define custom authentication and authorization logic.



## Request Flow

![](images/ExtAuth_Request_Flow_d0858c0.png)

To expose a workload with an `APIRule` and an external authorizer, you need the following resources:

-   A Kyma Gateway that configures the Istio Ingress Gateway. You can use the default Kyma Gateway or define your own in any namespace. For details, see [Istio Gateways](istio-gateways-8297fa1.md).
-   An `APIRule` with the `extAuth` access strategy that references:
    -   The `Service` you want to expose.
    -   The Istio Gateway \(in this case, Kyma Gateway\) to route traffic through.
    -   An external authorization provider, configured in the `authorizers` field.


With this setup, a request is processed as follows:

1.  The client sends an HTTP request with a JWT to the exposed hostname, which enters the cluster through the Istio Ingress Gateway.
2.  Istio Ingress Gateway routes the request to the `Service` based on the `APIRule` configuration.
3.  The Istio proxy next to your application sends the authorization request to the configured external authorization provider.
4.  If the external authorization provider allows the request, the Istio proxy forwards the request to the application. If the external authorization provider denies the request, the request does not reach the application.



## Minimal Configuration

To use `extAuth`, you must first define the authorization provider in the Istio configuration, most commonly in the Istio CR. For example, the following Istio CR defines a provider named `ext-auth-provider`.

```
apiVersion: operator.kyma-project.io/v1alpha2
kind: Istio
metadata:
  name: default
  namespace: kyma-system
spec:
  config:
    authorizers:
    - headers:
        inCheck:
          include:
          - x-ext-authz
      name: ext-auth-provider
      port: 8000
      service: ext-auth-provider.provider-system.svc.cluster.local

```

Once you define the provider in the Istio configuration, you can reference it in the `APIRule` CR. This configuration allows access to the `/get` path of the `user-service` service. Based on this `APIRule`, a `CUSTOM` Istio `AuthorizationPolicy` is created with the `ext-auth-provider` provider, securing access.

```
apiVersion: gateway.kyma-project.io/v2
kind: APIRule
metadata:
  name: ext-authz
  namespace: user-system
spec:
  hosts:
    - na.example.com
  service:
    name: user-service
    port: 8000
  gateway: kyma-system/kyma-gateway
  rules:
    - path: "/get"
      methods: ["GET"]
      extAuth:
        authorizers:
        - ext-auth-provider

```



## Securing an Endpoint with `extAuth` and JWT Restrictions

The following configuration allows access to the `/get` path of the `user-service` service, as in the example in the previous section. The access is further restricted by the JWT configuration, specified in the `restrictions` field.

```
apiVersion: gateway.kyma-project.io/v2
kind: APIRule
metadata:
  name: ext-authz
  namespace: user-system
spec:
  hosts:
    - na.example.com
  service:
    name: user-service
    port: 8000
  gateway: kyma-system/kyma-gateway
  rules:
    - path: "/get"
      methods: ["GET"]
      extAuth:
        authorizers:
          - x-ext-authz
        restrictions:
          authentications:
            - issuer: https://example.com
              jwksUri: https://example.com/.well-known/jwks.json
          authorizations:
            - audiences: ["app1"]

```

