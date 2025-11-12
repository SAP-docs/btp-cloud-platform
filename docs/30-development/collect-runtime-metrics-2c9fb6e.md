<!-- loio2c9fb6e7efe84c34b3d3f99ca3e787fc -->

# Collect Runtime Metrics

To monitor the health and resource usage of your Kubernetes cluster, enable the `runtime` input in your `MetricPipeline`. This uses an agent on each node to gather metrics for resources like Pods, Nodes, and Deployments. You can choose the specific resources to monitor and control from which namespaces metrics are collected.



<a name="loio2c9fb6e7efe84c34b3d3f99ca3e787fc__section_activate_runtime_metrics"/>

## Activate Runtime Metrics

By default, the `runtime` input is disabled. If you want to monitor your Kubernetes resources, enable the collection of runtime metrics:

```
...
  input:
    runtime:
      enabled: true
```

With this, the metric agent starts collecting all runtime metrics from all resources \(Pod, container, Node, Volume, DaemonSet, Deployment, StatefulSet, and Job\).

> ### Tip:  
> To select metrics from specific namespaces or to include system namespaces, see [Filter Metrics](filter-metrics-6bd4bfd.md).



<a name="loio2c9fb6e7efe84c34b3d3f99ca3e787fc__section_select_resources"/>

## Select Resource Types

By default, metrics for all supported resource types are collected. To enable or disable the collection of metrics for a specific resource, use the `resources` section in the `runtime` input.

The following example collects only DaemonSet, Deployment, StatefulSet, and Job metrics:

```
...
  input:
    runtime:
      enabled: true
      resources:
        pod:
          enabled: false
        container:
          enabled: false
        node:
          enabled: false
        volume:
          enabled: false
        daemonset:
          enabled: true
        deployment:
          enabled: true
        statefulset:
          enabled: true
        job:
          enabled: true
```

See a summary of the types of information you can gather for each resource:


<table>
<tr>
<th valign="top">

**Resource** 

</th>
<th valign="top">

Metrics Collected

</th>
</tr>
<tr>
<td valign="top">

`pod` 

</td>
<td valign="top">

CPU, memory, filesystem, and network usage; current Pod phase

</td>
</tr>
<tr>
<td valign="top">

`container` 

</td>
<td valign="top">

CPU/memory requests, limits, and usage; container restart count

</td>
</tr>
<tr>
<td valign="top">

`node` 

</td>
<td valign="top">

Aggregated CPU, memory, filesystem, and network usage for the Node

</td>
</tr>
<tr>
<td valign="top">

`volume` 

</td>
<td valign="top">

Filesystem capacity, usage, and inode statistics for persistent volumes

</td>
</tr>
<tr>
<td valign="top">

`deployment` 

</td>
<td valign="top">

Number of desired versus available replicas

</td>
</tr>
<tr>
<td valign="top">

`daemonset` 

</td>
<td valign="top">

Number of desired, current, and ready Nodes

</td>
</tr>
<tr>
<td valign="top">

`statefulset` 

</td>
<td valign="top">

Number of desired, current, and ready Pods

</td>
</tr>
<tr>
<td valign="top">

`job` 

</td>
<td valign="top">

Counts of active, successful, and failed Pods

</td>
</tr>
</table>

To learn which specific metrics are collected from which source \(`kubletstatsreceiver` or `k8sclusterreceiver`\), see [Runtime Metrics](https://github.com/kyma-project/telemetry-manager/tree/main/docs/user/collecting-metrics/runtime-metrics.md).

