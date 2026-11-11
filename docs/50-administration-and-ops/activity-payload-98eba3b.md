<!-- loio98eba3b586f24844a99ac48cb0885fb5 -->

# Activity Payload


<table>
<tr>
<td valign="top">

CDS View Name

</td>
<td valign="top">

`C_BusEvtLogActyFldChgDEX`

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
<tr>
<td valign="top">

Represented Objects

</td>
<td valign="top">

This view represents the following SAP object type:

-   `BusinessEventLogActivity` \(TechnicalObject\)




</td>
</tr>
</table>



## Purpose

This CDS view provides field-level change records captured within Business Event Log activities. For each business activity recorded against an SAP object, it surfaces the individual payload fields that changed — including the old and new values, units, and currencies — along with references to the underlying change document.

This CDS view provides the data to answer the following business questions:

-   Which fields changed during a specific business activity on an SAP object?

-   What were the old and new values of a changed field?

-   In which unit or currency was a changed quantity or amount expressed, and did that change too?

-   Was a previous value actually present before the change, or was the field newly populated?

-   Is a changed field a qualifier \(a field that contextualizes another field's value\) rather than a standalone value?

-   Which change document and change type is associated with a field change?

-   What field changes have occurred since a given point in time?




## Prerequisites



### Authorizations

This CDS view doesn't perform any authorization checks. You can use it without assigning additional authorizations to your business users. However, users still need access to the app or API that exposes the data.



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

`BusEvtLogBusinessActivity`

</td>
<td valign="top">

Activity ID

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

`BusEvtLogFieldChgHash`

</td>
<td valign="top">

Identifier for field name hash value

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

`BuEvLgGlobalFieldNameUpperCase`

</td>
<td valign="top">

Property Name of the Object

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

`BusEvtLogOldFieldValue`

</td>
<td valign="top">

Previous Value of an Attribute

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogOldFieldUnit`

</td>
<td valign="top">

Previous Unit of Measure

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogNewFieldValue`

</td>
<td valign="top">

Updated Value of an Attribute

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogNewFieldUnit`

</td>
<td valign="top">

Updated Unit of Measure

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogOldFieldCurrency`

</td>
<td valign="top">

Previous Currency Key

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogNewFieldCurrency`

</td>
<td valign="top">

Updated Currency Key

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogFieldHasOldValue`

</td>
<td valign="top">

Field has an Old Value

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogFieldIsQualifier`

</td>
<td valign="top">

Specifies if the Attribute is a Qualifier

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

`ChangeDocument`

</td>
<td valign="top">

Number of the Change Document

</td>
</tr>
<tr>
<td valign="top">

`ChangeDocItemChangeType`

</td>
<td valign="top">

Change Indicator of Change Document

</td>
</tr>
</table>



<a name="loio98eba3b586f24844a99ac48cb0885fb5__section_x5y_hfj_kfb"/>

## Data Extraction



### Data Extraction Type

This CDS view is enabled for data extraction in full mode as well as in delta mode. Deltas are determined automatically by change data capture.

