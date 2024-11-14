<!-- loio163e644d223843f29b5951c99bb2ec15 -->

# Business Event Property Changes \(v2\)


<table>
<tr>
<td valign="top">

CDS View Name

</td>
<td valign="top">

`C_BUSEVTLOGPAYLOADDEX_2`

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

This view represents the following SAP object type:

-   `BusEvtLogEvent` \(TechnicalObject\)




</td>
</tr>
</table>



## Purpose

This CDS view provides a subset of event payload details.

This CDS view provides the data to answer the following business questions:

-   What are the event qualifiers?

-   What are the field changes?

To help you decide which CDS view to use for your purposes, SAP has introduced the annotation `ObjectModel.supportedCapabilities` that indicates the most appropriate use cases for each CDS view. To find out what use cases are best supported by this CDS view, access the entry of the CDS view in the *View Browser* app and find the values for this annotation under the *Annotation* tab.



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

Unique identifier for business events.

</td>
</tr>
<tr>
<td valign="top">

`SAPObjectType` 

</td>
<td valign="top">

The object type, a business object, or a technical object corresponding to the specified SAP object node type. For example: Outbound Delivery for Outbound Delivery Item.

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogGlobalFieldName`

</td>
<td valign="top">

Field of an SAP object. Example: Amount

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogFieldHasOldValue`

</td>
<td valign="top">

This is a Boolean flag that indicates whether there was a value for the field.

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogFieldIsQualifier`

</td>
<td valign="top">

This is a Boolean flag that indicates whether the field is an event qualifier. A qualifier is an annotated field in a generic event that defines the event in more detail. The value of the qualifier field describes a generic event in detail.

Example: For the event Outb Deliv Goods Issue Status Changed the qualified field or Qualifier is OverallGoodsMovementStatus, with the values: Not yet started, Partially Completed, Completed, or Not Relevant

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogLastChangedDateTime`

</td>
<td valign="top">

The date and timestamp of when the payload entry was last updated.

</td>
</tr>
</table>

