<!-- loio109ce9c7234246c397d6c1e9c19e0d5e -->

# Business Event Data


<table>
<tr>
<td valign="top">

CDS View Name

</td>
<td valign="top">

`I_BuEvLgBusEvtFullPyldJSON` 

</td>
</tr>
</table>



## Purpose

This CDS view is designed to provide a comprehensive representation of business event data, including the full payload in JSON format. It serves as a transactional data source with high service quality and is capable of handling large volumes of data. The view is intended to facilitate the analysis and tracking of business events by capturing essential details such as the event's unique identifier, object type, payload content, and the last modification timestamp.

This CDS view provides the data to answer the following business questions:

-   What is the complete JSON payload associated with each business event?




## Prerequisites



### Authorizations

Users who want to use this CDS view must have the following authorization objects assigned:

-   <code><code>BEL_SOT</code></code> \(SAP Object Type\)




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

BusinessEventUUID

</td>
<td valign="top">

Unique identifier for business events.

</td>
</tr>
<tr>
<td valign="top">

SAPObjectType

</td>
<td valign="top">

The object type, a business object, or a technical object corresponding to the specified SAP object node type, for example: Outbound Delivery for Outbound Delivery Item.

</td>
</tr>
<tr>
<td valign="top">

BusEvtLogPayloadJSONString

</td>
<td valign="top">

Business Event Payload

</td>
</tr>
<tr>
<td valign="top">

BusEvtLogLastChangedDateTime

</td>
<td valign="top">

The date and timestamp of when the payload entry was last updated.

</td>
</tr>
</table>

