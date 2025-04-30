<!-- loio27ca5c25f93749298f85a6fcdfab1600 -->

# Automating Integrations with SAP Ariba Central Invoice Management



<a name="loio27ca5c25f93749298f85a6fcdfab1600__section_hnr_zjf_lcc"/>

## Use

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

SAP Ariba Central Invoice Management on SAP BTP provides a unified solution for receiving and managing supplier invoices, with connection to different backend systems like SAP S/4HANA Cloud.

Using a formation of type *Integration with SAP Ariba Central Invoice Management*, you automatically set up an integration between systems of type *SAP Ariba Central Invoice Management* and *SAP S/4HANA Cloud*.

> ### Note:  
> This documentation refers to SAP S/4HANA Cloud Public Edition. See [Introduction to the Universe of SAP S/4HANA Cloud Public Edition](https://help.sap.com/docs/SAP_S4HANA_CLOUD/f77dde055ecb4541b57787d362c46a36/2962fce53eef47b4b3a8e6c945adafbe.html).



<a name="loio27ca5c25f93749298f85a6fcdfab1600__section_upy_xjf_lcc"/>

## Rules

When creating formations of type *Integration with SAP Ariba Central Invoice Management*, keep in mind the following rules:

-   System of type *SAP Ariba Central Invoice Management* can be included in at most one *Integration with SAP Ariba Central Invoice Management* formation.

-   Formation of type *Integration with SAP Ariba Central Invoice Management* can contain exactly one system of type *SAP Ariba Central Invoice Management*.

-   System of type *SAP S/4HANA Cloud* can be included in at most one *Integration with SAP Ariba Central Invoice Management* formation when creating this formation.

-   When registering the *SAP S/4HANA Cloud* system, you have to choose one of the following communication scenario groups:

    -   All Communication Scenarios

    -   Integration with SAP Ariba Central Invoice Management


    See [Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](register-an-sap-s-4hana-cloud-system-in-a-global-account-in-sap-btp-28171b6.md).




<a name="loio27ca5c25f93749298f85a6fcdfab1600__section_znb_p1c_dwb"/>

## Prerequisites

-   You are a global account administrator, or you are a system landscape administrator. See [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).

-   You have a system of type *SAP Ariba Central Invoice Management* in the *Systems* list. This system is auto-discovered because it is associated with your global account and has been discovered and added automatically to the list based on information of the existing system landscape.

-   You have registered the *SAP S/4HANA Cloud* system that you are going to include in the formation of type *Integration with SAP Ariba Central Invoice Management*.

    When you register an SAP S/4HANA Cloud system, use the *All Communication Scenarios* or the *Integration with SAP Ariba Central Invoice Management* communication scenario groups when you get the registration token for the SAP S/4HANA Cloud system. This allows the automatic enablement of the `SAP_COM_0897`, `SAP_COM_0516`, and `SAP_COM_0531` communication scenarios after the corresponding system is added to the formation of type *Integration with SAP Ariba Central Invoice Management*. See [Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](register-an-sap-s-4hana-cloud-system-in-a-global-account-in-sap-btp-28171b6.md).

-   You have created a formation of type *Integration with SAP Master Data Integration* and have included in it the *SAP Ariba Central Invoice Management* and the *SAP S/4HANA Cloud* systems. See [Enabling Integration with SAP Master Data Integration](enabling-integration-with-sap-master-data-integration-9743f20.md).




<a name="loio27ca5c25f93749298f85a6fcdfab1600__section_v4q_p1c_dwb"/>

## Procedure

As an alternative to the steps that follow, you can use the *Set Up SAP Ariba Central Invoice Management* booster in the SAP BTP cockpit and have the end-to-end scenario set up. The booster includes:

-   Creating new subaccounts

-   Creating required service instances and subscriptions

-   Configuring all the required business integrations with the Identity Authentication service, SAP Master Data Integration, and SAP S/4HANA Cloud


> ### Tip:  
> We recommend that you use the *Set Up SAP Ariba Central Invoice Management* booster.

1.  In the *System Landscape* \> *Systems* page of the SAP BTP cockpit, browse the already added systems in your system landscape.

    The *SAP S/4HANA Cloud* and the *SAP Ariba Central Invoice Management* systems you are going to include in this formation must not be part of another formation.

2.  In the *System Landscape* \> *Formations* page, create a formation of type *Integration with SAP Ariba Central Invoice Management* and include the relevant systems in it.

    1.  Add any name that helps you identify your formation.

    2.  In the *Formation Type* dropdown menu, select *Integration with SAP Ariba Central Invoice Management*.

    3.  Choose *Next Step*.

    4.  Select the *SAP Ariba Central Invoice Management* system that you want to include in the formation.

    5.  Select the other systems that you want to include. In the list you can select only systems that are allowed to be included in this formation.

    6.  Choose *Next Step*.

    7.  Review your selections and create the formation.



