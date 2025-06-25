<!-- loio78c9fd9cb71d47dc8807f0366e9fa80d -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Enabling SAP Business Data Cloud



<a name="loio78c9fd9cb71d47dc8807f0366e9fa80d__section_kbh_41c_dwb"/>

## Use

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

SAP Business Data Cloud is a fully managed Software-as-a-Service \(SaaS\) solution that unifies and governs all SAP data and seamlessly connects with third-party data, giving users the context to make more impactful decisions.

To connect the data from various systems, you have to integrate these systems with SAP Business Data Cloud. To do that, you have to include the systems in a formation of type *Integration with SAP Business Data Cloud* on the *System Landscape* \> *Formations* page of the SAP BTP cockpit or the *Customer Landscape* \> *Formations* in SAP for Me. The integration is between the SAP Business Data Cloud system and every system in the formation, but not between each and every SAP system.

The supported systems that can be included in a *Integration with SAP Business Data Cloud* formation are listed at [Creating SAP Business Data Cloud Formations](https://help.sap.com/docs/business-data-cloud/administering-sap-business-data-cloud/integrate-sap-business-data-cloud-provisioned-systems).



<a name="loio78c9fd9cb71d47dc8807f0366e9fa80d__section_h1s_5t2_lcc"/>

## Rules

When creating *Integration with SAP Business Data Cloud* formations, keep in mind the following rules:

-   At most one system of type *SAP Business Data Cloud*, *SAP Analytics Cloud*, or *SAP Datasphere* can be included in one *Integration with SAP Business Data Cloud* formation.

-   A system of type *SAP Business Data Cloud*, *SAP Analytics Cloud*, or *SAP Datasphere* can be included in at most one *Integration with SAP Business Data Cloud* formation.




<a name="loio78c9fd9cb71d47dc8807f0366e9fa80d__section_znb_p1c_dwb"/>

## Prerequisites

-   You are a global account administrator, or you are a system landscape administrator. See [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).

-   You have a SAP Business Data Cloud system and at least one other system of the supported types that fulfill the rules in the *Systems* page. The SAP Business Data Cloud system is auto-discovered.




<a name="loio78c9fd9cb71d47dc8807f0366e9fa80d__section_v4q_p1c_dwb"/>

## Procedure

The following procedure outlines the steps you need to perform to enable the integration between Integration with SAP Business Data Cloud and SAP systems that are part of the SAP Business Data Cloud suite such as SAP Analytics Cloud, SAP Databricks, and SAP Datasphere.

1.  In the SAP BTP cockpit, in the *System Landscape* \> *Systems* page of the SAP BTP cockpit, browse the already added systems in your customer system landscape. If there are systems that are missing, you have to provision them first in the SAP Business Data Cloud suite in SAP for Me. See [Provisioning SAP Business Data Cloud Applications](https://help.sap.com/docs/business-data-cloud/administering-sap-business-data-cloud/provision-sap-business-data-cloud-applications).

    The *SAP Business Data Cloud* system you are going to include in this formation must not be part of another formation.

    > ### Note:  
    > If a given SAP system is missing on the *Systems* page, it may be associated with a different customer ID on the SAP BTP global account or SAP for Me. In this case, you have to provision it in SAP for Me.

2.  Create a formation of type *Integration with SAP Business Data Cloud* and include the relevant systems in it.

    1.  Add any name that helps you identify your formation.

    2.  In the *Formation Type* dropdown menu, select *Integration with SAP Business Data Cloud*.

    3.  Select the systems that you want to include in the formation. One of these systems must be of type *SAP Business Data Cloud*.

        > ### Note:  
        > Systems can only be added to one formation of type *Integration with SAP Business Data Cloud*.
        > 
        > Also, a formation of type *Integration with SAP Business Data Cloud* can contain only one system of type *SAP Business Data Cloud*.

    4.  Review your selections and create the formation.





<a name="loio78c9fd9cb71d47dc8807f0366e9fa80d__section_bbm_s3m_vvb"/>

## Next Steps

Once the formation is ready, you have to configure additionally the SAP S/4HANA Cloud Private Edition system:

1.  In the *Formations* page, select the formation of type *Integration with SAP Business Data Cloud*.
2.  Choose the SAP S/4HANA Cloud Private Edition system to open its details.
3.  Go to the *Configuration for System... Provided By* section and in the *Actions* column, choose <span class="SAP-icons-V5"></span> \(Syntax\).
4.  You get the configuration details in a visual or in a JSON format. Copy the details that you need.
5.  Follow these steps listed at [Integrating SAP S/4HANA Cloud Private Edition to SAP Business Data Cloud](https://help.sap.com/docs/business-data-cloud/administering-sap-business-data-cloud/set-up-connectivity-with-sap-s-4hana-cloud-private-edition):
    -   Step 4: Set Up Outbound Communication for SAP S/4HANA Cloud Private Edition
    -   Step 5: Configure the SAP Cloud Connector


