<!-- loio77eb15cc136a40968f9119f183d66c92 -->

# Istio Trust Domain

Configure a trust domain to align identities across multiple clusters, enable seamless multi-mesh mTLS communication with shared root CAs, and match your organizational naming standards.



## What Is a Trust Domain?

A trust domain defines the security boundary of a service mesh. The trust domain becomes part of each proxy identity and is embedded into the Subject Alternative Name \(SAN\) of workload certificates.

Istio uses Secure Production Identity Framework For Everyone \(SPIFFE\) identities in the following format:

```
spiffe://<trust-domain>/ns/<namespace>/sa/<service-account>
```

By default, Istio uses the trust domain `cluster.local`. You can override this default to align identities across clusters or to match organizational naming standards.



## Configure a Trust Domain in the Istio Custom Resource

Set the trust domain under `spec.config.trustDomain` in the Istio custom resource \(CR\). When you don't specify this field, the default value `cluster.local` is used.

```
apiVersion: operator.kyma-project.io/v1alpha2
kind: Istio
metadata:
  name: default
  namespace: kyma-system
spec:
  config:
    trustDomain: "example.com"
```



## Where Does the Trust Domain Appear?

The trust domain appears in the following key contexts:

-   Istio proxy identity certificate: The trust domain is included in the SAN of the certificate issued to every Istio proxy in the mesh.
-   AuthorizationPolicies: When you define AuthorizationPolicies, you can use either the default value `cluster.local` or your custom trust domain in the SPIFFE IDs to specify the workloads to which the policy applies.



## Multi-Mesh Seamless mTLS Communication

If a shared Root CA is configured to issue proxy certificates in multiple meshes \(see [Configure Istio Certificate Authority \(CA\) with Custom Certificates](configure-istio-certificate-authority-ca-with-custom-certificates-00b052c.md)\), you can use a Gateway with `tls.mode: ISTIO_MUTUAL` to seamlessly allow mTLS communication between them. In this case, you don't need to manually set up mTLS for the Gateway.

Additionally, you can use the trust domain to differentiate the source of requests in the upstream mesh \(whether they come from within the same mesh or from another mesh\). This is possible because the SPIFFE ID in the client certificate includes the trust domain of the originating mesh.

To configure this setup, you can use the following example Gateway configuration in the target mesh:

```
apiVersion: networking.istio.io/v1alpha3
kind: Gateway
metadata:
  name: multi-mesh-gateway
  namespace: istio-system
spec:
  selector:
    istio: ingressgateway
  servers:
  - port:
      number: 443
      name: https
      protocol: HTTPS
    tls:
      mode: ISTIO_MUTUAL
    hosts:
    - "*.example-target.com"
```

In the source mesh, configure a ServiceEntry and DestinationRule to direct traffic to the target mesh with mTLS. See the following example:

```
apiVersion: networking.istio.io/v1
kind: ServiceEntry
metadata:
  name: external-httpbin
spec:
  hosts:
    - "httpbin.example-target.com"
  ports:
    - number: 80
      name: http
      protocol: HTTP
      targetPort: 443
  resolution: DNS
  location: MESH_EXTERNAL
---
apiVersion: networking.istio.io/v1
kind: DestinationRule
metadata:
  name: external-httpbin-mtls
spec:
  host: "httpbin.example-target.com"
  trafficPolicy:
    tls:
      mode: ISTIO_MUTUAL
```



## Migration Considerations

Changing the trust domain is a sensitive operation. After you update the trust domain, existing workloads may fail authentication until they receive new certificates.

The default `cluster.local` value is treated as a special case that is compatible with custom trust domains. This means that setting the trust domain from `cluster.local` to a new, custom value doesn't cause authentication failures for existing workloads until they restart and receive new certificates with the updated trust domain.

However, you should still plan the change carefully and perform it during a maintenance window to minimize disruption. For a detailed migration guide, see [Trust Domain Migration](https://istio.io/latest/docs/tasks/security/authorization/authz-td-migration).

**Related Information**  


[Istio trust domain migration](https://istio.io/latest/docs/tasks/security/authorization/authz-td-migration/)

[Istio mesh configuration reference](https://istio.io/latest/docs/reference/config/istio.mesh.v1alpha1/)

[SPIFFE trust domain specification](https://github.com/spiffe/spiffe/blob/main/standards/SPIFFE-ID.md#21-trust-domain)

