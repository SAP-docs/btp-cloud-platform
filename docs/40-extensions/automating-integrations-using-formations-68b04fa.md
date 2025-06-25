<!-- loio68b04fa73aa740cb96ed380a85a4761a -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Automating Integrations Using Formations

You can use the automated integration that allows you to include various SAP systems into a formation and thus combine diverse SAP solutions into an extended business scenario.



<a name="loio68b04fa73aa740cb96ed380a85a4761a__prereq_b4m_xrd_jlb"/>

## Prerequisites

-   You are a global account administrator, or you are a system landscape administrator. See [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).

-   The SAP solution systems that you want to include to a formation must be listed in the *Systems* page. See [Adding, Registering and Deregistering Systems](adding-registering-and-deregistering-systems-2ffdaff.md).




## Context

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

A formation is a logical grouping of SAP systems following a business scenario. Formations allow you to combine SAP solution systems to simplify the connectivity setup and to provide a unified view of all components required for the implementation of your integration or extension scenario. There are three formation types: formations for business scenarios, for integrating with a specific service in SAP BTP, and for extensibility.

When creating a formation in the SAP BTP cockpit, you include the systems of the different SAP solutions you want to extend. If your business case features more than one SAP solution system, you can use the corresponding button to include additional systems in the formation. You can start the dialog as many times and add systems to your formation as you want.

A formation can have the following status values:

-   *Ready*

    The formation has been added as a record to the list and all registered systems are included successfully.

-   *Draft*

    Not all the systems were included when creating the formation. Include all the missing systems and choose *Finalize Formation*.

-   *Action Required*

    The formation has been created but you cannot use it productively yet.

    Based on the formation type and the subaccount that you specified, it might require an SAP BTP Kyma environment instance or an SAP Business Application Studio subscription. Although the SAP BTP cockpit allows you to create such a formation, to enable and make use of it, you must also create the respective instance or subscription.

-   *Synchronizing*

    Systems that are included in the formation are currently synchronizing in the background.

-   *Error*

    An error occurred while some of the systems that are included in the formation were synchronizing in the background. In this case, report an incident in the `BC-CP-MP` component.


When you include systems in a formation, these systems are synchronized in the background. If an error occurs, you can resynchronize these systems to restart the synchronization process. To do that, choose *Resynchronize* for the particular formation. You will have this action available only for formations that are in status *Error*.

If you want to reconfigure the systems in a formation from scratch without excluding them, you have to choose *Reset and Resynchronize*. You will have this action available only for formations that have no status in SAP BTP cockpit and their formation type is *Side-by-Side Extensibility with Kyma*.

> ### Note:  
> When registering a system or creating a formation, the data you provide in the given input fields is not encrypted with your customer managed key. The data you enter is only encrypted at rest.



## Procedure

1.  Open the SAP BTP cockpit and navigate to your global account.

2.  Choose *System Landscape* \> *Formations*.

3.  Choose *Create Formation*.

    The *Create Formation* dialog opens. There, in a wizard, you can create a formation and include one or more SAP systems to it.

4.  On the *General Information* step of the wizard, enter the following information:

    1.  Enter a unique formation name.

        The formation name must be up to 128 symbols which can be lowercase or uppercase Latin letters, numbers, hyphens, spaces, or underscores only. The name must start and end with an alphanumeric character.

    2.  Specify a type for the formation.

        The formation type defines the use case.

        Depending on the type, a list of systems that can be included in this formation is loaded at the following step of the wizard.


5.  Choose *Next Step*.

6.  On the *Include Systems* step, select one or more systems that you want to include in the newly created formation, and then, choose *Next Step*.

    The wizard prefilters the systems that were added to the *Systems* page and are valid for the formation type that you specified at the previous step.

7.  On the *Review* step, double check your entries before you create the formation.

    If you want to make any changes, either you can edit the corresponding section directly, or use the *Previous* button.

8.  Choose *Create*.

9.  Optionally, you can include additional systems to the newly created formation, by choosing *Include System*.

    On the systems list that opens, select a system, and then, choose *Include*.




<a name="loio68b04fa73aa740cb96ed380a85a4761a__result_ll5_vsd_jlb"/>

## Results

> ### Note:  
> When you delete a formation, several activities are performed at one go. First, the systems are excluded from the formation. Then, the subaccount is unassigned. Finally, the formation is deleted from the *Formations* page completely.
> 
> To restore a deleted formation, first you must create it anew, and then, include all of its systems again, one by one.



<a name="loio68b04fa73aa740cb96ed380a85a4761a__postreq_lly_n2t_pfc"/>

## Next Steps

Once the formation is ready, you might need to configure additionally some of the systems that are part of this formation. You get the configuration details from the formation and then you go to the respective system and add these details. Such a system is the SAP S/4HANA Cloud Private Edition. To get the configuration details, you have to:

1.  In the *Formations* page, select the formation you are working with.
2.  Choose the system that needs additional configuration to open its details. In this example, this is the SAP S/4HANA Cloud Private Edition system.
3.  Go to the *Configuration for System... Provided By* section and in the *Actions* column, choose <span class="SAP-icons-V5"></span> \(Syntax\).
4.  You get the configuration details in a visual or in a JSON format. Copy the details that you need.

Depending on the system type, use the details you've copied to configure the system.

**Related Information**  


[Automating Integrations with SAP Ariba Buying](automating-integrations-with-sap-ariba-buying-3c98c84.md "")

[Automating Integrations with SAP Start](automating-integrations-with-sap-start-f7d3f5e.md "")

[Automating Integrations with Data Ingestion for Industry Cloud Solutions](automating-integrations-with-data-ingestion-for-industry-cloud-solutions-0b23a32.md "")

[Automating Integrations with SAP Ariba Central Invoice Management](automating-integrations-with-sap-ariba-central-invoice-management-27ca5c2.md "")

[Automating Integrations with SAP Subscription Billing](automating-integrations-with-sap-subscription-billing-08f42b2.md "")

[Automating Integrations with SAP Collaboration Manager](automating-integrations-with-sap-collaboration-manager-b4297f9.md "")

[Automating Integrations with SAP Advanced Financial Closing](automating-integrations-with-sap-advanced-financial-closing-46d0881.md "")

[Enabling Joule](enabling-joule-e208f1f.md "")

[Enabling Events Exchange Between SAP Cloud Systems](enabling-events-exchange-between-sap-cloud-systems-1592246.md "")

[Enabling Integration with SAP Master Data Integration](enabling-integration-with-sap-master-data-integration-9743f20.md "")

[Enabling SAP Business Data Cloud](enabling-sap-business-data-cloud-78c9fd9.md "")

[Setting Up System Landscape for Kyma](setting-up-system-landscape-for-kyma-9154051.md "")

[Setting Up System Landscape for SAP Build](setting-up-system-landscape-for-sap-build-6424311.md "")

[Setting Up System Landscape for SAP Integration Suite](setting-up-system-landscape-for-sap-integration-suite-a14c276.md "")

[Setting Up System Landscape for SAP Business Application Studio](setting-up-system-landscape-for-sap-business-application-studio-272ca23.md "")

