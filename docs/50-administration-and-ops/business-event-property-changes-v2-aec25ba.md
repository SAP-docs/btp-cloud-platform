<!-- loioaec25ba6054e4ee5976b2a687f1bcd72 -->

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

Data Category

</td>
<td valign="top">

@Analytics.dataCategory: \#FACT

</td>
</tr>
</table>



<a name="loioaec25ba6054e4ee5976b2a687f1bcd72__section_ivj_ffm_dsb"/>

## Purpose

This CDS view provides a subset of event payload details.

This CDS view provides the answer to these business questions:

-   What are the event qualifiers?

-   What are the field changes?


The CDS view supports \#EXTRACTION\_DATA\_SOURCE.



<a name="loioaec25ba6054e4ee5976b2a687f1bcd72__section_t2s_gfm_dsb"/>

## Structure

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



<a name="loioaec25ba6054e4ee5976b2a687f1bcd72__section_ahl_hfm_dsb"/>

## Data Extraction

**Data Extraction Type**

-   Full
-   Delta \(change data capture\)

> ### Note:  
> Data conversion using the Cloud Data Integration \(CDI\) channel can be different from that of the other channels \(ODATA, ABAP SQL Service, and so on\). For example:
> 
> -   The timestamps could appear in a different format
> -   The IDs might not contain leading zeros
> 
> There could be formatting changes for other data as well.

