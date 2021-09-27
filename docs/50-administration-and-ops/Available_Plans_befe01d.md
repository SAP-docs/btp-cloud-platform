<!-- loiobefe01d5d8864e59bf847fa5a5f3d669 -->

# Available Plans

Depending on your global account type, you will have access to a different plan that specifies cluster parameters for the Kyma environment.



<a name="loiobefe01d5d8864e59bf847fa5a5f3d669__section_y4g_qld_hpb"/>

## Amazon Web Services \(AWS\)

See the specification for the enterprise account.

<a name="loiobefe01d5d8864e59bf847fa5a5f3d669__table_z4g_qld_hpb"/>AWS plan specification


<table>
<tr>
<th>

Field



</th>
<th>

Description



</th>
<th>

Default value



</th>
</tr>
<tr>
<td>

*Cluster Name*



</td>
<td>

Defines the name of your cluster. Use only alphanumeric characters and hyphens.



</td>
<td>

n/a



</td>
</tr>
<tr>
<td>

*Region*



</td>
<td>

Defines a region \(set of datacenters\) where your cluster will run.



</td>
<td>

-   `eu-central-1` \(Europe\)
-   `us-east-1` \(Americas\)
-   `ap-southeast-1` \(Asia Pacific\)



</td>
</tr>
<tr>
<td>

*Machine Type*



</td>
<td>

Specifies memory and CPU limits for one virtual machine. See [AWS docs](https://aws.amazon.com/ec2/instance-types/) for details. The available machine types are `m5.2xlarge`, `m5.4xlarge`, `m5.8xlarge`, and `m5.12xlarge`.



</td>
<td>

`m5.2xlarge`



</td>
</tr>
<tr>
<td>

*Auto Scaler Min*



</td>
<td>

Specifies the minimum number of virtual machines to create.



</td>
<td>

`2`



</td>
</tr>
<tr>
<td>

*Auto Scaler Max*



</td>
<td>

Specifies the maximum number of virtual machines to create. This number cannot be greater than `40`.



</td>
<td>

`10`



</td>
</tr>
</table>



<a name="loiobefe01d5d8864e59bf847fa5a5f3d669__section_whn_t5z_1pb"/>

## Azure

See the specification for the enterprise account.

<a name="loiobefe01d5d8864e59bf847fa5a5f3d669__table_uy2_zvz_1pb"/>Azure plan specification


<table>
<tr>
<th>

Field



</th>
<th>

Description



</th>
<th>

Default value



</th>
</tr>
<tr>
<td>

*Cluster Name*



</td>
<td>

Defines the name of your cluster. Use only alphanumeric characters and hyphens.



</td>
<td>

n/a



</td>
</tr>
<tr>
<td>

*Region*



</td>
<td>

Defines a region \(set of datacenters\) where your cluster will run.



</td>
<td>

`eastus`



</td>
</tr>
<tr>
<td>

*Machine Type*



</td>
<td>

Specifies memory and CPU limits for one virtual machine. See [Azure docs](https://docs.microsoft.com/en-us/azure/cloud-services/cloud-services-sizes-specs#dv3-series) for details.



</td>
<td>

`Standard_D8_v3`



</td>
</tr>
<tr>
<td>

*Auto Scaler Min*



</td>
<td>

Specifies the minimum number of virtual machines to create.



</td>
<td>

`2`



</td>
</tr>
<tr>
<td>

*Auto Scaler Max*



</td>
<td>

Specifies the maximum number of virtual machines to create. This number cannot be greater than `40`.



</td>
<td>

`10`



</td>
</tr>
</table>



<a name="loiobefe01d5d8864e59bf847fa5a5f3d669__section_tmw_v5z_1pb"/>

## Azure Lite

See the specification for the partner's test, demo, and development account.

<a name="loiobefe01d5d8864e59bf847fa5a5f3d669__table_w1q_nxz_1pb"/>Azure Lite plan specification


<table>
<tr>
<th>

Field



</th>
<th>

Description



</th>
<th>

Default value



</th>
</tr>
<tr>
<td>

*Cluster Name*



</td>
<td>

Defines the name of your cluster. Use only alphanumeric characters and hyphens.



</td>
<td>

n/a



</td>
</tr>
<tr>
<td>

*Region*



</td>
<td>

Defines a region \(set of datacenters\) where your cluster will run.



</td>
<td>

`eastus`



</td>
</tr>
<tr>
<td>

*Machine Type*



</td>
<td>

Specifies memory and CPU limits for one virtual machine. See [Azure docs](https://docs.microsoft.com/en-us/azure/cloud-services/cloud-services-sizes-specs#dv3-series) for details.



</td>
<td>

`Standard_D4_v3`



</td>
</tr>
<tr>
<td>

*Auto Scaler Min*



</td>
<td>

Specifies the minimum number of virtual machines to create.



</td>
<td>

`2`



</td>
</tr>
<tr>
<td>

*Auto Scaler Max*



</td>
<td>

Specifies the maximum number of virtual machines to create.



</td>
<td>

`4`



</td>
</tr>
</table>



<a name="loiobefe01d5d8864e59bf847fa5a5f3d669__section_jl3_cdm_1qb"/>

## Free

See the specification for the free plan.

<a name="loiobefe01d5d8864e59bf847fa5a5f3d669__table_kl3_cdm_1qb"/>Free plan specification


<table>
<tr>
<th>

Field



</th>
<th>

Description



</th>
<th>

Default value



</th>
</tr>
<tr>
<td>

*Cluster Name*



</td>
<td>

Defines the name of your cluster. Use only alphanumeric characters and hyphens.



</td>
<td>

n/a



</td>
</tr>
<tr>
<td>

*Region*



</td>
<td>

Defines a region \(set of datacenters\) where your cluster will run.



</td>
<td>

`eu-central-1`



</td>
</tr>
</table>

> ### Note:  
> The free plan offers you a one-node cluster and is only available on AWS. The upgrade to the paid plan is not yet supported. Only community support is available for free tier service plans and these are not subject to SLAs. For more information, read [Using Free Service Plans](../10-concepts/Using_Free_Service_Plans_524e108.md).



<a name="loiobefe01d5d8864e59bf847fa5a5f3d669__section_mt2_vxz_1pb"/>

## Trial

See the specification for the SAP BTP trial account.

<a name="loiobefe01d5d8864e59bf847fa5a5f3d669__table_otp_zxz_1pb"/>Trial plan specification


<table>
<tr>
<th>

Field



</th>
<th>

Description



</th>
<th>

Default value



</th>
</tr>
<tr>
<td>

*Cluster Name*



</td>
<td>

Defines the name of your cluster. Use only alphanumeric characters and hyphens.



</td>
<td>

n/a



</td>
</tr>
</table>

> ### Note:  
> For details on the trial cluster specification, see the **Scope and limitations** section in [About the Trial Account](../20-getting-started/About_the_Trial_Account_c4fff0f.md).

**Related Information**  


[Regions for the Kyma Environment](../10-concepts/Regions_350356d.md#loio557ec3adc3174ed4914ec9d6d13487cf "To work with the Kyma environment, you need to specify the region for both your subaccount and the cluster.")

