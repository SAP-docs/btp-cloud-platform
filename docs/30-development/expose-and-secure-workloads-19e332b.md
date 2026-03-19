<!-- loio19e332b59c084a928d4117b1f0d53d9b -->

# Expose and Secure Workloads

Use APIRules to expose and secure your workloads in Kyma.

When you expose a workload in Kyma, you make a Kubernetes Service reachable from outside the cluster. By default, workloads run only inside the cluster. To allow external clients \(applications, tools, or users in a browser\) to call a workload, you publish it under a host name such as `myapp.example.com`, decide which paths and HTTP methods can be called \(for example, `GET /headers`\), and choose whether the endpoint is open or requires authentication.



## What Is an APIRule?

An APIRule is a Kyma custom resource that describes how a workload is exposed.

You use an APIRule to define the following:

-   Which host names are used.
-   Which Services and ports receive the traffic.
-   Which paths and HTTP methods are allowed.
-   Which access strategy is used \(`noAuth`, `jwt`, or `extAuth`\).

The API Gateway module watches APIRules and translates them into Istio configuration, such as `VirtualService` and `AuthorizationPolicy` objects. This means you don't need to create these Istio objects yourself.

For a detailed field description, see [APIRule Custom Resource](https://kyma-project.io/external-content/api-gateway/docs/user/custom-resources/apirule/README.html).



## APIRule Capabilities

With an APIRule, you can configure the following options:

-   Choose an access strategy per path:

    -   `jwt` – Protect an endpoint with JSON Web Tokens. See [JWT Validation](jwt-validation-50ea52b.md).
    -   `extAuth` – Delegate authentication and authorization to an external provider. See [External Authorization](external-authorization-7f21c6a.md).
    -   `noAuth` – Expose an endpoint without authentication. See [noAuth Configuration](noauth-configuration-c4fddf6.md).

    > ### Recommendation:  
    > For most common scenarios, it's recommended to use the **jwt** access strategy as it provides built‑in, token‑based authentication and authorization without requiring additional infrastructure.
    > 
    > The **extAuth** access strategy allows you to provide your custom authorization and authentication logic. Use this access strategy when the built-in Istio JWT authentication and authorization mechanisms don't meet your specific requirements, and you want to offload the logic to a custom external service.
    > 
    > Use **noAuth** for endpoints that must remain openly accessible. This setup is suitable for development and testing environments where security requirements are lower and quick access to services is necessary, or when the data being accessed isn't sensitive and doesn't require strict security measures.

-   Use short host names instead of full domain names. The domain suffix is taken from the referenced Istio Gateway. See [Using a Short Host Name](using-a-short-host-name-dec7a0b.md).
-   Expose multiple workloads on the same host and route traffic to different Services based on paths and HTTP methods. See [Expose Multiple Workloads on the Same Host](expose-multiple-workloads-on-the-same-host-ac66329.md).
-   Expose and secure workloads with mTLS by using an APIRule together with an mTLS-enabled Istio Gateway. See [Configure an mTLS Gateway](configure-an-mtls-gateway-e7c6c6a.md).

You can combine these options in a single APIRule. For example, you can expose several Services under one host, protect some paths with `jwt` or `extAuth`, and leave public status and health check endpoints open with `noAuth`.



## Exposing Workloads with Istio

In most scenarios, using APIRules to expose and secure workloads is recommended. However, you can also configure access with Istio resources directly, for example, if you need to manage Istio configuration yourself or require a feature that APIRule does not yet support.

See the following topics:

-   [Restricting IP-Based Access](restricting-ip-based-access-8eccd49.md)
-   [Exposing Workloads with Istio VirtualService](exposing-workloads-with-istio-virtualservice-5484296.md) 

