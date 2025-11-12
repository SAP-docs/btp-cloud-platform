<!-- loio6bd4bfdc97b94fa2923041dc96cf5012 -->

# Filter Metrics

Filter metrics from the OTLP, Istio, Prometheus, and runtime input to control which data your pipeline processes. You can define filters to include or exclude metrics based on their source namespace and resource type.



<a name="loio6bd4bfdc97b94fa2923041dc96cf5012__section_filter_metric_inputs"/>

## Overview


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

Istio

</td>
<td valign="top">

Namespace

</td>
<td valign="top">

**excludes** system namespaces

</td>
<td valign="top">

Add `namespaces: {}` to the input's configuration

</td>
<td valign="top">

Use the `include` or `exclude` filter

</td>
</tr>
<tr>
<td valign="top">

Prometheus

</td>
<td valign="top">

Namespace

</td>
<td valign="top">

**excludes** system namespaces

</td>
<td valign="top">

Add `namespaces: {}` to the input's configuration

</td>
<td valign="top">

Use the `include` or `exclude` filter

</td>
</tr>
<tr>
<td valign="top">

Runtime

</td>
<td valign="top">

Namespace, Resource Type\*

</td>
<td valign="top">

**excludes** system namespaces

</td>
<td valign="top">

Add `namespaces: {}` to the input's configuration

</td>
<td valign="top">

Use the `include` or `exclude` filter

</td>
</tr>
</table>

\* The `runtime` input provides additional filters for Kubernetes resources such as Pods or Nodes. For details, see [Select Resource Types](collect-runtime-metrics-2c9fb6e.md#loio2c9fb6e7efe84c34b3d3f99ca3e787fc__section_select_resources).



<a name="loio6bd4bfdc97b94fa2923041dc96cf5012__section_runtime_include_namespaces"/>

## Filter Metrics by Namespace

For the all inputs \(`otlp`, `prometheus`, `istio`, and `runtime`\), you can filter incoming metrics by namespace. The `include` and `exclude` filters are mutually exclusive.

-   To collect metrics from specific namespaces, use the `include` filter:

    > ### Sample Code:  
    > ```
    >   ...
    >   input:
    >     <otlp | prometheus | istio | runtime>:
    >       enabled: true
    >       namespaces:
    >         include:
    >           - namespaceA
    >           - namespaceB
    > ```

-   To collect metrics from all namespaces except specific ones, use the `exclude` filter:

    > ### Sample Code:  
    > ```
    >   ...
    >   input:
    >     <otlp | prometheus | istio | runtime>:
    >       enabled: true
    >       namespaces:
    >         exclude:
    >           - namespaceA
    >           - namespaceB
    > ```




<a name="loio6bd4bfdc97b94fa2923041dc96cf5012__section_istio_include_system_namespaces"/>

## Collect Metrics From System Namespaces

For `otlp` metrics, system namespaces are included by default.

To include system namespaces for `prometheus`, `istio`, and `runtime` metrics without specifying any other namespaces, explicitly configure an empty namespace object: `namespaces: {}`:

> ### Sample Code:  
> ```
>   ...
>   input:
>     <prometheus | istio | runtime>:
>       enabled: true
>       namespaces: {}
>         
> ```

