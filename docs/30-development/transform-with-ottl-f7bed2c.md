<!-- loiof7bed2c944a0479ca0820840559dcad7 -->

# Transform with OTTL

Use transformations to modify telemetry data as it flows through a pipeline. You can modify telemetry fields to enrich data or conform to a specific schema.



<a name="loiof7bed2c944a0479ca0820840559dcad7__section_ottl_transform_overview"/>

## Overview

You define these rules in the `transform` section of your Telemetry pipeline's `spec`.

Each rule in the `transform` list contains:

-   `statements`: One or more OTTL functions that modify the data. These are the actions that you want to perform.

-   `conditions` \(optional\): One or more OTTL conditions that must be met. If you provide conditions, the statements only run on data that matches at least one of the conditions.

    If you don't provide any conditions, the statements apply to all telemetry data passing through the pipeline.


> ### Note:  
> -   The pipeline applies all transformation rules **before** it evaluates any filter rules. Any change you make during the transformation affects the data that your filters see.
> 
> -   This feature is based on the [OpenTelemetry Transform Processor](https://github.com/open-telemetry/opentelemetry-collector-contrib/blob/main/processor/transformprocessor/README.md), with some limitations \(see [Limitations](transform-and-filter-with-ottl-4c64598.md#loio4c645988c8224424a470bdc6257b27ff__section_ottl_limitations)\).



<a name="loiof7bed2c944a0479ca0820840559dcad7__section_ottl_add_global_attribute"/>

## Example: Add a Global Attribute to All Metrics

You can add a `deployment.environment.name` attribute with the value *production* to all metrics. This is useful for tagging all data from a specific cluster.

```
# In your MetricPipeline spec
spec:
  input:
    prometheus:
      enabled: true
  output:
    otlp:
      endpoint:
        value: http://metrics.example.com:4317
  transform:
    - statements:
        - 'set(resource.attributes["deployment.environment.name"], "production")'
```



<a name="loiof7bed2c944a0479ca0820840559dcad7__section_ottl_set_conditional_span_status"/>

## Example: Conditionally Set a Span's Status

If you want to identify system-related spans in your observability backend, mark all spans from workloads in system namespaces by adding a `system` attribute with the value *true*.

```
# In your TracePipeline spec
spec:
  output:
    otlp:
      endpoint:
        value: http://traces.example.com:4317
  transform:
    - conditions:
        - 'IsMatch(resource.attributes["k8s.namespace.name"], ".*-system")'
      statements:
        - 'set(span.attributes["system"], "true")'
```



<a name="loiof7bed2c944a0479ca0820840559dcad7__section_tfj_hqt_3hc"/>

## Example: Parse Custom Log Formats

If your application writes logs to stdout in a custom format, you can use a series of OTTL statements to parse these logs into structured data, so you can easily query and analyze them in your observability backend. The following example parses the payload and enriches core attributes:

```
# In your LogPipeline spec
spec:
  input:
    application:
      enabled: true
  output:
    otlp:
      endpoint:
        value: http://traces.example.com:4317
  transform:
    # Try to parse the body as custom parser (default spring boot logback)
    # 2025-11-12T14:40:36.828Z  INFO 1 --- [demo] [           main] c.e.restservice.RestServiceApplication   : Started Application
    - statements:
        - merge_maps(log.attributes, ExtractPatterns(log.body,"^(?P<timestamp>\\d{4}-\\d{2}-\\d{2}T\\d{2}:\\d{2}:\\d{2}\\.\\d+Z)\\s+(?P<level>[A-Z]+)\\s+(?P<pid>\\d+)\\s+---\\s+\\[(?P<mdc>[^\\]]+)\\]\\s+\\[\\s*(?P<thread>[^\\]]+)\\s*\\]\\s+(?P<logger>[^\\s:]+)\\s*:\\s*(?P<msg>.*)$"), "upsert")

    # Try to enrich core attributes if custom parsing was successful
    - conditions:
        - log.attributes["msg"] != nil
      statements:
        - set(log.body, log.attributes["msg"])
        - delete_key(log.attributes, "msg")
    - conditions:
        - log.attributes["timestamp"] != nil
      statements:
        - set(log.time, Time(log.attributes["timestamp"], "2006-01-02T15:04:05.000Z"))
        - delete_key(log.attributes, "timestamp")
    - conditions:
        - log.attributes["level"] != nil
      statements:
        - set(log.severity_text, ToUpperCase(log.attributes["level"]))
        - delete_key(log.attributes, "level")
```



<a name="loiof7bed2c944a0479ca0820840559dcad7__section_phz_3qt_3hc"/>

## Example: Redact Sensitive Data in Spans

To improve security and meet compliance requirements, you can redact sensitive information from your telemetry data before it leaves the cluster.

```
# In your TracePipeline spec
spec:
  output:
    otlp:
      endpoint:
        value: http://traces.example.com:4317
  transform:
      - statements:
          - replace_pattern(span.attributes["http.url"], "client_id=[^&]+", "client_id=[REDACTED]")
          - replace_pattern(span.attributes["http.url"], "client_secret=[^&]+", "client_secret=[REDACTED]")
```

