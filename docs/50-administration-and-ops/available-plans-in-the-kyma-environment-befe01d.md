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

Provides a custom OpenID Connect \(OIDC\) configuration.

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

The technical name of the plan is `free`. Using the free service plans for Kyma allows you to try out services in global accounts without any additional cost for 30 days. However, the free model account has certain limitations.

-   The free plan offers you a one-node cluster and is only available on AWS.

-   Only community support is available for free tier service plans and these are not subject to SLAs.

-   Before you enable the Kyma environment, you must first assign it as an entitlement to your subaccount.

-   You can use the free plan only once in a global account for up to 30 days.

    > ### Remember:  
    > Once you have started the free plan in a subaccount, you cannot use it in another subaccount within the same global account even though the 30-day period has not ended.

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

## Standard: Amazon Web Services, Google Cloud, and Microsoft Azure

The technical names of the standard enterprise plans are `aws`, `gcp`, and `azure`. They offer highly available Kubernetes clusters, where the Kubernetes and Kyma configurations are optimized for production use cases. The Kubernetes worker nodes are deployed in three availability zones of the respective [cloud region](../10-concepts/regions-for-the-kyma-environment-557ec3a.md), and thus can provide zone level failure tolerance for Kyma and applications deployed on Kyma runtime.

The [Kubernetes control plane](https://kubernetes.io/docs/reference/glossary/?all=true#term-control-plane) is also hosted in three availability zones of the respective region.

While the high availability is guaranteed for Kubernetes and native Kyma components, by default, it's not guaranteed for the customer's own applications. To guarantee high availability for your applications deployed on Kyma, you must manually configure these applications.

> ### Note:  
> To indicate that your Kyma runtime is used for production, select *Used for production* in your subaccount details. This setting allows SAP BTP, Kyma runtime operators to prioritize incidents and support cases affecting production subaccounts over subaccounts used for non-production purposes. See [Change Subaccount Details](change-subaccount-details-567d4a8.md).

> ### Remember:  
> The parameters marked with an asterisk "\*" are mandatory.

**Standard Plan Specification**


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
<tr>
<td valign="top">

*Additional Worker Node Pools*

btp CLI parameter: `additionalWorkerNodePools`

</td>
<td valign="top">

Defines a custom list of additional worker node pools.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

[Additional Worker Node Pools](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Additional_WN_Pools)

</td>
</tr>
</table>



<a name="loiobefe01d5d8864e59bf847fa5a5f3d669__section_hnj_3nz_bfc"/>

## Build Runtime: Amazon Web Services, Google Cloud, and Microsoft Azure

The technical names of these enterprise plans are `build-runtime-aws`, `build-runtime-azure`, and `build-runtime-gcp`. Use them to integrate Kyma's functionalities within SAP Build. See the [SAP Build documentation](https://help.sap.com/docs/build-service/build-service-guide/what-is-sap-build?version=Cloud).

> ### Remember:  
> The parameters marked with an asterisk "\*" are mandatory.

**Build Runtime Plan Specification**


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
<tr>
<td valign="top">

*Additional Worker Node Pools*

btp CLI parameter: `additionalWorkerNodePools`

</td>
<td valign="top">

Defines a custom list of additional worker node pools.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

[Additional Worker Node Pools](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Additional_WN_Pools)

</td>
</tr>
</table>



<a name="loiobefe01d5d8864e59bf847fa5a5f3d669__section_vbl_4w4_wsb"/>

## Kyma Test Demo and Development \(Azure Lite\)

The technical name of the plan is `azure_lite`. The Kyma Test Demo and Development plan is offered to Partners, whithin the [*Pay-As-You-Go for SAP BTP for cloud test, demo, and development*](https://partneredge.sap.com/en/profile/create-profile.html) commercial model. You can use this plan for testing, development, and demo purposes. In the SAP BTP cockpit, the plan is called "Kyma Runtime Partner TDD".

> ### Remember:  
> The parameters marked with an asterisk "\*" are mandatory.

**Kyma Test Demo and Development Plan Specification**


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
<tr>
<td valign="top">

*Additional Worker Node Pools*

btp CLI parameter: `additionalWorkerNodePools`

</td>
<td valign="top">

Defines a custom list of additional worker node pools.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

[Additional Worker Node Pools](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Additional_WN_Pools)

</td>
</tr>
</table>

**Related Information**  


[Provisioning and Updating Parameters in the Kyma Environment](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md "You can configure the cluster parameters in the Kyma environment.")

[Regions for the Kyma Environment](../10-concepts/regions-for-the-kyma-environment-557ec3a.md "To work with the Kyma environment, you need to specify the region for both your subaccount and the cluster.")

[Kyma Modules](../10-concepts/kyma-modules-0dda141.md "With Kyma's modular approach, you can install just the modules you need, instead of a predefined set of components.")

[Account Administration Using the SAP BTP Command Line Interface \(btp CLI\)](account-administration-using-the-sap-btp-command-line-interface-btp-cli-7c6df2d.md "Use the SAP BTP command line interface (btp CLI) for all account administration tasks, such as creating or updating subaccounts, authorization management, and working with service brokers and platforms. It is an alternative to the SAP BTP cockpit for users who like to work in a terminal or want to automate operations using scripts.")

[Service Plans and Metering for Kyma Runtime](../10-concepts/service-plans-and-metering-for-kyma-runtime-c33bb11.md "This page explains the relationship between the service plans of the SAP Discovery Center and the service plans of the SAP BTP cockpit and provides information to help you understand how the service is billed.")

[What Is the Consumption-Based Commercial Model?](../10-concepts/what-is-the-consumption-based-commercial-model-7047eb4.md "With the consumption-based model, your organization purchases an entitlement to all current and future SAP BTP services that are eligible for this model. Throughout the duration of your contract, you have complete flexibility to turn services on and off and to switch between services as your business requires.")

