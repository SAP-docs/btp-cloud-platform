<!-- loioc3fbc7dadd5c40e793f0d195c546acae -->

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

Data Category

</td>
<td valign="top">

@Analytics.dataCategory: \#FACT

</td>
</tr>
</table>



<a name="loioc3fbc7dadd5c40e793f0d195c546acae__section_i3r_zpq_gbc"/>

## Purpose

This CDS view provides full business event data \(payload\) in JSON format.

This CDS view provides the answer to these business questions:

-   What is the full business data contained in the event?


The CDS view supports \#EXTRACTION\_DATA\_SOURCE.



<a name="loioc3fbc7dadd5c40e793f0d195c546acae__section_znx_fqq_gbc"/>

## Structure



### Important fields

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

The object type, a business object, or a technical object corresponding to the specified SAP object node type. For example: Outbound Delivery for Outbound Delivery Item.

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



<a name="loioc3fbc7dadd5c40e793f0d195c546acae__section_mcj_3qq_gbc"/>

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

