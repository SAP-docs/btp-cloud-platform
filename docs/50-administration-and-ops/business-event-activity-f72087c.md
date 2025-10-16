<!-- loiof72087cdfcf74ddc91c58447dd398295 -->

# Business Event Activity


<table>
<tr>
<td valign="top">

CDS View Name

</td>
<td valign="top">

`C_BUSEVTLOGACTIVITYDEX`

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

This CDS view retrieves activities.

This CDS view provides the data to answer the following business questions:

-   What are the logged activities?


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

RAP SOT: SAP Object Type

</td>
</tr>
<tr>
<td valign="top">

`SAPObjectNodeType`

</td>
<td valign="top">

RAP SOT: SAP Object Node Type

</td>
</tr>
<tr>
<td valign="top">

`EventOperation`

</td>
<td valign="top">

Business Event Operation

</td>
</tr>
<tr>
<td valign="top">

`SAPBusinessObjectNodeKey1` \(1-8\)

</td>
<td valign="top">

Object Key Part \(1-8\)

</td>
</tr>
<tr>
<td valign="top">

`CreatedByUser`

</td>
<td valign="top">

Users Who Executed the Action

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogCreationDateTime`

</td>
<td valign="top">

Action Execution Time Stamp

</td>
</tr>
<tr>
<td valign="top">

`BusinessEventLogLogicalSystem`

</td>
<td valign="top">

Logical system

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogTransactionID`

</td>
<td valign="top">

Identifies the session in which a business event was created

</td>
</tr>
<tr>
<td valign="top">

`IsTechnicalUser`

</td>
<td valign="top">

Is a Technical User

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLogUserInteractionType`

</td>
<td valign="top">

Application Type

</td>
</tr>
<tr>
<td valign="top">

`BusEvtLgUsrIntactnTypeValue`

</td>
<td valign="top">

Application ID

</td>
</tr>
<tr>
<td valign="top">

`SAPBusinessObjectNodeKey1Name`\(1-8\)

</td>
<td valign="top">

Key Names

</td>
</tr>
</table>



<a name="loiof72087cdfcf74ddc91c58447dd398295__section_x5y_hfj_kfb"/>

## Data Extraction

This CDS view is enabled for data extraction in full mode as well as in delta mode. Deltas are determined automatically by change data capture.

**Related Information**  


[Virtual Data Model and CDS Views in SAP S/4HANA Cloud Public Edition](https://help.sap.com/docs/SAP_S4HANA_CLOUD/c0c54048d35849128be8e872df5bea6d/8573b810511948c8a99c0672abc159aa.html)

