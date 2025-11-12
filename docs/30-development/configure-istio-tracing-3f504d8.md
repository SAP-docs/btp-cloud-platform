<!-- loio3f504d838f7841d19aac71baaa1801e9 -->

# Configure Istio Tracing

To get an end-to-end view of requests in your service mesh, configure Istio to send trace data. The `TracePipeline` receives these traces through its default OTLP input. You can adjust the sampling rate and apply settings to specific namespaces or workloads.



<a name="loio3f504d838f7841d19aac71baaa1801e9__section_prerequisites"/>

## Prerequisites

-   You have the Istio module in your cluster. See [Adding and Deleting a Kyma Module](../50-administration-and-ops/adding-and-deleting-a-kyma-module-1b548e9.md#loio1b548e9ad4744b978b8b595288b0cb5c).
-   You have access to Kyma dashboard. Alternatively, if you prefer CLI, you need [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl) and [curl](https://curl.se/).



<a name="loio3f504d838f7841d19aac71baaa1801e9__section_istio_tracing_context"/>

## Context

By default, Istio traces are disabled because they can generate a high volume of data. To collect them, you create an Istio `Telemetry` resource in the `istio-system` namespace. When you enable this feature, the Istio proxy sidecars automatically propagate the trace context and report spans for traffic between your services.

The Istio module provides a preconfigured [extension provider](https://istio.io/latest/docs/tasks/observability/telemetry/) called `kyma-traces` to send this data to the Telemetry module's trace gateway.

Istio plays a key role in distributed tracing. Its [Ingress Gateway](https://istio.io/latest/docs/tasks/traffic-management/ingress/ingress-control/) is typically where external requests enter your cluster. If a request doesn't have a trace context, Istio adds it. Furthermore, every component within the Istio service mesh runs an Istio proxy, which propagates the trace context and creates span data. When you enable Istio tracing, and it manages trace propagation in your application, you get a complete picture of a trace, because every component automatically contributes span data. Also, Istio tracing is preconfigured to use the vendor-neutral [W3C Trace Context](https://www.w3.org/TR/trace-context/) protocol.

> ### Caution:  
> Enabling Istio traces can significantly increase data volume and might quickly consume your trace storage. Start with a low sampling rate in production environments.



<a name="loio3f504d838f7841d19aac71baaa1801e9__section_traces_entire_mesh"/>

## Enable Istio Tracing for the Entire Mesh

To enable tracing for all workloads in the service mesh, apply an Istio `Telemetry` resource to the `istio-system` namespace. Use this option to establish a baseline configuration for your mesh.

> ### Note:  
> You can only have one mesh-wide Istio `Telemetry` resource in the `istio-system` namespace. If you also want to configure Istio access logs, combine both configurations into a single resource \(see [Configure Istio Access Logs](configure-istio-access-logs-808c167.md)\).

The following example enables tracing with a default sampling rate of 1%:

```
apiVersion: telemetry.istio.io/v1
kind: Telemetry
metadata:
  name: mesh-default
  namespace: istio-system
spec:
  tracing:
  - providers:
    - name: "kyma-traces"
    randomSamplingPercentage: 1.00
```

> ### Tip:  
> After setting a mesh-wide default in the `istio-system` namespace, you can apply more specific tracing configurations for an entire namespace or for individual workloads within a namespace. This is useful for debugging a particular service by increasing its sampling rate without affecting the entire mesh. For details, see [Filter Traces](filter-traces-6a03a1b.md).



<a name="loio3f504d838f7841d19aac71baaa1801e9__section_configure_sampling_rate"/>

## Configure the Sampling Rate

By default, Istio samples 1% of traces to reduce data volume. To change it, set the `randomSamplingPercentage` value. The sampling decision is propagated within the trace context to ensure that either all or no spans for a given trace are reported.

> ### Note:  
> For production environments, a low sampling rate \(1–5%\) is recommended to manage costs and performance. For development or debugging, you can set it to 100.00 to capture every trace.

```
apiVersion: telemetry.istio.io/v1
kind: Telemetry
metadata:
  name: mesh-default
  namespace: istio-system
spec:
  tracing:
  - providers:
    - name: "kyma-traces"
    randomSamplingPercentage: 5.00 # Samples 5% of all traces
```



<a name="loio3f504d838f7841d19aac71baaa1801e9__section_propagate_tracecontext_without_spans"/>

## Propagate Trace Context Without Reporting Spans

In some cases, you may want Istio to propagate the W3C Trace Context for context-aware logging but not report any trace spans. This approach enriches your access logs with `traceId` and `spanId` without the overhead of full distributed tracing.

To achieve this, set `randomSamplingPercentage` to `0.00` in your mesh-wide configuration.

> ### Tip:  
> For guidance on Istio access logs, see [Configure Istio Access Logs](configure-istio-access-logs-808c167.md).

```
apiVersion: telemetry.istio.io/v1
kind: Telemetry
metadata:
  name: mesh-default
  namespace: istio-system
spec:
  tracing:
  - providers:
    - name: "kyma-traces"
    randomSamplingPercentage: 0
```

