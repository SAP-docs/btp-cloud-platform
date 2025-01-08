<!-- loiob4297f9e82054a9ab45300b21c53452a -->

# Automating Integrations with SAP Collaboration Manager



<a name="loiob4297f9e82054a9ab45300b21c53452a__section_kbh_41c_dwb"/>

## Use

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

SAP Collaboration Manager is a chat solution that is integrated into the SAP Fiori launchpad, enabling you to accomplish tasks quickly in your business applications. Collaborate with colleagues on activities, create notes and chats, and share attachments and screenshots.

To set up SAP Collaboration Manager with SAP S/4HANA Cloud on SAP BTP, you need to have all the necessary systems included in a formation of type *Integration with SAP Collaboration Manager* in the *System Landscape* \> *Systems* page of the SAP BTP cockpit.

> ### Note:  
> This documentation refers to SAP S/4HANA Cloud Public Edition. See [Introduction to the Universe of SAP S/4HANA Cloud Public Edition](https://help.sap.com/docs/SAP_S4HANA_CLOUD/f77dde055ecb4541b57787d362c46a36/2962fce53eef47b4b3a8e6c945adafbe.html).



<a name="loiob4297f9e82054a9ab45300b21c53452a__section_lmn_xwk_lcc"/>

## Rules

When creating *Integration with SAP Collaboration Manager* formations, keep in mind the following rule:

-   Only SAP S/4HANA Cloud systems that are registered with the *All Communication Scenarios* communication scenario group can be part of a *Integration with SAP Collaboration Manager* formation. See [Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](register-an-sap-s-4hana-cloud-system-in-a-global-account-in-sap-btp-28171b6.md).




<a name="loiob4297f9e82054a9ab45300b21c53452a__section_znb_p1c_dwb"/>

## Prerequisites

-   You are a global account administrator, or you are a system landscape administrator. See [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).

-   You have an Identity Authentication tenant. See [Identity Authentication: Initial Setup](https://help.sap.com/docs/identity-authentication/identity-authentication/initial-setup?version=Cloud).

-   You have an SAP Collaboration Manager subscription. See [Subscribe to SAP Collaboration Manager](https://help.sap.com/docs/SAP%20Collaboration%20Manager/cb0f914082ac49ddac2aecc728117530/fec597ad7865477a86665a5403cd969c.html).

-   Register the SAP S/4HANA Cloud system in the *Systems* page.

    When you register an SAP S/4HANA Cloud system, use the *All Communication Scenarios* communication scenario group when you get the registration token for the SAP S/4HANA Cloud system. This allows the automatic enablement of the `SAP_COM_0835` communication scenario after the corresponding system is added to the formation of type *Integration with SAP Collaboration Manager*. See [Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](register-an-sap-s-4hana-cloud-system-in-a-global-account-in-sap-btp-28171b6.md).




<a name="loiob4297f9e82054a9ab45300b21c53452a__section_v4q_p1c_dwb"/>

## Procedure

If you have SAP Collaboration Manager set up in your subaccount in SAP BTP, follow these steps to configure the integration between SAP Collaboration Manager and SAP S/4HANA Cloud using a formation of type *Integration with SAP Collaboration Manager*.

As an alternative to the steps that follow, you can use the *SAP Collaboration Manager* booster in the SAP BTP cockpit and have the end-to-end scenario set up. See [Run the SAP Collaboration Manager Booster](https://help.sap.com/docs/SAP%20Collaboration%20Manager/cb0f914082ac49ddac2aecc728117530/b4093f2ed3e747f0b9aaebb946e6e411.html).

> ### Note:  
> We recommend that you use the *SAP Collaboration Manager* booster.

1.  In the *Systems* page, find the systems of type *SAP Collaboration Manager* and *SAP S/4HANA Cloud* that you want to include in a formation.

2.  In the *System Landscape* \> *Formations* page, create a formation of type *Integration with SAP Collaboration Manager* and include the relevant systems in it.

    1.  Add any name that helps you identify your formation.

    2.  In the *Formation Type* dropdown menu, select *Integration with SAP Collaboration Manager*.

    3.  Select the *SAP Collaboration Manager* and *SAP S/4HANA Cloud* systems that you want to include in the formation.

    4.  Review your selections and create the formation.





<a name="loiob4297f9e82054a9ab45300b21c53452a__section_bbm_s3m_vvb"/>

## Next Steps

When the formation is created, you have SAP Collaboration Manager set up with SAP S/4HANA Cloud on SAP BTP. Then, follow the next steps at [Run the SAP Collaboration Manager Booster: Next Steps](https://help.sap.com/docs/SAP%20Collaboration%20Manager/cb0f914082ac49ddac2aecc728117530/b4093f2ed3e747f0b9aaebb946e6e411.html).

