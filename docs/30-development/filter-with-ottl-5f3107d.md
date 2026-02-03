<!-- loio5f3107d111314d448e589b4e368e23fb -->

# Filter with OTTL

Use filters to drop unwanted telemetry data from a pipeline. Filtering helps you reduce noise, lower storage and processing costs, and focus on the data that matters most.



<a name="loio5f3107d111314d448e589b4e368e23fb__section_ottl_filter_overview"/>

## Overview

You define these rules in the `filter` section of your Telemetry pipeline's `spec`.

Each rule in the `filter` list contains one or more `conditions`.

The pipeline drops any log, metric, or trace that matches **at least one** of the conditions you define. This means that multiple conditions are always combined with a logical `OR`. If any single condition evaluates to *true*, the data is dropped.

> ### Note:  
> -   Filters run **after** all transformations. Your filter conditions must operate on the final, modified state of your data, not its original state.
> 
> -   This feature is based on the [OpenTelemetry Filter Processor](https://github.com/open-telemetry/opentelemetry-collector-contrib/blob/main/processor/filterprocessor/README.md), with some limitations and differences \(see [Limitations](transform-and-filter-with-ottl-4c64598.md#loio4c645988c8224424a470bdc6257b27ff__section_ottl_limitations)\).



<a name="loio5f3107d111314d448e589b4e368e23fb__section_byp_rl2_fhc"/>

## Predefined Contexts

For each signal type, your OTTL conditions automatically operate on a predefined data context:

-   `LogPipeline`: Conditions act on individual log records \(context: `log`\). For the list of supported field paths in this context, see [OTel Log Context](https://github.com/open-telemetry/opentelemetry-collector-contrib/blob/main/pkg/ottl/contexts/ottllog/README.md).

-   `TracePipeline`: Conditions act on individual spans \(context: `span`\). For the list of supported field paths in this context, see [OTel Span Context](https://github.com/open-telemetry/opentelemetry-collector-contrib/blob/main/pkg/ottl/contexts/ottlspan/README.md).

-   `MetricPipeline`: Conditions act on individual metric data points \(context: `datapoint`\). For the list of supported field paths in this context, see [OTel DataPoint Context](https://github.com/open-telemetry/opentelemetry-collector-contrib/blob/main/pkg/ottl/contexts/ottldatapoint/README.md).




<a name="loio5f3107d111314d448e589b4e368e23fb__section_ottel_drop_logs"/>

## Example: Drop Low-Severity Logs

You can filter out `DEBUG` and `INFO` logs to reduce noise and storage costs:

```
# In your LogPipeline spec
spec:
  input:
    runtime:
      enabled: true
  output:
    otlp:
      endpoint:
        value: http://logs.example.com:4317
  filter:
    - conditions:
        - 'log.severity_number < SEVERITY_NUMBER_WARN'
```



<a name="loio5f3107d111314d448e589b4e368e23fb__section_keep_specific_metrics"/>

## Example: Keep Only Specific Envoy Metrics

> ### Tip:  
> To start collecting envoy metrics, see [Collect Envoy Metrics](collect-istio-metrics-aa786e0.md#loioaa786e09fbb9403cbe73a11f417f0460__section_envoy_metrics).

You can keep all standard Istio metrics but filter the verbose Envoy metrics \(those prefixed with `envoy_`\) to retain only those related to outlier detection \(circuit breaking\) and host ejections in your service mesh.

```
# In your MetricPipeline spec
spec:
  input:
    istio:
      enabled: true
      envoyMetrics:
        enabled: true
  output:
    otlp:
      endpoint:
        value: http://metrics.example.com:4317
  filter:
    - conditions:
        - 'IsMatch(metric.name, "^envoy_") == true and IsMatch(metric.name, ".*outlier_detection.*") == false'
```

