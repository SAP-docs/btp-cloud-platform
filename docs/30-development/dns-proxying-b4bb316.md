<!-- loiob4bb3160a83a47a1b59ac06c5270e88c -->

# DNS Proxying

Learn how DNS proxying in Istio improves DNS resolution performance, enables external \(outside of mesh\) service resolution with `ServiceEntry` resources, and solves routing issues for external TCP services, which share the same port.



## Overview

DNS resolution is a vital component of any application infrastructure on Kubernetes. When your application code attempts to access another service in the Kubernetes cluster, or even a service on the internet, it must first look up the IP address corresponding to the service's hostname before initiating a connection to the service.

DNS proxying intercepts DNS requests from applications and resolves them locally at the Istio proxy level. The proxy maintains a local mapping of host names to IP addresses based on the Kubernetes services and `ServiceEntry` resources in the cluster. If a hostname can be resolved locally within the mesh, the proxy responds immediately. Otherwise, it forwards the request upstream following the standard DNS resolution.



## Improvements DNS Proxying Introduces



### Reduced Load on Upstream DNS

Without DNS proxying, every DNS query from workloads goes to the upstream DNS server. With DNS proxying enabled, the Istio proxy resolves known service addresses locally in the mesh, reducing traffic to the upstream DNS server.



### `ServiceEntry` Resolution

When you define a [`ServiceEntry`](https://istio.io/latest/docs/reference/config/networking/service-entry/) with a custom hostname \(for example, `address.internal`\) that the upstream DNS does not know about, applications cannot resolve these addresses without DNS proxying. DNS proxying allows the Istio proxy to resolve `ServiceEntry` hostnames directly.



### DNS Resolution for External TCP Services on the Same Port

In some cases, TCP traffic in Istio is routed based on destination IP and port only. Unlike HTTP traffic, which includes a Host header, TCP has no additional metadata for routing decisions.

For example, when multiple external TCP services share the same port \(for example, two databases on port `3306`\) and they do not have stable IP addresses, the specified `ServiceEntry` resources have resolution set to *DNS*, and Istio cannot distinguish between them. The proxy creates a single listener on `0.0.0.0:{port}` and forwards traffic to a single destination \(an external TCP service\).

DNS proxying solves this by auto-allocating virtual IPs \(VIPs\) from the `240.240.0.0/16` range to each `ServiceEntry`. This gives each external TCP service a unique address, enabling the proxy to route traffic correctly even when multiple services share the same port.



## How to Enable DNS Proxying

DNS proxying is disabled by default. You can enable it globally for the entire mesh or locally per workload. Local per-workload configuration overrides the global mesh configuration.



### Global Mesh Configuration

You can enable DNS proxying globally using the Kyma Dashboard or `kubectl`.

To enable DNS proxying using the Kyma Dashboard, perform these steps:

1.  Go to *Cluster Details* in Kyma dashboard.

2.  In the `kyma-system` namespace, go to the *Istio* section.

3.  Choose *Edit*.

4.  In the configuration, set `Enable global DNS Proxying` to *true*.

5.  Save the changes.


With kubectl, run the following command to set `enableDNSProxying` to *true* in the Istio custom resource \(CR\):

```
apiVersion: operator.kyma-project.io/v1alpha2
kind: Istio
metadata:
  name: default
  namespace: kyma-system
spec:
  config:
    enableDNSProxying: true
```

You can also use `kubectl patch`:

```
kubectl patch istio default -n kyma-system --type=merge -p '{"spec":{"config":{"enableDNSProxying":true}}}'
```

To verify the configuration, run:

```
kubectl get istio default -n kyma-system -o jsonpath='{.spec.config.enableDNSProxying}'
```

This enables DNS proxying globally for all proxies in the mesh.



### Local Per-Workload Configuration

Add the `proxy.istio.io/config` annotation to enable DNS proxying for a specific workload:

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
spec:
  template:
    metadata:
      annotations:
        proxy.istio.io/config: |
          proxyMetadata:
            ISTIO_META_DNS_CAPTURE: "true"
    spec:
      containers:
      - name: my-app
        image: my-app:latest
```

You can also use `kubectl` to add the annotation to an existing `Deployment`:

```
kubectl patch deployment my-app -p '{"spec":{"template":{"metadata":{"annotations":{"proxy.istio.io/config":"proxyMetadata:\n  ISTIO_META_DNS_CAPTURE: \"true\"\n"}}}}}'
```

To verify the annotation is applied, run:

```
kubectl get deployment my-app -o jsonpath='{.spec.template.metadata.annotations.proxy\.istio\.io/config}'
```



## Auto-Allocation of Virtual IPs

The DNS proxy additionally supports automatically allocating addresses for `ServiceEntry` resources that do not explicitly define one. When enabled, the DNS response includes a distinct and automatically assigned address for each `ServiceEntry` from the reserved Class E range \(`240.240.0.0/16`\). The proxy is then configured to match requests to this IP address and forward the request to the corresponding `ServiceEntry`.

See the following example `ServiceEntry`:

```
apiVersion: networking.istio.io/v1
kind: ServiceEntry
metadata:
  name: external-db
spec:
  hosts:
  - db.example.com
  ports:
  - number: 3306
    name: tcp
    protocol: TCP
  resolution: DNS
```

Results in DNS queries for `db.example.com` return an auto-allocated IP like `240.240.0.1` instead of the actual external IP. The proxy then routes traffic for `240.240.0.1:3306` to the resolved backend.

To opt out of auto-allocation for a specific `ServiceEntry`, add the following label:

```
metadata:
  labels:
    networking.istio.io/enable-autoallocate-ip: "false"
```

You can also use `kubectl` to add this label:

```
kubectl label serviceentry external-db networking.istio.io/enable-autoallocate-ip=false
```

***NOTE:*** Auto-allocation does not work for wildcard hosts \(for example, `*.example.com`\).



## Consequences



### Benefits

The benefits of DNS proxying include:

-   `Performance`: Reduced DNS query latency and lower load on upstream DNS.

-   `ServiceEntry` support: Applications can resolve hostnames defined in `ServiceEntry` resources.

-   TCP routing: Multiple external TCP services on the same port work correctly with auto-allocated VIPs.

-   Mesh visibility: Istio gains visibility and control over DNS resolution.




### Considerations

Consider the following aspects when using DNS proxying:

-   Non-routable IPs: Auto-allocated addresses use the `240.240.0.0/16` range. Applications that validate or log IP addresses may see unexpected values.

-   Proxy complexity: The proxy takes on DNS resolution responsibilities, slightly increasing resource usage.

-   No wildcard support: Auto-allocation does not apply to `ServiceEntry` resources with wildcard hosts.




## Related Information

For more details, see the following resources:

-   [Istio DNS Proxy documentation](https://istio.io/latest/docs/ops/configuration/traffic-management/dns-proxy/)

-   [DNS Configuration in Istio](https://istio.io/latest/docs/ops/configuration/traffic-management/dns/)

-   [Egress Traffic Control](https://istio.io/latest/docs/tasks/traffic-management/egress/egress-control/)


