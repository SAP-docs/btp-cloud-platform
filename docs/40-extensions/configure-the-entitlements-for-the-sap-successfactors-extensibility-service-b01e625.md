<!-- loiob01e6255607a42889483115dbd56cc1f -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Configure the Entitlements for the SAP SuccessFactors Extensibility Service

Configure the required entitlements to make the SAP SuccessFactors HXM Suite OData APIs of the registered SAP SuccessFactors system accessible in your subaccount in which your extension applications will reside.



<a name="loiob01e6255607a42889483115dbd56cc1f__prereq_szz_lb1_x3b"/>

## Prerequisites

-   You are an administrator of the global account in SAP BTP.

-   The subaccount is in the SAP BTP, Cloud Foundry environment with enabled Cloud Foundry, or Kyma, or both capabilities.

-   You have registered an SAP SuccessFactors system. See [Register an SAP SuccessFactors System in a Global Account in SAP BTP](register-an-sap-successfactors-system-in-a-global-account-in-sap-btp-e956ba2.md).




<a name="loiob01e6255607a42889483115dbd56cc1f__context_rvd_hxm_3pb"/>

## Context

An entitlement is your right to provision and consume a resource. In other words, the entitlement is the *api-access* service plan that you're entitled to use, and the *sso-configuration* service plan that allows you to register an assertion consumer service in SAP SuccessFactors automatically.

Depending on feature set you are using, you need to follow different steps to configure the entitlements. See [Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md).



<a name="loiob01e6255607a42889483115dbd56cc1f__steps_ynv_cxm_3pb"/>

## Procedure

1.  In the SAP BTP cockpit, navigate to your global account.

2.  Depending on the feature set you are using, you need to follow different steps to configure the entitlements.

    -   For feature set A, follow these steps:
        1.  In the navigation area, choose *Entitlements* \> *Subaccount Assignments*.
        2.  Select your subaccount from the drop down menu, choose *Go*, and then choose *Configure Entitlements*.

            > ### Tip:  
            > If your global account contains more than 20 subaccounts, choose <span class="SAP-icons"></span> to open up the value help dialog. There you can filter subaccounts by role, environment and region to make your selection easier and faster. You can only select a maximum of 50 subaccounts at once.


    -   If you are using feature set B, you have to:
        1.  In the navigation area, choose *Entitlements* \> *Entity Assignments*.
        2.  On the *Entity Assignments* screen, select your subaccount in the*Select Entities* field.
        3.  Choose *Go*, and then choose *Configure Entitlements*.


3.  Choose *Add Service Plans*, and then select the *SAP SuccessFactors Extensibility* service.

    > ### Note:  
    > To have the *SAP SuccessFactors Extensibility* service in the list, you need to have registered at least one SAP SuccessFactors system.

4.  In the *Available Service Plans* area, select the system you have registered and the *api-access* and *sso-configuration* service plans, and then choose *Add 2 Service Plans*.


**Related Information**  


[Configure Entitlements and Quotas for Subaccounts](../50-administration-and-ops/configure-entitlements-and-quotas-for-subaccounts-5ba357b.md "Assign entitlements to subaccounts by adding service plans and distribute the quotas available in your global account to your subaccounts using the SAP BTP cockpit.")

