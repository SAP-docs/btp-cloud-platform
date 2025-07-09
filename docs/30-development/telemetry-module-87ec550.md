<!-- loio87ec55072f394ac48d91c8c723e26e3b -->

# Telemetry Module

Learn more about the Telemetry Module. Use it to enable observability for your application.



<a name="loio87ec55072f394ac48d91c8c723e26e3b__section_telemetry_what_is"/>

## What Is Telemetry?

Fundamentally, “Observability” is a measure of how well the application’s external outputs can reflect the internal states of single components. The insights that an application and the surrounding infrastructure expose are displayed in the form of metrics, traces, and logs - collectively, that’s called “telemetry” or “[signals](https://opentelemetry.io/docs/concepts/signals/)”. These can be exposed by employing modern instrumentation.

![](images/telemetry-stages_352d704.svg)

1.  In order to implement Day-2 operations for a distributed application running in a container runtime, the single components of an application must expose these signals by employing modern instrumentation.

2.  Furthermore, the signals must be collected and enriched with the infrastructural metadata in order to ship them to a target system.

3.  Instead of providing a one-size-for-all backend solution, the Telemetry module supports you with instrumenting and shipping your telemetry data in a vendor-neutral way.

4.  This way, you can conveniently enable observability for your application by integrating it into your existing or desired backends. Pick your favorite among many observability backends \(available either as a service or as a self-manageable solution\) that focus on different aspects and scenarios.


The Telemetry module focuses exactly on the aspects of instrumentation, collection, and shipment that happen in the runtime and explicitly defocuses on backends.

> ### Tip:  
> An enterprise-grade setup demands a central solution outside the cluster, so we recommend in-cluster solutions only for testing purposes. If you want to install lightweight in-cluster backends for demo or development purposes, see [Integration Guides](telemetry-module-87ec550.md#loio87ec55072f394ac48d91c8c723e26e3b__section_telemetry_integration).



<a name="loio87ec55072f394ac48d91c8c723e26e3b__section_telemetry_features"/>

## Features

To support telemetry for your applications, the Telemetry module provides the following features:

-   Tooling for collection, filtering, and shipment: Based on the [Open Telemetry Collector](https://opentelemetry.io/docs/collector/) and [Fluent Bit](https://fluentbit.io/), you can configure basic pipelines to filter and ship telemetry data.

-   Integration in a vendor-neutral way to a vendor-specific observability system \(traces and metrics only\): Based on the [OpenTelemetry protocol \(OTLP\)](https://opentelemetry.io/docs/specs/otel/protocol/), you can integrate backend systems.

-   Guidance for the instrumentation \(traces and metrics only\): Based on [Open Telemetry](https://opentelemetry.io/), you get community samples on how to instrument your code using the [Open Telemetry SDKs](https://opentelemetry.io/docs/languages/) in nearly every programming language.

-   Enriching telemetry data by automatically adding common attributes. This is done in compliance with established semantic conventions, ensuring that the enriched data adheres to industry best practices and is more meaningful for analysis. For details, see [Data Enrichment](telemetry-gateways-61567b7.md#loio61567b79e6db41cd81de5f58ec077201__section_telemetry_data_enrichment).

-   Opt-out of features for advanced scenarios: At any time, you can opt out for each data type, and use custom tooling to collect and ship the telemetry data.

-   SAP BTP as first-class integration: Integration into SAP BTP Observability services, such as SAP Cloud Logging, is prioritized. For more information, see [Integrate with SAP Cloud Logging](integrate-with-sap-cloud-logging-eac5771.md).




<a name="loio87ec55072f394ac48d91c8c723e26e3b__section_telemetry_scope"/>

## Scope

The Telemetry module focuses only on the signals of application logs, distributed traces, and metrics. Other kinds of signals are not considered. Also, audit logs are not in scope.

Supported integration scenarios are neutral to the vendor of the target system.



<a name="loio87ec55072f394ac48d91c8c723e26e3b__section_telemetry_architecture"/>

## Architecture

![](images/Telemetry_Architecture_ff3f9de.svg)



### Telemetry Manager

The Telemetry module ships Telemetry Manager as its core component. Telemetry Manager is a Kubernetes [operator](https://kubernetes.io/docs/concepts/extend-kubernetes/operator/) that implements the Kubernetes controller pattern and manages the whole lifecycle of all other components covered in the Telemetry module. Telemetry Manager watches for the user-created Kubernetes resources: `LogPipeline`, `TracePipeline`, and `MetricPipeline`. In these resources, you specify what data of a signal type to collect and where to ship it. If Telemetry Manager detects a configuration, it deploys the related gateway and agent components accordingly and keeps them in sync with the requested pipeline definition.

For more information, see [Telemetry Manager](telemetry-manager-04d79d5.md).



### Gateways

The Traces and Metrics features share the common approach of providing a gateway based on the [OTel Collector](https://opentelemetry.io/docs/collector/). It acts as a central point in the cluster to push data in the OTLP format. From here, the data is enriched and filtered and then dispatched as defined in the individual pipeline resources.

For more information, see [Telemetry Gateways](telemetry-gateways-61567b7.md).



### Log Agent

The log agent is based on a [Fluent Bit](https://fluentbit.io/) installation running as a [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/). It reads all containers’ logs in the runtime and ships them according to a `LogPipeline` configuration.

For more information, see [Application Logs \(Fluent Bit\)](application-logs-fluent-bit-1287132.md).



### Trace Gateway

The trace gateway is based on an [OTel Collector](https://opentelemetry.io/docs/collector/) [Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/). The gateway provides an [OTLP](https://opentelemetry.io/docs/specs/otel/protocol/)-based endpoint to which applications can push the trace signals. According to a `TracePipeline` configuration, the gateway processes and ships the trace data to a target system.

For more information, see [Traces](traces-f98cda5.md) and [Telemetry Gateways](telemetry-gateways-61567b7.md).



### Metric Gateway/Agent

The metric gateway and agent are based on an [OTel Collector](https://opentelemetry.io/docs/collector/) [Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) and a [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/). The gateway provides an [OTLP](https://opentelemetry.io/docs/specs/otel/protocol/)-based endpoint to which applications can push the metric signals. The agent scrapes annotated Prometheus-based workloads. According to a `MetricPipeline` configuration, the gateway processes and ships the metric data to a target system.

For more information, see [Metrics](metrics-44ac6c5.md) and [Telemetry Gateways](telemetry-gateways-61567b7.md).



<a name="loio87ec55072f394ac48d91c8c723e26e3b__section_telemetry_integration"/>

## Integration Guides

To learn about integration with SAP Cloud Logging, read [Integrate with SAP Cloud Logging](integrate-with-sap-cloud-logging-eac5771.md).

For integration with other backends, such as Dynatrace, or to learn how to collect data from applications based on the OpenTelemetry Demo App, see [Integration Guides](https://kyma-project.io/#/telemetry-manager/user/integration/README).



<a name="loio87ec55072f394ac48d91c8c723e26e3b__section_telemetry_crd"/>

## API / Custom Resource Definitions

The API of the Telemetry module is based on Kubernetes Custom Resource Definitions \(CRD\), which extend the Kubernetes API with custom additions. To inspect the specification of the Telemetry module API, see:

-   [Telemetry CRD](https://kyma-project.io/#/telemetry-manager/user/resources/01-telemetry)

-   [LogPipeline CRD](https://kyma-project.io/#/telemetry-manager/user/resources/02-logpipeline)

-   [TracePipeline CRD](https://kyma-project.io/#/telemetry-manager/user/resources/04-tracepipeline)

-   [MetricPipeline CRD](https://kyma-project.io/#/telemetry-manager/user/resources/05-metricpipeline)




<a name="loio87ec55072f394ac48d91c8c723e26e3b__section_telemetry_resource_consumption"/>

## Resource Consumption

To learn more about the resources used by the Telemetry module, see [Telemetry](../50-administration-and-ops/kyma-modules-sizing-3a92490.md#loio3a924906857b4f01969cb684ccd25309__section_telemetry).

