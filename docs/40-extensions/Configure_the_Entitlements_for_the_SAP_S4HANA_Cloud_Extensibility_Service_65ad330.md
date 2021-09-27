<!-- loio65ad330d11ac49a196948aa8db6470fb -->

# Configure the Entitlements for the SAP S/4HANA Cloud Extensibility Service

Configure the required entitlements to make the APIs of the registered SAP S/4HANA Cloud system accessible in your subaccount in which your extension applications will reside.



<a name="loio65ad330d11ac49a196948aa8db6470fb__prereq_zxm_j3c_fhb"/>

## Prerequisites

-   You are an administrator of the global account in SAP BTP.

-   The subaccount is in the SAP BTP, Cloud Foundry environment with enabled Cloud Foundry, or Kyma, or both capabilities.

-   You have registered an SAP S/4HANA Cloud system. See [Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](Register_an_SAP_S4HANA_Cloud_System_in_a_Global_Account_in_SAP_BTP_28171b6.md).




<a name="loio65ad330d11ac49a196948aa8db6470fb__context_rvd_hxm_3pb"/>

## Context

An entitlement is your right to provision and consume a resource. In other words, the entitlement is the respective service plan, *api-access* or *messaging*, that you're entitled to use. Depending on feature set you are using, you need to follow different steps to configure the entitlements. See [Cloud Management Tools — Feature Set Overview](../10-concepts/Cloud_Management_Tools_—_Feature_Set_Overview_caf4e4e.md).



## Procedure

1.  In the SAP BTP cockpit, navigate to your global account.

2.  Depending on the feature set you are using, you need to follow different steps to configure the entitlements.

    -   For feature set A, follow these steps:
        1.  In the navigation area, choose *Entitlements* \> *Subaccount Assignments*.
        2.  Select your subaccount from the drop down menu, choose *Go*, and then choose *Configure Entitlements*.

            > ### Tip:  
            > If your global account contains more than 20 subaccounts, choose     to open up the value help dialog. There you can filter subaccounts by role, environment and region to make your selection easier and faster. You can only select a maximum of 50 subaccounts at once.

    -   If you are using feature set B, you have to:
        1.  In the navigation area, choose *Entitlements* \> *Entity Assignments*.
        2.  On the *Entity Assignments* screen, select your subaccount in the*Select Entities* field.
        3.  Choose *Go*, and then choose *Configure Entitlements*.
3.  Choose *Add Service Plans*, and then select the *SAP S/4HANA Cloud Extensibility* service.

    > ### Note:  
    > To have the *SAP S/4HANA Cloud Extensibility* service in the list, you need to have registered at least one SAP S/4HANA Cloud system.

4.  In the *Available Service Plans* area, select the system you have registered and the required service plans, and then choose *Add Service Plan*.

    > ### Note:  
    > For more information about the available service plans for SAP S/4HANA Cloud Extensibility service, see [Supported Service Plans for SAP S/4HANA Cloud](Supported_Service_Plans_for_SAP_S4HANA_Cloud_925c00a.md).


**Related Information**  


[Configure Entitlements and Quotas for Subaccounts](../50-administration-and-ops/Configure_Entitlements_and_Quotas_for_Subaccounts_5ba357b.md "Assign entitlements to subaccounts by adding service plans and distribute the quotas available in your global account to your subaccounts using the SAP BTP cockpit.")

