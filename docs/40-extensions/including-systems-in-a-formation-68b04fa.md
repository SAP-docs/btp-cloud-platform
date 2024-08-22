<!-- loio68b04fa73aa740cb96ed380a85a4761a -->

# Including Systems in a Formation

You can include various SAP systems into a formation and thus combine diverse SAP solutions into an extended business scenario.



<a name="loio68b04fa73aa740cb96ed380a85a4761a__prereq_b4m_xrd_jlb"/>

## Prerequisites

-   You are a global account administrator, or you are a system landscape administrator. See [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).

-   The SAP solution systems that you want to include to a formation must be added at the *Systems* list in the *System Landscape* page. See [Registering an SAP System](registering-an-sap-system-2ffdaff.md).




## Context

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

A formation is a logical grouping of SAP systems that can be extended in a business scenario. Formations allow you to combine SAP solution systems and a subaccount in SAP BTP to simplify the connectivity setup and to provide a unified view of all components required for the implementation of your extension scenario. To create a fully functional formation, you can use a two-step wizard. At the first step, you specify a custom formation name and assign a subaccount to it. At the second step, you can include an SAP solution system in the formation. You do this configuration once and you can change it anytime.

> ### Note:  
> You can assign a subaccount to the formation during the formation creation only. While you can include or exclude systems in the formation anytime, you cannot unassign or reassign subaccounts later on. Instead, you must recreate the formation.

Extension business cases often involve extending several SAP solutions at a time. For example, for a given business case you might need to extend the functionality or the UI as follows:

-   An SAP SuccessFactors system, and an SAP S/4HANA Cloud system. First, you need to configure the connectivity of each of these systems to Cloud Foundry, Kyma, or both environments. Extension applications of both solutions are part of the same business need.

-   An SAP Commerce Cloud system, and an SAP S/4HANA Cloud system. Again, you first configure the connectivity of each of these systems to the Kyma environment.

-   A single system of the supported SAP solutions.

-   SAP systems that expose event data, which can be shared and exchanged with the systems included in the formation.


When creating a formation in the SAP BTP cockpit, you include the systems of the different SAP solutions you want to extend. If your business case features more than one SAP solution system, you can use the corresponding button to include additional systems in the formation. You can start the dialog as many times and add systems to your formation as you want.

A formation can have the following status values:

-   No status

    The formation has been added as a record to the list and all registered systems are included successfully.

-   *Action Required*

    The formation has been created but you cannot use it productively yet.

    Based on the formation type and the subaccount that you specified, it might require an SAP BTP Kyma environment instance or an SAP Business Application Studio subscription. Although the SAP BTP cockpit allows you to create such a formation, to enable and make use of it, you must also create the respective instance or subscription.

-   *Synchronizing*

    Systems that are included in the formation are currently synchronizing in the background.

-   *Error*

    An error occurred while some of the systems that are included in the formation were synchronizing in the background. In this case, report an incident in the `BC-CP-MP` component.


When you include systems in a formation, these systems are synchronized in the background. If an error occurs, you can resynchronize these systems to restart the synchronization process. To do that, choose *Resynchronize* for the particular formation. You will have this action available only for formations that are in status *Error*.

If you want to reconfigure the systems in a formation from scratch without excluding them, you have to choose *Reset and Resynchronize*. You will have this action available only for formations that have no status in SAP BTP cockpit and their formation type is Side-by-Side Extensibility with Kyma.

> ### Note:  
> When registering a system or creating a formation, the data you provide in the given input fields is not encrypted with your customer managed key. The data you enter is only encrypted at rest.



## Procedure

1.  Open the SAP BTP cockpit and navigate to your global account.

2.  Choose *System Landscape* \> *Formations*.

3.  Choose *Create Formation*.

    The *Create Formation* dialog opens. There, in a wizard, you can create a formation and include one or more SAP systems to it.

4.  On the *General Information* step of the wizard, enter the following information:

    1.  Enter a unique formation name.

        The formation name can contain lowercase or uppercase Latin letters, numbers, hyphens, spaces, or underscores only. The name must start and end with an alphanumeric character.

    2.  Specify a type for the formation.

        The formation type defines the use case. Therefore, depending on the use case, you can specify one of the following formation types:

        ****


        <table>
        <tr>
        <th valign="top">

        Formation Type
        
        </th>
        <th valign="top">

        Description
        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
        *Side-by-Side Extensibility with Kyma* 
        
        </td>
        <td valign="top">
        
        Formations of type *Side-by-Side extensibility with Kyma* enable business scenarios that involve extending the functionality of several SAP systems at a time with SAP BTP Kyma environment instance.

        See [Enabling Side-by-Side Extensibility with Kyma](enabling-side-by-side-extensibility-with-kyma-9154051.md).
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *Developing with SAP Business Application Studio* 
        
        </td>
        <td valign="top">
        
        Formations of type *Developing with SAP Business Application Studio* enable connectivity between given SAP systems of type *SAP S/4HANA Cloud* from the *System Landscape* page of SAP BTP cockpit and the SAP Business Application Studio, you must create a formation of the corresponding type and include the SAP S/4HANA Cloud systems in it.

        See [Enabling System Landscape for SAP Business Application Studio](enabling-system-landscape-for-sap-business-application-studio-272ca23.md).
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *Integration with SAP Build* 
        
        </td>
        <td valign="top">
        
        Formations of type *Integration with SAP Build* enable connectivity between given SAP systems of type *SAP S/4HANA Cloud* from the *System Landscape* page of SAP BTP cockpit and SAP Build. Уou must create a formation of the corresponding type and include the SAP S/4HANA Cloud systems in it.

        See [Enabling System Landscape for SAP Build](enabling-system-landscape-for-sap-build-6424311.md).
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *Integration with SAP Integration Suite* 
        
        </td>
        <td valign="top">
        
        Formations of type *Integration with SAP Integration Suite* enable the communication flow between SAP S/4HANA Cloud systems and SAP Integration Suite.

        See [Enabling System Landscape for SAP Integration Suite](enabling-system-landscape-for-sap-integration-suite-a14c276.md).
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *Eventing Between SAP Cloud Systems* 
        
        </td>
        <td valign="top">
        
        Formations of type *Eventing Between SAP Cloud Systems* enable end-to-end communication flow of events between the SAP systems that are included in the given formation. As the name of the formation suggests, the systems transmit information about events using SAP Event Broker. To be able to exchange such events information, the SAP systems must be also visible and configurable in the SAP Event Broker user interface. The formation makes the systems visible in SAP Event Broker, however, it requires a subscription to SAP Event Broker in the corresponding SAP BTP subaccount first.

        See [Enabling Events Exchange Between SAP Cloud Systems](enabling-events-exchange-between-sap-cloud-systems-1592246.md).
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *Integration with SAP Ariba Buying* 
        
        </td>
        <td valign="top">
        
        Formations of type *Integration with SAP Ariba Buying* set up SAP Ariba Buying with SAP S/4HANA Cloud on SAP BTP.

        See [Enabling SAP Ariba Buying](enabling-sap-ariba-buying-3c98c84.md).
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *Integration with SAP Start* 
        
        </td>
        <td valign="top">
        
        Formations of type *Integration with SAP Start* set up SAP Start with SAP S/4HANA Cloud on SAP BTP.

        See [Enabling SAP Start](enabling-sap-start-f7d3f5e.md).
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        *Data Ingestion for Industry Cloud Solutions* 
        
        </td>
        <td valign="top">
        
        Formations of type *Data Ingestion for Industry Cloud Solutions* set systems that support data ingestion and are part of the industry cloud solutions published by SAP and SAP BTP.

        See [Enabling Data Ingestion for Industry Cloud Solutions](enabling-data-ingestion-for-industry-cloud-solutions-0b23a32.md).
        
        </td>
        </tr>
        </table>
        
        Depending on the type, a list of systems that can be included in this formation is loaded at the following step of the wizard.

    3.  Specify a subaccount that you want to associate with the formation.

        All systems that you include in the formation will be available and can be managed in the respective application or runtime in this subaccount.


    > ### Note:  
    > Based on the formation type and the subaccount that you specified in the newly created formation, it might require an SAP BTP Kyma environment instance. Although the SAP BTP cockpit allows you to create such a formation, to enable and make use of it, you must also create an SAP BTP Kyma environment instance for the corresponding SAP BTP subaccount.

5.  Choose *Next Step*.

6.  On the *Include Systems* step, select one or more systems that you want to include in the newly created formation, and then, choose *Next Step*.

    The wizard prefilters the systems that were added to the *Systems* tab and are valid for the formation type that you specified at the previous step.

7.  On the *Review* step, double check your entries before you create the formation.

    If you want to make any changes, either you can edit the corresponding section directly, or use the *Previous* button.

8.  Choose *Create*.

9.  Optionally, you can include additional systems to the newly created formation, by choosing *Include System*.

    On the systems list that opens, select a system, and then, choose *Include*.




<a name="loio68b04fa73aa740cb96ed380a85a4761a__result_ll5_vsd_jlb"/>

## Results

For systems of type SAP Commerce Cloud, SAP Cloud for Customer, and SAP Field Service Management, the access to the corresponding solution's APIs has been enabled. After you have created a formation, you can edit it and change the included systems. The status of each system depends on whether you have registered that system in the global account.

> ### Note:  
> When you delete a formation, several activities are performed at one go. First, the systems are excluded from the formation. Then, the subaccount is unassigned. Finally, the formation is deleted from the formations list completely.
> 
> To restore a deleted formation, first you must create it anew, and then, include all of its systems again, one by one.



<a name="loio68b04fa73aa740cb96ed380a85a4761a__postreq_jls_r5d_jlb"/>

## Next Steps

For the systems of type SAP S/4HANA Cloud, SAP Marketing Cloud, and SAP SuccessFactors and a formation using the Cloud Foundry environment, or the Kyma environment, to be able to consume the respective APIs, you need to continue with assigning the required entitlements and creating a service instance.

-   SAP S/4HANA Cloud, and SAP Marketing Cloud:

    1.  [Configure the Entitlements for the SAP S/4HANA Cloud Extensibility Service](configure-the-entitlements-for-the-sap-s-4hana-cloud-extensibility-service-65ad330.md)

    2.  [Create a Service Instance to Consume the SAP S/4HANA Cloud APIs](create-a-service-instance-to-consume-the-sap-s-4hana-cloud-apis-a735641.md)


-   SAP SuccessFactors:

    1.  [Configure the Entitlements for the SAP SuccessFactors Extensibility Service](configure-the-entitlements-for-the-sap-successfactors-extensibility-service-b01e625.md)

    2.  [Create a Service Instance to Consume the SAP SuccessFactors HXM Suite OData API](create-a-service-instance-to-consume-the-sap-successfactors-hxm-suite-odata-api-46c5ea1.md)



