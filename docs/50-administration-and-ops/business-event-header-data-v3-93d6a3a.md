<!-- loio93d6a3af359642c793d24e93a3245c83 -->

# Business Event Header Data \(v3\)


<table>
<tr>
<td valign="top">

CDS View Name

</td>
<td valign="top">

`C_BUSEVTLOGEVENTDEX_3`

</td>
</tr>
<tr>
<td valign="top">

Analytical Data Category

</td>
<td valign="top">

Fact

</td>
</tr>
</table>



## Purpose

This CDS view is used to extract business event header data for C2-released external events, C1-released internal events, and direct APIs.

This CDS view provides the data to answer the following business questions:

-   Which business event has been logged?


To help you decide which CDS view to use for your purposes, SAP has introduced the annotation `ObjectModel.supportedCapabilities` that indicates the most appropriate use cases for each CDS view. To find out what use cases are best supported by this CDS view, access the entry of the CDS view in the *View Browser* app and find the values for this annotation under the *Annotation* tab. For more information, see [Supported Capabilities for CDS Views](https://help.sap.com/docs/SAP_S4HANA_CLOUD/c0c54048d35849128be8e872df5bea6d/6a6ff32b25dd473080e6aeddbefecfca.html).



## Structure



### Important Fields

Important fields in this view include the following:


<table>
<tr>
<th valign="top">

Field Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`EventOperation` 

</td>
<td valign="top">

Event operation, for example: Created, Deleted, Changed, and so on.

</td>
</tr>
<tr>
<td valign="top">

`SAPObjectType` 

</td>
<td valign="top">

The object type, a business object, or a technical object corresponding to the specified SAP object node type, for example: Outbound Delivery for Outbound Delivery Item.

</td>
</tr>
<tr>
<td valign="top">

`SAPObjectNodeType`

</td>
<td valign="top">

Node type of an object type, for example, for an Outbound Delivery SAP object type, the SAP object node types are Outbound Delivery \(header\) and Outbound Delivery Item \(item\).

</td>
</tr>
<tr>
<td valign="top">

`SAPBusinessObjectNodeKey1`

</td>
<td valign="top">

First part of the key of an object node instance, for example, in one event for an Outbound Delivery Item, the first part of the key is 80013910 \(outbound delivery number\).

</td>
</tr>
<tr>
<td valign="top">

`SAPBusinessObjectNodeKey2`

</td>
<td valign="top">

Second part of the key of an object node instance, for example, in one event for an Outbound Delivery Item, the second part of the key is 00020 \(item number\). If an event refers to an SAP object node type with only one key part \(such as: Outbound Delivery \[header\]\), then all subsequent key parts are empty.

> ### Note:  
> There can be many more node keys, depending on how many parts the object key has. For example: SAPBusinessObjectNodeKey3, SAPBusinessObjectNodeKey4, and so on.
> 
> SAPObjectNodeType and SAPBusinessObjectNodeKey \(1-7\) identify a node instance of an SAP object. Outbound Delivery Item is an example of an SAP object node.



</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogCreationDateTime`

</td>
<td valign="top">

Event execution timestamp

</td>
</tr>
<tr>
<td valign="top">

`CreatedByUser`

</td>
<td valign="top">

Users who created the event

</td>
</tr>
<tr>
<td valign="top">

`EventProducerNamespace`

</td>
<td valign="top">

Provides the event's namespace. This can either be a Standard or Custom

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogBusinessActivity`

</td>
<td valign="top">

Activity ID

</td>
</tr>
<tr>
<td valign="top">

`BusinessEventLogLogicalSystem`

</td>
<td valign="top">

Logical system

</td>
</tr>
<tr>
<td valign="top">

`IsTechnicalUser`

</td>
<td valign="top">

Is a technical user

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogUserInteractionType`

</td>
<td valign="top">

Application type

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogIsDeleted`

</td>
<td valign="top">

Deletion indicator

</td>
</tr>
<tr>
<td valign="top">

`BusinessEventLogEventVersion` 

</td>
<td valign="top">

Business event version

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogTransactionID` 

</td>
<td valign="top">

Identifies the session in which a business event was created

</td>
</tr>
<tr>
<td valign="top">

`BusinessEventLogSource` 

</td>
<td valign="top">

Business event source

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogEventHasFullPayload` 

</td>
<td valign="top">

Has all business event data

</td>
</tr>
</table>



<a name="loio93d6a3af359642c793d24e93a3245c83__section_x5y_hfj_kfb"/>

## Data Extraction



### Data Extraction Type

-   Full
-   Delta \(change data capture\)

> ### Note:  
> Data conversion using the Cloud Data Integration \(CDI\) channel can be different from that of the other channels \(ODATA, ABAP SQL Service, and so on\). For example:
> 
> -   The timestamps could appear in a different format
> 
> -   The IDs might not contain leading zeros
> 
> 
> There could be formatting changes for other data as well.

**Related Information**  


[Virtual Data Model and CDS Views in SAP S/4HANA Cloud Public Edition](https://help.sap.com/docs/SAP_S4HANA_CLOUD/c0c54048d35849128be8e872df5bea6d/8573b810511948c8a99c0672abc159aa.html)

