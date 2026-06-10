<!-- loiof515bd74f3a04d338a8f004f9f1b48b7 -->

# Kyma Gateway

is a preconfigured [Istio Gateway CR](https://istio.io/latest/docs/reference/config/networking/gateway/) named `kyma-gateway` located in the `kyma-system` namespace. It describes the ports and protocols exposed for a particular domain.

> ### Caution:  
> `Kyma Gateway` is not recommended for production environments. For production use, set up a custom gateway with your own domain and certificate. For more information, see [Istio Gateways](kyma-gateway-f515bd7.md).
> 
> For instructions on how to set up a custom gateway, see the following topics:
> 
> -   For TLS, see [Configure a TLS Gateway in SAP BTP, Kyma Runtime](kyma-gateway-f515bd7.md).
> -   For mutual TLS \(mTLS\), see [Mutual TLS Authentication](kyma-gateway-f515bd7.md) and [Configure mTLS Authentication in SAP BTP, Kyma Runtime](kyma-gateway-f515bd7.md).



<a name="loiof515bd74f3a04d338a8f004f9f1b48b7__section_gateway_configuration"/>

## Gateway Configuration

Kyma Gateway is configured with the following settings:

-   It listens on port *443* \(HTTPS\) using TLS mode *SIMPLE*, with a TLS credential supplied from the `kyma-gateway-certs` Secret in the `istio-system` namespace.
-   It listens on port *80* \(HTTP\) and automatically redirects all HTTP requests to HTTPS \(responds with a *301* status code\).
-   It serves all hosts matching the wildcard `*.{domain}`, where `{domain}` is the cluster domain resolved at reconciliation time. In an SAP BTP, Kyma runtime cluster, Kyma Gateway uses the Gardener Shoot domain.
-   The gateway selector targets the default Istio ingress gateway \(`app: istio-ingressgateway`, `istio: ingressgateway`\).
-   The `istio-healthz` VirtualService is reconciled in the `istio-system` namespace. It exposes the Istio readiness endpoint at `healthz.{GARDENER_SHOOT_DOMAIN}/healthz/ready` through Kyma Gateway.

![Architecture diagram showing Kyma Gateway resources in SAP BTP, Kyma Runtime. The kube-system namespace contains the shoot-info ConfigMap. The kyma-system namespace contains the kyma-gateway Istio Gateway and kyma-gateway Gardener DNSEntry. The istio-system namespace contains the kyma-tls-cert Gardener Certificate, kyma-gateway-certs Secrets, istio-ingressgateway Service, and istio-healthz VirtualService. Arrows show relationships: the ConfigMap provides cluster domain information, the DNSEntry retrieves Ingress IP from the Service, and the Certificate manages the Secrets.](images/API_Gateway_Architecture_401fe29.png)



## DNS Resolution

The cluster domain is resolved from the Gardener `shoot-info` ConfigMap. The operator creates and manages a [DNSEntry CR](https://gardener.cloud/docs/guides/networking/DNS-extension#creating-a-dnsentry-resource-explicitly) named `kyma-gateway` in the `kyma-system` namespace. The `DNSEntry` points to the external IP addresses or hostnames of the `istio-ingressgateway` LoadBalancer Service in the `istio-system` namespace.

The operator detects the IP stack of the `istio-ingressgateway` Service by inspecting the `spec.ipFamilies` field:


<table>
<tr>
<th valign="top">

IP families detected

</th>
<th valign="top">

IP stack type

</th>
<th valign="top">

Annotation set on DNSEntry

</th>
</tr>
<tr>
<td valign="top">

Single entry: `IPv4`

</td>
<td valign="top">

IPv4

</td>
<td valign="top">

**\(none\)**

</td>
</tr>
<tr>
<td valign="top">

Single entry: `IPv6`

</td>
<td valign="top">

IPv6

</td>
<td valign="top">

`dns.gardener.cloud/ip-stack: ipv6`

</td>
</tr>
<tr>
<td valign="top">

Two entries

</td>
<td valign="top">

Dual-stack

</td>
<td valign="top">

`dns.gardener.cloud/ip-stack: dual-stack`

</td>
</tr>
</table>



## Certificate Management

The operator creates and manages a [Gardener Certificate CR](https://gardener.cloud/docs/guides/networking/certificate-extension#using-the-custom-certificate-resource) named `kyma-tls-cert` in the `istio-system` namespace. The certificate covers all subdomains of the cluster domain \(`*.{domain}`\) and automatically stores the TLS data in the `kyma-gateway-certs` Secret.



## Enable or Disable Kyma Gateway

By default, Kyma Gateway is enabled. To disable it, remove the `enableKymaGateway` field from the [APIGateway CR](kyma-gateway-f515bd7.md) or set `enableKymaGateway` to *false*:

```
apiVersion: operator.kyma-project.io/v1alpha1
kind: APIGateway
metadata:
  name: default
spec:
  enableKymaGateway: false
```

When you disable Kyma Gateway or delete the APIGateway CR, the operator removes all managed resources: Gateway, DNSEntry, Certificate or certificate Secret, and VirtualService.

You can only disable Kyma Gateway if there are no APIRule or VirtualService resources in the cluster that reference `kyma-system/kyma-gateway`. If such resources exist, the operator returns a warning listing up to five of them. Remove or migrate those resources to a different gateway before disabling Kyma Gateway.

