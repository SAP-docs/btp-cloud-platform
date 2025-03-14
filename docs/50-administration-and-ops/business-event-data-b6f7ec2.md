<!-- loiob6f7ec27a22142658138b9fe4c8d87cb -->

# Business Event Data


<table>
<tr>
<td valign="top">

CDS View Name

</td>
<td valign="top">

`C_BuEvLgEvtFullPayloadJSONDEX` 

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

This view represents the following object:

-   `BusEvtLogEvent` \(TechnicalObject\)




</td>
</tr>
</table>



<a name="loiob6f7ec27a22142658138b9fe4c8d87cb__section_fkf_qsd_22c"/>

## Purpose

This CDS view provides full business event data \(payload\) in JSON format.

This CDS view provides the data to answer the following business questions:

-   What is the full business data contained in the event?


To help you decide which CDS view to use for your purposes, SAP has introduced the annotation `ObjectModel.supportedCapabilities` that indicates the most appropriate use cases for each CDS view. To find out what use cases are best supported by this CDS view, access the entry of the CDS view in the *View Browser* app and find the values for this annotation under the *Annotation* tab.



<a name="loiob6f7ec27a22142658138b9fe4c8d87cb__section_gkf_qsd_22c"/>

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

`SAPObjectType` 

</td>
<td valign="top">

The object type, a business object, or a technical object corresponding to the specified object component. For example: Outbound Delivery for Outbound Delivery Item.

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogPayloadJSONString` 

</td>
<td valign="top">

Event Payload details in JSON format.

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogLastChangedDateTime`

</td>
<td valign="top">

Timestamp of when the event was changed.

</td>
</tr>
</table>

