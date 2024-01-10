<!-- loiobefe01d5d8864e59bf847fa5a5f3d669 -->

# Available Plans in the Kyma Environment

Depending on your global account type, you have access to a different plan that specifies the cluster parameters for the Kyma environment.



<a name="loiobefe01d5d8864e59bf847fa5a5f3d669__section_mt2_vxz_1pb"/>

## Trial

The technical name of the plan is `trial`. For details on the trial cluster specification, see [Scope and Limitations](../20-getting-started/about-the-trial-account-c4fff0f.md#loioc4fff0f58f90424f8e0af28975ac7f0f__section_trial_scope_limitations).

> ### Remember:  
> The parameters marked with an asterisk "\*" are mandatory.

**Trial Plan Specification**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Description

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

More Information

</th>
</tr>
<tr>
<td valign="top">

*Cluster Name\**

btp CLI parameter: `name`

</td>
<td valign="top">

Defines the name of your cluster.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

[Cluster Name\*](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Cluster_Name)

</td>
</tr>
<tr>
<td valign="top">

*Modules*

btp CLI parameter: `modules`

</td>
<td valign="top">

Defines which Kyma modules are provisioned in your cluster.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

[Modules](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Modules)

</td>
</tr>
<tr>
<td valign="top">

*OpenID Connect*

btp CLI parameter: `oidc`

</td>
<td valign="top">

Provides a custom Open ID Connect \(OIDC\) configuration.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

[OpenID Connect \(OIDC\)](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_OIDC)

</td>
</tr>
<tr>
<td valign="top">

*Administrators*

btp CLI parameter: `administrators`

</td>
<td valign="top">

Specifies the list of runtime administrators.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

[Administrators](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Administrators)

</td>
</tr>
</table>



<a name="loiobefe01d5d8864e59bf847fa5a5f3d669__section_jl3_cdm_1qb"/>

## Free

The technical name of the plan is `free`. Using the free service plans for Kyma allows you to try out services in global accounts without any additional cost. However, the free model account has certain limitations.

-   The free plan offers you a one-node cluster and is only available on AWS.

-   Only community support is available for free tier service plans and these are not subject to SLAs.

-   Before you enable the Kyma environment, you must first assign it as an entitlement to your subaccount.

-   You have only one free service plan quota available per global account.

-   The services you plan to use must be available in the same region as the subaccount for the Kyma runtime. If necessary, change the default subaccount region.

-   The upgrade to the paid plan is not yet supported.


For more information, read [Using Free Service Plans](../10-concepts/using-free-service-plans-524e108.md).

> ### Remember:  
> The parameters marked with an asterisk "\*" are mandatory.

**Free Plan Specification**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Description

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

More Information

</th>
</tr>
<tr>
<td valign="top">

*Cluster Name\**

btp CLI parameter: `name`

</td>
<td valign="top">

Defines the name of your cluster.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

[Cluster Name\*](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Cluster_Name)

</td>
</tr>
<tr>
<td valign="top">

*Region\**

btp CLI parameter: `region`

</td>
<td valign="top">

Defines a region \(set of datacenters\) where your cluster runs.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

[Region\*](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Region)

</td>
</tr>
<tr>
<td valign="top">

*Modules*

btp CLI parameter: `modules`

</td>
<td valign="top">

Defines which Kyma modules are provisioned in your cluster.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

[Modules](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Modules)

</td>
</tr>
<tr>
<td valign="top">

*Networking*

btp CLI parameter: `networking`

</td>
<td valign="top">

Provides a custom IP range for worker nodes.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

[Networking](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Networking)

</td>
</tr>
<tr>
<td valign="top">

*OpenID Connect*

btp CLI parameter: `oidc`

</td>
<td valign="top">

Provides a custom Open ID Connect \(OIDC\) configuration.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

[OpenID Connect \(OIDC\)](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_OIDC)

</td>
</tr>
<tr>
<td valign="top">

*Administrators*

btp CLI parameter: `administrators`

</td>
<td valign="top">

Specifies the list of runtime administrators.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

[Administrators](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Administrators)

</td>
</tr>
</table>



<a name="loiobefe01d5d8864e59bf847fa5a5f3d669__section_y4g_qld_hpb"/>

## Amazon Web Services, Google Cloud, and Microsoft Azure

The technical names of the enterprise plans are `aws`, `gcp`, and `azure`. They offer highly available Kubernetes clusters, where the Kubernetes and Kyma configurations are optimized for production use cases. The Kubernetes worker nodes are deployed in three availability zones of the respective [cloud region](../10-concepts/regions-for-the-kyma-environment-557ec3a.md), and thus can provide zone level failure tolerance for Kyma and applications deployed on the Kyma runtime.

The [Kubernetes control plane](https://kubernetes.io/docs/reference/glossary/?all=true#term-control-plane) is also hosted in three availability zones of the respective region.

While the high availability is guaranteed for Kubernetes and native Kyma components, by default it's not guaranteed for the customer's own applications. To guarantee high availability for your applications deployed on Kyma, you must manually configure these applications.

> ### Remember:  
> The parameters marked with an asterisk "\*" are mandatory.

**Amazon Web Services, Google Cloud, and Microsoft Azure Plans Specification**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Description

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

More Information

</th>
</tr>
<tr>
<td valign="top">

*Cluster Name\**

btp CLI parameter: `name`

</td>
<td valign="top">

Defines the name of your cluster.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

[Cluster Name\*](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Cluster_Name)

</td>
</tr>
<tr>
<td valign="top">

*Region\**

btp CLI parameter: `region`

</td>
<td valign="top">

Defines a region \(set of datacenters\) where your cluster runs.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

[Region\*](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Region)

</td>
</tr>
<tr>
<td valign="top">

*Machine Type*

btp CLI parameter: `machineType`

</td>
<td valign="top">

Specifies the provider-specific virtual machine type.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

[Machine Type](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Machine_Type)

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

Provisioning

Updating

</td>
<td valign="top">

[Auto Scaler Min](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Auto_Scaler_Min)

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

Provisioning

Updating

</td>
<td valign="top">

[Auto Scaler Max](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Auto_Scaler_Max)

</td>
</tr>
<tr>
<td valign="top">

*Modules*

btp CLI parameter: `modules`

</td>
<td valign="top">

Defines which Kyma modules are provisioned in your cluster.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

[Modules](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Modules)

</td>
</tr>
<tr>
<td valign="top">

*Networking*

btp CLI parameter: `networking`

</td>
<td valign="top">

Provides a custom IP range for worker nodes.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

[Networking](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Networking)

</td>
</tr>
<tr>
<td valign="top">

*OpenID Connect*

btp CLI parameter: `oidc`

</td>
<td valign="top">

Provides a custom Open ID Connect \(OIDC\) configuration.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

[OpenID Connect \(OIDC\)](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_OIDC)

</td>
</tr>
<tr>
<td valign="top">

*Administrators*

btp CLI parameter: `administrators`

</td>
<td valign="top">

Specifies the list of runtime administrators.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

[Administrators](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Administrators)

</td>
</tr>
</table>



<a name="loiobefe01d5d8864e59bf847fa5a5f3d669__section_vbl_4w4_wsb"/>

## Azure Lite

The technical name of the plan is `azure_lite`. The Asure Lite plan is offered to Partners, who can use it for testing, development and demo purposes.

> ### Remember:  
> The parameters marked with an asterisk "\*" are mandatory.

**Azure Lite Plan Specification**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Description

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

More Information

</th>
</tr>
<tr>
<td valign="top">

*Cluster Name\**

btp CLI parameter: `name`

</td>
<td valign="top">

Defines the name of your cluster.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

[Cluster Name\*](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Cluster_Name)

</td>
</tr>
<tr>
<td valign="top">

*Region\**

btp CLI parameter: `region`

</td>
<td valign="top">

Defines a region \(set of datacenters\) where your cluster runs.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

[Region\*](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Region)

</td>
</tr>
<tr>
<td valign="top">

*Machine Type*

btp CLI parameter: `machineType`

</td>
<td valign="top">

Specifies the provider-specific virtual machine type.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

[Machine Type](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Machine_Type)

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

Provisioning

Updating

</td>
<td valign="top">

[Auto Scaler Min](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Auto_Scaler_Min)

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

Provisioning

Updating

</td>
<td valign="top">

[Auto Scaler Max](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Auto_Scaler_Max)

</td>
</tr>
<tr>
<td valign="top">

*Modules*

btp CLI parameter: `modules`

</td>
<td valign="top">

Defines which Kyma modules are provisioned in your cluster.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

[Modules](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Modules)

</td>
</tr>
<tr>
<td valign="top">

*Networking*

btp CLI parameter: `networking`

</td>
<td valign="top">

Provides a custom IP range for worker nodes.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

[Networking](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Networking)

</td>
</tr>
<tr>
<td valign="top">

*OpenID Connect*

btp CLI parameter: `oidc`

</td>
<td valign="top">

Provides a custom Open ID Connect \(OIDC\) configuration.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

[OpenID Connect \(OIDC\)](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_OIDC)

</td>
</tr>
<tr>
<td valign="top">

*Administrators*

btp CLI parameter: `administrators`

</td>
<td valign="top">

Specifies the list of runtime administrators.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

[Administrators](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Administrators)

</td>
</tr>
</table>

**Related Information**  


[Provisioning and Updating Parameters in the Kyma Environment](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md "You can configure the cluster parameters in the Kyma environment.")

[Regions for the Kyma Environment](../10-concepts/regions-for-the-kyma-environment-557ec3a.md "To work with the Kyma environment, you need to specify the region for both your subaccount and the cluster.")

[Kyma Modules](../10-concepts/kyma-modules-0dda141.md "With Kyma's modular approach, you can install just the modules you need, instead of a predefined set of components.")

[Account Administration Using the SAP BTP Command Line Interface \(btp CLI\)](account-administration-using-the-sap-btp-command-line-interface-btp-cli-7c6df2d.md "Use the SAP BTP command line interface (btp CLI) for all account administration tasks, such as creating or updating subaccounts, authorization management, and working with service brokers and platforms. It is an alternative to the SAP BTP cockpit for users who like to work in a terminal or want to automate operations using scripts.")

