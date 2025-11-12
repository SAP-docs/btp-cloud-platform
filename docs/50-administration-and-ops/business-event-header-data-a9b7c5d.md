<!-- loioa9b7c5da770f48ef9f129b211d023f54 -->

# Business Event Header Data


<table>
<tr>
<td valign="top">

CDS View Name

</td>
<td valign="top">

`I_BusEvtLogBusinessEvent` 

</td>
</tr>
</table>



## Purpose

This CDS view provides a structured representation of business event header data, capturing essential details about business events logged in the system. It serves as a composite view that aggregates information from detailed event logs, enabling users to analyze and track business events effectively.

This CDS view provides the data to answer the following business questions:

-   When were specific business events created, and who created them?

-   What operations were performed during these business events?

-   What are the key attributes and names associated with the business object nodes involved in these events?

-   What is the source and logical system associated with each business event?




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

Event GUID

</td>
</tr>
<tr>
<td valign="top">

SAPObjectType

</td>
<td valign="top">

The object type, a business object, or a technical object corresponding to the specified SAP object node type, for example: Outbound Delivery for Outbound Delivery Item..

</td>
</tr>
<tr>
<td valign="top">

BusEvtLogCreationDate

</td>
<td valign="top">

Action Executed Date

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

EventOperation

</td>
<td valign="top">

Business Event Operation. For example: Created, Deleted, Changed, and so on.

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
> SAPObjectNodeType and SAPBusinessObjectNodeKey \(1-8\) identify a node instance of an SAP object. Outbound Delivery Item is an example of an SAP object node.



</td>
</tr>
<tr>
<td valign="top">

CreatedByUser

</td>
<td valign="top">

Users Who Executed the Action

</td>
</tr>
<tr>
<td valign="top">

BusEvtLogCreationDateTime

</td>
<td valign="top">

Action Execution Time Stamp

</td>
</tr>
<tr>
<td valign="top">

BusinessEventLogLogicalSystem

</td>
<td valign="top">

Logical System

</td>
</tr>
<tr>
<td valign="top">

BusEvtLogIsDeleted

</td>
<td valign="top">

Deletion Indicator

</td>
</tr>
<tr>
<td valign="top">

BusinessEventLogEventVersion

</td>
<td valign="top">

Business Event Version

</td>
</tr>
<tr>
<td valign="top">

BusEvtLogTransactionID

</td>
<td valign="top">

Identifies the session in which a business event was created

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

IsTechnicalUser

</td>
<td valign="top">

Is Technical User

</td>
</tr>
<tr>
<td valign="top">

BusinessEventLogSource

</td>
<td valign="top">

Business Event Source

</td>
</tr>
<tr>
<td valign="top">

EventProducerNamespace

</td>
<td valign="top">

Producer Event Namespace

</td>
</tr>
<tr>
<td valign="top">

BusEvtLogEventHasFullPayload

</td>
<td valign="top">

Has All Business Event Data

</td>
</tr>
<tr>
<td valign="top">

BusEvtLogUserInteractionType

</td>
<td valign="top">

Application Type

</td>
</tr>
<tr>
<td valign="top">

BusEvtLgUsrIntactnTypeValue

</td>
<td valign="top">

Application ID

</td>
</tr>
<tr>
<td valign="top">

ChangeDocument

</td>
<td valign="top">

Number of the Change Document

</td>
</tr>
<tr>
<td valign="top">

ChangeDocItemChangeType

</td>
<td valign="top">

Change Indicator of Change Document

</td>
</tr>
<tr>
<td valign="top">

SAPBusinessObjectNodeKey1Name

</td>
<td valign="top">

Key1 Name

</td>
</tr>
<tr>
<td valign="top">

SAPBusinessObjectNodeKey2Name

</td>
<td valign="top">

Key2 Name

</td>
</tr>
<tr>
<td valign="top">

SAPBusinessObjectNodeKey3Name

</td>
<td valign="top">

Key3 Name

</td>
</tr>
<tr>
<td valign="top">

SAPBusinessObjectNodeKey4Name

</td>
<td valign="top">

Key4 Name

</td>
</tr>
<tr>
<td valign="top">

SAPBusinessObjectNodeKey5Name

</td>
<td valign="top">

Key5 Name

</td>
</tr>
<tr>
<td valign="top">

SAPBusinessObjectNodeKey6Name

</td>
<td valign="top">

Key6 Name

</td>
</tr>
<tr>
<td valign="top">

SAPBusinessObjectNodeKey7Name

</td>
<td valign="top">

Key7 Name

</td>
</tr>
<tr>
<td valign="top">

SAPBusinessObjectNodeKey8Name

</td>
<td valign="top">

Key8 Name

</td>
</tr>
<tr>
<td valign="top">

BusEvtLogReferenceEventUUID

</td>
<td valign="top">

Event GUID

</td>
</tr>
<tr>
<td valign="top">

BusEvtLogBusinessActivity

</td>
<td valign="top">

Activity ID

</td>
</tr>
</table>

