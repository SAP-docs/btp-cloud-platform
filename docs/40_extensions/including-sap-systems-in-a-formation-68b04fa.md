<!-- loio68b04fa73aa740cb96ed380a85a4761a -->

# Including SAP Systems in a Formation

You can create a formation and assign to it the different SAP systems of the different SAP solutions that you want to extend in the context of the same business case.



<a name="loio68b04fa73aa740cb96ed380a85a4761a__prereq_b4m_xrd_jlb"/>

## Prerequisites

-   You are a global account administrator, or you are a system landscape administrator. See [Working with Role Collections](../50_administration_and_ops/working-with-role-collections-393ea0b.md)

-   You have enabled the environment, Cloud Foundry and/or Kyma, for the subaccount you want to assign to a formation.

-   You have registered the systems of the SAP solutions you want to assign to a formation. See [Registering an SAP System](registering-an-sap-system-2ffdaff.md).




## Context

You can create a formation and assign to it the different SAP systems of the different SAP solutions that you want to extend.

Extension business cases often involve extending several SAP solutions at a time. For example, for a single business case you have to extend the functionality and/or the UI of:

-   An SAP SuccessFactors system, and an SAP S/4HANA Cloud system. First, you need to configure the connectivity of each of these systems to Cloud Foundry, Kyma or both environments. Both extension applications are part of the same business need.

-   An SAP Commerce Cloud system, and an SAP S/4HANA Cloud system. Again, you first configure the connectivity of each of these systems to the Kyma environment.

-   A single system of the supported SAP solutions.


When creating a formation in the SAP BTP cockpit, you assign to it the systems of the different SAP solutions you want to extend, and an existing subaccount. You do this configuration once but you can change it any time.

These are the system types that can take part of a single formation and the respective supported environment:


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

 



</td>
<td valign="top">

Supported



</td>
</tr>
</table>

> ### Note:  
> When registering a system or creating a formation, the data you provide in the given input fields is not encrypted with your customer managed key. The data you enter is only encrypted at rest.



## Procedure

1.  Open the SAP BTP cockpit.

2.  Navigate to your global account.

3.  Choose *System Landscape* \> *Formations* from the left hand-side navigation.

4.  At the right top of the page, choose *Create Formation*.

5.  For the new formation you have to specify:

    -   Unique name

        > ### Note:  
        > The formation name must contain only lowercase alphanumeric characters, periods, or dashes. The name must start and end with an alphanumeric character.

    -   A subaccount that you have previously created

    -   All the systems of the different SAP systems that will be assigned to this formation


6.  Choose *Create*.




<a name="loio68b04fa73aa740cb96ed380a85a4761a__result_ll5_vsd_jlb"/>

## Results

For systems of type SAP Commerce Cloud, SAP Cloud for Customer, and SAP Field Service Management, the access to the corresponding solution's APIs has been enabled. After you have created a formation, you can edit it, change the assigned systems, and the subaccount. The status of each system depends on whether you have registered that system in the global account.

> ### Note:  
> If you want to delete a formation, you need to unassign all systems and the subaccount in advance. To do that, first, you have to edit the formation in the *Formations* page, unassign the systems and the subaccount, and get back to the list of available formations. Then, for the formation you want to delete, choose *Actions* \> *Delete*.



<a name="loio68b04fa73aa740cb96ed380a85a4761a__postreq_jls_r5d_jlb"/>

## Next Steps

For the systems of type SAP S/4HANA Cloud, SAP Marketing Cloud, and SAP SuccessFactors and a formation using the Cloud Foundry, or Kyma environment, you need to continue with assigning the required entitlements and creating a service instance to be able to consume the respective APIs.

-   SAP S/4HANA Cloud, and SAP Marketing Cloud:

    1.  [Configure the Entitlements for the SAP S/4HANA Cloud Extensibility Service](configure-the-entitlements-for-the-sap-s-4hana-cloud-extensibility-service-65ad330.md)

    2.  [Create a Service Instance to Consume the SAP S/4HANA Cloud APIs](create-a-service-instance-to-consume-the-sap-s-4hana-cloud-apis-a735641.md)


-   SAP SuccessFactors:

    1.  [Configure the Entitlements for the SAP SuccessFactors Extensibility Service](configure-the-entitlements-for-the-sap-successfactors-extensibility-service-b01e625.md)

    2.  [Create a Service Instance to Consume the SAP SuccessFactors HXM Suite OData API](create-a-service-instance-to-consume-the-sap-successfactors-hxm-suite-odata-api-46c5ea1.md)



