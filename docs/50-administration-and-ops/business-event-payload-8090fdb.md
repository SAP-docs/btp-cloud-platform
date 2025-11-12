<!-- loio8090fdbda2e6425690991697be49c5fe -->

# Business Event Payload


<table>
<tr>
<td valign="top">

CDS View Name

</td>
<td valign="top">

`I_BusEvtLogBusEventPayload` 

</td>
</tr>
</table>



<a name="loio8090fdbda2e6425690991697be49c5fe__section_bh3_lwc_bhc"/>

## Purpose

This CDS view is designed to capture and provide detailed information about changes in business event payloads. It tracks the old and new values of fields, along with their units and currencies, and records metadata about the changes, such as the last change date and the relevant database tables and fields.

This CDS view provides the data to answer the following business questions:

-   Which fields in the business object have been modified, and what are their previous and current states?

-   Which database tables and fields are associated with the changes in the business event payloads in case the change is related to change documents?

-   Are there any fields qualifying the event semantics?




<a name="loio8090fdbda2e6425690991697be49c5fe__section_ch3_lwc_bhc"/>

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

BusEvtLogFieldName

</td>
<td valign="top">

Field of an SAP object. Example: Amount

</td>
</tr>
<tr>
<td valign="top">

BusEvtLogOldFieldValue

</td>
<td valign="top">

Previous Value of an Attribute

</td>
</tr>
<tr>
<td valign="top">

BusEvtLogOldFieldUnit

</td>
<td valign="top">

Previous Unit of Measure

</td>
</tr>
<tr>
<td valign="top">

BusEvtLogNewFieldValue

</td>
<td valign="top">

Updated Value of an Attribute

</td>
</tr>
<tr>
<td valign="top">

BusEvtLogNewFieldUnit

</td>
<td valign="top">

Updated Unit of Measure

</td>
</tr>
<tr>
<td valign="top">

BusEvtLogOldFieldCurrency

</td>
<td valign="top">

Previous Currency Key

</td>
</tr>
<tr>
<td valign="top">

BusEvtLogNewFieldCurrency

</td>
<td valign="top">

Updated Currency Key

</td>
</tr>
<tr>
<td valign="top">

BusEvtLogFieldHasOldValue

</td>
<td valign="top">

This is a Boolean flag that indicates whether there was a value for the field.

</td>
</tr>
<tr>
<td valign="top">

BusEvtLogFieldIsQualifier

</td>
<td valign="top">

This is a Boolean flag that indicates whether the field is an event qualifier. A qualifier is an annotated field in a generic event that defines the event in more detail. The value of the qualifier field describes a generic event in detail.

Example: For the event Outb Deliv Goods Issue Status Changed the qualified field or Qualifier is OverallGoodsMovementStatus, with the values: Not yet started, Partially Completed, Completed, or Not Relevant

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
<tr>
<td valign="top">

BusEvtLogGlobalFieldName

</td>
<td valign="top">

Field of an SAP object. Example: Amount

</td>
</tr>
<tr>
<td valign="top">

BuEvLgGlobalFieldNameUpperCase

</td>
<td valign="top">

Property Name of the Object

</td>
</tr>
<tr>
<td valign="top">

ChangeDocumentDatabaseTable

</td>
<td valign="top">

Table Name

</td>
</tr>
<tr>
<td valign="top">

ChangeDocDatabaseTableField

</td>
<td valign="top">

Field Name

</td>
</tr>
</table>

