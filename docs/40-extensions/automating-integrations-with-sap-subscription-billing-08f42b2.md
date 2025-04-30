<!-- loio08f42b2327f6472ba44b9ef9e631450f -->

# Automating Integrations with SAP Subscription Billing



<a name="loio08f42b2327f6472ba44b9ef9e631450f__section_kbh_41c_dwb"/>

## Use

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

SAP Subscription Billing is a public cloud solution that supports innovative, subscription-based business models. It enables flexible definition of product prices and automates processes such as subscription generation, rating, and preparation of billing data. SAP Subscription Billing offers comprehensive management of subscriptions throughout their life cycle. See [SAP Subscription Billing](https://help.sap.com/docs/subscription-billing/feature-overview/sap-subscription-billing).

To set up SAP Subscription Billing with SAP S/4HANA Cloud on SAP BTP you need to have all the necessary systems included in a formation of type *Integration with SAP Subscription Billing* in the *System Landscape* \> *Systems* page of the SAP BTP cockpit.

> ### Note:  
> This documentation refers to SAP S/4HANA Cloud Public Edition. See [Introduction to the Universe of SAP S/4HANA Cloud Public Edition](https://help.sap.com/docs/SAP_S4HANA_CLOUD/f77dde055ecb4541b57787d362c46a36/2962fce53eef47b4b3a8e6c945adafbe.html).



<a name="loio08f42b2327f6472ba44b9ef9e631450f__section_lmn_xwk_lcc"/>

## Rules

When creating *Integration with SAP Subscription Billing* formations, keep in mind the following rule:

-   Formation of type *Integration with SAP Subscription Billing* can contain exactly one system of type SAP Subscription Billing and one system of type SAP S/4HANA Cloud.
-   System of type SAP Subscription Billing can be included in at most one *Integration with SAP Subscription Billing* formation.
-   System of type SAP S/4HANA Cloud can be included in at most one *Integration with SAP Subscription Billing* formation when creating this formation.
-   Only SAP S/4HANA Cloud systems that are registered with *All Communication Scenarios* or the *Integration with SAP Subscription Billing* communication scenario groups, can be part of an *Integration with SAP Subscription Billing* formation. See [Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](register-an-sap-s-4hana-cloud-system-in-a-global-account-in-sap-btp-28171b6.md).




<a name="loio08f42b2327f6472ba44b9ef9e631450f__section_znb_p1c_dwb"/>

## Prerequisites

-   You are a global account administrator, or you are a system landscape administrator. See [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).

-   Register the SAP S/4HANA Cloud system in the *Systems* page.

    When you register an SAP S/4HANA Cloud system, use the *All Communication Scenarios* or the *Integration with SAP Subscription Billing* communication scenario groups when you get the registration token for the SAP S/4HANA Cloud system. This allows the automatic enablement of the `SAP_COM_0845` and `SAP_COM_0642` communication scenarios after the corresponding system is added to the formation of type *Integration with SAP Subscription Billing*. See [Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](register-an-sap-s-4hana-cloud-system-in-a-global-account-in-sap-btp-28171b6.md).




<a name="loio08f42b2327f6472ba44b9ef9e631450f__section_v4q_p1c_dwb"/>

## Procedure

If you have SAP Subscription Billing set up in your subaccount in SAP BTP, follow these steps to configure the integration between SAP Subscription Billing and SAP S/4HANA Cloud using a formation of type *Integration with SAP Subscription Billing*.

1.  In the *Systems* page, find the systems of type *SAP Subscription Billing* and *SAP S/4HANA Cloud* that you want to include in a formation.

    The **SAP S/4HANA Cloud** and the *SAP Subscription Billing* systems you are going to include in this formation must not be part of another formation.

2.  In the *System Landscape* \> *Formations* page, create a formation of type *Integration with SAP Subscription Billing* and include the relevant systems in it.

    1.  Add any name that helps you identify your formation.

    2.  In the *Formation Type* dropdown menu, select *Integration with SAP Subscription Billing*.

    3.  Select the *SAP Subscription Billing* and *SAP S/4HANA Cloud* systems that you want to include in the formation.

    4.  Review your selections and create the formation.





<a name="loio08f42b2327f6472ba44b9ef9e631450f__section_bbm_s3m_vvb"/>

## Next Steps

When the formation is created, you have SAP Subscription Billing set up with SAP S/4HANA Cloud on SAP BTP. Continue with your setup activities for the integration scope item 57Z or 5IK. See:

-   [Setup Guide for 57Z \(Subscription Management with Sales Billing\)](https://support.sap.com/content/dam/SAAP/Sol_Pack/S4C/Library/Setup/57Z_Set-Up_EN_XX.pdf)
-   [Setup Guide for 5IK \(Subscription Management with Convergent Invoicing\)](https://support.sap.com/content/dam/SAAP/Sol_Pack/S4C/Library/Setup/5IK_Set-Up_EN_XX.pdf)

