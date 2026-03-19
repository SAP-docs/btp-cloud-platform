<!-- loiodb28c29b313d40bcb5e4836eb34c9a75 -->

# Taints Configuration

Learn how to use taints to effectively schedule your workloads to nodes in additional worker node pools.

The [Additional Worker Node Pools](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Additional_WN_Pools) \(`additionalWorkerNodePools`\) parameter supports an optional *Taints* list. Use it to control which workloads are scheduled to nodes in a given worker pool.

> ### Note:  
> Taints alone dictate scheduling restrictions on nodes, but these restrictions take effect only when combined with tolerations. While you configure taints on nodes, you set tolerations on your workloads \(Pods\) to allow them to run on tainted nodes. For more information on configuring tolerations, see [Taints and Tolerations](https://kubernetes.io/docs/concepts/scheduling-eviction/taint-and-toleration/).



## Taints Parameters

The *Taints* \(`taints`\) parameter includes three nested parameters: *Key\**, *Value*, and *Effect\**.

> ### Remember:  
> The parameters marked with an asterisk "\*" are mandatory.

**Taints Nested Parameters**


<table>
<tr>
<th valign="top">

Nested Parameter

</th>
<th valign="top">

Description

</th>
<th valign="top">

Allowed Input

</th>
</tr>
<tr>
<td valign="top">

*Key\**

btp CLI parameter: `key`

</td>
<td valign="top">

Identifies the taint.

</td>
<td valign="top">

String

</td>
</tr>
<tr>
<td valign="top">

*Value*

btp CLI parameter: `value`

</td>
<td valign="top">

Provides additional context.

</td>
<td valign="top">

String

</td>
</tr>
<tr>
<td valign="top">

*Effect\**

btp CLI parameter: `effect`

</td>
<td valign="top">

Defines what happens to workloads that do not tolerate the taint.

</td>
<td valign="top">

`NoSchedule` \(excludes certain types of Pods from running on a specific set of nodes\)

`PreferNoSchedule` \(discourages scheduling Pods on certain nodes, but allows it as a last resort, such as if no other nodes are available, to maintain availability or resource utilization\)

`NoExecute` \(prevents any new workloads that cannot tolerate the taint from being scheduled onto a given node and evicts any existing Pods that already violate the taint and do not have the required toleration\)

</td>
</tr>
</table>

For each taint within a single worker node pool, the combination of the `key` and `effect` parameters must be unique. However, you can use the same `key` value with different `effect` values.



## Provisioning a Cluster with Taints

To provision a cluster with taints in an additional worker node pool, use a configuration similar to the following in your request:

```
{
  "additionalWorkerNodePools": [
    {
      ...
      "taints": [
        {
          "key": "dedicated",
          "value": "gpu",
          "effect": "NoSchedule"
        },
        {
          "key": "dedicated",
          "value": "gpu",
          "effect": "NoExecute"
        }
      ]
    }
  ]
}
```



## Updating Taints

To update or overwrite the existing taints for your worker node pool, you must explicitly provide a complete list of desired taints, for example:

```
{
  "additionalWorkerNodePools": [
    {
      ...
      "taints": [
        {
          "key": "dedicated",
          "value": "gpu",
          "effect": "NoSchedule"
        },
        {
          "key": "dedicated",
          "value": "gpu",
          "effect": "NoSchedule"
        }
      ]
    }
  ]
}
```



## Removing Taints

To remove existing taints for a worker node pool, either omit the `taints` field in the update request or set it to an empty list \(`[]`\), for example:

```
{
  "additionalWorkerNodePools": [
    {
      ...
      "taints": []
    }
  ]
}
```

**Related Information**  


[Assigning Workloads to Worker Node Pools](assigning-workloads-to-worker-node-pools-1bf21c1.md "In addition to the mandatory worker node pool existing in each Kyma runtime, you can add and configure custom worker node pools. These additional worker nodes are reserved for running your workloads with special computing requirements on optimized machines. To ensure your workload runs on the right worker node pool, assign workloads to particular worker nodes.")

