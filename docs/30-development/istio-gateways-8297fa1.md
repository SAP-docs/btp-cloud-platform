<!-- loio8297fa15c2054fdb8c1570a2af41c4c4 -->

# Istio Gateways

Learn what Istio Gateways are, why you might need a custom Gateway, and how to choose the right Gateway configuration for your use case in Kyma.



## **What is a Gateway?**

> ### Note:  
> This document refers to Istio Gateway custom resources, which are Istio-specific and use VirtualServices for routing. This is different from the Kubernetes Gateway API, which is a vendor-neutral standard also supported by the Istio module. To learn more about Gateway API, see the [Kubernetes Gateway API documentation](https://gateway-api.sigs.k8s.io/) and [Exposing Workloads Using Gateway API](https://kyma-project.io/external-content/istio/docs/user/tutorials/01-20-expose-httbin-gateway-api.html).

A Gateway manages inbound and outbound traffic for the service mesh. It acts as a load balancer operating at the edge of the mesh, receiving incoming HTTP/HTTPS connections.

The Gateway performs the following functions:

-   Decrypts incoming HTTPS traffic and encrypts responses.
-   Directs requests to the appropriate services based on traffic redirection rules.
-   Applies authentication, authorization, and traffic management rules in a centralized location.
-   Acts as the entry point for traffic from outside the cluster to reach services inside.



## Choosing Istio Ingress Gateway Configuration

To configure an Istio Ingress Gateway, choose the domain type \(your cluster's default domain or your own custom domain\) and the TLS mode \(simple TLS or mTLS\). These choices determine the setup steps in Kyma. See the following matrix:

****


<table>
<tr>
<th valign="top">

TLS mode \\ Domain name

</th>
<th valign="top">

Default Kyma domain

</th>
<th valign="top">

Custom domain

</th>
</tr>
<tr>
<td valign="top">

TLS

</td>
<td valign="top">

-   Default Kyma Gateway `kyma-system/kyma-gateway` - pre-configured and ready to use for quick start and development.

    > ### Caution:  
    > Because the default Kyma domain is a wildcard domain, which uses a simple TLS Gateway, it is recommended that you set up your custom domain for use in a production environment.

-   Custom TLS Gateway on the default Kyma domain - Gateway isolation with minimal setup and no DNS configuration required.

    For configuration procedure, see [Configure a TLS Gateway: Kyma Domain Scenario](configure-a-tls-gateway-87a874c.md#loio87a874c616e04740a14235acff6597a3__task_m5h_srj_vhc).




</td>
<td valign="top">

Custom TLS Gateway on your custom domain - recommended for production environments, provides full control over the domain name.

For configuration procedure, see [Configure a TLS Gateway: Custom Domain Scenario](configure-a-tls-gateway-87a874c.md#loio87a874c616e04740a14235acff6597a3__task_fc1_4rj_vhc).

</td>
</tr>
<tr>
<td valign="top">

mTLS

</td>
<td valign="top">

Custom mTLS Gateway on the default Kyma domain - secure B2B APIs with client authentication, no DNS configuration required.

For configuration procedure, see [Configure an mTLS Gateway: Kyma Domain Scenario](configure-an-mtls-gateway-e7c6c6a.md#loioe7c6c6a2b47744dbaa405b422e454303__task_m2p_3zl_dhc).

</td>
<td valign="top">

Custom mTLS Gateway on your custom domain - recommended for production B2B APIs integrations, provides strongest security with full control over domain name.

For configuration procedure, see [Configure an mTLS Gateway: Custom Domain Scenario](configure-an-mtls-gateway-e7c6c6a.md#loioe7c6c6a2b47744dbaa405b422e454303__h5l_rnt_wgc).

</td>
</tr>
</table>



### Domain Name

A Gateway host is the domain name or hostname that the Gateway listens on to accept incoming traffic. It defines which domain names the Gateway responds to. As for the domain name, you can choose from the following options:

-   Use your custom domain.

    To use a custom domain, you must own the DNS zone and supply credentials for a provider supported by Gardener so the ACME DNS challenge can be completed. For this, you must first register this DNS provider in your Kyma runtime cluster and create a DNS entry resource.

-   Use the default domain of your Kyma cluster.

    When you create an SAP BTP, Kyma runtime instance, your cluster receives a default wildcard domain that provides the endpoint for the Kubernetes API server. This is the primary access point for all cluster management operations, used by kubectl and other tools.

    By default, the default Ingress Gateway `kyma-gateway` is configured under this domain. To learn what the domain is, you can check the APIServer URL in your subaccount overview, or get the domain name from the default simple TLS Gateway:

    ```
    kubectl get gateway -n kyma-system kyma-gateway -o jsonpath='{.spec.servers[0].hosts[0]}'
    ```

    You can request any subdomain of the assigned default domain and use it to create a TLS or mTLS Gateway, as long as it is not used by another resource. For example, if your default domain is `*.c12345.kyma.ondemand.com` you can use such subdomains as `example.c12345.kyma.ondemand.com`, `*.example.c12345.kyma.ondemand.com`, and more. If you use the Kyma runtime default domain, Gardener’s issuer can issue certificates for subdomains of that domain without additional DNS delegation.




### TLS Mode

You can either use simple TLS or mTLS:

-   Use simple TLS.

    In TLS mode, the server presents a certificate to prove its identity to clients, but clients don't need to provide certificates. This is the most common configuration for public-facing websites and APIs.

-   Use mTLS.

    In mTLS mode, both the server and client present certificates to verify each other's identity. This provides stronger authentication by ensuring only clients with valid certificates can connect.




### Additional Configuration Options

For additional configuration options, see [Gateway](https://istio.io/latest/docs/reference/config/networking/gateway/#Gateway).

