<!-- loioe2e13bfaa2f54a4fb179f0f1f840353a -->

# Provisioning and Updating Parameters in the Kyma Environment

When creating a Kyma cluster, you can configure various parameters to adjust it to your specific needs.



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_qzp_1wv_yzb"/>

## Overview

To configure the cluster parameters, you can use your preferred interface, the SAP BTP cockpit, or the SAP BTP command line interface \(btp CLI\).

To check which parameters are available for configuration in a particular plan, see [Available Plans in the Kyma Environment](available-plans-in-the-kyma-environment-befe01d.md).



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Access_Control_List"/>

## Access Control List

*Access Control List* \(`accessControlList`\) specifies the IP ranges that can access the Kubernetes API. Internally, the list of IP ranges includes additional entries necessary for the continuous operation of your cluster.

> ### Caution:  
> Enabling *Access Control List* blocks access to Kyma dashboard. You can then manage your cluster only through kubectl.

**Access Control List Parameter**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

Default Value

</th>
<th valign="top">

Allowed Input

</th>
</tr>
<tr>
<td valign="top">

*Access Control List*

btp CLI parameter: `accessControlList`

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

By default, the feature is disabled, and your cluster is created with no IP restrictions.

</td>
<td valign="top">

See the Access Control List Nested Parameters table.

</td>
</tr>
</table>

> ### Remember:  
> The parameters marked with an asterisk "\*" are mandatory.

**Access Control List Nested Parameters**


<table>
<tr>
<th valign="top">

Nested Parameter

</th>
<th valign="top">

Default Value

</th>
<th valign="top">

Allowed Input

</th>
</tr>
<tr>
<td valign="top">

*Allowed CIDRs\**

btp CLI parameter: `allowedCIDRs`

type: list of strings

</td>
<td valign="top">

Empty list \(`[]`\)

</td>
<td valign="top">

List of IP ranges or an empty list.

</td>
</tr>
</table>



### Configuration

To define your access control list, provide the `accessControlList` parameter with `allowedCIDRs` listing any correct IP ranges in the provisioning request. See the example configuration:

```
"accessControlList": {
    "allowedCIDRs": ["1.2.3.0/24", "2.3.4.0/24"]
    }
```

To modify the set of IP ranges after the cluster is provisioned, send an update request with the new set of IP ranges. If the update request does not contain the `accessControlList` parameter, the existing access control list remains unchanged.

To remove your access control list, set `allowedCIDRs` to an empty list.

```
"accessControlList": {
    "allowedCIDRs": []
    }
```



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Additional_Volume_Size"/>

## Additional Volume Size

With the *Additional Volume Size* \(`additionalVolumeSizeGi`\) parameter, you can add extra disk space on top of the default volume size for your worker nodes. The total volume size is the sum of the default volume size and `additionalVolumeSizeGi`.

**Additional Volume Size Parameter**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

Default Value

</th>
<th valign="top">

Allowed Input

</th>
</tr>
<tr>
<td valign="top">

*Additional Volume Size*

btp CLI parameter: `additionalVolumeSizeGi`

type: integer

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

*0*

</td>
<td valign="top">

Integer between 0 and 100.

</td>
</tr>
</table>



### Configuration

> ### Tip:  
> Before requesting additional disk space, check your current default volume size. See [Machine Type](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Machine_Type).

You can set `additionalVolumeSizeGi` on the main Kyma worker pool and on additional worker node pools. See [Additional Worker Node Pools](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Additional_WN_Pools).

To add extra disk space to the main Kyma worker pool, set `additionalVolumeSizeGi` at the root level of the request.

```
"additionalVolumeSizeGi": 50
```

To add extra disk space to an additional worker node pool, set `additionalVolumeSizeGi` within the respective entry in the `additionalWorkerNodePools` array.

```
{
  "additionalWorkerNodePools": [
    {
      "name": "worker-1",
      "machineType": "Standard_D4s_v5",
      "haZones": true,
      "autoScalerMin": 3,
      "autoScalerMax": 10,
      "additionalVolumeSizeGi": 50
    }
  ]
}
```

When updating an existing cluster, the behavior differs depending on the worker pool:

-   Main Kyma worker pool: If `additionalVolumeSizeGi` changes, the total volume size is recomputed as the sum of the default volume size and the new `additionalVolumeSizeGi` value. If you don't include `additionalVolumeSizeGi` in the update request, the existing volume is preserved.

-   Additional worker node pools: To update the additional volume size of an existing pool, you must explicitly provide the new `additionalVolumeSizeGi` value in the update request. To remove the additional volume size, either omit `additionalVolumeSizeGi` from the update request or set it to `0`.




<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Additional_WN_Pools"/>

## Additional Worker Node Pools

With the *Additional Worker Node Pools* \(`additionalWorkerNodePools`\), parameter, you can add customized worker node pools to your Kyma runtime and introduce worker nodes optimized and reserved for your particular workload requirements.

**Additional Worker Node Pools Parameter**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

Default Value

</th>
<th valign="top">

Allowed Input

</th>
</tr>
<tr>
<td valign="top">

*Additional Worker Node Pools*

btp CLI parameter: `additionalWorkerNodePools`

type: array

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

None \(if not provided, no additional worker node pools are created\)

</td>
<td valign="top">

See the Additional Worker Node Pools Nested Parameters table.

</td>
</tr>
</table>

> ### Remember:  
> The parameters marked with an asterisk "\*" are mandatory.

**Additional Worker Node Pools Nested Parameters**


<table>
<tr>
<th valign="top">

Nested Parameter

</th>
<th valign="top">

Description

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

Allowed Input

</th>
</tr>
<tr>
<td valign="top">

*Name\**

btp CLI parameter: `name`

type: string

</td>
<td valign="top">

Specifies the unique name of your additional worker node pool.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

Short string of up to 15 characters that contains only alphanumeric lowercase characters \(a-z, 0–9\), and hyphens \(-\). It must begin and end with an alphanumeric character, and can't contain whitespace characters.

</td>
</tr>
<tr>
<td valign="top">

*Machine Type\**

btp CLI parameter: `machineType`

type: string

</td>
<td valign="top">

Specifies the provider-specific virtual machine type.

</td>
<td valign="top">

Provisioning

Updating <sup>[1](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_mt_update)</sup>

</td>
<td valign="top">

See [Machine Type](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Machine_Type).

</td>
</tr>
<tr>
<td valign="top">

*High Availability Zones\**

btp CLI parameter: `haZones`

type: boolean

</td>
<td valign="top">

Specifies if high availability zones are supported. This setting is permanent and cannot be updated <sup>[2](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_ha_update)</sup>.

If enabled, your resources are distributed across three zones to enhance fault tolerance.

If you disable high availability, all resources are placed in a single, randomly selected zone. Disabling `haZones` is not recommended for production environments.

High availability is not supported in the `azure_lite` plan.

</td>
<td valign="top">

Provisioning

Updating <sup>[2](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_ha_update)</sup>

</td>
<td valign="top">

`true` or `false`

</td>
</tr>
<tr>
<td valign="top">

*Auto Scaler Min\**

btp CLI parameter: `autoScalerMin`

type: integer

</td>
<td valign="top">

Specifies the minimum number of virtual machines to create.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

With high availability disabled, you can set it to `0`. With high availability enabled, you must set it to at least `3`.

You can also set it to `0` in `azure_lite` because the plan does not support high availability.

See [Auto Scaler Min](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Auto_Scaler_Min).

</td>
</tr>
<tr>
<td valign="top">

*Auto Scaler Max\**

btp CLI parameter: `autoScalerMax`

type: integer

</td>
<td valign="top">

Specifies the maximum number of virtual machines to create.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

With high availability disabled, you can set it to `1`. With high availability enabled, you must set it to at least `3`.

You can also set it to `1` in `azure_lite` because the plan does not support high availability.

See [Auto Scaler Max](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Auto_Scaler_Max).

</td>
</tr>
<tr>
<td valign="top">

*Taints*

btp CLI parameter: `taints`

type: list

</td>
<td valign="top">

Specifies which workloads are scheduled to nodes in a given worker pool.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

See [Taints Configuration](taints-configuration-db28c29.md).

</td>
</tr>
<tr>
<td valign="top">

*Additional Volume Size*

btp CLI parameter: `additionalVolumeSizeGi`

</td>
<td valign="top">

Specifies extra disk space added on top of the default volume size for a worker node pool.

See [Additional Volume Size](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Additional_Volume_Size).

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

Integer between 0 and 100.

</td>
</tr>
<tr>
<td valign="top">

*Annotations*

btp CLI parameter: `annotations`

</td>
<td valign="top">

Attaches arbitrary non-identifying metadata to worker nodes, such as tooling configuration or operational notes.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

Key-value pairs where each key is a non-empty string and each value is a string.

</td>
</tr>
<tr>
<td valign="top">

*Labels*

btp CLI parameter: `labels`

</td>
<td valign="top">

Attaches identifying metadata to worker nodes that you can use to identify, filter, and organize them.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

Key-value pairs where each key is a non-empty string and each value is a string.

</td>
</tr>
</table>

<sup>1</sup> You can update your virtual machine type only within the general-purpose machine types. You cannot perform updates on compute-intensive machine types. For details, see [Machine Type](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Machine_Type).

<sup>2</sup> You can only use this parameter to update your Kyma runtime by creating a new additional worker node pool. You cannot use it to update an existing additional worker node pool.



### Configuration

If you do not provide the `additionalWorkerNodePools` array in the provisioning request, no additional worker node pools are created.

If you do not provide the `additionalWorkerNodePools` array in the update request, the saved additional worker node pools stay unchanged. However, if you provide an empty array in the update request, all existing additional worker node pools are removed. If you rename your existing additional worker node pool, it is deleted and a new one is created.

See also [Assigning Workloads to Worker Node Pools](assigning-workloads-to-worker-node-pools-1bf21c1.md).

When updating optional parameters of an existing additional worker node pool, the following rules apply:

-   If you omit an optional field in the update request, the existing setting for that pool is removed.
-   If you set an optional field to an empty object \(*\[\]*\), the existing setting for that pool is also removed.
-   To update an optional field, provide the new setting - the update overwrites the existing setting for that pool.

See the example configuration:

> ### Sample Code:  
> ```
> {
>   "additionalWorkerNodePools": [
>     {
>       "name": "worker-1",
>       "machineType": "Standard_D2s_v5",
>       "haZones": true,
>       "autoScalerMin": 3,
>       "autoScalerMax": 20,
>       "labels": {
>         "env": "prod",
>         "team": "platform"
>       },
>       "annotations": {
>         "owner": "team-platform",
>         "cost-center": "12345"
>       }
>     },
>     {
>       "name": "worker-2",
>       "machineType": "Standard_D4s_v5",
>       "haZones": false,
>       "autoScalerMin": 1,
>       "autoScalerMax": 1,
>       "taints": [
>         {
>           "key": "dedicated",
>           "value": "gpu",
>           "effect": "NoSchedule"
>         },
>         {
>           "key": "dedicated",
>           "value": "gpu",
>           "effect": "NoExecute"
>         }
>       ]
>     }
>   ]
> }
> ```

See also [Assigning Workloads to Worker Node Pools](assigning-workloads-to-worker-node-pools-1bf21c1.md).



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Administrators"/>

## Administrators

With the *Administrators* \(`administrators`\) parameter, you can define the list of runtime administrators.

**Administrators Parameter**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Supported Operations

</th>
<th valign="top">

Default Value

</th>
<th valign="top">

Allowed Input

</th>
</tr>
<tr>
<td valign="top">

*Administrators*

btp CLI name: `administrators`

type: an array of strings

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

If you don't provide the parameter or provide an empty array during provisioning, the email address of the provisioning user is used.

</td>
<td valign="top">

A list of administrators' email addresses.

</td>
</tr>
</table>



### Configuration

See an example of the JSON input:

> ### Sample Code:  
> ```
> "administrators": [
>         "example_1@mail.com",
>         "example_2@mail.com",
>         "example_3@mail.com"
>     ]
> ```

If you don't include `administrators` or provide an empty array in an update request, the existing list of administrators remains unchanged.

To revoke all administrators, set the parameter to a list with a single entry. The entry does not have to correspond to an existing user.



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_audit_log_access"/>

## Audit Log Access

With the *Audit Log Access* \(`auditLogAccess`\) parameter, you can gain direct read access to your own audit log data using the SAP Audit Log Retrieval API v2. When you enable the parameter, Kyma stores the required credentials in a Kubernetes Secret named `auditlog-read-credentials` in the `kyma-system` namespace of your cluster.

> ### Caution:  
> Enabling *Audit Log Access* is irreversible. If you enable the feature, you cannot disable it.
> 
> When you enable *Audit Log Access* during an update, you can only access the logs created after enabling the feature.

**Audit Log Access Parameter**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Supported Operations

</th>
<th valign="top">

Default Value

</th>
<th valign="top">

Allowed Input

</th>
</tr>
<tr>
<td valign="top">

*Audit Log Access*

btp CLI name: `auditLogAccess`

type: boolean

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

*false*

</td>
<td valign="top">

`true` or `false`

</td>
</tr>
</table>

See an example of the JSON input:

> ### Sample Code:  
> ```
> "auditLogAccess": true
> ```

See also [Accessing Your Audit Log Data](accessing-your-audit-log-data-3f0002b.md).



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Auto_Scaler_Max"/>

## Auto Scaler Max

With the *Auto Scaler Max* \(`autoScalerMax`\) integer parameter, you can set the maximum number of virtual machines to create.

> ### Caution:  
> Cluster autoscaling is not subject to the Service Level Agreement \(SLA\). Successful autoscaling is not guaranteed. The mechanism may fail or take longer than expected due to constraints of the underlying cloud providers.

**Auto Scaler Max Parameter**


<table>
<tr>
<th valign="top">

Plan

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

Default Value

</th>
<th valign="top">

Maximum Value

</th>
<th valign="top">

Allowed Input

</th>
</tr>
<tr>
<td valign="top">

Standard:

-   Amazon Web Services \(`aws`\)
-   Google Cloud \(`gcp`\)
-   Microsoft Azure \(`azure`\)
-   Alibaba Cloud \(`alicloud`\)

Build Runtime:

-   Amazon Web Services \(`build-runtime-aws`\)
-   Google Cloud \(`build-runtime-gcp`\)
-   Microsoft Azure \(`build-runtime-azure`\)



</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

20

</td>
<td valign="top">

300

</td>
<td valign="top">

Number between 3 and 300, but greater than or equal to *Auto Scaler Min*.

Within the *Additional Worker Node Pools* array, with high availability disabled, you can set it to `1`. See [Additional Worker Node Pools](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Additional_WN_Pools).

</td>
</tr>
<tr>
<td valign="top">

Kyma Test Demo and Development \(Azure Lite\)

technical name: `azure_lite`

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

10

</td>
<td valign="top">

40

</td>
<td valign="top">

Number between 2 and 40, but greater than or equal to *Auto Scaler Min*.

Within the *Additional Worker Node Pools* array, you can set it to `1`. See [Additional Worker Node Pools](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Additional_WN_Pools).

</td>
</tr>
<tr>
<td valign="top">

SAP Cloud Infrastructure

technical name: `sap-converged-cloud`

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

20

</td>
<td valign="top">

300

</td>
<td valign="top">

Number between 3 and 300, but greater than or equal to *Auto Scaler Min*.

Within the *Additional Worker Node Pools* array, with high availability disabled, you can set it to `1`. See [Additional Worker Node Pools](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Additional_WN_Pools).

</td>
</tr>
</table>

See the default JSON input:

> ### Sample Code:  
> ```
> "autoScalerMax": 20
> ```



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Auto_Scaler_Min"/>

## Auto Scaler Min

With the *Auto Scaler Min* \(`autoScalerMin`\) integer parameter, you can set the minimum number of virtual machines to create.

**Auto Scaler Min Parameter**


<table>
<tr>
<th valign="top">

Plan

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

Default Value

</th>
<th valign="top">

Minimum Value

</th>
<th valign="top">

Allowed Input

</th>
</tr>
<tr>
<td valign="top">

Standard:

-   Amazon Web Services \(`aws`\)
-   Google Cloud \(`gcp`\)
-   Microsoft Azure \(`azure`\)
-   Alibaba Cloud \(`alicloud`\)

Build Runtime:

-   Amazon Web Services \(`build-runtime-aws`\)
-   Google Cloud \(`build-runtime-gcp`\)
-   Microsoft Azure \(`build-runtime-azure`\)



</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

3

</td>
<td valign="top">

3

</td>
<td valign="top">

Number between 3 and the current value set in *Auto Scaler Max*.

Within the *Additional Worker Node Pools* array, with high availability disabled, you can set it to `0`. See [Additional Worker Node Pools](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Additional_WN_Pools).

</td>
</tr>
<tr>
<td valign="top">

Kyma Test Demo and Development \(Azure Lite\)

technical name: `azure_lite`

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

2

</td>
<td valign="top">

2

</td>
<td valign="top">

Number between 2 and the current value set in *Auto Scaler Max*.

Within the *Additional Worker Node Pools* array, you can set it to `0`. See [Additional Worker Node Pools](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Additional_WN_Pools).

</td>
</tr>
<tr>
<td valign="top">

SAP Cloud Infrastructure

technical name: `sap-converged-cloud`

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

3

</td>
<td valign="top">

3

</td>
<td valign="top">

Number between 3 and the current value set in *Auto Scaler Max*.

Within the *Additional Worker Node Pools* array, with high availability disabled, you can set it to `0`. See [Additional Worker Node Pools](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Additional_WN_Pools).

</td>
</tr>
</table>

See an example of the JSON input:

> ### Sample Code:  
> ```
> "autoScalerMin": 3
> ```



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Cluster_Name"/>

## Cluster Name\*

Use the *Cluster Name* \(`name`\) parameter to set the name of your cluster.

> ### Remember:  
> The parameters marked with an asterisk "\*" are mandatory.

**Cluster Name Parameter**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

Default Value

</th>
<th valign="top">

Allowed Input

</th>
</tr>
<tr>
<td valign="top">

*Cluster Name\**

btp CLI parameter: `name`

type: string

</td>
<td valign="top">

Provisioning

Updating \(for updates, the *Cluster Name* parameter is optional\)

</td>
<td valign="top">

Defaults to your subaccount’s subdomain.

</td>
<td valign="top">

Short string of 1 to 64 alphanumeric characters \(A-Z, a-z, 0–9\) and hyphens \(-\). It must not contain whitespace characters.

</td>
</tr>
</table>

See also [Tracking Kubeconfig and Cluster Associations in Kyma](tracking-kubeconfig-and-cluster-associations-in-kyma-f026eda.md).



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_shoot_and_seed"/>

## Colocate Control Plane

With the *Colocate Control Plane* \(`colocateControlPlane`\) parameter, you can specify that your control plane and worker nodes are in the same region.

**Colocate Control Plane Parameter**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Supported Operations

</th>
<th valign="top">

Default Value

</th>
<th valign="top">

Allowed Input

</th>
</tr>
<tr>
<td valign="top">

*Colocate Control Plane*

btp CLI name: `colocateControlPlane`

type: boolean

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

`false`

</td>
<td valign="top">

`true`\(control plane in the same region as cluster's worker nodes\)

`false` \(control plane can be deployed in a different region than worker nodes\)

</td>
</tr>
</table>



### Configuration

If you set it to `true`, it ensures the location of the control plane in the same region where your cluster's worker nodes are deployed. With this setting, you can control where your sensitive data is stored. If the control plane cannot be colocated in the selected region, the provisioning process fails. The error message offers you a list of regions supporting the control plane colocation.

If you set the parameter to `false` or leave the field empty, your control plane can sometimes be deployed in a different region than the worker nodes.

To learn which regions support the control plane colocation, see the [Region\*](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Region) section.

See an example of the JSON input:

> ### Sample Code:  
> ```
> "colocateControlPlane": true
> ```



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Machine_Type"/>

## Machine Type

With the *Machine Type* \(`machineType`\) parameter, you can specify the IaaS provider-specific virtual machine type.

**Machine Type Parameter**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Supported Operations

</th>
<th valign="top">

Default Value

</th>
<th valign="top">

Allowed Input

</th>
</tr>
<tr>
<td valign="top">

*Machine Type*

btp CLI parameter: `machineType`

type: string

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

Varies by IaaS provider and service plan. Expand the table for your preferred provider to see the default.

</td>
<td valign="top">

Varies by IaaS provider and service plan. Expand the table for your preferred provider for the full list.

To ensure smooth updates and avoid disruptions during upgrades, choose version-agnostic machine type names, such as `Standard_D2s` or `mi.large`. The version-agnostic machine type name represents the underlying instance family that powers this machine type. The most optimized underlying instance families are assigned to the version-agnostic machine type names and can be updated to newer generations during maintenance windows without affecting your configurations. Where present, the parenthetical values in the tables show the specific instance types that are actually provisioned.

</td>
</tr>
</table>

See an example input for the *Machine Type* parameter:

> ### Sample Code:  
> ```
> "machineType": "mi.large"
> ```

The available categories of machine types are the following:

-   General-purpose — available for use in both the mandatory Kyma worker node pool and in your additional worker node pools.
-   Compute-intensive — available for use only in additional worker node pools. See [Machine Types in Additional Worker Node Pools](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__mts_in_additional_wnp).

To see the general-purpose machine types available for specific service plans, expand the table for your preferred IaaS provider.



### Amazon Web Services

You can use the machine types listed in the table with the following plans:

-   Standard: Amazon Web Services \(technical name: `aws`\)
-   Build Runtime: Amazon Web Services \(technical name: `build-runtime-aws`\)

The `m5` and `m6i` machine types have been deprecated and can no longer be provisioned. To avoid breaking existing configurations, these inputs are automatically mapped to the equivalent `m7i` generation, so you do not need to adjust your configurations.

**AWS Machine Types**


<table>
<tr>
<th valign="top">

Default Value

</th>
<th valign="top">

Allowed Input \(Resolved Machine Type\)

</th>
<th valign="top">

Virtual Machine Size

</th>
<th valign="top">

Default Volume Size

</th>
</tr>
<tr>
<td valign="top" rowspan="21">

`mi.large`

</td>
<td valign="top">

`mi.large` \(`m7i.large`\)

</td>
<td valign="top">

2 vCPU, 8 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`mi.xlarge` \(`m7i.xlarge`\)

</td>
<td valign="top">

4 vCPU, 16 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`mi.2xlarge` \(`m7i.2xlarge`\)

</td>
<td valign="top">

8 vCPU, 32 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`mi.4xlarge` \(`m7i.4xlarge`\)

</td>
<td valign="top">

16 vCPU, 64 GB RAM

</td>
<td valign="top">

94 Gi

</td>
</tr>
<tr>
<td valign="top">

`mi.8xlarge` \(`m7i.8xlarge`\)

</td>
<td valign="top">

32 vCPU, 128 GB RAM

</td>
<td valign="top">

158 Gi

</td>
</tr>
<tr>
<td valign="top">

`mi.12xlarge` \(`m7i.12xlarge`\)

</td>
<td valign="top">

48 vCPU, 192 GB RAM

</td>
<td valign="top">

222 Gi

</td>
</tr>
<tr>
<td valign="top">

`mi.16xlarge` \(`m7i.16xlarge`\)

</td>
<td valign="top">

64 vCPU, 256 GB RAM

</td>
<td valign="top">

250 Gi

</td>
</tr>
<tr>
<td valign="top">

`m6i.large` \(`m7i.large`\)

</td>
<td valign="top">

2 vCPU, 8 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`m6i.xlarge` \(`m7i.xlarge`\)

</td>
<td valign="top">

4 vCPU, 16 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`m6i.2xlarge` \(`m7i.2xlarge`\)

</td>
<td valign="top">

8 vCPU, 32 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`m6i.4xlarge` \(`m7i.4xlarge`\)

</td>
<td valign="top">

16 vCPU, 64 GB RAM

</td>
<td valign="top">

94 Gi

</td>
</tr>
<tr>
<td valign="top">

`m6i.8xlarge` \(`m7i.8xlarge`\)

</td>
<td valign="top">

32 vCPU, 128 GB RAM

</td>
<td valign="top">

158 Gi

</td>
</tr>
<tr>
<td valign="top">

`m6i.12xlarge` \(`m7i.12xlarge`\)

</td>
<td valign="top">

48 vCPU, 192 GB RAM

</td>
<td valign="top">

222 Gi

</td>
</tr>
<tr>
<td valign="top">

`m6i.16xlarge` \(`m7i.16xlarge`\)

</td>
<td valign="top">

64 vCPU, 256 GB RAM

</td>
<td valign="top">

250 Gi

</td>
</tr>
<tr>
<td valign="top">

`m5.large` \(`m7i.large`\)

</td>
<td valign="top">

2 vCPU, 8 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`m5.xlarge` \(`m7i.xlarge`\)

</td>
<td valign="top">

4 vCPU, 16 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`m5.2xlarge` \(`m7i.2xlarge`\)

</td>
<td valign="top">

8 vCPU, 32 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`m5.4xlarge` \(`m7i.4xlarge`\)

</td>
<td valign="top">

16 vCPU, 64 GB RAM

</td>
<td valign="top">

94 Gi

</td>
</tr>
<tr>
<td valign="top">

`m5.8xlarge` \(`m7i.8xlarge`\)

</td>
<td valign="top">

32 vCPU, 128 GB RAM

</td>
<td valign="top">

158 Gi

</td>
</tr>
<tr>
<td valign="top">

`m5.12xlarge` \(`m7i.12xlarge`\)

</td>
<td valign="top">

48 vCPU, 192 GB RAM

</td>
<td valign="top">

222 Gi

</td>
</tr>
<tr>
<td valign="top">

`m5.16xlarge` \(`m7i.16xlarge`\)

</td>
<td valign="top">

64 vCPU, 256 GB RAM

</td>
<td valign="top">

250 Gi

</td>
</tr>
</table>



### Google Cloud

You can use the machine types listed in the table with the following plans:

-   Standard: Google Cloud \(technical name: `gcp`\)
-   Build Runtime: Google Cloud \(technical name: `build-runtime-gcp`\)

**Google Cloud Machine Types**


<table>
<tr>
<th valign="top">

Default Value

</th>
<th valign="top">

Allowed Input

</th>
<th valign="top">

Virtual Machine Size

</th>
<th valign="top">

Default Volume Size

</th>
</tr>
<tr>
<td valign="top" rowspan="7">

`n2-standard-2`

</td>
<td valign="top">

`n2-standard-2`

</td>
<td valign="top">

2 vCPU, 8 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`n2-standard-4`

</td>
<td valign="top">

4 vCPU, 16 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`n2-standard-8`

</td>
<td valign="top">

8 vCPU, 32 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`n2-standard-16`

</td>
<td valign="top">

16 vCPU, 64 GB RAM

</td>
<td valign="top">

94 Gi

</td>
</tr>
<tr>
<td valign="top">

`n2-standard-32`

</td>
<td valign="top">

32 vCPU, 128 GB RAM

</td>
<td valign="top">

158 Gi

</td>
</tr>
<tr>
<td valign="top">

`n2-standard-48`

</td>
<td valign="top">

48 vCPU, 192 GB RAM

</td>
<td valign="top">

222 Gi

</td>
</tr>
<tr>
<td valign="top">

`n2-standard-64`

</td>
<td valign="top">

64 vCPU, 256 GB RAM

</td>
<td valign="top">

250 Gi

</td>
</tr>
</table>



### Microsoft Azure

You can use the machine types listed in the table with the following plans:

-   Standard: Microsoft Azure \(technical name: `azure`\)
-   Build Runtime: Microsoft Azure \(technical name: `build-runtime-azure`\)

The `Standard_D_v3` machine types have been deprecated by Microsoft Azure and can no longer be provisioned. To avoid breaking existing configurations, these inputs are automatically mapped to the equivalent `Standard_Ds_v5` generation, so you do not need to adjust your configurations.

**Microsoft Azure Machine Type Parameter**


<table>
<tr>
<th valign="top">

Default Value

</th>
<th valign="top">

Allowed Input \(Resolved Machine Type\)

</th>
<th valign="top">

Virtual Machine Size

</th>
<th valign="top">

Default Volume Size

</th>
</tr>
<tr>
<td valign="top" rowspan="20">

`Standard_D2s`

</td>
<td valign="top">

`Standard_D2s` \(`Standard_D2s_v5`\)

</td>
<td valign="top">

2 vCPU, 8 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_D4s` \(`Standard_D4s_v5`\)

</td>
<td valign="top">

4 vCPU, 16 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_D8s` \(`Standard_D8s_v5`\)

</td>
<td valign="top">

8 vCPU, 32 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_D16s` \(`Standard_D16s_v5`\)

</td>
<td valign="top">

16 vCPU, 64 GB RAM

</td>
<td valign="top">

94 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_D32s` \(`Standard_D32s_v5`\)

</td>
<td valign="top">

32 vCPU, 128 GB RAM

</td>
<td valign="top">

158 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_D48s` \(`Standard_D48s_v5`\)

</td>
<td valign="top">

48 vCPU, 192 GB RAM

</td>
<td valign="top">

222 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_D64s` \(`Standard_D64s_v5`\)

</td>
<td valign="top">

64 vCPU, 256 GB RAM

</td>
<td valign="top">

250 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_D2s_v5`

</td>
<td valign="top">

2 vCPU, 8 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_D4s_v5`

</td>
<td valign="top">

4 vCPU, 16 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_D8s_v5`

</td>
<td valign="top">

8 vCPU, 32 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_D16s_v5`

</td>
<td valign="top">

16 vCPU, 64 GB RAM

</td>
<td valign="top">

94 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_D32s_v5`

</td>
<td valign="top">

32 vCPU, 128 GB RAM

</td>
<td valign="top">

158 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_D48s_v5`

</td>
<td valign="top">

48 vCPU, 192 GB RAM

</td>
<td valign="top">

222 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_D64s_v5`

</td>
<td valign="top">

64 vCPU, 256 GB RAM

</td>
<td valign="top">

250 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_D4_v3` \(`Standard_D4s_v5`\)

</td>
<td valign="top">

4 vCPU, 16 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_D8_v3` \(`Standard_D8s_v5`\)

</td>
<td valign="top">

8 vCPU, 32 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_D16_v3` \(`Standard_D16s_v5`\)

</td>
<td valign="top">

16 vCPU, 64 GB RAM

</td>
<td valign="top">

94 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_D32_v3` \(`Standard_D32s_v5`\)

</td>
<td valign="top">

32 vCPU, 128 GB RAM

</td>
<td valign="top">

158 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_D48_v3` \(`Standard_D48s_v5`\)

</td>
<td valign="top">

48 vCPU, 192 GB RAM

</td>
<td valign="top">

222 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_D64_v3` \(`Standard_D64s_v5`\)

</td>
<td valign="top">

64 vCPU, 256 GB RAM

</td>
<td valign="top">

250 Gi

</td>
</tr>
</table>

You can use the machine types listed in the table with the Test Demo and Development \(Azure Lite\) \(technical name: `azure_lite`\) plan.

**Azure Lite Machine Types**


<table>
<tr>
<th valign="top">

Default Value

</th>
<th valign="top">

Allowed Input \(Resolved Machine Type\)

</th>
<th valign="top">

Virtual Machine Size

</th>
<th valign="top">

Default Volume Size

</th>
</tr>
<tr>
<td valign="top" rowspan="5">

`Standard_D4s`

</td>
<td valign="top">

`Standard_D2s` \(`Standard_D2s_v5`\)

</td>
<td valign="top">

2 vCPU, 8 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_D4s` \(`Standard_D4s_v5`\)

</td>
<td valign="top">

4 vCPU, 16 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_D2s_v5`

</td>
<td valign="top">

2 vCPU, 8 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_D4s_v5`

</td>
<td valign="top">

4 vCPU, 16 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_D4_v3` \(`Standard_D4s_v5`\)

</td>
<td valign="top">

4 vCPU, 16 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
</table>



### SAP Cloud Infrastructure

You can use the machine types listed in the table with the SAP Cloud Infrastructure \(`sap-converged-cloud`\) plan.

**SAP Cloud Infrastructure Machine Types**


<table>
<tr>
<th valign="top">

Default Value

</th>
<th valign="top">

Allowed Input

</th>
<th valign="top">

Virtual Machine Size

</th>
<th valign="top">

Default Volume Size

</th>
</tr>
<tr>
<td valign="top" rowspan="8">

`g_c2_m8`

</td>
<td valign="top">

`g_c2_m8`

</td>
<td valign="top">

2 vCPU, 8 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`g_c4_m16`

</td>
<td valign="top">

4 vCPU, 16 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`g_c6_m24`

</td>
<td valign="top">

6 vCPU, 24 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`g_c8_m32`

</td>
<td valign="top">

8 vCPU, 32 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`g_c12_m48`

</td>
<td valign="top">

12 vCPU, 48 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`g_c16_m64`

</td>
<td valign="top">

16 vCPU, 64 GB RAM

</td>
<td valign="top">

94 Gi

</td>
</tr>
<tr>
<td valign="top">

`g_c32_m128`

</td>
<td valign="top">

32 vCPU, 128 GB RAM

</td>
<td valign="top">

158 Gi

</td>
</tr>
<tr>
<td valign="top">

`g_c64_m256`

</td>
<td valign="top">

64 vCPU, 256 GB RAM

</td>
<td valign="top">

250 Gi

</td>
</tr>
</table>



### Alibaba Cloud

You can use the machine types listed in the table with the standard Alibaba Cloud \(technical name: `alicloud`\) plan.

**Alibaba Cloud Machine Types**


<table>
<tr>
<th valign="top">

Default Value

</th>
<th valign="top">

Allowed Input

</th>
<th valign="top">

Virtual Machine Size

</th>
<th valign="top">

Default Volume Size

</th>
</tr>
<tr>
<td valign="top" rowspan="7">

`ecs.g9i.large`

</td>
<td valign="top">

`ecs.g9i.large`

</td>
<td valign="top">

2 vCPU, 8GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`ecs.g9i.xlarge`

</td>
<td valign="top">

4 vCPU, 16GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`ecs.g9i.2xlarge`

</td>
<td valign="top">

8 vCPU, 32GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`ecs.g9i.4xlarge`

</td>
<td valign="top">

16 vCPU, 64GB RAM

</td>
<td valign="top">

94 Gi

</td>
</tr>
<tr>
<td valign="top">

`ecs.g9i.8xlarge`

</td>
<td valign="top">

32 vCPU, 128GB RAM

</td>
<td valign="top">

158 Gi

</td>
</tr>
<tr>
<td valign="top">

`ecs.g9i.12xlarge`

</td>
<td valign="top">

48 vCPU, 192GB RAM

</td>
<td valign="top">

222 Gi

</td>
</tr>
<tr>
<td valign="top">

`ecs.g9i.16xlarge`

</td>
<td valign="top">

64 vCPU, 256GB RAM

</td>
<td valign="top">

250 Gi

</td>
</tr>
</table>



### Machine Types in Additional Worker Node Pools

In your additional worker node pools, you can use both the general-purpose and compute-intensive virtual machines. To see the compute-intensive machine types available for specific service plans, expand the table for your preferred IaaS provider.



### Amazon Web Services

You can use the machine types listed in the table with the following plans:

-   Standard: Amazon Web Services \(technical name: `aws`\)
-   Build Runtime: Amazon Web Services \(technical name: `build-runtime-aws`\)

**AWS Machine Types in Additional Worker Node Pools**


<table>
<tr>
<th valign="top">

Allowed Input \(Resolved Machine Type\)

</th>
<th valign="top">

Virtual Machine Size

</th>
<th valign="top">

Default Volume Size

</th>
<th valign="top">

Availability Regions

</th>
</tr>
<tr>
<td valign="top">

`c7i.large`

</td>
<td valign="top">

2 vCPU, 4 GB RAM

</td>
<td valign="top">

80 Gi

</td>
<td valign="top" rowspan="7">

`eu-central-1`

`eu-west-2`

`eu-south-1`

`ca-central-1`

`sa-east-1`

`us-east-1`

`ap-northeast-1`

`ap-northeast-2`

`ap-south-1`

`ap-southeast-1`

`ap-southeast-2`

`us-west-2`

</td>
</tr>
<tr>
<td valign="top">

`c7i.xlarge`

</td>
<td valign="top">

4 vCPU, 8 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`c7i.2xlarge`

</td>
<td valign="top">

8 vCPU, 16 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`c7i.4xlarge`

</td>
<td valign="top">

16 vCPU, 32 GB RAM

</td>
<td valign="top">

94 Gi

</td>
</tr>
<tr>
<td valign="top">

`c7i.8xlarge`

</td>
<td valign="top">

32 vCPU, 64 GB RAM

</td>
<td valign="top">

158 Gi

</td>
</tr>
<tr>
<td valign="top">

`c7i.12xlarge`

</td>
<td valign="top">

48 vCPU, 96 GB RAM

</td>
<td valign="top">

222 Gi

</td>
</tr>
<tr>
<td valign="top">

`c7i.16xlarge`

</td>
<td valign="top">

64 vCPU, 128 GB RAM

</td>
<td valign="top">

250 Gi

</td>
</tr>
<tr>
<td valign="top">

`ri.large` \(`r8i.large`\)

</td>
<td valign="top">

2 vCPU, 16 GB RAM

</td>
<td valign="top">

80 Gi

</td>
<td valign="top" rowspan="7">

`eu-central-1`

`eu-west-2`

`us-east-1`

`us-west-2`

`ap-south-1`

`ap-southeast-2`

</td>
</tr>
<tr>
<td valign="top">

`ri.xlarge` \(`r8i.xlarge`\)

</td>
<td valign="top">

4 vCPU, 32 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`ri.2xlarge` \(`r8i.2xlarge`\)

</td>
<td valign="top">

8 vCPU, 64 GB RAM

</td>
<td valign="top">

94 Gi

</td>
</tr>
<tr>
<td valign="top">

`ri.4xlarge` \(`r8i.4xlarge`\)

</td>
<td valign="top">

16 vCPU, 132 GB RAM

</td>
<td valign="top">

158 Gi

</td>
</tr>
<tr>
<td valign="top">

`ri.8xlarge` \(`r8i.8xlarge`\)

</td>
<td valign="top">

32 vCPU, 256 GB RAM

</td>
<td valign="top">

250 Gi

</td>
</tr>
<tr>
<td valign="top">

`ri.12xlarge` \(`r8i.12xlarge`\)

</td>
<td valign="top">

48 vCPU, 384 GB RAM

</td>
<td valign="top">

250 Gi

</td>
</tr>
<tr>
<td valign="top">

`ri.16xlarge` \(`r8i.16xlarge`\)

</td>
<td valign="top">

64 vCPU, 512 GB RAM

</td>
<td valign="top">

250 Gi

</td>
</tr>
</table>



### Google Cloud

You can use the machine types listed in the table with the following plans:

-   Standard: Google Cloud \(technical name: `gcp`\)
-   Build Runtime: Google Cloud \(technical name: `build-runtime-gcp`\)

**Google Cloud Machine Types in Additional Worker Node Pools**


<table>
<tr>
<th valign="top">

Allowed Input \(Resolved Machine Type\)

</th>
<th valign="top">

Virtual Machine Size

</th>
<th valign="top">

Default Volume Size

</th>
<th valign="top">

Availability Regions

</th>
</tr>
<tr>
<td valign="top">

`c2d-highcpu-2`

</td>
<td valign="top">

2 vCPU, 4 GB RAM

</td>
<td valign="top">

80 GI

</td>
<td valign="top" rowspan="6">

`europe-west3`

`europe-west4`

`us-central1`

`us-west1`

`us-east4`

`asia-southeast1`

`asia-south1`

</td>
</tr>
<tr>
<td valign="top">

`c2d-highcpu-4`

</td>
<td valign="top">

4 vCPU, 8 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`c2d-highcpu-8`

</td>
<td valign="top">

8 vCPU, 16 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`c2d-highcpu-16`

</td>
<td valign="top">

16 vCPU, 32 GB RAM

</td>
<td valign="top">

94 Gi

</td>
</tr>
<tr>
<td valign="top">

`c2d-highcpu-32`

</td>
<td valign="top">

32 vCPU, 64 GB RAM

</td>
<td valign="top">

158 Gi

</td>
</tr>
<tr>
<td valign="top">

`c2d-highcpu-56`

</td>
<td valign="top">

56 vCPU, 112 GB RAM

</td>
<td valign="top">

250 Gi

</td>
</tr>
</table>



### Microsoft Azure

You can use the machine types listed in the table with the following plans:

-   Standard: Microsoft Azure \(technical name: `azure`\)
-   Build Runtime: Microsoft Azure \(technical name: `build-runtime-azure`\)

**Microsoft Azure Machine Types in Additional Worker Node Pools**


<table>
<tr>
<th valign="top">

Allowed Input \(Resolved Machine Type\)

</th>
<th valign="top">

Virtual Machine Size

</th>
<th valign="top">

Default Volume Size

</th>
<th valign="top">

Availability Regions

</th>
</tr>
<tr>
<td valign="top">

`Standard_F2s_v2`

</td>
<td valign="top">

2 vCPU, 4 GB RAM

</td>
<td valign="top">

80 Gi

</td>
<td valign="top" rowspan="7">

All Microsoft Azure regions. See [Region\*](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Region).

</td>
</tr>
<tr>
<td valign="top">

`Standard_F4s_v2`

</td>
<td valign="top">

4 vCPU, 8 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_F8s_v2`

</td>
<td valign="top">

8 vCPU, 16 GB RAM

</td>
<td valign="top">

80 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_F16s_v2`

</td>
<td valign="top">

16 vCPU, 32 GB RAM

</td>
<td valign="top">

94 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_F32s_v2`

</td>
<td valign="top">

32 vCPU, 64 GB RAM

</td>
<td valign="top">

158 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_F48s_v2`

</td>
<td valign="top">

48 vCPU, 96 GB RAM

</td>
<td valign="top">

222 Gi

</td>
</tr>
<tr>
<td valign="top">

`Standard_F64s_v2`

</td>
<td valign="top">

64 vCPU, 128 GB RAM

</td>
<td valign="top">

250 Gi

</td>
</tr>
</table>



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Modules"/>

## Modules

With the *Modules* \(`modules`\) object, you can define which Kyma modules you want to provision in your cluster. You can also use it to create a cluster without any modules.

API for module configuration is built on the `oneOf` feature from the JSON schema. If the `modules` object is passed to API, it must have only one valid option: *Default* \(`default`\) or *Custom* \(`list`\).

Even if you omit the `modules` object from the request, the default Kyma modules are provisioned in your cluster.

> ### Remember:  
> The parameters marked with an asterisk "\*" are mandatory.

**Modules Nested Parameters**


<table>
<tr>
<th valign="top" colspan="2">

Nested Parameter

</th>
<th valign="top" colspan="2">

Description

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

Default Value

</th>
</tr>
<tr>
<td valign="top" colspan="2">

*Default*

btp CLI parameter: `default`

type: boolean

</td>
<td valign="top" colspan="2">

Defines whether to use the default list of Kyma modules. Check the [Default Kyma Modules](https://help.sap.com/docs/btp/sap-business-technology-platform/kyma-modules?locale=en-US&version=Cloud) to find out which modules are in the default modules list.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

`true`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

*Custom*

btp CLI parameter: `list`

type: array of objects

</td>
<td valign="top" colspan="2">

Defines a custom list of Kyma modules.

Leave your custom list of Kyma modules empty if you don't want any modules provisioned.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

\[ \] \(empty array\)

</td>
</tr>
<tr>
<td valign="top" colspan="2">

*Default Module Channel*

btp CLI parameter: `channel`

type: string

</td>
<td valign="top" colspan="2">

Specifies your preferred release channel, regular or fast, for the whole default or custom list of modules.

If needed, you can override this setting for individual modules in your custom list of modules.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

Taken from the `runtimeConfiguration` setting, where the Kyma resource spec channel is specified per plan.

</td>
</tr>
</table>

The *Custom* \(`list`\) parameter includes three nested parameters: *Name\**, *Channel*, and *Custom Resource Policy*.

**Custom list Parameters**


<table>
<tr>
<th valign="top">

Nested Parameter

</th>
<th valign="top">

Description

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

Default Value

</th>
</tr>
<tr>
<td valign="top">

*Name\**

btp CLI parameter: `name`

type: string

</td>
<td valign="top">

Defines the module's technical name. To check the available Kyma modules and their technical names, see [Kyma Modules](../10-concepts/kyma-modules-0dda141.md).

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

n/a

</td>
</tr>
<tr>
<td valign="top">

*Channel*

btp CLI parameter: `channel`

type: string

</td>
<td valign="top">

Defines the preferred release channel. The default is `regular`. The other option is `fast`. See [Kyma Release Channels](../10-concepts/kyma-module-releases-95a4101.md#loio95a410144d7c449687c957da0cc43a0d__section_kyma_release_channels).

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

"" \(an empty string\)

</td>
</tr>
<tr>
<td valign="top">

*Custom Resource Policy*

btp CLI parameter: `customResourcePolicy`

type: string

</td>
<td valign="top">

Specifies whether Kyma manages the module's default custom resource \(CR\).

If you set `customResourcePolicy` to `CreateAndDelete` or leave the field empty, Kyma provides the default module's configuration and applies it during runtime provisioning. This configuration is stored in the default module CR. You can edit this CR at any time, and Kyma doesn't overwrite your changes. When you delete the module, Kyma automatically removes the default module CR.

If you set `customResourcePolicy` to `Ignore`, the module is available in your cluster but it is not installed. Module-related CustomResourceDefinitions \(for example, APIRule for API Gateway module or Istio VirtualService for the Istio module\) are not available until the module is installed. To install the module, you must apply the module CR with your configuration. Before deleting the module, you must delete the CR first. Use this setting when you want to provide your own configuration from the start, for example in automated provisioning workflows where you manage CRs as YAML files.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

"" \(an empty string\)

</td>
</tr>
</table>



### Configuration

If you don't provide the `modules` object in the JSON payload, or if you use the following input, you have the default Kyma modules provisioned in your cluster :

> ### Sample Code:  
> ```
> "modules": { 
>     "default": true 
> } 
> ```

See an example of JSON input for a custom list of Kyma modules.

> ### Sample Code:  
> ```
> "modules": {
>     "list": [
>         {
>             "name": "btp-operator"
>         },
>         {
>             "name": "keda",
>             "channel": "regular",
>             "customResourcePolicy": "CreateAndDelete"
>         }
>     ]
> }
> ```

If you use the following JSON input, Kyma doesn't create the Istio module's default CR and doesn't install Istio CRDs \(such as VirtualServices or Gateways\). To complete the setup, you must apply your own Istio CR. You can set `customResourcePolicy` to `Ignore` for any Kyma module. To configure the module CR, find reference documentation on kyma-project.io. For example, [Istio Custom Resource](https://kyma-project.io/external-content/istio/docs/user/04-00-istio-custom-resource.html).

> ### Sample Code:  
> ```
> "modules": {
>     "list": [
>         {
>             "name": "istio",
>             "customResourcePolicy": "Ignore"
>         }
>     ]
> }
> ```

If you apply the following values, your Kyma runtime is provisioned without any Kyma modules.

> ### Sample Code:  
> ```
> "modules": {
>     "list": []
> }
> ```

> ### Sample Code:  
> ```
> "modules": {
>     "default": false
> }
> ```



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Networking"/>

## Networking

With the *Networking* \(`networking`\) object, you provide networking configuration. These values are immutable and cannot be updated later.

> ### Remember:  
> The parameters marked with an asterisk "\*" are mandatory.

**Networking Nested Parameters**


<table>
<tr>
<th valign="top">

Nested Parameter

</th>
<th valign="top">

Description

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

Default Value

</th>
<th valign="top">

Allowed Input

</th>
</tr>
<tr>
<td valign="top">

*Enable dual stack*

btp CLI parameter: `dualStack`

type: boolean

</td>
<td valign="top">

Enables dual-stack networking \(IPv4 and IPv6\).

> ### Caution:  
> The Istio module does not support the dual-stack mode.

For more information, see [Kyma Runtime with Dual-Stack Support](kyma-runtime-with-dual-stack-support-c9811ea.md).

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

`false` 

</td>
<td valign="top">

`true` or `false`

</td>
</tr>
<tr>
<td valign="top">

*CIDR range for Nodes\**

btp CLI parameter: `nodes`

type: string

</td>
<td valign="top">

Defines a custom IP range for worker nodes.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

10.250.0.0/16

</td>
<td valign="top">

The CIDR range for nodes must not overlap with the following CIDRs: 10.242.0.0/16, 10.64.0.0/11, 10.254.0.0/16, 10.243.0.0/16, 192.168.123.0/24, 240.0.0.0/8.

Also, the range for nodes must not overlap with those used for Pods or Services. The same restriction applies to the default ranges set for Pods or Services if you don’t provide your own.

</td>
</tr>
<tr>
<td valign="top">

*CIDR range for Pods*

btp CLI parameter: `pods`

type: string

</td>
<td valign="top">

Defines a custom IP range for Pods.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

10.96.0.0/13

</td>
<td valign="top">

CIDR range for Pods must not overlap with the following CIDRs: 10.242.0.0/16, 10.64.0.0/11, 10.254.0.0/16, 10.243.0.0/16, 192.168.123.0/24, 240.0.0.0/8.

Also, the range for Pods must not overlap with those used for nodes or Services. The same restriction applies to the default range set for Services if you don’t provide your own.

</td>
</tr>
<tr>
<td valign="top">

*CIDR range for Services*

btp CLI parameter: `services`

type: string

</td>
<td valign="top">

Defines a custom IP range for Services.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

10.104.0.0/13

</td>
<td valign="top">

CIDR range for Services must not overlap with the following CIDRs: 10.242.0.0/16, 10.64.0.0/11, 10.254.0.0/16, 10.243.0.0/16, 192.168.123.0/24, 240.0.0.0/8.

Also, the range for Services must not overlap with those used for nodes or Pods. The same restriction applies to the default range set for Pods if you don’t provide your own.

</td>
</tr>
</table>

See the default JSON input for the `networking` object:

> ### Sample Code:  
> ```
> "networking": {
>         "nodes": "10.250.0.0/16",
>         "pods": "10.96.0.0/13",
>         "services": "10.104.0.0/13"
>     }
> ```



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_OIDC"/>

## OpenID Connect \(OIDC\)

With the *OpenID Connect* \(OIDC\) \(`oidc`\) parameter, you can configure a custom identity provider. You can configure the property in the following ways:

-   As a list of `oidc` objects \(recommended\)
-   As a single `oidc` object



### OIDC Configured as a List of `oidc` Objects

The*OpenID Connect* property is a list of `oidc` objects. You can use it to configure one or several `oidc` objects.

> ### Remember:  
> The parameters marked with an asterisk "\*" are mandatory.

**OIDC Parameters for a List of oidc Objects**


<table>
<tr>
<th valign="top">

Nested Parameter

</th>
<th valign="top">

Description

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

Default Value

</th>
<th valign="top">

Allowed Input

</th>
</tr>
<tr>
<td valign="top">

*Client ID\**

btp CLI parameter: `clientID`

type: string

</td>
<td valign="top">

The client ID for the OpenID Connect client.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

n/a

</td>
<td valign="top">

n/a

</td>
</tr>
<tr>
<td valign="top">

*Issuer URL\**

btp CLI parameter: `issuerURL`

type: string

</td>
<td valign="top">

Provides the URL of the OpenID issuer.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

n/a

</td>
<td valign="top">

Only HTTPS scheme is accepted.

</td>
</tr>
<tr>
<td valign="top">

*Groups Claim\**

btp CLI parameter: `groupsClaim`

type: string

</td>
<td valign="top">

If provided, specifies the name of a custom OIDC claim for identifying user groups.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

n/a

</td>
<td valign="top">

n/a

</td>
</tr>
<tr>
<td valign="top">

*Groups Prefix\**

btp CLI parameter: `groupsPrefix`

type: string

</td>
<td valign="top">

If specified, causes claims mapping to group names to be prefixed with the provided value.

If not provided, the prefix defaults to `-` \(dash character without additional characters\), which disables prefixing.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

n/a

</td>
<td valign="top">

For example, the value `oidc:` results in groups like `oidc:engineering` and `oidc:marketing`.

To skip any prefixing, provide the value `-` \(dash character without additional characters\).

</td>
</tr>
<tr>
<td valign="top">

*Username Claim\**

btp CLI parameter: `usernameClaim`

type: string

</td>
<td valign="top">

Provides the OpenID claim to use as the user name.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

n/a

</td>
<td valign="top">

n/a

</td>
</tr>
<tr>
<td valign="top">

*Required Claims*

btp CLI parameter: `requiredClaims`

type: array

</td>
<td valign="top">

Describes a required claim in the ID Token.

If set, the claim is verified to be present in the ID Token with the matching value.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

n/a

</td>
<td valign="top">

List of key=value pairs.

To remove a previously set value, leave the array empty.

</td>
</tr>
<tr>
<td valign="top">

*Signing Algs\**

btp CLI parameter: `signingAlgs`

type: array

</td>
<td valign="top">

Provides the OIDC signing algorithms for Kyma runtime.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

n/a

</td>
<td valign="top">

Comma-separated list of allowed JOSE asymmetric signing algorithms, for example, `RS256`, `ES256`.

</td>
</tr>
<tr>
<td valign="top">

*Username Prefix\**

btp CLI parameter: `usernamePrefix`

type: string

</td>
<td valign="top">

Provides an OIDC username prefix for Kyma runtime.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

n/a

</td>
<td valign="top">

To skip any prefixing, provide the value `-` \(dash character without additional characters\).

</td>
</tr>
<tr>
<td valign="top">

*Encoded JWKS Array*

btp CLI parameter: `encodedJwksArray`

type: string

</td>
<td valign="top">

The JSON Web Key Set \(JWKS\) array encoded in base64.

Use it when your OIDC metadata discovery endpoint is inaccessible from the public internet.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

n/a

</td>
<td valign="top">

Base64 encoded string.

To remove a previously set value, leave the input empty.

</td>
</tr>
</table>

The following example shows the default configuration of a list of `oidc` objects. To revert your changes to the default settings, copy and paste the following values:

> ### Sample Code:  
> ```
> "oidc": {
>   "list": [
>     {
>       "clientID": "12b13a26-d993-4d0c-aa08-5f5852bbdff6",
>       "groupsClaim": "groups",
>       "issuerURL": "https://kyma.accounts.ondemand.com",
>       "groupsPrefix": "-",
>       "signingAlgs": ["RS256"],
>       "usernameClaim": "sub",
>       "usernamePrefix": "-",
>       "requiredClaims": [],
>       "encodedJwksArray": ""
>     }
>   ]
> }
> ```

For more configuration options, see [Custom OpenID Connect Configuration](custom-openid-connect-configuration-97fc95d.md).



### OIDC Configured as a Single `oidc` Object

This approach is not recommended. Use it only to maintain backward compatibility with existing automations.

> ### Remember:  
> The parameters marked with an asterisk "\*" are mandatory.

**OIDC Parameters for a Single oidc Object**


<table>
<tr>
<th valign="top">

Nested Parameter

</th>
<th valign="top">

Description

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

Default Value

</th>
<th valign="top">

Allowed Input

</th>
</tr>
<tr>
<td valign="top">

*Client ID\**

btp CLI parameter: `clientID`

type: string

</td>
<td valign="top">

The client ID for the OpenID Connect client.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

n/a

</td>
<td valign="top">

n/a

</td>
</tr>
<tr>
<td valign="top">

*Issuer URL\**

btp CLI parameter: `issuerURL`

type: string

</td>
<td valign="top">

Provides the URL of the OpenID issuer.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

n/a

</td>
<td valign="top">

Only HTTPS scheme is accepted.

</td>
</tr>
<tr>
<td valign="top">

*Groups Claim*

btp CLI parameter: `groupsClaim`

type: string

</td>
<td valign="top">

If provided, specifies the name of a custom OIDC claim for specifying user groups.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

`groups`

</td>
<td valign="top">

n/a

</td>
</tr>
<tr>
<td valign="top">

*Groups Prefix*

btp CLI parameter: `groupsPrefix`

type: string

</td>
<td valign="top">

If specified, causes claims mapping to group names to be prefixed with the provided value.

If not provided, the prefix defaults to `-` \(dash character without additional characters\), and disables prefixing.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

`-`

</td>
<td valign="top">

For example, the value `oidc:` results in groups like `oidc:engineering` and `oidc:marketing`.

To skip any prefixing, provide the value `-` \(dash character without additional characters\).

</td>
</tr>
<tr>
<td valign="top">

*Username Claim*

btp CLI parameter: `usernameClaim`

type: string

</td>
<td valign="top">

Provides the OpenID claim to use as the user name.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

n/a

</td>
<td valign="top">

n/a

</td>
</tr>
<tr>
<td valign="top">

*Required Claims*

btp CLI parameter: `requiredClaims`

type: array

</td>
<td valign="top">

Describes a required claim in the ID Token.

If set, the claim is verified to be present in the ID Token with the matching value.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

n/a

</td>
<td valign="top">

List of key=value pairs.

To remove a previously set value, provide only the value `-` \(dash character without additional characters\).

</td>
</tr>
<tr>
<td valign="top">

*Signing Algs*

btp CLI parameter: `signingAlgs`

type: array

</td>
<td valign="top">

Provides the OIDC signing algorithms for Kyma runtime.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

`RS256`

</td>
<td valign="top">

Comma-separated list of allowed JOSE asymmetric signing algorithms, for example, `RS256`, `ES256`.

</td>
</tr>
<tr>
<td valign="top">

*Username Prefix*

btp CLI parameter: `usernamePrefix`

type: string

</td>
<td valign="top">

Provides an OIDC username prefix for Kyma runtime.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

`-`

</td>
<td valign="top">

To skip any prefixing, provide the value `-` \(dash character without additional characters\).

</td>
</tr>
<tr>
<td valign="top">

*Encoded JWKS Array*

btp CLI parameter: `encodedJwksArray`

type: string

</td>
<td valign="top">

The JSON Web Key Set \(JWKS\) array encoded in base64.

Use it when your OIDC metadata discovery endpoint is inaccessible from the public internet.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

n/a

</td>
<td valign="top">

Base64 encoded string.

To remove a previously set value, provide only the value `-` \(dash character without additional characters\).

</td>
</tr>
</table>

The following example shows the default configuration of an `oidc` object. To revert your changes to the default settings, copy and paste the following values:

```
{
  ...
  "oidc" : {
    "clientID" : "12b13a26-d993-4d0c-aa08-5f5852bbdff6",
    "issuerURL" : "https://kyma.accounts.ondemand.com",
    "groupsClaim" : "groups",
    "groupsPrefix" : "-",
    "signingAlgs" : ["RS256"],
    "usernamePrefix" : "-",
    "usernameClaim" : "sub",
    "requiredClaims" : ["-"],
    "encodedJwksArray": "-"
  }
  ...
}
```

For more configuration options, see [Custom OpenID Connect Configuration](custom-openid-connect-configuration-97fc95d.md).



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Region"/>

## Region\*

Use the *Region\** \(`region`\) parameter \(string\) to define a region where your cluster runs.

> ### Remember:  
> The parameters marked with an asterisk "\*" are mandatory.

**Region Parameter**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

Default Value

</th>
<th valign="top">

Allowed Input

</th>
</tr>
<tr>
<td valign="top">

*Region\**

btp CLI parameter: `region`

type: string

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

None

</td>
<td valign="top">

Varies by plan. Expand the table for your preferred IaaS provider for the full list of available regions.

</td>
</tr>
</table>

Here is an example of the JSON input for the *Region* parameter:

> ### Sample Code:  
> ```
> "region": "us-east-1"
> ```

The available regions vary by IaaS provider. Expand the table for your preferred provider to see the supported regions for specific service plans.



### Amazon Web Services

You can use the regions listed in the table with the following plans:

-   Standard: Amazon Web Services \(`aws`\)
-   Free \(`free`\)
-   Build Runtime: Amazon Web Services \(`build-runtime-aws`\)

**Amazon Web Services Regions**


<table>
<tr>
<th valign="top">

Region Technical Key

</th>
<th valign="top">

Region Name

</th>
</tr>
<tr>
<td valign="top">

`eu-central-1`

</td>
<td valign="top">

Europe \(Frankfurt\)<sup>[7](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_colocate_cp)</sup>

</td>
</tr>
<tr>
<td valign="top">

`eu-west-2`

</td>
<td valign="top">

Europe \(London\) <sup>[7](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_colocate_cp)</sup>

</td>
</tr>
<tr>
<td valign="top">

`eu-south-1`

</td>
<td valign="top">

Europe \(Milan\) <sup>[7](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_colocate_cp)</sup>

</td>
</tr>
<tr>
<td valign="top">

`ca-central-1`

</td>
<td valign="top">

Canada \(Montreal\) <sup>[7](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_colocate_cp)</sup>

</td>
</tr>
<tr>
<td valign="top">

`sa-east-1`

</td>
<td valign="top">

Brazil \(São Paulo\)

</td>
</tr>
<tr>
<td valign="top">

`us-east-1`

</td>
<td valign="top">

US East \(VA\)<sup>[7](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_colocate_cp)</sup>

</td>
</tr>
<tr>
<td valign="top">

`us-west-2`

</td>
<td valign="top">

US West \(Oregon\)<sup>[7](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_colocate_cp)</sup>

</td>
</tr>
<tr>
<td valign="top">

`ap-northeast-1`

</td>
<td valign="top">

Japan \(Tokyo\)

</td>
</tr>
<tr>
<td valign="top">

`ap-northeast-2`

</td>
<td valign="top">

South Korea \(Seoul\)<sup>[7](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_colocate_cp)</sup>

</td>
</tr>
<tr>
<td valign="top">

`ap-south-1`

</td>
<td valign="top">

India \(Mumbai\) <sup>[7](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_colocate_cp)</sup>

</td>
</tr>
<tr>
<td valign="top">

`ap-southeast-1`

</td>
<td valign="top">

Singapore<sup>[7](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_colocate_cp)</sup>

</td>
</tr>
<tr>
<td valign="top">

`ap-southeast-2`

</td>
<td valign="top">

Australia \(Sydney\)<sup>[7](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_colocate_cp)</sup>

</td>
</tr>
</table>



### Google Cloud Regions

You can use the regions listed in the table with the following plans:

-   Standard: Google Cloud \(`gcp`\)
-   Build Runtime: Google Cloud \(`build-runtime-gcp`\)

**Google Cloud Regions**


<table>
<tr>
<th valign="top">

Region Technical Key

</th>
<th valign="top">

Region Name

</th>
</tr>
<tr>
<td valign="top">

`europe-west3`

</td>
<td valign="top">

Europe \(Frankfurt\) <sup>[7](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_colocate_cp)</sup>

</td>
</tr>
<tr>
<td valign="top">

`europe-west4`

</td>
<td valign="top">

Europe \(Netherlands\)

</td>
</tr>
<tr>
<td valign="top">

`us-central1`

</td>
<td valign="top">

US Central \(IA\)<sup>[7](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_colocate_cp)</sup>

</td>
</tr>
<tr>
<td valign="top">

`us-west1`

</td>
<td valign="top">

North America \(Oregon\)

</td>
</tr>
<tr>
<td valign="top">

`us-east4`

</td>
<td valign="top">

North America \(Virginia\)<sup>[7](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_colocate_cp)</sup>

</td>
</tr>
<tr>
<td valign="top">

`southamerica-east1`

</td>
<td valign="top">

Brazil \(São Paulo\)

</td>
</tr>
<tr>
<td valign="top">

`asia-south1`

</td>
<td valign="top">

India \(Mumbai\)<sup>[7](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_colocate_cp)</sup>

</td>
</tr>
<tr>
<td valign="top">

`asia-south2`

</td>
<td valign="top">

India \(Delhi\) <sup>[7](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_colocate_cp)</sup>

</td>
</tr>
<tr>
<td valign="top">

`asia-northeast2`

</td>
<td valign="top">

Japan \(Osaka\)

</td>
</tr>
<tr>
<td valign="top">

`asia-northeast1`

</td>
<td valign="top">

Japan \(Tokyo\) <sup>[7](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_colocate_cp)</sup>

</td>
</tr>
<tr>
<td valign="top">

`asia-southeast1`

</td>
<td valign="top">

Singapore \(Jurong West\)

</td>
</tr>
<tr>
<td valign="top">

`australia-southeast1`

</td>
<td valign="top">

Australia \(Sydney\)

</td>
</tr>
<tr>
<td valign="top">

`me-central2`

</td>
<td valign="top">

KSA \(Dammam\) <sup>[7](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_colocate_cp)</sup>

</td>
</tr>
<tr>
<td valign="top">

`me-west1`

</td>
<td valign="top">

Israel \(Tel Aviv\)

</td>
</tr>
</table>



### Microsoft Azure Regions

You can use the regions listed in the table with the following plans:

-   Standard: Microsoft Azure \(`azure`\)
-   Kyma Test Demo and Development \(Azure Lite\) \(`azure_lite`\)
-   Build Runtime: Microsoft Azure \(`build-runtime-azure`\)

**Microsoft Azure Regions**


<table>
<tr>
<th valign="top">

Region Technical Key

</th>
<th valign="top">

Region Name

</th>
</tr>
<tr>
<td valign="top">

`eastus`

</td>
<td valign="top">

US East \(VA\)<sup>[7](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_colocate_cp)</sup>

</td>
</tr>
<tr>
<td valign="top">

`eastus2`

</td>
<td valign="top">

US East 2 \(VA\)

</td>
</tr>
<tr>
<td valign="top">

`centralus`

</td>
<td valign="top">

US Central \(IA\)

</td>
</tr>
<tr>
<td valign="top">

`westus2`<sup></sup>

</td>
<td valign="top">

US West \(WA\)<sup>[7](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_colocate_cp)</sup>

</td>
</tr>
<tr>
<td valign="top">

`uksouth`

</td>
<td valign="top">

UK South \(London\)

</td>
</tr>
<tr>
<td valign="top">

`germanywestcentral`

</td>
<td valign="top">

Europe \(Frankfurt\)

</td>
</tr>
<tr>
<td valign="top">

`northeurope`

</td>
<td valign="top">

North EU \(Ireland\)

</td>
</tr>
<tr>
<td valign="top">

`westeurope`<sup></sup>

</td>
<td valign="top">

Europe \(Netherlands\)<sup>[7](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_colocate_cp)</sup>

</td>
</tr>
<tr>
<td valign="top">

`switzerlandnorth`

</td>
<td valign="top">

Switzerland \(Zurich\)<sup>[7](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_colocate_cp)</sup>, <sup>[8](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_not_azure_lite)</sup>

</td>
</tr>
<tr>
<td valign="top">

`japaneast`

</td>
<td valign="top">

Japan \(Tokyo\) <sup>[7](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_colocate_cp)</sup>

</td>
</tr>
<tr>
<td valign="top">

`southeastasia`

</td>
<td valign="top">

Singapore

</td>
</tr>
<tr>
<td valign="top">

`australiaeast`<sup></sup>

</td>
<td valign="top">

Australia \(Sydney\)<sup>[7](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_colocate_cp)</sup>

</td>
</tr>
<tr>
<td valign="top">

`brazilsouth`

</td>
<td valign="top">

Brazil \(São Paulo\)

</td>
</tr>
<tr>
<td valign="top">

`canadacentral`

</td>
<td valign="top">

Canada \(Toronto\)

</td>
</tr>
<tr>
<td valign="top">

`chinanorth3`

</td>
<td valign="top">

China \(North 3\) <sup>[9](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_china_on_azure)</sup>

</td>
</tr>
</table>

<sup>8</sup> Not available with the `azure_lite` plan.

<sup>9</sup> This region is available only in the subaccount region cf-cn20 and is the sole region available within the Microsoft Azure \(`azure`\) plan in China.



### SAP Cloud Infrastructure Regions

You can use the regions listed in the table with the SAP Cloud Infrastructure \(`sap-converged-cloud`\) plan.

For the exact mapping between the subaccount regions and the available IaaS regions, see [Regions for the Kyma Environment](../10-concepts/regions-for-the-kyma-environment-557ec3a.md).

**Region Parameter**


<table>
<tr>
<th valign="top">

Region Technical Key

</th>
<th valign="top">

Region Name

</th>
</tr>
<tr>
<td valign="top">

`eu-de-1`

</td>
<td valign="top">

Germany \(Rot\)<sup>[7](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_colocate_cp)</sup>

</td>
</tr>
<tr>
<td valign="top">

`eu-de-2`

</td>
<td valign="top">

Germany \(Frankfurt\)

</td>
</tr>
<tr>
<td valign="top">

`na-us-1`

</td>
<td valign="top">

US East \(Sterling\)<sup>[7](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__footnote_colocate_cp)</sup>

</td>
</tr>
<tr>
<td valign="top">

`na-us-2`

</td>
<td valign="top">

US West \(Colorado\)

</td>
</tr>
<tr>
<td valign="top">

`ap-au-1`

</td>
<td valign="top">

Australia \(Sydney\)

</td>
</tr>
<tr>
<td valign="top">

`ap-jp-1`

</td>
<td valign="top">

Japan \(Tokyo\)

</td>
</tr>
<tr>
<td valign="top">

`ap-ae-1`

</td>
<td valign="top">

UAE \(Dubai\)

</td>
</tr>
</table>



### Alibaba Cloud Regions

You can use the regions listed in the table with the Alibaba Cloud \(`alicloud`\) plan.

**Alibaba Cloud Regions**


<table>
<tr>
<th valign="top">

Region Technical Key

</th>
<th valign="top">

Region Name

</th>
</tr>
<tr>
<td valign="top">

`cn-shanghai`

</td>
<td valign="top">

China \(Shanghai\)

</td>
</tr>
</table>

<sup>7</sup> Supports the *Colocate Control Plane* feature. For more information, see [Colocate Control Plane](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_shoot_and_seed).

**Related Information**  


[Creating Kyma Instances](creating-kyma-instances-09dd313.md "Set up a Kubernetes cluster with SAP BTP, Kyma runtime and use it to build applications and extensions to your SAP and third-party solutions. You can create one or multiple Kyma clusters in a single SAP BTP subaccount.")

[Available Plans in the Kyma Environment](available-plans-in-the-kyma-environment-befe01d.md "Depending on your global account type, you have access to a different plan that specifies the cluster parameters for the Kyma environment.")

[Regions for the Kyma Environment](../10-concepts/regions-for-the-kyma-environment-557ec3a.md "To work with the Kyma environment, you must specify the region for both your subaccount and the cluster.")

[Kyma Modules](../10-concepts/kyma-modules-0dda141.md "With Kyma's modular approach, you can install just the modules you need, instead of a predefined set of components.")

[Account Administration Using the SAP BTP Command Line Interface \(btp CLI\)](account-administration-using-the-sap-btp-command-line-interface-btp-cli-7c6df2d.md "Use the SAP BTP command line interface (btp CLI) for all account administration tasks, such as creating or updating subaccounts, authorization management, and working with service brokers and platforms. It is an alternative to the SAP BTP cockpit for users who like to work in a terminal or want to automate operations using scripts.")

