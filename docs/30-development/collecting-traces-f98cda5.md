<!-- loiof98cda5d058e48ff808ade541a64a6ad -->

# Collecting Traces

With the Telemetry module, you can collect distributed traces to understand the flow of requests through your applications and infrastructure. To begin collecting traces, you create a `TracePipeline` resource. It automatically collects OTLP traces and can be configured to collect traces from the Istio service mesh.



<a name="loiof98cda5d058e48ff808ade541a64a6ad__section_traces_overview"/>

## Overview

A `TracePipeline` is a Kubernetes custom resource \(CR\) that configures trace collection for your cluster. When you create a `TracePipeline`, it automatically provisions a trace gateway that provides a central OTLP endpoint receiving traces pushed from applications \(for details, see [Traces Architecture](traces-architecture-5f650d7.md)\).

The pipeline enriches all collected traces with Kubernetes metadata before sending them to your chosen backend.

Trace collection is optional. If you don't create a `TracePipeline`, the trace gateway is not deployed.



<a name="loiof98cda5d058e48ff808ade541a64a6ad__section__kyma_traces_prerequisites"/>

## Prerequisites

For the recording of a distributed trace, every involved component must propagate at least the trace context. For details, see [Trace Context](https://www.w3.org/TR/trace-context/#problem-statement).

-   In Kyma, all modules involved in users’ requests support the [W3C Trace Context](https://www.w3.org/TR/trace-context/) protocol. The involved Kyma modules are, for example, Istio, Serverless, and Eventing.

-   Your application also must propagate the W3C Trace Context for any user-related activity. This can be achieved easily using the [Open Telemetry SDKs](https://opentelemetry.io/docs/languages/) available for all common programming languages. If your application follows that guidance and is part of the Istio Service Mesh, it’s already outlined with dedicated span data in the trace data collected by the Kyma telemetry setup.

-   Furthermore, your application must enrich a trace with additional span data and send these data to the cluster-central telemetry services. You can achieve this with [Open Telemetry SDKs](https://opentelemetry.io/docs/instrumentation/).




With the default configuration, the trace gateway collects push-based OTLP traces of any container running in Kyma runtime, and the data is shipped to your backend.



<a name="loiof98cda5d058e48ff808ade541a64a6ad__section_traces_minimal_pipeline"/>

## Minimal TracePipeline

For a minimal setup, you only need to create a `TracePipeline` that specifies your backend destination \(see [Integrate With Your OTLP Backend](integrate-with-your-otlp-backend-e726417.md)\):

```
apiVersion: telemetry.kyma-project.io/v1alpha1
kind: TracePipeline
metadata:
  name: backend
output:
    otlp:
      endpoint:
        value: http://<myEndpoint>:4317
```

By default, this minimal pipeline collects push-based OTLP traces of any container running in Kyma runtime.

It activates cluster-internal endpoints to receive traces in the OTLP format. Applications can push traces directly to these URLs:

-   gRPC: `http://telemetry-otlp-traces.kyma-system:4317`
-   HTTP: `http://telemetry-otlp-traces.kyma-system:4318`



<a name="loiof98cda5d058e48ff808ade541a64a6ad__section_traces_configuration"/>

## Configure Trace Collection

You can adjust the `TracePipeline` using runtime configuration with the available parameters and attributes \(see [TracePipeline: Custom Resource Parameters](https://kyma-project.io/#/telemetry-manager/user/resources/04-tracepipeline?id=custom-resource-parameters)\).

-   If you use Istio, activate Istio tracing. For details, see [Configure Istio Tracing](configure-istio-tracing-3f504d8.md). You can adjust which percentage of the trace data is collected.

-   The Serverless module integrates the [OpenTelemetry SDK](https://opentelemetry.io/docs/specs/otel/metrics/sdk/) by default. It automatically propagates the trace context for chained calls and reports custom spans for incoming and outgoing requests. You can add more spans within your Function's source code. For details, see [Customize Function Traces](https://kyma-project.io/external-content/serverless/docs/user/tutorials/01-100-customize-function-traces.html).

-   The Eventing module uses the [CloudEvents](https://cloudevents.io/) protocol, which natively supports [W3C Trace Context](https://www.w3.org/TR/trace-context/) propagation. It ensures that the trace context is passed along but doesn't enrich a trace with more advanced span data.




<a name="loiof98cda5d058e48ff808ade541a64a6ad__section_kyma_traces_limitations"/>

## Limitations

-   **Throughput**: Assuming an average span with 40 attributes with 64 characters, the maximum throughput is 4200 span/sec ~= 15.000.000 spans/hour. If this limit is exceeded, spans are refused. To increase the maximum throughput, manually scale out the gateway by increasing the number of replicas for the trace gateway. For details, see [Telemetry CRD](https://kyma-project.io/#/telemetry-manager/user/resources/01-telemetry).

-   **Unavailability of Output**: For up to 5 minutes, a retry for data is attempted when the destination is unavailable. After that, data is dropped.

-   **No Guaranteed Delivery**: The used buffers are volatile. If the OTel Collector instance crashes, trace data can be lost.

-   **Multiple TracePipeline Support**: The maximum amount of `TracePipeline` resources is 5.

-   **System Span Filtering**: System-related spans reported by Istio are filtered out without the opt-out option, for example:

    -   Any communication of applications to the Telemetry gateways

    -   Any communication from the gateways to backends



