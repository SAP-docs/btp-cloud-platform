<!-- loio04d79d5517204da68029f43b9f052396 -->

# Telemetry Manager

As the core element of the Telemetry module, Telemetry Manager manages the lifecycle of other Telemetry module components by watching user-created resources.



<a name="loio04d79d5517204da68029f43b9f052396__section_telemetry_module_lifecycle"/>

## Module Lifecycle

The Telemetry module includes Telemetry Manager, a Kubernetes [operator](https://kubernetes.io/docs/concepts/extend-kubernetes/operator/) that's described by a custom resource of type `Telemetry`. Telemetry Manager has the following tasks:

1.  Watch the module configuration for changes and sync the module status to it.

2.  Watch for the user-created Kubernetes resources `LogPipeline`, `TracePipeline`, and `MetricPipeline`. In these resources, you specify what data of a signal type to collect and where to ship it.

3.  Manage the lifecycle of the self monitor and the user-configured agents and gateways. For example, only if you defined a LogPipeline resource, the Fluent Bit DaemonSet is deployed as log agent.


![](images/Telemetry_Manager_196e666.svg)



<a name="loio04d79d5517204da68029f43b9f052396__section_wb3_snq_fcc"/>

## Self Monitor

The Telemetry module contains a self monitor, based on [Prometheus](https://prometheus.io/), to collect and evaluate metrics from the managed gateways and agents. Telemetry Manager retrieves the current pipeline health from the self monitor and adjusts the status of the pipeline resources and the module status.

Additionally, you can monitor the health of your pipelines in an integrated backend like SAP Cloud Logging: To set up alerts and reports in the backend, use the pipeline health metrics emitted by your `MetricPipeline`. For details, see [Setting up a MetricPipeline](metrics-44ac6c5.md#loio44ac6c5afef0464480fa18acb7483972__section_kyma_metrics_metricpipeline_setup), step *Monitor Pipeline Health*, as well as [Integrate with SAP Cloud Logging](integrate-with-sap-cloud-logging-eac5771.md).

![](images/Telemetry_Manager_Architecture_ad71283.svg)



<a name="loio04d79d5517204da68029f43b9f052396__section_telemetry_module_configuration"/>

## Module Configuration and Status

For configuration options and the overall status of the module, see the specification of the related [Telemetry resource](https://kyma-project.io/#/telemetry-manager/user/resources/01-telemetry).

