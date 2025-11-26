<!-- loio4c645988c8224424a470bdc6257b27ff -->

# Transform and Filter with OTTL

To apply custom transformations and filters to your telemetry data, use the OpenTelemetry Transformation Language \(OTTL\). You can modify, enrich, and filter logs, metrics, and traces before they're sent to your backend.



<a name="loio4c645988c8224424a470bdc6257b27ff__section_ottl_overview"/>

## Overview

You define OTTL rules in the `spec` of your `LogPipeline`, `MetricPipeline`, and `TracePipeline` resources.

1.  With the `transform` section, you can standardize and enrich your data: Add, rename, or modify fields to conform to a standard schema, add valuable context, or redact sensitive information. For details, see [Transform with OTTL](transform-with-ottl-f7bed2c.md).

2.  With the `filter` section, you can reduce data volume and cost: Drop unwanted logs, metrics, or traces to lower your ingestion costs and reduce noise in your observability backend. For details, see [Filter with OTTL](filter-with-ottl-5f3107d.md).


When you define rules, the Telemetry module configures processors in the underlying OpenTelemetry Collector to apply your rules.

> ### Note:  
> -   The underlying [OpenTelemetry Transformation Language \(OTTL\)](https://github.com/open-telemetry/opentelemetry-collector-contrib/blob/main/pkg/ottl/README.md) is a beta feature. Its syntax and function signatures may change in future releases. Always test complex expressions in a non-production environment first.
> 
> -   Each processing rule consumes CPU and memory. Complex rules can significantly impact the pipeline performance.
> 
> -   This feature requires Telemetry module v1.52.0 or later.



<a name="loio4c645988c8224424a470bdc6257b27ff__section_ottl_processing_order"/>

## Processing Order

The Telemetry module processes data in a fixed sequence. Understanding this order is critical for designing efficient and correct pipelines:

1.  Input Filtering: First, the pipeline applies any basic filters defined in the `spec.input` section of your pipeline. These filters operate on the source of the data, such as its namespace or container. This is the most efficient way to drop large, unwanted blocks of telemetry data before any complex processing occurs. For details, see [Filter Logs](filter-logs-58445a0.md), [Filter Traces](filter-traces-6a03a1b.md), and [Filter Metrics](filter-metrics-6bd4bfd.md).

2.  OTTL Transformation: Next, the pipeline applies the transformation rules from the `transform` section. These rules modify the data that passed the input filters. You can add, rename, or delete fields.

3.  OTTL Filtering: Finally, the pipeline evaluates the transformed data against the filter rules from the `filter` section. Any data matching a filter condition is dropped.


This sequence means that your OTTL rules only operate on data that has already passed the initial input filters. Furthermore, your OTTL `filter` conditions must use the final, transformed state of your data, not its original state. For example, if you rename a field in a transformation rule, your OTTL filter must use the new name.



<a name="loio4c645988c8224424a470bdc6257b27ff__section_ottl_limitations"/>

## Limitations



### Always Use the Full Context Path

You must specify the full path for every field. Short-hand references are not supported.

-   Correct: `resource.attributes["k8s.namespace.name"] == "default"`, `log.attributes["level"]`, `datapoint.value_int`, `span.name`

-   Incorrect: `attributes["k8s.namespace.name"] == "default"`, `attributes["level"]`, `value_int`, `name`


> ### Tip:  
> For details on the underlying implementation details of context inference, see [OTel Transform Processor Context Inference](https://github.com/open-telemetry/opentelemetry-collector-contrib/blob/main/processor/transformprocessor/README.md#context-inference).



### Trace Filtering Applies to Entire Spans

When you write a filter for a `TracePipeline`, the condition applies to the parent span. If the condition matches, the entire span is dropped, including all of its events.

You cannot use filters to remove individual events within a span \(the [`spanevent` context](https://github.com/open-telemetry/opentelemetry-collector-contrib/blob/main/pkg/ottl/contexts/ottlspanevent/README.md)\).



### Unsupported Metric Functions

The metric-specific functions in the filter processor \([HasAttrKeyOnDatapoint](https://github.com/open-telemetry/opentelemetry-collector-contrib/tree/main/processor/filterprocessor#hasattrkeyondatapoint) and [HasAttrOnDatapoint](https://github.com/open-telemetry/opentelemetry-collector-contrib/tree/main/processor/filterprocessor#hasattrondatapoint)\) are not supported. But you can achieve the same results by using general-purpose OTTL functions:

-   To replace `HasAttrKeyOnDatapoint("my.key")`, use: `ContainsValue(Keys(datapoint.attributes), "my.key")`

-   To replace `HasAttrOnDatapoint("my.key", "my.value")`, use: `datapoint.attributes["my.key"] == "my.value"`


