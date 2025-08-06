<!-- loio1c38309b07c44272ae165e1e01e8296f -->

# Business Event Header Data \(v2\)


<table>
<tr>
<td valign="top">

CDS View Name

</td>
<td valign="top">

`C_BUSEVTLOGEVENTDEX_2` 

</td>
</tr>
<tr>
<td valign="top">

Analytical Data Category

</td>
<td valign="top">

@Analytics.dataCategory: \#FACT

</td>
</tr>
<tr>
<td valign="top">

Represented Objects

</td>
<td valign="top">

This view represents the following objects:

-   `BusEvtLogEvent` \(TechnicalObject\)




</td>
</tr>
</table>



<a name="loio1c38309b07c44272ae165e1e01e8296f__section_qqk_dsd_22c"/>

## Purpose

This CDS view is used to extract business event header data for C2-released “external” events, and direct APIs.

This CDS view provides the data to answer the following business questions:

-   Which business event has been logged?


To help you decide which CDS view to use for your purposes, SAP has introduced the annotation `ObjectModel.supportedCapabilities` that indicates the most appropriate use cases for each CDS view. To find out what use cases are best supported by this CDS view, access the entry of the CDS view in the *View Browser* app and find the values for this annotation under the *Annotation* tab.



<a name="loio1c38309b07c44272ae165e1e01e8296f__section_rqk_dsd_22c"/>

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



</td>
</tr>
<tr>
<td valign="top">

`SAPObjectType` 

</td>
<td valign="top">

The object type, a business object, or a technical object corresponding to the specified object component, for example: Outbound Delivery for Outbound Delivery Item.

</td>
</tr>
<tr>
<td valign="top">

`SAPObjectNodeType`

</td>
<td valign="top">

Object component, for example, for an Outbound Delivery object, the object components are Outbound Delivery \(header\) and Outbound Delivery Item \(item\).

</td>
</tr>
<tr>
<td valign="top">

`SAPBusinessObjectNodeKey1`

</td>
<td valign="top">

First part of the key of an object instance, for example, in one event for an Outbound Delivery Item, the first part of the key is 80013910 \(outbound delivery number\).

</td>
</tr>
<tr>
<td valign="top">

`SAPBusinessObjectNodeKey2`

</td>
<td valign="top">

Second part of the key of an object instance, for example, in one event for an Outbound Delivery Item, the second part of the key is 00020 \(item number\). If an event refers to an object component with only one key part \(such as: Outbound Delivery \[header\]\), then all subsequent key parts are empty.

> ### Note:  
> There can be many more object ID, depending on how many parts the object key has. For example: SAPBusinessObjectNodeKey3, SAPBusinessObjectNodeKey4, and so on.
> 
> SAPObjectNodeType and SAPBusinessObjectNodeKey \(1-7\) identify an instance of an object. Outbound Delivery Item is an example of an instance.



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
</table>



<a name="loio1c38309b07c44272ae165e1e01e8296f__section_tqk_dsd_22c"/>

## Examples

An example of events include:

BusinessPartner

-   Business partner created

-   Business partner changed

For more information on other events, refer to the SAP Business Accelerator Hub.

