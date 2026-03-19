<!-- loio50ea52b9a129448a9a0c6080e8425db0 -->

# JWT Validation

Learn how to configure the `jwt` access strategy in an `APIRule` custom resource to secure your workload with JSON Web Tokens \(JWTs\).



## Request Flow

![](images/JWT_Validation_Request_Flow_f82c7cd.png)



To expose a workload with an APIRule and enforce JWT validation, you need the following resources:

-   A Kyma Gateway that configures the Istio Ingress Gateway. You can use the default Kyma Gateway or define your own in any namespace. For details, see [Istio Gateways](istio-gateways-8297fa1.md).
-   An APIRule with the `jwt` access strategy that references:
    -   The Service you want to expose.
    -   The Istio Gateway \(in this case, Kyma Gateway\) to route traffic through.


With this setup, a request is processed as follows:

1.  The client sends an HTTP request with a JWT to the exposed hostname, which enters the cluster through the Istio Ingress Gateway.
2.  The Istio Ingress Gateway routes the request to the `Service` selected by the `APIRule`.
3.  The Istio sidecar proxy next to your workload validates the JWT by using the issuer, JWKS URI, and other settings derived from the `APIRule`.
    -   If the token is valid and passes any configured authorization checks, the proxy forwards the request to the workload.
    -   If the token is missing or invalid, the proxy rejects the request, and it doesn't reach the application.




## Minimal Configuration

Minimal `jwt` configuration secures a path with a single issuer and JWKS URI.

In the following example, the API Gateway module only accepts JWTs issued by `https://example.com`, and Istio uses the configured `jwksUri` to fetch the public keys and verify the token signature. Because no additional authorization rules are defined, any valid token from that issuer is treated as authorized.

```
...
rules:
  - path: /headers
    methods: ["GET"]
    jwt:
      authentications:
        - issuer: https://example.com
          jwksUri: https://example.com/.well-known/jwks.json
```



## Configure Authentications

Use the `authentications` section to define where the token comes from.

By default, Istio reads the token from `Authorization: Bearer <token>`. You can override this and use custom headers or query parameters:

```
jwt:
  authentications:
    - issuer: https://example.com
      jwksUri: https://example.com/.well-known/jwks.json
      fromHeaders:
        - name: X-JWT-Assertion
          prefix: "Kyma "
      fromParameters:
        - "access_token"
```

The `authentications` section contains the following fields:

-   `issuer` – The expected value of the JWT `iss` claim.
-   `jwksUri` – The URL where Istio fetches the JWKS \(public keys\) to verify the token signature.
-   \(Optional\) `fromHeaders` – One or more HTTP headers to read the token from. Use *prefix* to remove a static prefix before parsing the token.
-   \(Optional\) `fromParameters` – One or more URL query parameter names to read the token from.

Under the hood, the `authentications` array creates a corresponding `requestPrincipals` array in Istio’s `AuthorizationPolicy`. Each entry is formatted as `<ISSUER>/*`.



## Configure Authorizations

Use the `authorizations` section to further define the token's scopes and audiences. If authorizations are not defined, a request is authorized as long as the JWT is valid for the configured issuer. If multiple authorization entries are defined, the request is allowed if at least one entry matches.

```
jwt:
  authorizations:
    - requiredScopes: ["read", "write"]
      audiences: ["app1"]
```

The `authorizations` section contains the following fields:

-   \(Optional\) `requiredScopes` – The token must contain all listed scopes in one of the `scp`, `scope`, or `scopes` claims.
-   \(Optional\) `audiences` – The token’s `aud` claim must contain all listed audiences.

