<!-- loio412866b422904f35841fbea7a66d5291 -->

# Configure Application Logs

To collect logs that your applications write to `stdout` and `stderr`, create a `LogPipeline`. The `runtime` input is enabled by default and uses an agent on each node to tail container log files. You can control which namespaces and containers to include or exclude.



<a name="loio412866b422904f35841fbea7a66d5291__section_prerequisites"/>

## Prerequisites

-   You have the Telemetry module in your cluster.
-   You have access to Kyma dashboard. Alternatively, if you prefer CLI, you need [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl).



<a name="loio412866b422904f35841fbea7a66d5291__section_context"/>

## Context

Use the `runtime` input section to restrict or specify which resources you want to include. You can define the namespaces to include in the input collection, exclude namespaces from the input collection, or choose that only system namespaces are included. For details, see [LogPipeline: Custom Resource Parameters](https://kyma-project.io/#/telemetry-manager/user/resources/02-logpipeline?id=custom-resource-parameters).

When you apply the `LogPipeline` resource to your Kubernetes cluster, a log agent is deployed and starts collecting the log data, transforms them to OTLP, and sends them to your backend. For details, see [Transformation to OTLP Logs](transformation-to-otlp-logs-d013ab9.md).



<a name="loio412866b422904f35841fbea7a66d5291__section_disable_log_collection"/>

## Enable or Disable Log Collection

The `runtime` input is enabled by default. To create a pipeline that only accepts logs pushed with OTLP, you can disable it.

```
  ...
  input:
    runtime:
      enabled: false     # Default is true
```

By default, input is collected from all namespaces, except the system namespaces `kube-system`, `istio-system`, `kyma-system`, which are excluded by default.

> ### Tip:  
> To select logs from specific namespaces and containers, or to include system namespaces, see [Filter Logs](filter-logs-58445a0.md).



<a name="loio412866b422904f35841fbea7a66d5291__section_discard_original_log_body"/>

## Discard the Original Log Body

By default, the log agent preserves the original JSON log message by moving it to the `attributes."log.original"` field after parsing. For details, see [Transformation to OTLP Logs](transformation-to-otlp-logs-d013ab9.md).

To reduce data volume, you can disable this behavior. Set the parameter to `false` to discard the original JSON string after its contents are parsed into attributes.

```
...
  input:
    runtime:
      keepOriginalBody: false     # Default is true
```

