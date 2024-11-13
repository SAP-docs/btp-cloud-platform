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

This view represents the following SAP object type:

-   `BusEvtLogEvent` \(TechnicalObject\)




</td>
</tr>
</table>



## Purpose

This CDS view provides full business event data \(payload\) in JSON format.

This CDS view provides the data to answer the following business questions:

-   What is the full business data contained in the event?


To help you decide which CDS view to use for your purposes, SAP has introduced the annotation `ObjectModel.supportedCapabilities` that indicates the most appropriate use cases for each CDS view. To find out what use cases are best supported by this CDS view, access the entry of the CDS view in the *View Browser* app and find the values for this annotation under the *Annotation* tab. For more information, see  <?sap-ot O2O class="- topic/xref " href="6a6ff32b25dd473080e6aeddbefecfca.xml" text="" desc="" xtrc="xref:1" xtrf="file:/home/builder/src/dita-all/jjq1673438782153/loio2080d0faf9d84ce6aa14caa4caa32935_en-US/src/content/localization/en-us/3d8bf4c7269c4bdfbc35dbb91d77668b.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> .



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

