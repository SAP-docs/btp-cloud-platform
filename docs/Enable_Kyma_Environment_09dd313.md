<!-- loio09dd313bf6644250a14f8f38c3d644c0 -->

# Enable Kyma Environment

Set up a Kubernetes cluster with project "Kyma" and use it to build applications and extensions to your SAP and third-party solutions.



<a name="loio09dd313bf6644250a14f8f38c3d644c0__context_er4_224_5pb"/>

## Context

There are two ways to enable the Kyma environment - the one described here, and alternatively, in the Service Marketplace \(for details, see [Create the Kyma Environment Instance from Service Marketplace](Create_the_Kyma_Environment_Instance_from_Service_Marketplace_284ac5e.md)\).



## Procedure

1.  Navigate to your subaccount and select *Enable Kyma* in the *Kyma Environment* section.

    > ### Caution:  
    > If you created a subaccount before April 23, 2020, you won't be able to enable the Kyma environment due to an XSUAA issuer configuration issue. To fix it, change the issuer of a subaccount following the instructions in [Rotate Signing Keys of Access Tokens](Rotate_Signing_Keys_of_Access_Tokens_b279adf.md).

    > ### Note:  
    > If you cannot see the *Enable Kyma* button in your subacccount view, make sure that your subaccount has entitlements for Kyma Runtime configured. For more information, read [Managing Entitlements and Quotas Using the Cockpit](Managing_Entitlements_and_Quotas_Using_the_Cockpit_c824874.md).

2.  When the dialog box opens, provide the required details:

    -   Plan
    -   Cluster Name
    You can also specify *Additional Parameters*, such as a region, machine type, and auto scaler data. After specifying all the details, choose *Create*.




<a name="loio09dd313bf6644250a14f8f38c3d644c0__result_ghx_pcv_dlb"/>

## Results

You have the Kyma environment enabled.



<a name="loio09dd313bf6644250a14f8f38c3d644c0__postreq_jdw_z24_5pb"/>

## Next Steps

To access the Kyma environment and the Kyma Console, assign the subaccount to a proper role in the SAP BTP cockpit. For more details, see [Assign Roles in the Kyma Environment](Assign_Roles_in_the_Kyma_Environment_148ae38.md).

-   **[Create the Kyma Environment Instance from Service Marketplace](Create_the_Kyma_Environment_Instance_from_Service_Marketplace_284ac5e.md "Enable the Kyma environment from Service Marketplace.")**  
Enable the Kyma environment from Service Marketplace.
-   **[Available Plans](Available_Plans_befe01d.md "Depending on your global account type, you will have access to a different plan that
		specifies cluster parameters for the Kyma environment.")**  
Depending on your global account type, you will have access to a different plan that specifies cluster parameters for the Kyma environment.

