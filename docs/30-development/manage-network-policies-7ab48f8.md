<!-- loio7ab48f8496d84bfda479ca651011d064 -->

# Manage Network Policies

Network policy support in the Istio module is disabled by default. Learn how to enable the network policy support and allow egress traffic to your workloads.



<a name="loio7ab48f8496d84bfda479ca651011d064__context_network_policies"/>

## Context

To support secure-by-default configurations, the Istio module can create network policies in the `istio-system` and `kyma-system` namespaces. These policies restrict traffic to and from Istio components so that only the required baseline communication is allowed. This helps ensure that the Istio module's components continue to function even when a deny-by-default policy is applied at the cluster or namespace level.

All module-managed policies use the following labels:

-   `kyma-project.io/module: istio`
-   `kyma-project.io/managed-by: kyma`

Do not modify these resources manually. The module updates them automatically and overwrites any manual changes.



### Networking Diagram

The following diagram illustrates the allowed traffic flows between Istio components and user workloads when network policy support is enabled.

In the diagram, network policies appear as resources that traffic flows through. In practice, a network policy is a custom resource that defines which traffic is allowed or denied, while the Istio module's components perform the actual filtering.

![Architecture diagram showing allowed traffic flows between Istio components and user workloads when network policy support is enabled. The istio-system namespace contains istio-ingressgateway, istio-egressgateway, istiod, and istio-cni-node components. Network policies control ingress and egress traffic between these Istio components and user workloads in other namespaces. Arrows indicate permitted traffic paths, including inbound HTTP/HTTPS traffic, XDS config distribution, metrics scraping, and workload-to-egressgateway routing.](images/Network_Policies_in_Istio_efdbfcf.png)



### List of Network Policies

See the list of network policies that the Istio module creates when network policy support is enabled.

**Show table**


<table>
<tr>
<th valign="top">

Component

</th>
<th valign="top">

Namespace

</th>
<th valign="top">

Port

</th>
<th valign="top">

Protocol

</th>
<th valign="top">

Direction

</th>
<th valign="top">

Source/Destination

</th>
<th valign="top">

Purpose

</th>
</tr>
<tr>
<td valign="top">

`istio-controller-manager`

</td>
<td valign="top">

`kyma-system`

</td>
<td valign="top">

`53`

</td>
<td valign="top">

UDP/TCP

</td>
<td valign="top">

Egress

</td>
<td valign="top">

destination: `*`

</td>
<td valign="top">

DNS resolution

</td>
</tr>
<tr>
<td valign="top">

`istio-controller-manager`

</td>
<td valign="top">

`kyma-system`

</td>
<td valign="top">

`443`

</td>
<td valign="top">

TCP

</td>
<td valign="top">

Egress

</td>
<td valign="top">

destination: `*`

</td>
<td valign="top">

Kubernetes API server access

</td>
</tr>
<tr>
<td valign="top">

`istiod`

</td>
<td valign="top">

`istio-system`

</td>
<td valign="top">

`53`

</td>
<td valign="top">

UDP/TCP

</td>
<td valign="top">

Egress

</td>
<td valign="top">

destination: `*`

</td>
<td valign="top">

DNS resolution

</td>
</tr>
<tr>
<td valign="top">

`istiod`

</td>
<td valign="top">

`istio-system`

</td>
<td valign="top">

`80`

</td>
<td valign="top">

TCP

</td>
<td valign="top">

Egress

</td>
<td valign="top">

destination: `*`

</td>
<td valign="top">

Access to external JWKS endpoints for JWT validation \(HTTP\)

</td>
</tr>
<tr>
<td valign="top">

`istiod`

</td>
<td valign="top">

`istio-system`

</td>
<td valign="top">

`443`

</td>
<td valign="top">

TCP

</td>
<td valign="top">

Egress

</td>
<td valign="top">

destination: `*`

</td>
<td valign="top">

Access to external JWKS endpoints for JWT validation \(HTTPS\) / Kubernetes API server access

</td>
</tr>
<tr>
<td valign="top">

`istiod`

</td>
<td valign="top">

`istio-system`

</td>
<td valign="top">

`15012`

</td>
<td valign="top">

TCP/gRPC

</td>
<td valign="top">

Ingress

</td>
<td valign="top">

source \(any of\): podSelector `security.istio.io/tlsMode: istio` \(any namespace\); podSelector `istio: ingressgateway`

</td>
<td valign="top">

XDS config distribution to sidecars and gateways

</td>
</tr>
<tr>
<td valign="top">

`istiod`

</td>
<td valign="top">

`istio-system`

</td>
<td valign="top">

`15014`

</td>
<td valign="top">

TCP/HTTP

</td>
<td valign="top">

Ingress

</td>
<td valign="top">

source \(any of\): has label `kyma-project.io/module` \(any namespace\); podSelector `networking.kyma-project.io/istio-metrics: allowed` \(any namespace\); podSelector `networking.kyma-project.io/metrics-scraping: allowed` \(any namespace\)

</td>
<td valign="top">

Control plane metrics \(Prometheus scrape\)

</td>
</tr>
<tr>
<td valign="top">

`istiod`

</td>
<td valign="top">

`istio-system`

</td>
<td valign="top">

`15017`

</td>
<td valign="top">

TCP/HTTPS

</td>
<td valign="top">

Ingress

</td>
<td valign="top">

source: `*`

</td>
<td valign="top">

Webhook endpoint \(defaulting/mutation/admission\). It is generally only accessed by the Kubernetes API server.

</td>
</tr>
<tr>
<td valign="top">

`istio-egressgateway`

</td>
<td valign="top">

`istio-system`

</td>
<td valign="top">

`*`

</td>
<td valign="top">

UDP/TCP

</td>
<td valign="top">

Egress

</td>
<td valign="top">

destination: `*`

</td>
<td valign="top">

All outbound traffic from egress is allowed, as the configuration is done via Istio resources

</td>
</tr>
<tr>
<td valign="top">

`istio-egressgateway`

</td>
<td valign="top">

`istio-system`

</td>
<td valign="top">

`*`

</td>
<td valign="top">

UDP/TCP

</td>
<td valign="top">

Ingress

</td>
<td valign="top">

source: podSelector `networking.kyma-project.io/to-egressgateway: allowed` \(any namespace\)

</td>
<td valign="top">

Traffic from labeled user Pods \(`networking.kyma-project.io/to-egressgateway: allowed`\)

</td>
</tr>
<tr>
<td valign="top">

`istio-egressgateway`

</td>
<td valign="top">

`istio-system`

</td>
<td valign="top">

`15020`

</td>
<td valign="top">

TCP/HTTP

</td>
<td valign="top">

Ingress

</td>
<td valign="top">

source \(any of\): has label `kyma-project.io/module` \(any namespace\); podSelector `networking.kyma-project.io/istio-metrics: allowed` \(any namespace\); podSelector `networking.kyma-project.io/metrics-scraping: allowed` \(any namespace\)

</td>
<td valign="top">

Merged Prometheus metrics

</td>
</tr>
<tr>
<td valign="top">

`istio-egressgateway`

</td>
<td valign="top">

`istio-system`

</td>
<td valign="top">

`15021`

</td>
<td valign="top">

TCP/HTTP

</td>
<td valign="top">

Ingress

</td>
<td valign="top">

source \(any of\): has label `kyma-project.io/module` \(any namespace\); podSelector `networking.kyma-project.io/istio-metrics: allowed` \(any namespace\); podSelector `networking.kyma-project.io/metrics-scraping: allowed` \(any namespace\)

</td>
<td valign="top">

Health check endpoint

</td>
</tr>
<tr>
<td valign="top">

`istio-egressgateway`

</td>
<td valign="top">

`istio-system`

</td>
<td valign="top">

`15090`

</td>
<td valign="top">

TCP/HTTP

</td>
<td valign="top">

Ingress

</td>
<td valign="top">

source \(any of\): has label `kyma-project.io/module` \(any namespace\); podSelector `networking.kyma-project.io/istio-metrics: allowed` \(any namespace\); podSelector `networking.kyma-project.io/metrics-scraping: allowed` \(any namespace\)

</td>
<td valign="top">

Envoy Prometheus telemetry

</td>
</tr>
<tr>
<td valign="top">

`istio-ingressgateway`

</td>
<td valign="top">

`istio-system`

</td>
<td valign="top">

`*`

</td>
<td valign="top">

TCP

</td>
<td valign="top">

Egress

</td>
<td valign="top">

destination: podSelector `networking.kyma-project.io/from-ingressgateway: allowed` \(any namespace\)

</td>
<td valign="top">

Traffic to labeled user Pods \(`networking.kyma-project.io/from-ingressgateway: allowed`\)

</td>
</tr>
<tr>
<td valign="top">

`istio-ingressgateway`

</td>
<td valign="top">

`istio-system`

</td>
<td valign="top">

`53`

</td>
<td valign="top">

UDP/TCP

</td>
<td valign="top">

Egress

</td>
<td valign="top">

destination: `*`

</td>
<td valign="top">

DNS resolution

</td>
</tr>
<tr>
<td valign="top">

`istio-ingressgateway`

</td>
<td valign="top">

`istio-system`

</td>
<td valign="top">

`8080`

</td>
<td valign="top">

TCP

</td>
<td valign="top">

Ingress

</td>
<td valign="top">

source: `*`

</td>
<td valign="top">

HTTP traffic inbound to cluster

</td>
</tr>
<tr>
<td valign="top">

`istio-ingressgateway`

</td>
<td valign="top">

`istio-system`

</td>
<td valign="top">

`8443`

</td>
<td valign="top">

TCP

</td>
<td valign="top">

Ingress

</td>
<td valign="top">

source: `*`

</td>
<td valign="top">

HTTPS traffic inbound to cluster

</td>
</tr>
<tr>
<td valign="top">

`istio-ingressgateway`

</td>
<td valign="top">

`istio-system`

</td>
<td valign="top">

`15012`

</td>
<td valign="top">

TCP/gRPC

</td>
<td valign="top">

Egress

</td>
<td valign="top">

destination: podSelector `istio: pilot`

</td>
<td valign="top">

Request XDS config from istiod

</td>
</tr>
<tr>
<td valign="top">

`istio-ingressgateway`

</td>
<td valign="top">

`istio-system`

</td>
<td valign="top">

`15020`

</td>
<td valign="top">

TCP/HTTP

</td>
<td valign="top">

Ingress

</td>
<td valign="top">

source \(any of\): has label `kyma-project.io/module` \(any namespace\); podSelector `networking.kyma-project.io/istio-metrics: allowed` \(any namespace\); podSelector `networking.kyma-project.io/metrics-scraping: allowed` \(any namespace\)

</td>
<td valign="top">

Merged Prometheus metrics

</td>
</tr>
<tr>
<td valign="top">

`istio-ingressgateway`

</td>
<td valign="top">

`istio-system`

</td>
<td valign="top">

`15021`

</td>
<td valign="top">

TCP/HTTP

</td>
<td valign="top">

Ingress

</td>
<td valign="top">

source \(any of\): has label `kyma-project.io/module` \(any namespace\); podSelector `networking.kyma-project.io/istio-metrics: allowed` \(any namespace\); podSelector `networking.kyma-project.io/metrics-scraping: allowed` \(any namespace\)

</td>
<td valign="top">

Health check endpoint

</td>
</tr>
<tr>
<td valign="top">

`istio-ingressgateway`

</td>
<td valign="top">

`istio-system`

</td>
<td valign="top">

`15090`

</td>
<td valign="top">

TCP/HTTP

</td>
<td valign="top">

Ingress

</td>
<td valign="top">

source \(any of\): has label `kyma-project.io/module` \(any namespace\); podSelector `networking.kyma-project.io/istio-metrics: allowed` \(any namespace\); podSelector `networking.kyma-project.io/metrics-scraping: allowed` \(any namespace\)

</td>
<td valign="top">

Envoy Prometheus telemetry

</td>
</tr>
<tr>
<td valign="top">

`istio-cni-node`

</td>
<td valign="top">

`istio-system`

</td>
<td valign="top">

`53`

</td>
<td valign="top">

UDP/TCP

</td>
<td valign="top">

Egress

</td>
<td valign="top">

destination: `*`

</td>
<td valign="top">

DNS resolution

</td>
</tr>
<tr>
<td valign="top">

`istio-cni-node`

</td>
<td valign="top">

`istio-system`

</td>
<td valign="top">

`443`

</td>
<td valign="top">

TCP

</td>
<td valign="top">

Egress

</td>
<td valign="top">

destination: `*`

</td>
<td valign="top">

Kubernetes API server access

</td>
</tr>
</table>



## Procedure

1.  To enable support for network policies, set the flag `networkPoliciesEnabled` to *true* in the `Istio` custom resource. This setting is disabled by default.

    ```
    apiVersion: operator.kyma-project.io/v1alpha2
    kind: Istio
    metadata:
      name: default
      namespace: kyma-system
    spec:
      networkPoliciesEnabled: true
    ```

    When the flag changes, Istio components are restarted, terminating existing TCP connections and enforcing the policies immediately.

2.  Enable egress from `istio-ingressgateway` to your workloads.

    The egress traffic from `istio-ingressgateway` to user workloads is restricted by default. To allow egress traffic from `istio-ingressgateway` to your workloads, add the label `networking.kyma-project.io/from-ingressgateway: allowed` to the Pods that should be reachable from `istio-ingressgateway`.

    See the following example workload template snippet:

    ```
    spec:
      template:
        metadata:
          labels:
            networking.kyma-project.io/from-ingressgateway: allowed
    ```

3.  Enable egress traffic from your workloads to `istio-egressgateway`.

    If you have `egressgateway` enabled and want to allow traffic from your workloads to `egressgateway`, add the label `networking.kyma-project.io/to-egressgateway: allowed` to the Pods.

    See the following example workload template snippet:

    ```
    spec:
      template:
        metadata:
          labels:
            networking.kyma-project.io/to-egressgateway: allowed
    ```

4.  Enable access to metrics and health check endpoints.

    To allow access to the metrics and health check endpoints of `istio-ingressgateway` and `istio-egressgateway`, add either of these labels to the Pods that should be able to access those endpoints:

    -   `networking.kyma-project.io/istio-metrics: allowed`
    -   `networking.kyma-project.io/metrics-scraping: allowed`

    See the following example workload template snippet:

    ```
    spec:
      template:
        metadata:
          labels:
            networking.kyma-project.io/istio-metrics: allowed
            networking.kyma-project.io/metrics-scraping: allowed
    ```

5.  Apply a deny-by-default policy.

    To isolate a workload's namespace with a deny-by-default policy, make sure to allow ingress from `istio-ingressgateway` in that policy. See an example `NetworkPolicy` resource allowing ingress from `istio-ingressgateway` to the workload:

    ```
    apiVersion: networking.k8s.io/v1
    kind: NetworkPolicy
    metadata:
        name: allow-ingress-from-istio-ingressgateway
        namespace: my-namespace
    spec:
        podSelector:
          matchLabels:
            app: my-app
        policyTypes:
        - Ingress
        ingress:
        - from:
          - namespaceSelector:
              matchLabels:
                kubernetes.io/metadata.name: istio-system
            podSelector:
              matchLabels:
                istio: ingressgateway
          ports:
            - protocol: TCP
              port: 8080 # The targetPort of the application container
    ```


