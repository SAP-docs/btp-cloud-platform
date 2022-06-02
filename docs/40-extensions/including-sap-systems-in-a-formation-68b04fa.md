<!-- loio68b04fa73aa740cb96ed380a85a4761a -->

# Including SAP Systems in a Formation

You can include various SAP systems into a formation and thus combine diverse SAP solutions into an extended business scenario.



<a name="loio68b04fa73aa740cb96ed380a85a4761a__prereq_b4m_xrd_jlb"/>

## Prerequisites

-   You are a global account administrator, or you are a system landscape administrator. See [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).

-   The SAP solution systems that you want to include to a formation must be added at the *Systems* screen. See [Registering an SAP System](registering-an-sap-system-2ffdaff.md).




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


When creating a formation in the SAP BTP cockpit, you include the systems of the different SAP solutions you want to extend. If your business case features more than one SAP solution system, you can use the corresponding button to include additional systems in the formation. You can start the dialog as many times and add systems as you want to your formation.

The table below outlines the system types that you can include in a formation, as well as, the supported SAP BTP environment:


<table>
<tr>
<th valign="top">

System Type



</th>
<th valign="top">

 Cloud Foundry Environment



</th>
<th valign="top">

 Kyma Environment



</th>
</tr>
<tr>
<td valign="top">

SAP S/4HANA Cloud



</td>
<td valign="top">

Supported



</td>
<td valign="top">

Supported



</td>
</tr>
<tr>
<td valign="top">

SAP Marketing Cloud



</td>
<td valign="top">

Supported



</td>
<td valign="top">

Supported



</td>
</tr>
<tr>
<td valign="top">

SAP SuccessFactors



</td>
<td valign="top">

Supported



</td>
<td valign="top">

Supported



</td>
</tr>
<tr>
<td valign="top">

SAP Commerce Cloud



</td>
<td valign="top">

\-



</td>
<td valign="top">

Supported



</td>
</tr>
<tr>
<td valign="top">

SAP Cloud for Customer



</td>
<td valign="top">

\-



</td>
<td valign="top">

Supported



</td>
</tr>
<tr>
<td valign="top">

SAP Field Service Management



</td>
<td valign="top">

\-



</td>
<td valign="top">

Supported



</td>
</tr>
</table>

> ### Note:  
> When registering a system or creating a formation, the data you provide in the given input fields is not encrypted with your customer managed key. The data you enter is only encrypted at rest.



## Procedure

1.  Open the SAP BTP cockpit and navigate to your global account.

2.  Choose *System Landscape* \> *Formations*.

3.  Choose *Create Formation*.

    The *Create Formation* dialog opens. There, in a two-step wizard, you can create a formation, and then, include an SAP system to it.

4.  Enter a unique formation name.

    The formation name can contain lowercase or uppercase Latin letters, numbers, hyphens, spaces, or underscores only. The name must start and end with an alphanumeric character.

5.  Specify a subaccount that you want to associate with the formation.

6.  Choose *Create*.

7.  Optionally, to include an SAP solution system to the newly created formation, choose *Include System*.

    On the systems list that opens, select a system, and then, choose *Include*.




<a name="loio68b04fa73aa740cb96ed380a85a4761a__result_ll5_vsd_jlb"/>

## Results

For systems of type SAP Commerce Cloud, SAP Cloud for Customer, and SAP Field Service Management, the access to the corresponding solution's APIs has been enabled. After you have created a formation, you can edit it and change the included systems. The status of each system depends on whether you have registered that system in the global account.

> ### Note:  
> When you delete a formation, several activities are performed at one go. First, the SAP solution systems are excluded from the formation. Then, the subaccount is unassigned. Finally, the formation is deleted from the formations list completely.
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



