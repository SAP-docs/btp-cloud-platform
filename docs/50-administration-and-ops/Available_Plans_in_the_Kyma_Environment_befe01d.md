<!-- loiobefe01d5d8864e59bf847fa5a5f3d669 -->

# Available Plans in the Kyma Environment

Depending on your global account type, you will have access to a different plan that specifies cluster parameters for the Kyma environment.



<a name="loiobefe01d5d8864e59bf847fa5a5f3d669__section_y4g_qld_hpb"/>

## Amazon Web Services \(AWS\)

See the specification for the enterprise account.

<a name="loiobefe01d5d8864e59bf847fa5a5f3d669__table_z4g_qld_hpb"/>AWS plan specification


<table>
<tr>
<th valign="top">

Field



</th>
<th valign="top">

Description



</th>
<th valign="top">

Default value



</th>
</tr>
<tr>
<td valign="top">

*Cluster Name*



</td>
<td valign="top">

Defines the name of your cluster. Use only alphanumeric characters and hyphens.



</td>
<td valign="top">

n/a



</td>
</tr>
<tr>
<td valign="top">

*Region*



</td>
<td valign="top">

Defines a region \(set of datacenters\) where your cluster will run.



</td>
<td valign="top">

-   `eu-central-1` \(Europe\)
-   `us-east-1` \(Americas\)
-   `ap-southeast-1` \(Asia Pacific\)



</td>
</tr>
<tr>
<td valign="top">

*Machine Type*



</td>
<td valign="top">

Specifies memory and CPU limits for one virtual machine. See [AWS docs](https://aws.amazon.com/ec2/instance-types/) for details. The available machine types are `m5.2xlarge`, `m5.4xlarge`, `m5.8xlarge`, and `m5.12xlarge`.



</td>
<td valign="top">

`m5.2xlarge`



</td>
</tr>
<tr>
<td valign="top">

*Auto Scaler Min*



</td>
<td valign="top">

Specifies the minimum number of virtual machines to create.



</td>
<td valign="top">

`2`



</td>
</tr>
<tr>
<td valign="top">

*Auto Scaler Max*



</td>
<td valign="top">

Specifies the maximum number of virtual machines to create. This number cannot be greater than `40`.



</td>
<td valign="top">

`10`



</td>
</tr>
</table>



<a name="loiobefe01d5d8864e59bf847fa5a5f3d669__section_yq5_513_grb"/>

## Google Cloud Platform \(GCP\)

See the specification for the enterprise account.

<a name="loiobefe01d5d8864e59bf847fa5a5f3d669__table_ym3_jb3_grb"/>GCP plan specification


<table>
<tr>
<th valign="top">

Field



</th>
<th valign="top">

Description



</th>
<th valign="top">

Default value



</th>
</tr>
<tr>
<td valign="top">

*Cluster Name*



</td>
<td valign="top">

Defines the name of your cluster. Use only alphanumeric characters and hyphens.



</td>
<td valign="top">

n/a



</td>
</tr>
<tr>
<td valign="top">

*Region*



</td>
<td valign="top">

Defines a region \(set of datacenters\) where your cluster will run.



</td>
<td valign="top">

-   `europe-west3` \(Europe\)
-   `us-central1` \(Americas\)
-   `asia-northeast1` \(Asia Pacific\)



</td>
</tr>
<tr>
<td valign="top">

*Machine Type*



</td>
<td valign="top">

Specifies memory and CPU limits for one virtual machine. See [GCP docs](https://cloud.google.com/compute/docs/general-purpose-machines#n2_machines) for details. The available machine types are `n2-standard-8`, `n2-standard-16`, `n2-standard-32`, and `n2-standard-64`.



</td>
<td valign="top">

`n2-standard-8`



</td>
</tr>
<tr>
<td valign="top">

*Auto Scaler Min*



</td>
<td valign="top">

Specifies the minimum number of virtual machines to create.



</td>
<td valign="top">

`2`



</td>
</tr>
<tr>
<td valign="top">

*Auto Scaler Max*



</td>
<td valign="top">

Specifies the maximum number of virtual machines to create. This number cannot be greater than `40`.



</td>
<td valign="top">

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
<th valign="top">

Field



</th>
<th valign="top">

Description



</th>
<th valign="top">

Default value



</th>
</tr>
<tr>
<td valign="top">

*Cluster Name*



</td>
<td valign="top">

Defines the name of your cluster. Use only alphanumeric characters and hyphens.



</td>
<td valign="top">

n/a



</td>
</tr>
<tr>
<td valign="top">

*Region*



</td>
<td valign="top">

Defines a region \(set of datacenters\) where your cluster will run.



</td>
<td valign="top">

`eastus`



</td>
</tr>
<tr>
<td valign="top">

*Machine Type*



</td>
<td valign="top">

Specifies memory and CPU limits for one virtual machine. See [Azure docs](https://docs.microsoft.com/en-us/azure/cloud-services/cloud-services-sizes-specs#dv3-series) for details.



</td>
<td valign="top">

`Standard_D8_v3`



</td>
</tr>
<tr>
<td valign="top">

*Auto Scaler Min*



</td>
<td valign="top">

Specifies the minimum number of virtual machines to create.



</td>
<td valign="top">

`2`



</td>
</tr>
<tr>
<td valign="top">

*Auto Scaler Max*



</td>
<td valign="top">

Specifies the maximum number of virtual machines to create. This number cannot be greater than `40`.



</td>
<td valign="top">

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
<th valign="top">

Field



</th>
<th valign="top">

Description



</th>
<th valign="top">

Default value



</th>
</tr>
<tr>
<td valign="top">

*Cluster Name*



</td>
<td valign="top">

Defines the name of your cluster. Use only alphanumeric characters and hyphens.



</td>
<td valign="top">

n/a



</td>
</tr>
<tr>
<td valign="top">

*Region*



</td>
<td valign="top">

Defines a region \(set of datacenters\) where your cluster will run.



</td>
<td valign="top">

`eastus`



</td>
</tr>
<tr>
<td valign="top">

*Machine Type*



</td>
<td valign="top">

Specifies memory and CPU limits for one virtual machine. See [Azure docs](https://docs.microsoft.com/en-us/azure/cloud-services/cloud-services-sizes-specs#dv3-series) for details.



</td>
<td valign="top">

`Standard_D4_v3`



</td>
</tr>
<tr>
<td valign="top">

*Auto Scaler Min*



</td>
<td valign="top">

Specifies the minimum number of virtual machines to create.



</td>
<td valign="top">

`2`



</td>
</tr>
<tr>
<td valign="top">

*Auto Scaler Max*



</td>
<td valign="top">

Specifies the maximum number of virtual machines to create.



</td>
<td valign="top">

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
<th valign="top">

Field



</th>
<th valign="top">

Description



</th>
<th valign="top">

Default value



</th>
</tr>
<tr>
<td valign="top">

*Cluster Name*



</td>
<td valign="top">

Defines the name of your cluster. Use only alphanumeric characters and hyphens.



</td>
<td valign="top">

n/a



</td>
</tr>
<tr>
<td valign="top">

*Region*



</td>
<td valign="top">

Defines a region \(set of datacenters\) where your cluster will run.



</td>
<td valign="top">

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
<th valign="top">

Field



</th>
<th valign="top">

Description



</th>
<th valign="top">

Default value



</th>
</tr>
<tr>
<td valign="top">

*Cluster Name*



</td>
<td valign="top">

Defines the name of your cluster. Use only alphanumeric characters and hyphens.



</td>
<td valign="top">

n/a



</td>
</tr>
</table>

> ### Note:  
> For details on the trial cluster specification, see the **Scope and limitations** section in [About the Trial Account](../20-getting-started/About_the_Trial_Account_c4fff0f.md).

**Related Information**  


[Regions for the Kyma Environment](../10-concepts/Regions_350356d.md#loio557ec3adc3174ed4914ec9d6d13487cf "To work with the Kyma environment, you need to specify the region for both your subaccount and the cluster.")

