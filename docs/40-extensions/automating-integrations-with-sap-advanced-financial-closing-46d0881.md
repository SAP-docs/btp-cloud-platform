<!-- loio46d08817551c41309388a2d7311deb88 -->

# Automating Integrations with SAP Advanced Financial Closing



<a name="loio46d08817551c41309388a2d7311deb88__section_kbh_41c_dwb"/>

## Use

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

SAP Advanced Financial Closing supports you in planning, processing, monitoring, and analyzing financial closing tasks for the entities of your group. See [SAP Advanced Financial Closing User Guide](https://help.sap.com/docs/advanced-financial-closing/user/financial-closing).

To set up SAP Advanced Financial Closing with SAP S/4HANA Cloud on SAP BTP you need to have all the necessary systems included in a formation of type *Integration with SAP Advanced Financial Closing* in the *System Landscape* \> *Systems* page of the SAP BTP cockpit.

> ### Note:  
> This documentation refers to SAP S/4HANA Cloud Public Edition. See [Introduction to the Universe of SAP S/4HANA Cloud Public Edition](https://help.sap.com/docs/SAP_S4HANA_CLOUD/f77dde055ecb4541b57787d362c46a36/2962fce53eef47b4b3a8e6c945adafbe.html).



<a name="loio46d08817551c41309388a2d7311deb88__section_lmn_xwk_lcc"/>

## Rules

When creating *Integration with SAP Advanced Financial Closing* formations, keep in mind the following rule:

-   Only SAP S/4HANA Cloud systems that are registered with *All Communication Scenarios* or the *Integration with SAP Advanced Financial Closing* communication scenario groups, can be part of a *Integration with SAP Advanced Financial Closing* formation. See [Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](register-an-sap-s-4hana-cloud-system-in-a-global-account-in-sap-btp-28171b6.md).




<a name="loio46d08817551c41309388a2d7311deb88__section_znb_p1c_dwb"/>

## Prerequisites

-   You are a global account administrator, or you are a system landscape administrator. See [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).

-   You have an Identity Authentication tenant. See [Indentity Authentication: Initial Setup](https://help.sap.com/docs/identity-authentication/identity-authentication/initial-setup?version=Cloud).

-   Register the SAP S/4HANA Cloud system in the *Systems* page.

    When you register an SAP S/4HANA Cloud system, use the *All Communication Scenarios* or the *Integration with SAP Advanced Financial Closing* communication scenario groups when you get the registration token for the SAP S/4HANA Cloud system. This allows the automatic enablement of the `SAP_COM_0566` communication scenario after the corresponding system is added to the formation of type *Integration with SAP Advanced Financial Closing*. See [Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](register-an-sap-s-4hana-cloud-system-in-a-global-account-in-sap-btp-28171b6.md).




<a name="loio46d08817551c41309388a2d7311deb88__section_v4q_p1c_dwb"/>

## Procedure

If you have SAP Advanced Financial Closing set up in your subaccount in SAP BTP, follow these steps to configure the integration between SAP Advanced Financial Closing and SAP S/4HANA Cloud using a formation of type *Integration with SAP Advanced Financial Closing*.

As an alternative to the steps that follow, you can use the *Set Up SAP Advanced Financial Closing* booster in the SAP BTP cockpit and have the end-to-end scenario set up. See [SAP Advanced Financial Closing Administration Guide: Automated Setup](https://help.sap.com/docs/advanced-financial-closing/administration/automated-setup).

> ### Note:  
> We recommend that you use the *Set Up SAP Advanced Financial Closing* booster.

1.  In the *Systems* page, find the systems of type *SAP Advanced Financial Closing* and *SAP S/4HANA Cloud* that you want to include in a formation.

2.  In the *System Landscape* \> *Formations* page, create a formation of type *Integration with SAP Advanced Financial Closing* and include the relevant systems in it.

    1.  Add any name that helps you identify your formation.

    2.  In the *Formation Type* dropdown menu, select *Integration with SAP Advanced Financial Closing*.

    3.  Select the *SAP Advanced Financial Closing* and *SAP S/4HANA Cloud* systems that you want to include in the formation.

    4.  Review your selections and create the formation.





<a name="loio46d08817551c41309388a2d7311deb88__section_bbm_s3m_vvb"/>

## Next Steps

When the formation is created, you have SAP Advanced Financial Closing set up with SAP S/4HANA Cloud on SAP BTP. See the *Next Steps* section at [SAP Advanced Financial Closing Administration Guide: Automated Setup](https://help.sap.com/docs/advanced-financial-closing/administration/automated-setup).

