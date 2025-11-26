<!-- loio58445a0789da46dea08ccda9b5ea149d -->

# Filter Logs

Filter logs from the OTLP, application, and Istio input to control which data your pipeline processes. You can define filters to include or exclude logs based on their source namespace, container, and other attributes.



<a name="loio58445a0789da46dea08ccda9b5ea149d__section_filter_log_inputs"/>

## Overview

> ### Tip:  
> The following settings filter data by source. For advanced, content-based filtering and transformation, use the OpenTelemetry Transformation Language \(OTTL\). For details, see [Transform and Filter with OTTL](transform-and-filter-with-ottl-4c64598.md).


<table>
<tr>
<th valign="top">

Source

</th>
<th valign="top">

Granularity

</th>
<th valign="top">

Behavior without `namespaces` Block

</th>
<th valign="top">

Collect from All Namespaces

</th>
<th valign="top">

Collect from Specific Namespaces

</th>
</tr>
<tr>
<td valign="top">

OTLP \(default\)

</td>
<td valign="top">

Namespace

</td>
<td valign="top">

**includes** system namespaces

</td>
<td valign="top">

This is the default, no action needed.

</td>
<td valign="top">

Use the `include` or `exclude` filter

</td>
</tr>
<tr>
<td valign="top">

Application

</td>
<td valign="top">

Namespace, Container\*

</td>
<td valign="top">

**excludes** system namespaces

</td>
<td valign="top">

Set the `system` attribute to `true`

</td>
<td valign="top">

Use the `include` or `exclude` filter

</td>
</tr>
<tr>
<td valign="top">

Istio

</td>
<td valign="top">

Namespace, Workload \(`selector`\), Log content \(`filter.expression`\)

</td>
<td valign="top">

n/a

</td>
<td valign="top">

Apply the Istio `Telemetry` resource mesh-wide

</td>
<td valign="top">

Apply the Istio `Telemetry` resource to specific namespaces

</td>
</tr>
</table>

\* The `application` input provides an additional `containers` selector that behaves the same way as the `namespaces` selector.



<a name="loio58445a0789da46dea08ccda9b5ea149d__section_filter_input_by_namespace"/>

## Filter OTLP Logs by Namespaces

You can filter incoming OTLP logs by namespace. By default, all system namespaces are included.

These filters only apply to logs that have an associated namespace. The pipeline always collects any logs that do not have a namespace.

The `include` and `exclude` filters are mutually exclusive.

-   To collect OTLP logs from specific namespaces, use the `include` filter:

    > ### Sample Code:  
    > ```
    >   ...
    >   input:
    >     otlp:
    >       namespaces:
    >         include:
    >           - namespaceA
    >           - namespaceB
    > ```

-   To collect OTLP logs from all namespaces except specific ones, use the `exclude` filter:

    > ### Sample Code:  
    > ```
    >   ...
    >   input:
    >     otlp:
    >       namespaces:
    >         exclude:
    >           - namespaceA
    >           - namespaceB
    > ```




<a name="loio58445a0789da46dea08ccda9b5ea149d__section_filter_by_namespaces"/>

## Filter Application Logs by Namespace

You can control which namespaces to collect logs from using `include`, `exclude`, and `system` filters. The `include` and `exclude` filters are mutually exclusive.

-   To collect logs from specific namespaces, use the `include` filter:

    ```
      ...
      input:
        application:
          namespaces:
            include:
              - namespaceA
              - namespaceB
    ```

-   To collect logs from all namespaces except specific ones, use the `exclude` filter:

    ```
      ...
      input:
        application:
          namespaces:
            exclude:
              - namespaceC
    ```




<a name="loio58445a0789da46dea08ccda9b5ea149d__section_collect_logs_system_namespaces"/>

## Collect Application Logs From System Namespaces

By default, application logs from `kube-system`, `istio-system`, and `kyma-system` are excluded. To override this and collect logs from them, set the `system` attribute to *true*:

```
  ...
  input:
    application:
      enabled: true
        namespaces:
          system: true
```



<a name="loio58445a0789da46dea08ccda9b5ea149d__section_filter_by_container"/>

## Filter Application Logs by Container

You can also filter logs based on the container name with `include` and `exclude` filters. These filters apply in addition to any namespace filters.

The following pipeline collects input from all namespaces excluding `kyma-system` and only from the `istio-proxy` containers:

```
...
  input:
    application:
      enabled: true
      namespaces:
        exclude:
          - myNamespace
      containers:
        exclude:
          - myContainer
    otlp:
      ...
```



<a name="loio58445a0789da46dea08ccda9b5ea149d__section_istio_logs_for_workload"/>

## Select Istio Logs From a Specific Application

To limit logging to a single application within a namespace, configure label-based selection for this workload with a [selector](https://istio.io/latest/docs/reference/config/type/workload-selector/#WorkloadSelector) in the Istio `Telemetry` resource.

```
apiVersion: telemetry.istio.io/v1
kind: Telemetry
metadata:
  name: access-config
  namespace: $YOUR_NAMESPACE
spec:
  selector:
    matchLabels:
      service.istio.io/canonical-name: $YOUR_LABEL
  accessLogging:
    - providers:
      - name: kyma-logs
```



<a name="loio58445a0789da46dea08ccda9b5ea149d__section_filter_istio_logs"/>

## Filter Istio Logs by Content

To reduce noise and cost, filter your Istio access logs. This is especially useful for filtering out traffic that doesn't use an HTTP-based protocol, as those log entries often lack useful details.

Add a `filter` expression to the same `accessLogging` block that you used to enable the logs. The expression uses [Envoy attributes](https://www.envoyproxy.io/docs/envoy/latest/intro/arch_overview/advanced/attributes) to define which log entries to keep.

The following example enables mesh-wide logging but only keeps logs that have a defined request protocol, effectively filtering out most non-HTTP traffic.

```
apiVersion: telemetry.istio.io/v1
kind: Telemetry
metadata:
 name: mesh-default
 namespace: istio-system
spec:
 accessLogging:
 - filter:
     expression: 'has(request.protocol)'
   providers:
   - name: kyma-logs
```

