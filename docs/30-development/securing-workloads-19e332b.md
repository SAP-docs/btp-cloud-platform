<!-- loio19e332b59c084a928d4117b1f0d53d9b -->

# Securing Workloads

Choose a security configuration for exposing your workload.

The APIRule custom resource \(CR\), installed by the API Gateway module, allows you to define the security configuration for an exposed endpoint using the concept of access strategies. The APIRule `v2` supports the following access strategies:

-   `jwt`
-   `extAuth`
-   `noAuth`

> ### Note:  
> To expose a workload using APIRule in version `v2`, the workload must be a part of the Istio service mesh. See [Enabling Istio Sidecar Proxy Injection](enabling-istio-sidecar-proxy-injection-b3c6f1d.md).

Furthermore, you can expose a workload using Istio VirtualService and restrict access based on the caller's IP, or configure Istio VirtualService and AuthorizationPolicy to enable mutual TLS \(mTLS\) authentication and validate access based on client certificate.

Read about each method to decide which one to use.

> ### Recommendation:  
> For most common scenarios, it is best to configure the `jwt` access strategy within the APIRule CR.



## Use the APIRule CR with the `jwt` Access Strategy

The `jwt` access strategy allows you to secure your workload with HTTPS using Istio JWT configuration. It offers a secure and efficient method for protecting your services and interacting with them using JSON Web Tokens \(JWTs\). This approach is highly recommended if you aim to secure your workloads without the need to implement custom authentication and authorization logic.

See [Expose and Secure a Workload with a JWT Using SAP Cloud Identity Services](expose-and-secure-a-workload-with-a-jwt-using-sap-cloud-identity-services-44bb2d3.md#loio44bb2d3596554bf4b94ea344e40937dd).



<a name="loio19e332b59c084a928d4117b1f0d53d9b__section_c1k_5mk_3fc"/>

## Use the APIRule CR with the `extAuth` Access Strategy

The `extAuth` access strategy allows you to provide your custom authorization and authentication logic. Use this access strategy when the built-in Istio JWT authentication and authorization mechanisms do not meet your specific requirements, and you want to offload the logic to a custom external service. It provides flexibility and the ability to tailor security to your application's specific needs.

To use the `extAuth` access strategy, you must first define the authorization provider in the Istio configuration, most commonly in the Istio custom resource \(CR\). Once you define the provider in the Istio configuration, you can reference it in the APIRule CR, specifying which endpoints and methods should be protected by this provider.

See [Expose and Secure a Workload with OAuth2 Proxy External Authorizer \(Client Credentials Flow\)](expose-and-secure-a-workload-with-oauth2-proxy-external-authorizer-client-credentials-flo-4dea5d5.md).



<a name="loio19e332b59c084a928d4117b1f0d53d9b__section_hyn_5mk_3fc"/>

## Use the APIRule CR with the `noAuth` Access Strategy

The `noAuth` access strategy provides a simple configuration for exposing workloads. Use it when you simply need to expose your workloads and allow access to specific HTTP methods without any authentication or authorization checks. This setup is suitable for development and testing environments where security requirements are lower and quick access to services is necessary, or when the data being accessed is not sensitive and does not require strict security measures.

> ### Caution:  
> Exposing a workload to the outside world is a potential security vulnerability, so be careful. In a production environment, always secure the workload you expose.

See [Exposing Workloads with noAuth](exposing-workloads-with-noauth-8b48971.md).



<a name="loio19e332b59c084a928d4117b1f0d53d9b__section_icf_ymk_3fc"/>

## Restrict IP-Based Access with Istio VirtualService and XFF Header

Applying IP-based access restriction is recommended when you want to limit access to a specific workload to a set of trusted IP addresses, or to prevent unauthorized access from certain IP addresses. By using the XFF header, you can ensure that requests are only coming from trusted sources, and block or allow access based on the originating IP address contained in the XFF header.

Using the XFF header is only supported when you expose your workload with Istio VirtualService instead of the APIRule CR.

See [Using the XFF Header to Configure IP-Based Access to a Workload](using-the-xff-header-to-configure-ip-based-access-to-a-workload-8eccd49.md).



<a name="loio19e332b59c084a928d4117b1f0d53d9b__section_ibg_ymk_3fc"/>

## Secure a Workload Using a Certificate

After you have set up an mTLS Gateway, you can use a certificate to enforce mutual authentication and ensure only authorized clients can access the workload. This adds an extra layer of security to your application by providing an encrypted communication channel between the client and the server, while also guaranteeing the authenticity of both parties involved in the communication.

To secure your workload with a certificate, you must create an Istio AuthorizationPolicy and VirtualService instead of the APIRule CR.

See [Configure an mTLS Gateway](configure-an-mtls-gateway-e7c6c6a.md).

