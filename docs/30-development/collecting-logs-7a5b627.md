<!-- loio7a5b6275e55744c9a2b89ec154144486 -->

# Collecting Logs

With the Telemetry module, you can observe and debug your applications by collecting, processing, and exporting logs. To begin collecting logs, you create a `LogPipeline` resource. It automatically collects OTLP logs and application logs from the `stdout/stderr` channel. You can also activate Istio log collection.



<a name="loio7a5b6275e55744c9a2b89ec154144486__section_section_logs_overview"/>

## Overview

A `LogPipeline` is a Kubernetes custom resource \(CR\) that configures log collection for your cluster. When you create a `LogPipeline`, the Telemetry Manager automatically deploys the necessary components \(for details, see [Logs Architecture](logs-architecture-9124dfd.md)\):

-   A log gateway that provides a central OTLP endpoint for receiving logs pushed from your applications.

-   A log agent that runs on each cluster node to collect logs written to `stdout` and `stderr` by your application containers.


The pipeline enriches all collected logs with Kubernetes metadata and transforms them into the OTLP format before sending them to your chosen backend.

The log collection feature is optional. If you don't create a `LogPipeline`, the log collection components are not deployed.



<a name="loio7a5b6275e55744c9a2b89ec154144486__section_logs_prerequisites"/>

## Prerequisites

-   Before you can collect logs from a component, it must emit the logs. Typically, it uses a logger framework for the used language runtime \(like Node.js\) and prints them to the `stdout` or `stderr` channel \(see [Kubernetes: How nodes handle container logs](https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/#customresourcedefinitions)\). Alternatively, you can use the [OTel SDK](https://opentelemetry.io/docs/languages/) to use the [push-based OTLP format](https://opentelemetry.io/docs/specs/otlp/).

-   If you want to emit the logs to the `stdout/stderr` channel, use structured logs in a JSON format with a logger library like log4J. With that, the log agent can parse your log and enrich all JSON attributes as log attributes, and a backend can use that.

-   If you prefer the push-based alternative with OTLP, also use a logger library like log4J. However, you must additionally instrument that logger and bridge it to the OTel SDK. For details, see [OpenTelemetry: New First-Party Application Logs](https://opentelemetry.io/docs/specs/otel/logs/#new-first-party-application-logs).




<a name="loio7a5b6275e55744c9a2b89ec154144486__section_logs_minimal_pipeline"/>

## Minimal LogPipeline

For a minimal setup, you only need to create a `LogPipeline` that specifies your backend destination \(see [Integrate With Your OTLP Backend](integrate-with-your-otlp-backend-e726417.md)\):

```
apiVersion: telemetry.kyma-project.io/v1beta1
kind: LogPipeline
metadata:
  name: backend
output:
    otlp:
      endpoint:
        value: http://<myEndpoint>:4317
```

By default, this minimal pipeline enables the following types of log collection:

-   Application logs: Collects `stdout` and `stderr` logs from all containers running in non-system namespaces \(such as `kyma-system` and `kube-system`\).

-   OTLP logs: Activates cluster-internal endpoints to receive logs in the OTLP format. Your applications can push logs directly to these URLs:

    -   gRPC: `http://telemetry-otlp-logs.kyma-system:4317`

    -   HTTP: `http://telemetry-otlp-logs.kyma-system:4318`





<a name="loio7a5b6275e55744c9a2b89ec154144486__section_logs_configuration"/>

## Configure Log Collection

You can customize your `LogPipeline` using the available parameters and attributes \(see [LogPipeline: Custom Resource Parameters](https://kyma-project.io/#/telemetry-manager/user/resources/02-logpipeline?id=custom-resource-parameters)\):

-   Configure or disable the collection of `application` logs from the `stdout/stderr` channel \(see [Configure Application Logs](configure-application-logs-412866b.md)\).

-   Set up the collection of Istio access logs \(see [Configure Istio Access Logs](configure-istio-access-logs-808c167.md)\).

-   Choose from which specific namespaces you want to include or exclude logs \(see [Filter Logs](filter-logs-58445a0.md)\).

-   If you have more than one backend, specify which input source sends logs to which backend \(see [Route Specific Inputs to Different Backends](set-up-the-otlp-input-61567b7.md#loio61567b79e6db41cd81de5f58ec077201__section_filter_input_for_backends)\).




<a name="loio7a5b6275e55744c9a2b89ec154144486__section_logs_limitations"/>

## Limitations

-   **Throughput**:

    -   When pushing OTLP logs of an average size of 2KB to the log gateway, using its default configuration \(two instances\), the Telemetry module can process approximately 12,000 logs per second \(LPS\). To ensure availability, the log gateway runs with multiple instances. For higher throughput, manually scale out the gateway by increasing the number of replicas \(see [Telemetry CRD](https://kyma-project.io/#/telemetry-manager/user/resources/01-telemetry)\). Ensure that the chosen scaling factor does not exceed the maximum throughput of the backend, as it may refuse logs if the rate is too high.

    -   For example, to scale out the gateway for scenarios like a `Large` instance of SAP Cloud Logging \(up to 30,000 LPS\), you can raise the throughput to about 20,000 LPS by increasing the number of replicas to 4 instances.

    -   The log agent, running one instance per node, handles tailing logs from `stdout` using the `runtime` input. When writing logs of an average size of 2KB to `stdout`, a single log agent instance can process approximately 9,000 LPS.


-   **Load Balancing With Istio**: By design, the connections to the gateway are long-living connections \(because OTLP is based on gRPC and HTTP/2\). For optimal scaling of the gateway, the clients or applications must balance the connections across the available instances, which is automatically achieved if you use an Istio sidecar. If your application has no Istio sidecar, the data is always sent to one instance of the gateway.

-   **Unavailability of Output**: For up to 5 minutes, a retry for data is attempted when the destination is unavailable. After that, data is dropped.

-   **No Guaranteed Delivery**: The used buffers are volatile. If the gateway or agent instances crash, logs data can be lost.

-   **Multiple `LogPipeline` Support**: The maximum amount of `LogPipeline` resources is 5.


