<!-- loioe2e13bfaa2f54a4fb179f0f1f840353a -->

# Provisioning and Updating Parameters in the Kyma Environment

You can configure the cluster parameters in the Kyma environment.



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_qzp_1wv_yzb"/>

## Overview

To configure the cluster parameters, you can use your preferred interface, the SAP BTP cockpit or the SAP BTP command line interface.

To check which parameters are available for configuration in a particular plan, see [Available Plans in the Kyma Environment](available-plans-in-the-kyma-environment-befe01d.md).

> ### Remember:  
> The parameters marked with an asterisk "\*" are mandatory.

These are the configurable cluster parameters:

-   [Additional Worker Node Pools](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Additional_WN_Pools)
-   [Administrators](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Administrators)
-   [Auto Scaler Max](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Auto_Scaler_Max)
-   [Auto Scaler Min](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Auto_Scaler_Min)
-   [Cluster Name\*](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Cluster_Name)
-   [Machine Type](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Machine_Type)
    -   [Machine Type in Additional Worker Node Pools](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__Additional_machine_types)

-   [Modules](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Modules)
-   [Networking](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Networking)
-   [OpenID Connect \(OIDC\)](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_OIDC)
-   [Region\*](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Region)
-   [Shoot and Seed Same Region](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_shoot_and_seed)



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Additional_WN_Pools"/>

## Additional Worker Node Pools

The *Additional Worker Node Pools* \(`additionalWorkerNodePools`\) array is an optional provisioning and updating parameter used for adding customized worker node pools to your Kyma runtime. It enables you to introduce worker nodes optimized and reserved for your particular workload requirements.

If you do not provide the `additionalWorkerNodePools` array in the provisioning request, no additional worker node pools are created.

If you do not provide the `additionalWorkerNodePools` array in the update request, the saved additional worker node pools stay unchanged. However, if you provide an empty array in the update request, all existing additional worker node pools are removed. If you rename your existing additional worker node pool, it is deleted and a new one is created.

See also [Assigning Workloads to Worker Node Pools](assigning-workloads-to-worker-node-pools-1bf21c1.md).

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

`name`

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

`machineType`

type: string

</td>
<td valign="top">

Specifies the provider-specific virtual machine type.

</td>
<td valign="top">

Provisioning

Updating <sup>[1](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__AWNP_footnote)</sup>

</td>
<td valign="top">

See [Machine Type](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Machine_Type).

</td>
</tr>
<tr>
<td valign="top">

*High Availability Zones\**

`haZones`

type: boolean

</td>
<td valign="top">

Specifies if high availability zones are supported. This setting is permanent and cannot be updated.

If enabled, your resources are distributed across three zones to enhance fault tolerance.

If high availability is disabled, all resources are placed in a single, randomly selected zone. Disabling `haZones` is not recommended for production environments.

High availability is not supported in the `azure_lite` plan.

</td>
<td valign="top">

Provisioning

Updating <sup>[1](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__AWNP_footnote)</sup>

</td>
<td valign="top">

`true` or `false`

</td>
</tr>
<tr>
<td valign="top">

*Auto Scaler Min\**

`autoScalerMin`

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

`autoScalerMax`

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
</table>

> ### Note:  
> <sup>1</sup> You can only use this parameter to update your Kyma runtime by creating a new additional worker node pool. You cannot use it to update an existing additional worker node pool.

See the example configuration:

> ### Sample Code:  
> ```
>    "additionalWorkerNodePools": [
>       {
>          "name": "worker-1",
>          "machineType": "Standard_D2s_v5",
>          "haZones": true,
>          "autoScalerMin": 3,
>          "autoScalerMax": 20
>       },
>       {
>          "name": "worker-2",
>          "machineType": "Standard_D4s_v5",
>          "haZones": false,
>          "autoScalerMin": 1,
>          "autoScalerMax": 1
>       }
>    ]
> ```

See also [Assigning Workloads to Worker Node Pools](assigning-workloads-to-worker-node-pools-1bf21c1.md).



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Administrators"/>

## Administrators

The *Administrators* \(`administrators`\) parameter is an array of strings. It is a provisioning and updating parameter, which specifies the list of runtime administrators. Complete the list with the administrators' email addresses as shown in the following example:

> ### Sample Code:  
> ```
> "administrators": [
>         "example_1@mail.com",
>         "example_2@mail.com",
>         "example_3@mail.com"
>     ]
> ```



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Auto_Scaler_Max"/>

## Auto Scaler Max

The *Auto Scaler Max* \(`autoScalerMax`\) is an integer parameter, which specifies the maximum number of virtual machines you can create.

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

Standard

technical names: `aws`, `gcp`, `azure`

Build Runtime

technical names: `build-runtime-aws`, `build-runtime-gcp`, or `build-runtime-azure`

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
</table>

See the default JSON input:

> ### Sample Code:  
> ```
> "autoScalerMax": 20
> ```



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Auto_Scaler_Min"/>

## Auto Scaler Min

The *Auto Scaler Min* \(`autoScalerMin`\) is an integer parameter, which specifies the minimum number of virtual machines you can create.

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

Standard

technical names: `aws`, `gcp`, `azure`

Build Runtime

technical names: `build-runtime-aws`, `build-runtime-gcp`, or `build-runtime-azure`

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
</table>

See an example of the JSON input:

> ### Sample Code:  
> ```
> "autoScalerMin": 3
> ```



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Cluster_Name"/>

## Cluster Name\*

The *Cluster Name* \(`name`\) is a string, which provides the name of your cluster.

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

</td>
<td valign="top">

Automatically generated as your Subaccount’s Subdomain.

</td>
<td valign="top">

Short string of up to 32 characters that contains only alphanumeric characters \(A-Z, a-z, 0–9\), periods, underscores, and hyphens. It must not contain whitespace characters.

</td>
</tr>
</table>



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Machine_Type"/>

## Machine Type

The *Machine Type* \(`machineType`\) parameter is a string, which specifies the provider-specific virtual machine type.

**Machine Type Parameter**


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

Allowed Input

</th>
<th valign="top">

Virtual Machine Size

</th>
</tr>
<tr>
<td valign="top" rowspan="14">

Standard: Amazon Web Services

technical name: `aws`

Build Runtime: Amazon Web Services

technical name: `build-runtime-aws`

</td>
<td valign="top" rowspan="14">

Provisioning

Updating

</td>
<td valign="top" rowspan="14">

`m6i.large`

</td>
<td valign="top">

`m6i.large`

</td>
<td valign="top">

2 vCPU, 8 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`m6i.xlarge`

</td>
<td valign="top">

4 vCPU, 16 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`m6i.2xlarge`

</td>
<td valign="top">

8 vCPU, 32 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`m6i.4xlarge`

</td>
<td valign="top">

16 vCPU, 64 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`m6i.8xlarge`

</td>
<td valign="top">

32 vCPU, 128 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`m6i.12xlarge`

</td>
<td valign="top">

48 vCPU, 192 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`m6i.16xlarge`

</td>
<td valign="top">

64 vCPU, 256 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`m5.large`

</td>
<td valign="top">

2 vCPU, 8 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`m5.xlarge`

</td>
<td valign="top">

4 vCPU, 16 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`m5.2xlarge`

</td>
<td valign="top">

8 vCPU, 32 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`m5.4xlarge`

</td>
<td valign="top">

16 vCPU, 64 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`m5.8xlarge`

</td>
<td valign="top">

32 vCPU, 128 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`m5.12xlarge`

</td>
<td valign="top">

48 vCPU, 192 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`m5.16xlarge`

</td>
<td valign="top">

64 vCPU, 256 GB RAM

</td>
</tr>
<tr>
<td valign="top" rowspan="7">

Standard: Google Cloud

technical name: `gcp`

Build Runtime: Google Cloud

technical name: `build-runtime-gcp`

</td>
<td valign="top" rowspan="7">

Provisioning

Updating

</td>
<td valign="top" rowspan="7">

`n2-standard-2`

</td>
<td valign="top">

`n2-standard-2`

</td>
<td valign="top">

2 vCPU, 8 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`n2-standard-4`

</td>
<td valign="top">

4 vCPU, 16 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`n2-standard-8`

</td>
<td valign="top">

8 vCPU, 32 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`n2-standard-16`

</td>
<td valign="top">

16 vCPU, 64 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`n2-standard-32`

</td>
<td valign="top">

32 vCPU, 128 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`n2-standard-48`

</td>
<td valign="top">

48 vCPU, 192 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`n2-standard-64`

</td>
<td valign="top">

64 vCPU, 256 GB RAM

</td>
</tr>
<tr>
<td valign="top" rowspan="13">

Standard: Microsoft Azure

technical name: `azure`

Build Runtime: Microsoft Azure

technical name: `build-runtime-azure`

</td>
<td valign="top" rowspan="13">

Provisioning

Updating

</td>
<td valign="top" rowspan="13">

`Standard_D2s_v5`

</td>
<td valign="top">

`Standard_D2s_v5`

</td>
<td valign="top">

2 vCPU, 8 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_D4s_v5`

</td>
<td valign="top">

4 vCPU, 16 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_D8s_v5`

</td>
<td valign="top">

8 vCPU, 32 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_D16s_v5`

</td>
<td valign="top">

16 vCPU, 64 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_D32s_v5`

</td>
<td valign="top">

32 vCPU, 128 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_D48s_v5`

</td>
<td valign="top">

48 vCPU, 192 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_D64s_v5`

</td>
<td valign="top">

64 vCPU, 256 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_D4_v3`

</td>
<td valign="top">

4 vCPU, 16 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_D8_v3`

</td>
<td valign="top">

8 vCPU, 32 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_D16_v3`

</td>
<td valign="top">

16 vCPU, 64 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_D32_v3`

</td>
<td valign="top">

32 vCPU, 128 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_D48_v3`

</td>
<td valign="top">

48 vCPU, 192 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_D64_v3`

</td>
<td valign="top">

64 vCPU, 256 GB RAM

</td>
</tr>
<tr>
<td valign="top" rowspan="2">

Kyma Test Demo and Development \(Azure Lite\)

technical name: `azure_lite`

</td>
<td valign="top" rowspan="2">

Provisioning

Updating

</td>
<td valign="top" rowspan="2">

`Standard_D4s_v5`

</td>
<td valign="top">

`Standard_D4s_v5`

</td>
<td valign="top">

4 vCPU, 16 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_D4_v3`

</td>
<td valign="top">

4 vCPU, 16 GB RAM

</td>
</tr>
</table>

See an example input for the *Machine Type* parameter:

> ### Sample Code:  
> ```
> "machineType": "m5.xlarge"
> ```



### Machine Type in Additional Worker Node Pools

> ### Note:  
> The virtual machines in the following table are only available for use in [Additional Worker Node Pools](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Additional_WN_Pools).

**Machine Type in Additional Worker Node Pools**


<table>
<tr>
<th valign="top">

Plan

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

Allowed Input

</th>
<th valign="top">

Virtual Machine Size

</th>
<th valign="top">

Availability Regions

</th>
</tr>
<tr>
<td valign="top" rowspan="7">

Standard: Amazon Web Services

technical name: `aws`

Build Runtime: Amazon Web Services

technical name: `build-runtime-aws`

</td>
<td valign="top" rowspan="7">

Provisioning

Updating

</td>
<td valign="top">

`c7i.large`

</td>
<td valign="top">

2 vCPU, 4 GB RAM

</td>
<td valign="top" rowspan="7">

All Amazon Web Services regions. See [Region\*](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Region).

</td>
</tr>
<tr>
<td valign="top">

`c7i.xlarge`

</td>
<td valign="top">

4 vCPU, 8 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`c7i.2xlarge`

</td>
<td valign="top">

8 vCPU, 16 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`c7i.4xlarge`

</td>
<td valign="top">

16 vCPU, 32 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`c7i.8xlarge`

</td>
<td valign="top">

32 vCPU, 64 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`c7i.12xlarge`

</td>
<td valign="top">

48 vCPU, 96 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`c7i.16xlarge`

</td>
<td valign="top">

64 vCPU, 128 GB RAM

</td>
</tr>
<tr>
<td valign="top" rowspan="6">

Standard: Google Cloud

technical name: `gcp`

Build Runtime: Google Cloud

technical name: `build-runtime-gcp`

</td>
<td valign="top" rowspan="6">

Provisioning

Updating

</td>
<td valign="top">

`c2d-highcpu-2`

</td>
<td valign="top">

2 vCPU, 4 GB RAM

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
</tr>
<tr>
<td valign="top">

`c2d-highcpu-8`

</td>
<td valign="top">

8 vCPU, 16 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`c2d-highcpu-16`

</td>
<td valign="top">

16 vCPU, 32 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`c2d-highcpu-32`

</td>
<td valign="top">

32 vCPU, 64 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`c2d-highcpu-56`

</td>
<td valign="top">

56 vCPU, 112 GB RAM

</td>
</tr>
<tr>
<td valign="top" rowspan="7">

Standard: Microsoft Azure

technical name: `azure`

Build Runtime: Microsoft Azure

technical name: `build-runtime-azure`

</td>
<td valign="top" rowspan="7">

Provisioning

Updating

</td>
<td valign="top">

`Standard_F2s_v2`

</td>
<td valign="top">

2 vCPU, 4 GB RAM

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
</tr>
<tr>
<td valign="top">

`Standard_F8s_v2`

</td>
<td valign="top">

8 vCPU, 16 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_F16s_v2`

</td>
<td valign="top">

16 vCPU, 32 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_F32s_v2`

</td>
<td valign="top">

32 vCPU, 64 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_F48s_v2`

</td>
<td valign="top">

48 vCPU, 96 GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_F64s_v2`

</td>
<td valign="top">

64 vCPU, 128 GB RAM

</td>
</tr>
</table>



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Modules"/>

## Modules

With the *Modules* \(`modules`\) object, you can define which Kyma modules you want to provision in your cluster. You can also use it to create a cluster without any modules.

> ### Note:  
> API for module configuration is built on the `oneOf` feature from the JSON schema. If the `modules` object is passed to API, it must have only one valid option: *Default* \(`default`\) or *Custom* \(`list`\). Even if you remove the `modules` object from the JSON schema, the default Kyma modules are provisioned in your cluster.

> ### Remember:  
> The parameters marked with an asterisk "\*" are mandatory.

**Modules Parameters**


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

Look up the available Kyma modules and their technical names at [Kyma Modules](../10-concepts/kyma-modules-0dda141.md).

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

Defines the preferred release channel. The default is `regular`. The other option is `fast`.

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

Defines how a module's custom resource configuration is handled during enablement and reconciliation.

By default, it is set to `CreateAndDelete` and allows the creation or deletion of a module's resource.

If you set it to `Ignore`, a module's resource is not created.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

"" \(an empty string\)

</td>
</tr>
</table>

You have the default Kyma modules provisioned in your cluster if you do not provide the `modules` object in the JSON payload, or if you use the following input:

> ### Sample Code:  
> ```
> "modules": { 
>     "default": true 
> } 
> ```

See an example of JSON input for a custom list of Kyma modules:

> ### Sample Code:  
> ```
> "modules": {
>     "list": [
>         {
>             "name": "btp-operator"
>         },
>         {
>             "name": "keda",
>             "customResourcePolicy": "CreateAndDelete",
>             "channel": "fast"
>         }
>     ]
> }
> ```

Applying the following values results in Kyma runtime provisioning without any Kyma modules.

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

The *Networking* \(`networking`\) object provides networking configuration. These values are immutable and cannot be updated later.

> ### Remember:  
> The parameters marked with an asterisk "\*" are mandatory.

**Networking Parameters**


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

Also, the range for nodes must not overlap with those used for Pods or Services. That is also valid for the default ranges set for Pods or Services if you don’t provide your own.

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

Also, the range for Pods must not overlap with those used for nodes or Services. That is also valid for the default range set for Services if you don’t provide your own.

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

CIDR range for Services must not overlap with the following CIDRs: 10.242.0.0/16, 10.64.0.0/11, 10.254.0.0/16, 10.243.0.0/16 192.168.123.0/24, 240.0.0.0/8.

Also, the range for Services must not overlap with those used for nodes or Pods. That is also valid for the default range set for Pods if you don’t provide your own.

</td>
</tr>
</table>

See the default JSON input for the *Networking* object:

> ### Sample Code:  
> ```
> "networking": {
>         "nodes": "10.250.0.0/16"
>         "pods": "10.96.0.0/13"
>         "services": "10.104.0.0/13"
>     }
> ```



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_OIDC"/>

## OpenID Connect \(OIDC\)

The *OpenID Connect* \(`oidc`\) configured as a single object allows you to provide OIDC configuration. If you do not provide the `oidc` object or any custom values in the provisioning request, the default OIDC configuration is used. If you do not provide the `oidc` object in the update request or leave all object’s properties empty, the saved OIDC configuration remains unchanged.

> ### Remember:  
> The parameters marked with an asterisk "\*" are mandatory.

**OIDC Parameters**


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

btp CLI parameter: issuerURL

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
</table>

The following example shows the default configuration of a single `oidc` object. To revert your changes to the default settings, copy and paste the following values:

> ### Sample Code:  
> ```
>  "oidc": {
>         "clientID": "12b13a26-d993-4d0c-aa08-5f5852bbdff6",
>         "groupsClaim": "groups",
>         "issuerURL": "https://kyma.accounts.ondemand.com",
>         "groupsPrefix": "-"
>         "signingAlgs": ["RS256"],
>         "usernameClaim": "sub",
>         "usernamePrefix": "-",
>         "requiredClaims": ["-"]
>     }
> ```



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Region"/>

## Region\*

*Region\** \(`region`\) is a mandatory string parameter, which defines a region where your cluster runs.

> ### Note:  
> The region marked with "<sup>3</sup>" has a `Seed` and supports the *Shoot and Seed Same Region* feature.
> 
> For more information, see [Shoot and Seed Same Region](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_shoot_and_seed).

**Region Parameter**


<table>
<tr>
<th valign="top">

Plan

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

Region Technical Key

</th>
<th valign="top">

Region Name

</th>
</tr>
<tr>
<td valign="top" rowspan="11">

Standard: Amazon Web Services

technical name: `aws`

Free

technical name: `free`

Build Runtime: Amazon Web Services

technical name: `build-runtime-aws`

</td>
<td valign="top" rowspan="11">

Provisioning

</td>
<td valign="top">

`eu-central-1`<sup>[3](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__note_seed_regions)</sup>

</td>
<td valign="top">

Europe \(Frankfurt\)<sup>[3](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__note_seed_regions)</sup>

</td>
</tr>
<tr>
<td valign="top">

`eu-west-2`

</td>
<td valign="top">

Europe \(London\)

</td>
</tr>
<tr>
<td valign="top">

`ca-central-1`

</td>
<td valign="top">

Canada \(Montreal\)

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

`us-east-1`<sup>[3](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__note_seed_regions)</sup>

</td>
<td valign="top">

US East \(VA\)<sup>[3](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__note_seed_regions)</sup>

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

`ap-northeast-2`<sup>[3](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__note_seed_regions)</sup>

</td>
<td valign="top">

South Korea \(Seoul\)<sup>[3](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__note_seed_regions)</sup>

</td>
</tr>
<tr>
<td valign="top">

`ap-south-1`

</td>
<td valign="top">

India \(Mumbai\)

</td>
</tr>
<tr>
<td valign="top">

`ap-southeast-1`<sup>[3](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__note_seed_regions)</sup>

</td>
<td valign="top">

Singapore<sup>[3](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__note_seed_regions)</sup>

</td>
</tr>
<tr>
<td valign="top">

`ap-southeast-2`<sup>[3](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__note_seed_regions)</sup>

</td>
<td valign="top">

Australia \(Sydney\)<sup>[3](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__note_seed_regions)</sup>

</td>
</tr>
<tr>
<td valign="top">

`us-west-2`<sup>[3](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__note_seed_regions)</sup>

</td>
<td valign="top">

US West \(Oregon\)<sup>[3](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__note_seed_regions)</sup>

</td>
</tr>
<tr>
<td valign="top" rowspan="13">

Standard: Google Cloud

technical name: `gcp`

Build Runtime: Google Cloud

technical name: `build-runtime-gcp`

</td>
<td valign="top" rowspan="13">

Provisioning

</td>
<td valign="top">

`europe-west3`

</td>
<td valign="top">

Europe \(Frankfurt\)

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

`asia-south1`<sup>[3](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__note_seed_regions)</sup>

</td>
<td valign="top">

India \(Mumbai\)<sup>[3](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__note_seed_regions)</sup>

</td>
</tr>
<tr>
<td valign="top">

`us-central1`<sup>[3](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__note_seed_regions)</sup>

</td>
<td valign="top">

US Central \(IA\)<sup>[3](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__note_seed_regions)</sup>

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

`me-central2`

</td>
<td valign="top">

KSA \(Dammam\)

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

`southamerica-east1`

</td>
<td valign="top">

Brazil \(São Paulo\)

</td>
</tr>
<tr>
<td valign="top">

`asia-northeast1`

</td>
<td valign="top">

Japan \(Tokyo\)

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

North America \(Virginia\)

</td>
</tr>
<tr>
<td valign="top" rowspan="12">

Standard: Microsoft Azure

technical name: `azure`

Kyma Test Demo and Development \(Azure Lite\)

technical name: `azure_lite`

Build Runtime: Microsoft Azure

technical name: `build-runtime-azure`

</td>
<td valign="top" rowspan="12">

Provisioning

</td>
<td valign="top">

`eastus`<sup>[3](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__note_seed_regions)</sup>

</td>
<td valign="top">

US East \(VA\)<sup>[3](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__note_seed_regions)</sup>

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

`westus2`<sup>[3](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__note_seed_regions)</sup>

</td>
<td valign="top">

US West \(WA\)<sup>[3](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__note_seed_regions)</sup>

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

`northeurope`

</td>
<td valign="top">

North EU \(Ireland\)

</td>
</tr>
<tr>
<td valign="top">

`westeurope`<sup>[3](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__note_seed_regions)</sup>

</td>
<td valign="top">

Europe \(Netherlands\)<sup>[3](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__note_seed_regions)</sup>

</td>
</tr>
<tr>
<td valign="top">

`japaneast`

</td>
<td valign="top">

Japan \(Tokyo\)

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

`australiaeast`<sup>[3](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__note_seed_regions)</sup>

</td>
<td valign="top">

Australia \(Sydney\)<sup>[3](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__note_seed_regions)</sup>

</td>
</tr>
<tr>
<td valign="top">

`switzerlandnorth`<sup>[3](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__note_seed_regions)</sup>

</td>
<td valign="top">

Switzerland \(Zurich\)<sup>[3](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__note_seed_regions)</sup>

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
</table>

Here is an example of the JSON input for the *Region* parameter:

> ### Sample Code:  
> ```
> "region": "us-east-1"
> ```



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_shoot_and_seed"/>

## Shoot and Seed Same Region

*Shoot and Seed Same Region* \(technical name: `ShootAndSeedSameRegion`\) is a provisioning parameter. It is a boolean that enables you to decide if your `Shoot` and `Seed` should be in the same region.

If you set it to `true`, your `Shoot` is matched with a `Seed` in the same region, which ensures the location of the control plane in the same region where your cluster's worker nodes are deployed. With this setting, you can control where your sensitive data is stored. If there's no `Seed` available in the specified region, a message offers you a list of regions where you can have both the `Seed` and the `Shoot`.

If you set the parameter to `false` or leave the field empty, your control plane can sometimes be deployed in a different region than the worker nodes.

To learn which regions have a `Seed` and support the *Shoot and Seed Same Region* feature, see the [Region\*](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Region) section.

See an example of the JSON input:

> ### Sample Code:  
> ```
> "shootAndSeedSameRegion": true
> ```

**Related Information**  


[Available Plans in the Kyma Environment](available-plans-in-the-kyma-environment-befe01d.md "Depending on your global account type, you have access to a different plan that specifies the cluster parameters for the Kyma environment.")

[Regions for the Kyma Environment](../10-concepts/regions-for-the-kyma-environment-557ec3a.md "To work with the Kyma environment, you need to specify the region for both your subaccount and the cluster.")

[Kyma Modules](../10-concepts/kyma-modules-0dda141.md "With Kyma's modular approach, you can install just the modules you need, instead of a predefined set of components.")

[Account Administration Using the SAP BTP Command Line Interface \(btp CLI\)](account-administration-using-the-sap-btp-command-line-interface-btp-cli-7c6df2d.md "Use the SAP BTP command line interface (btp CLI) for all account administration tasks, such as creating or updating subaccounts, authorization management, and working with service brokers and platforms. It is an alternative to the SAP BTP cockpit for users who like to work in a terminal or want to automate operations using scripts.")

