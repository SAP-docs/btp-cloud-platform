<!-- loio2e3f4d66458d40289d585a79d8e8c920 -->

# Business Event Logging Field Changes


<table>
<tr>
<td valign="top">

CDS View Name

</td>
<td valign="top">

`I_BusEvtLogFieldChange`

</td>
</tr>
</table>



## Purpose

This CDS view provides access to field-level changes captured in the Business Event Logging framework. It retrieves detailed information about field modifications including old and new values, units, currencies, and timestamps for business events.

This CDS view provides the data to answer the following business questions:

-   What fields were changed in a specific business event?

-   What were the old and new values for a changed field?

-   When was a specific field last changed in a business event?

-   Which business activities triggered field changes?




## Prerequisites



### Authorizations

-   This CDS view doesn't perform any authorization checks. You can use it without assigning additional authorizations to your business users. However, users still need access to the app or API that exposes the data.




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

`BusinessEventUUID`

</td>
<td valign="top">

Event GUID

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

`BusEvtLogChgDocFieldName`

</td>
<td valign="top">

Field Identifier for SAP Object

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogChgDocOldFieldValue`

</td>
<td valign="top">

Previous Value of an Attribute

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogChgDocOldUnit`

</td>
<td valign="top">

Previous Unit of Measure

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogChgDocNewFieldValue`

</td>
<td valign="top">

Updated Value of an Attribute

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogChgDocNewUnit`

</td>
<td valign="top">

Updated Unit of Measure

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogChgDocPrevCurrency`

</td>
<td valign="top">

Previous Currency Key

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogChgDocNewCurrency`

</td>
<td valign="top">

Updated Currency Key

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogLastChangedDateTime`

</td>
<td valign="top">

Timestamp of Last Change

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogPayloadFieldPath`

</td>
<td valign="top">

Path to the Field in BEL Payload

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogGlobalFieldName`

</td>
<td valign="top">

Field Name

</td>
</tr>
<tr>
<td valign="top">

`ChangeDocumentDatabaseTable`

</td>
<td valign="top">

Table Name

</td>
</tr>
<tr>
<td valign="top">

`ChangeDocDatabaseTableField`

</td>
<td valign="top">

Field Name

</td>
</tr>
<tr>
<td valign="top">

`BuEvLgGlobalFieldNameUpperCase`

</td>
<td valign="top">

Property Name of the Object

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
</table>

