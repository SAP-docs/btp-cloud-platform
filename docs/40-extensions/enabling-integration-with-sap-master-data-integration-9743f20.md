<!-- loio9743f20380de4f9f99385cf3737b59b7 -->

# Enabling Integration with SAP Master Data Integration



<a name="loio9743f20380de4f9f99385cf3737b59b7__section_kpl_4jf_lcc"/>

## Use

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

SAP Master Data Integration service is a central master data hub. Applications integrate with SAP Master Data Integration to synchronize their local master data databases with the master data database of the central hub. In a typical setup, there is exactly one tenant of SAP Master Data Integration for each landscape. See [What Is Master Data Integration?](https://help.sap.com/docs/master-data-integration/sap-master-data-integration-prod/what-is-master-data-integration?version=CLOUD).

Using a formation of type *Integration with SAP Master Data Integration*, you automatically set up an integration between systems of type SAP Master Data Integration and other systems or applications, for example SAP S/4HANA Cloud.

> ### Note:  
> This documentation refers to SAP S/4HANA Cloud Public Edition. See [Introduction to the Universe of SAP S/4HANA Cloud Public Edition](https://help.sap.com/docs/SAP_S4HANA_CLOUD/f77dde055ecb4541b57787d362c46a36/2962fce53eef47b4b3a8e6c945adafbe.html).



<a name="loio9743f20380de4f9f99385cf3737b59b7__section_jvz_4jf_lcc"/>

## Rules

When creating formations of type *Integration with SAP Master Data Integration*, keep in mind the following rules:

-   System of type *SAP Master Data Integration* can be included in at most one *Integration with SAP Master Data Integration* formation.

-   Formation of type *Integration with SAP Master Data Integration* can contain exactly one system of type *SAP Master Data Integration*.

-   System of type *SAP S/4HANA Cloud* can be included in at most one *Integration with SAP Master Data Integration* formation.

-   When registering the *SAP S/4HANA Cloud* system, you have to choose one of the following communication scenario groups:

    -   All Communication Scenarios

    -   Integration with SAP Master Data Integration

    -   Integration with SAP Ariba Central Invoice Management


    See [Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](register-an-sap-s-4hana-cloud-system-in-a-global-account-in-sap-btp-28171b6.md).




<a name="loio9743f20380de4f9f99385cf3737b59b7__section_znb_p1c_dwb"/>

## Prerequisites

-   You are a global account administrator, or you are a system landscape administrator. See [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).

-   You have a system of type *SAP Master Data Integration* in the *Systems* list. This system is auto-discovered because it is associated with your global account and has been discovered and added automatically to the list based on information of the existing system landscape.

-   You have registered the *SAP S/4HANA Cloud* system that you are going to include in the formation of type *Integration with SAP Master Data Integration*.




<a name="loio9743f20380de4f9f99385cf3737b59b7__section_v4q_p1c_dwb"/>

## Procedure

1.  In the *System Landscape* \> *Systems* page of the SAP BTP cockpit, browse the already added systems in your system landscape.

2.  In the *System Landscape* \> *Formations* page, create a formation of type *Integration with SAP Master Data Integration* and include the relevant systems in it.

    1.  Add any name that helps you identify your formation.

    2.  In the *Formation Type* dropdown menu, select *Integration with SAP Master Data Integration*.

    3.  Choose *Next Step*.

    4.  Select the *SAP Master Data Integration* system that you want to include in the formation.

    5.  Select the other systems that you want to include. In the list you can select only systems that are allowed to be included in this formation.

    6.  Choose *Next Step*.

    7.  Review your selections and create the formation.





<a name="loio9743f20380de4f9f99385cf3737b59b7__section_iqx_d2y_fdc"/>

## Next Steps

Depending on the specific scenario, the next steps would be different. For example, if an SAP Ariba Central Invoice Management system is included in a formation of type *Integration with SAP Master Data Integration*, then continue with the steps described in [Automating Integrations with SAP Ariba Central Invoice Management](automating-integrations-with-sap-ariba-central-invoice-management-27ca5c2.md).

