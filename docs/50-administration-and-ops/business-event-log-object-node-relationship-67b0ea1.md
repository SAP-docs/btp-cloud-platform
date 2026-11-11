<!-- loio67b0ea17d7c741a3969f8e2ce95b7030 -->

# Business Event Log Object Node Relationship


<table>
<tr>
<td valign="top">

CDS View Name

</td>
<td valign="top">

`C_BusEvtLogObjectNodeRelshpDEX`

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

This CDS view exposes the relationships between object nodes recorded in the Business Event Log. For each logged business event, it captures which primary SAP business object node is connected to which related object node, the type of association between them, and the key values that uniquely identify both sides of the relationship.

This CDS view provides the data to answer the following business questions:

-   Which business object nodes are linked to each other within the Business Event Log?

-   What type of relationship exists between two connected object nodes?

-   What are the key field values that uniquely identify each side of a relationship?




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

BusEvtLogObjectNodeID

</td>
<td valign="top">

BEL Identifier of Business Object Node

</td>
</tr>
<tr>
<td valign="top">

BusEvtLogRelatedObjectNodeID

</td>
<td valign="top">

BEL Identifier of Business Object Node

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

BusEvtLogAssociationName

</td>
<td valign="top">

Name of an Association

</td>
</tr>
<tr>
<td valign="top">

SAPObjectNodeType

</td>
<td valign="top">

Node type of an object type, for example, for an Outbound Delivery SAP object type, the SAP object node types are Outbound Delivery \(header\) and Outbound Delivery Item \(item\).

</td>
</tr>
<tr>
<td valign="top">

SAPBusinessObjectNodeKey1

</td>
<td valign="top">

First part of the key of an object node instance, for example, in one event for an Outbound Delivery Item, the first part of the key is 80013910 \(outbound delivery number\).

</td>
</tr>
<tr>
<td valign="top">

SAPBusinessObjectNodeKey2

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

RelatedSAPObjectType

</td>
<td valign="top">

SAP Object Type

</td>
</tr>
<tr>
<td valign="top">

RelatedSAPObjectNodeType

</td>
<td valign="top">

SAP Object Node Type

</td>
</tr>
<tr>
<td valign="top">

BuEvLgReltdSAPBusObjNodeKey1

</td>
<td valign="top">

Object Key Part \(1\)

</td>
</tr>
<tr>
<td valign="top">

BuEvLgReltdSAPBusObjNodeKey2

</td>
<td valign="top">

Object Key Part \(2\)

> ### Note:  
> There can be many more node keys, depending on how many parts the object key has. For example: SAPBusinessObjectNodeKey3, SAPBusinessObjectNodeKey4, and so on.
> 
> SAPObjectNodeType and SAPBusinessObjectNodeKey \(1-7\) identify a node instance of an SAP object. Outbound Delivery Item is an example of an SAP object node.



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
</table>



<a name="loio67b0ea17d7c741a3969f8e2ce95b7030__section_x5y_hfj_kfb"/>

## Data Extraction



### Data Extraction Type



This CDS view is enabled for data extraction in full mode as well as in delta mode. Deltas are determined automatically by change data capture.

