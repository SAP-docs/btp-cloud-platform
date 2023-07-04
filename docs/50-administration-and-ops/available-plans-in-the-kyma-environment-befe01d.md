<!-- loiobefe01d5d8864e59bf847fa5a5f3d669 -->

# Available Plans in the Kyma Environment

Depending on your global account type, you have access to a different plan that specifies the cluster parameters for the Kyma environment.



<a name="loiobefe01d5d8864e59bf847fa5a5f3d669__section_mt2_vxz_1pb"/>

## Trial

For details on the trial cluster specification, see [Scope and Limitations](../20-getting-started/about-the-trial-account-c4fff0f.md#loioc4fff0f58f90424f8e0af28975ac7f0f__section_trial_scope_limitations).

**Trial Plan Specification**


<table>
<tr>
<th valign="top">

Field



</th>
<th valign="top">

Description



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

*Plan*

btp CLI parameter: `plan`



</td>
<td valign="top">

Defines the plan you can use in your subaccount \(only relevant for btp CLI\).



</td>
<td valign="top">

Trial



</td>
<td valign="top">

`trial`



</td>
</tr>
<tr>
<td valign="top">

*Cluster Name*

btp CLI parameter: `name`



</td>
<td valign="top">

Defines the name of your cluster.



</td>
<td valign="top">

n/a



</td>
<td valign="top">

Short string \(up to 32 characters\) that contains only alphanumeric characters \(A-Z, a-z, 0–9\), periods, underscores, and hyphens.

It can't contain white spaces.



</td>
</tr>
</table>



<a name="loiobefe01d5d8864e59bf847fa5a5f3d669__section_jl3_cdm_1qb"/>

## Free

The free plan offers you a one-node cluster and is only available on AWS. The upgrade to the paid plan is not yet supported. Only community support is available for free tier service plans and these are not subject to SLAs. For more information, read [Using Free Service Plans](../10-concepts/using-free-service-plans-524e108.md).

**Free Plan Specification**


<table>
<tr>
<th valign="top">

Field



</th>
<th valign="top">

Description



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

*Plan*

btp CLI parameter: `plan`



</td>
<td valign="top">

Defines the plan you can use in your subaccount.



</td>
<td valign="top">

Free



</td>
<td valign="top">

`free`



</td>
</tr>
<tr>
<td valign="top">

*Cluster Name*

btp CLI parameter: `name`



</td>
<td valign="top">

Defines the name of your cluster.



</td>
<td valign="top">

n/a



</td>
<td valign="top">

Short string \(up to 32 characters\) that contains only alphanumeric characters \(A-Z, a-z, 0–9\), periods, underscores, and hyphens.

It can't contain white spaces.



</td>
</tr>
<tr>
<td valign="top">

*Region*

btp CLI parameter: `region`



</td>
<td valign="top">

Defines a region \(set of datacenters\) where your cluster will run.



</td>
<td valign="top">

`eu-central-1`



</td>
<td valign="top">

Look up the technical cluster region names at [Regions for the Kyma Environment](../10-concepts/regions-for-the-kyma-environment-557ec3a.md) - only “Amazon Web Services” regions available.



</td>
</tr>
</table>



<a name="loiobefe01d5d8864e59bf847fa5a5f3d669__section_y4g_qld_hpb"/>

## Enterprise \(AWS, Google Cloud, Azure\)

The Enterprise plans offer highly available Kubernetes clusters, where the Kubernetes and Kyma configurations are optimized for production use cases. The Kubernetes worker nodes are deployed in three availability zones of the respective [cloud region](../10-concepts/regions-for-the-kyma-environment-557ec3a.md), and thus can provide zone level failure tolerance for Kyma and applications deployed on the Kyma runtime.

While the high availability is guaranteed for Kubernetes and native Kyma components, by default it's not guaranteed for the customer's own applications. To guarantee high availability for your applications deployed on Kyma, you must manually configure these applications so.

**Enterprise Plan Specification**


<table>
<tr>
<th valign="top">

Field



</th>
<th valign="top">

Description



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

*Plan*

btp CLI parameter: `plan`



</td>
<td valign="top">

Defines the plan you can use in your subaccount.



</td>
<td valign="top">

The plan assigned to your subaccount.



</td>
<td valign="top">

-   `aws`
-   `gcp`
-   `azure`



</td>
</tr>
<tr>
<td valign="top">

*Cluster Name*

btp CLI parameter: `name`



</td>
<td valign="top">

Defines the name of your cluster.



</td>
<td valign="top">

n/a



</td>
<td valign="top">

Short string \(up to 32 characters\) that contains only alphanumeric characters \(A-Z, a-z, 0–9\), periods, underscores, and hyphens.

It can't contain white spaces.



</td>
</tr>
<tr>
<td valign="top">

*Region*

btp CLI parameter: `region`



</td>
<td valign="top">

Defines a region \(set of datacenters\) where your cluster will run.



</td>
<td valign="top">

-   AWS: `eu-central-1`
-   Google Cloud: `europe-west3`
-   Azure: `eastus`



</td>
<td valign="top">

Look up the technical cluster region names at [Regions for the Kyma Environment](../10-concepts/regions-for-the-kyma-environment-557ec3a.md).



</td>
</tr>
<tr>
<td valign="top">

*Machine Type*

btp CLI parameter: `machineType`



</td>
<td valign="top">

Specifies the provider-specific virtual machine type. For details, see:

-   [AWS docs](https://aws.amazon.com/ec2/instance-types/)

-   [Google Cloud docs](https://cloud.google.com/compute/docs/general-purpose-machines#n2_machines)
-   [Azure docs](https://docs.microsoft.com/en-us/azure/cloud-services/cloud-services-sizes-specs#dv3-series)



</td>
<td valign="top">

-   AWS: `m5.xlarge`
-   Google Cloud: `n2-standard-4`
-   Azure: `Standard_D4_v3`



</td>
<td valign="top">

See all options in the SAP BTP cockpit wizard to create Kyma runtime.



</td>
</tr>
<tr>
<td valign="top">

*Auto Scaler Min*

btp CLI parameter: `autoScalerMin`



</td>
<td valign="top">

Specifies the minimum number of virtual machines to create.



</td>
<td valign="top">

`3`



</td>
<td valign="top">

Number between 3 and 80, but smaller than or equal to *autoScalerMax*.



</td>
</tr>
<tr>
<td valign="top">

*Auto Scaler Max*

btp CLI parameter: `autoScalerMax`



</td>
<td valign="top">

Specifies the maximum number of virtual machines to create.



</td>
<td valign="top">

`20`



</td>
<td valign="top">

Number between 3 and 80, but greater than or equal to *autoScalerMin*.



</td>
</tr>
</table>

> ### Note:  
> You can configure *Auto Scaler Min*, *Auto Scaler Max* and *Machine Type* during both provisioning and update operations.



<a name="loiobefe01d5d8864e59bf847fa5a5f3d669__section_vbl_4w4_wsb"/>

## Partner Test, Demo, and Development \(Azure Lite\)

**Partner Test, Demo, and Development Plan Specification**


<table>
<tr>
<th valign="top">

Field



</th>
<th valign="top">

Description



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

*Plan*

btp CLI parameter: `plan`



</td>
<td valign="top">

Defines the plan you can use in your subaccount.



</td>
<td valign="top">

The plan assigned to your subaccount.



</td>
<td valign="top">

`azure_lite`



</td>
</tr>
<tr>
<td valign="top">

*Cluster Name*

btp CLI parameter: `name`



</td>
<td valign="top">

Defines the name of your cluster.



</td>
<td valign="top">

n/a



</td>
<td valign="top">

Short string \(up to 32 characters\) that contains only alphanumeric characters \(A-Z, a-z, 0–9\), periods, underscores, and hyphens.

It can't contain white spaces.



</td>
</tr>
<tr>
<td valign="top">

*Region*

btp CLI parameter: `region`



</td>
<td valign="top">

Defines a region \(set of datacenters\) where your cluster will run.



</td>
<td valign="top">

`eastus`



</td>
<td valign="top">

Look up the technical cluster region names at [Regions for the Kyma Environment](../10-concepts/regions-for-the-kyma-environment-557ec3a.md) \(only Azure regions available\).



</td>
</tr>
<tr>
<td valign="top">

*Machine Type*

btp CLI parameter: `machineType`



</td>
<td valign="top">

Specifies the provider-specific virtual machine type. For details, see [Azure docs](https://docs.microsoft.com/en-us/azure/cloud-services/cloud-services-sizes-specs#dv3-series).



</td>
<td valign="top">

`Standard_D4_v3`



</td>
<td valign="top">

`Standard_D4_v3`



</td>
</tr>
<tr>
<td valign="top">

*Auto Scaler Min*

btp CLI parameter: `autoScalerMin`



</td>
<td valign="top">

Specifies the minimum number of virtual machines to create.



</td>
<td valign="top">

`2`



</td>
<td valign="top">

Number between 2 and 40, but smaller than or equal to *autoScalerMax*.



</td>
</tr>
<tr>
<td valign="top">

*Auto Scaler Max*

btp CLI parameter: `autoScalerMax`



</td>
<td valign="top">

Specifies the maximum number of virtual machines to create.



</td>
<td valign="top">

`10`



</td>
<td valign="top">

Number between 2 and 40, but greater than or equal to *autoScalerMin*.



</td>
</tr>
</table>

**Related Information**  


[Regions for the Kyma Environment](../10-concepts/regions-for-the-kyma-environment-557ec3a.md "To work with the Kyma environment, you need to specify the region for both your subaccount and the cluster.")

[Account Administration Using the SAP BTP Command Line Interface \(btp CLI\)](account-administration-using-the-sap-btp-command-line-interface-btp-cli-7c6df2d.md "Use the SAP BTP command line interface (btp CLI) for all account administration tasks, such as creating or updating subaccounts, authorization management, and working with service brokers and platforms. It is an alternative to the SAP BTP cockpit for users who like to work in a terminal or want to automate operations using scripts.")

