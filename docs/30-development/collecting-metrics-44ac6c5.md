<!-- loio44ac6c5afef0464480fa18acb7483972 -->

# Collecting Metrics

With the Telemetry module, you can collect metrics from your workloads and Kubernetes resources to monitor their health, performance, and behavior. To begin collecting metrics, you create a `MetricPipeline` resource. You can collect Prometheus, Istio, and runtime metrics.



<a name="loio44ac6c5afef0464480fa18acb7483972__section_metrics_overview"/>

## Overview

A `MetricPipeline` is a Kubernetes custom resource \(CR\) that configures metric collection for your cluster. When you create a `MetricPipeline`, it automatically provisions the necessary components \(for details, see [Metrics Architecture](metrics-architecture-59d31e9.md)\):

-   A metric gateway that provides a central OTLP endpoint for receiving metrics pushed from applications.
-   A metric agent that runs on each cluster node to pull \(scrape\) metrics from applications and Kubernetes resources.

The pipeline enriches all collected metrics with Kubernetes metadata. It also transforms non-OTLP formats \(like Prometheus\) into the OTLP standard before sending them to your chosen backend.

Metric collection is optional. If you don't create a `MetricPipeline`, the metric collection components are not deployed.



<a name="loio44ac6c5afef0464480fa18acb7483972__section_kyma_metrics_prerequisites"/>

## Prerequisites

-   Before you can collect metrics data from a component, it must expose \(or instrument\) the metrics. Typically, it instruments specific metrics for the used language runtime \(like Node.js\) and custom metrics specific to the business logic. Also, the exposure can be in different formats, like the pull-based Prometheus format or the [push-based OTLP format](https://opentelemetry.io/docs/specs/otlp/).

-   If you want to use Prometheus-based metrics, you must have instrumented your application using a library like the [Prometheus client library](https://prometheus.io/docs/instrumenting/clientlibs/), with a port in your workload exposed serving as a Prometheus metrics endpoint.

-   If you want to scrape the metric endpoint with Istio, your Service `port` definition must define the app protocol. For details, see [Scrape Metrics from Istio-enabled Workloads](collect-prometheus-metrics-0afa66a.md#loio0afa66a49c2c4cd294b19529eaad8dec__section_enable_istio_scraping).

-   For the instrumentation, you typically use an SDK, namely the [Prometheus client libraries](https://prometheus.io/docs/instrumenting/clientlibs/) or the [Open Telemetry SDKs](https://opentelemetry.io/docs/languages/). Both libraries provide extensions to activate language-specific auto-instrumentation like for Node.js, and an API to implement custom instrumentation.




<a name="loio44ac6c5afef0464480fa18acb7483972__section_metrics_minimal_pipeline"/>

## Minimal MetricPipeline

For a minimal setup, you only need to create a `MetricPipeline` that specifies your backend destination \(see [Integrate With Your OTLP Backend](integrate-with-your-otlp-backend-e726417.md)\):

```
apiVersion: telemetry.kyma-project.io/v1beta1
kind: MetricPipeline
metadata:
  name: backend
output:
    otlp:
      endpoint:
        value: http://myEndpoint:4317
```

By default, this minimal pipeline collects the following types of metrics:

-   OTLP Metrics: Activates cluster-internal endpoints to receive metrics in the OTLP format. Your applications can push metrics directly to these URLs:

    -   gRPC: `http://telemetry-otlp-metrics.kyma-system:4317`

    -   HTTP: `http://telemetry-otlp-metrics.kyma-system:4318`


-   Health Metrics: Collects health and performance metrics about the Telemetry module's components. This input is always active and cannot be disabled. For details, see [Monitor Pipeline Health](monitor-pipeline-health-b56ed5c.md).


To collect metrics from Kyma modules like Istio, Eventing, or Serverless, enable additional inputs.



<a name="loio44ac6c5afef0464480fa18acb7483972__section_metrics_configuration"/>

## Configure Metrics Collection

You can adjust the `MetricPipeline` using runtime configuration with the available parameters \(see [MetricPipeline: Custom Resource Parameters](https://kyma-project.io/#/telemetry-manager/user/resources/05-metricpipeline?id=custom-resource-parameters)\).

-   Scrape `prometheus` metrics from applications that expose a Prometheus-compatible endpoint \(see [Collect Prometheus Metrics](collect-prometheus-metrics-0afa66a.md)\).

-   Collect `istio` service mesh metrics from Istio proxies and control plane components \(see [Collect Istio Metrics](collect-istio-metrics-aa786e0.md)\).

-   Collect `runtime` resource usage and status metrics from Kubernetes components like Pods, Nodes, and Deployments \(see [Collect Runtime Metrics](collect-runtime-metrics-2c9fb6e.md)\).

-   Use diagnostic metrics to debug your `prometheus` and `istio` configuration.

-   Choose from which specific namespaces you want to include or exclude metrics \(see [Filter Metrics](filter-metrics-6bd4bfd.md)\).

-   Avoid redundancy by dropping push-based OTLP metrics that are sent directly to the metric gateway \(see [Route Specific Inputs to Different Backends](set-up-the-otlp-input-61567b7.md#loio61567b79e6db41cd81de5f58ec077201__section_filter_input_for_backends)\).




<a name="loio44ac6c5afef0464480fa18acb7483972__section_kyma_metrics_limitations"/>

## Limitations

-   **Throughput**: Assuming an average metric with 20 metric data points and 10 labels, the default metric **gateway** setup has a maximum throughput of 34K metric data points/sec. If more data is sent to the gateway, it is refused. To increase the maximum throughput, manually scale out the gateway by increasing the number of replicas for the metric gateway \(see [Telemetry CRD](https://kyma-project.io/#/telemetry-manager/user/resources/01-telemetry)\).

    The metric **agent** setup has a maximum throughput of 14K metric data points/sec per instance. If more data must be ingested, it is refused. If a metric data endpoint emits more than 50.000 metric data points per scrape loop, the metric agent refuses all the data.

-   **Load Balancing With Istio**: To ensure availability, the metric gateway runs with multiple instances. If you want to increase the maximum throughput, use manual scaling and enter a higher number of instances.

    By design, the connections to the gateway are long-living connections \(because OTLP is based on gRPC and HTTP/2\). For optimal scaling of the gateway, the clients or applications must balance the connections across the available instances, which is automatically achieved if you use an Istio sidecar. If your application has no Istio sidecar, the data is always sent to one instance of the gateway.

-   **Unavailability of Output**: For up to 5 minutes, a retry for data is attempted when the destination is unavailable. After that, data is dropped.

-   **No Guaranteed Delivery**: The used buffers are volatile. If the gateway or agent instances crash, metric data can be lost.

-   **Multiple MetricPipeline Support**: The maximum amount of `MetricPipeline` resources is 5.


