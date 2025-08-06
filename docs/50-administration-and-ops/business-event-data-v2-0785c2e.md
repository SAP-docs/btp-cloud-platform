<!-- loio0785c2e0c6544c64b23f2d830a4d9d27 -->

# Business Event Data v2


<table>
<tr>
<td valign="top">

CDS View Name

</td>
<td valign="top">

`C_BuEvLgEvtFullPyldJSONDEX_2`

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

This CDS view provides full business event data \(payload\) in JSON format.

This CDS view provides the data to answer the following business questions:

-   What is the full business data contained in the event?


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

Event Payload details in JSON format

</td>
</tr>
<tr>
<td valign="top">

BusEvtLogLastChangedDateTime

</td>
<td valign="top">

Timestamp of when the event was changed

</td>
</tr>
</table>



<a name="loio0785c2e0c6544c64b23f2d830a4d9d27__section_x5y_hfj_kfb"/>

## Data Extraction



### Data Extraction Type

-   Full
-   Delta \(change data capture\)

> ### Note:  
> Data conversion using the Cloud Data Integration \(CDI\) channel can be different from that of the other channels \(ODATA, ABAP SQL Service, and so on\). For example:
> 
> -   The timestamps could appear in a different format
> -   The IDs might not contain leading zeros
> 
> There could be formatting changes for other data as well.

**Related Information**  


[Virtual Data Model and CDS Views in SAP S/4HANA Cloud Public Edition](https://help.sap.com/docs/SAP_S4HANA_CLOUD/c0c54048d35849128be8e872df5bea6d/8573b810511948c8a99c0672abc159aa.html)

