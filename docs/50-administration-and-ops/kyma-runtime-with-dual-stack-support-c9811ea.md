<!-- loioc9811ea2a1bf411987c8cfc5b323a95b -->

# Kyma Runtime with Dual-Stack Support

Learn how to apply dual-stack support in Kyma instances.



<a name="loioc9811ea2a1bf411987c8cfc5b323a95b__section_pby_2rm_3hc"/>

## Context

SAP BTP, Kyma runtime can support both Internet Protocol \(IP\) versions, IPv4 and IPv6, simultaneously \(dual stack\), when deployed on Google Cloud and Amazon Web Services IaaS providers. Compared to IPv4, IPv6 offers a significantly greater number of unique IP addresses, which enhances network flexibility. To retrieve support for both Internet protocols, create your Kyma runtime with dual-stack support enabled.

The dual-stack feature is only available for newly created Kyma instances. Existing instances are limited to IPv4.

> ### Caution:  
> The Kyma Istio module does not support dual-stack mode. Any traffic sent or received through the IPv6 network is not part of the Istio service mesh. Consequently, the Istio module does not protect IPv6 traffic, either by transparent encryption or by offering additional security mechanisms \(for example, authentication\).



<a name="loioc9811ea2a1bf411987c8cfc5b323a95b__section_nbq_xj4_3hc"/>

## Procedure

Create a service instance of type `LoadBalancer` in your Kyma cluster. In the service manifest, add the `ipFamilyPolicy` field with the value *RequireDualStack*, and add the value *IPv6* in the `ipFamilies` field.

```
apiVersion: v1
kind: Service
...
spec:
  ipFamilyPolicy: RequireDualStack
  ipFamilies:
    - IPv6
    - IPv4
...
```

In your Kyma cluster with dual-stack support, each deployed Pod automatically receives two IP addresses: IPv4 and IPv6.

**Related Information**  


[Creating an IPv4/IPv6 \(dual-stack\) Ingress](https://gardener.cloud/docs/guides/networking/dual-stack-ipv4-ipv6-ingress-aws/#creating-an-ipv4-ipv6-dual-stack-ingress)

