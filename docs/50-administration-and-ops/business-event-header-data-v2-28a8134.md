<!-- loio28a8134f142f4ac89fe72afaed167d55 -->

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

Data Category

</td>
<td valign="top">

@Analytics.dataCategory: \#FACT

</td>
</tr>
</table>



<a name="loio28a8134f142f4ac89fe72afaed167d55__section_ivj_ffm_dsb"/>

## Purpose

This CDS view is used to extract business event header data.

This CDS view provides the data that answers business question:

-   Which business event has been logged?


The CDS view supports \#EXTRACTION\_DATA\_SOURCE.



<a name="loio28a8134f142f4ac89fe72afaed167d55__section_t2s_gfm_dsb"/>

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

Event operation, for example: Created, Deleted, Changed, and so on.

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

`SAPObjectNodeType`

</td>
<td valign="top">

Node type of an object type, for example, for an Outbound Delivery SAP object type, the SAP object node types are Outbound Delivery \(header\) and Outbound Delivery Item \(item\).

</td>
</tr>
<tr>
<td valign="top">

`SAPBusinessObjectNodeKey1`

</td>
<td valign="top">

First part of the key of an object node instance, for example, in one event for an Outbound Delivery Item, the first part of the key is 80013910 \(outbound delivery number\).

</td>
</tr>
<tr>
<td valign="top">

`SAPBusinessObjectNodeKey2`

</td>
<td valign="top">

Second part of the key of an object node instance, for example, in one event for an Outbound Delivery Item, the second part of the key is 00020 \(item number\). If an event refers to an SAP object node type with only one key part \(such as: Outbound Delivery \[header\]\), then all subsequent key parts are empty.

> ### Note:  
> There can be many more node keys, depending on how many parts the object key has. For example: SAPBusinessObjectNodeKey3, SAPBusinessObjectNodeKey4, and so on.
> 
> SAPObjectNodeType and SAPBusinessObjectNodeKey \(1-7\) identify a node instance of an SAP object. Outbound Delivery Item is an example of an SAP object node.



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



<a name="loio28a8134f142f4ac89fe72afaed167d55__section_ahl_hfm_dsb"/>

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
> Other data can also have formatting changes.



<a name="loio28a8134f142f4ac89fe72afaed167d55__section_o11_g2t_4zb"/>

## Examples

Example of events include:

-   BillingDocument

    -   Billing document cancelled
    -   Billing document changed
    -   Billing document created


For more information on other events, refer to SAP Business Accelerator Hub.

**Related Information**  


 <?sap-ot O2O class="- topic/link " href="8573b810511948c8a99c0672abc159aa.xml" text="" desc="" xtrc="link:1" xtrf="file:/home/builder/src/dita-all/jjq1673438782153/loio2080d0faf9d84ce6aa14caa4caa32935_en-US/src/content/localization/en-us/28a8134f142f4ac89fe72afaed167d55.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

