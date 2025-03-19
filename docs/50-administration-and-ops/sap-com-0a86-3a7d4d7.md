<!-- loio3a7d4d7024af42b5a8ef16fd55a90572 -->

# SAP\_COM\_0A86

This document describes the print queue administrator integration. It provides the configuration steps that have to be carried out by customers to create and delete print queues using SAP\_COM\_0A86.



<a name="loio3a7d4d7024af42b5a8ef16fd55a90572__section_jtt_5tx_42c"/>

## Purpose

The communication scenario `SAP_COM_0A86` enables you to create and delete print queues directly using APIs without the need to enter the *Maintain Print Queues* app. This is especially helpful for defining print queues across different systems. With the API, you don't need to log in separately. You can create print queues from a single location using this API.



<a name="loio3a7d4d7024af42b5a8ef16fd55a90572__section_zng_wtx_42c"/>

## Prerequisites

-   You have the following business role assigned to your user:

    -   `SAP_BR_ADMINISTRATOR`


-   This business role contains the following business catalogs:

    -   `Communication Management (SAP_CORE_BC_COM)`

    -   `Output Management (SAP_CORE_BC_OM_PRT)`


-   Make sure you've followed integration scenario `SAP_COM_0466` until step 11 or `SAP_COM_0467` until step 15. See [SAP\_COM\_0466](sap-com-0466-524c13a.md) or [SAP\_COM\_0467](sap-com-0467-523eb80.md), respectively.




<a name="loio3a7d4d7024af42b5a8ef16fd55a90572__section_slj_ztx_42c"/>

## Process Steps

1.  Log in to your system and navigate to the *Display Communication Scenarios* app.

2.  Search for scenario ID `SAP_COM_0A86` and click on it.
3.  Now click on *Create Communication Arrangement* in the top right corner.

4.  Choose a name for your communication arrangement and click *Create*.

5.  You will now need to create a communication system. You can do this by clicking *New* next to the field *Communication System*. For more information on general concepts of communication management, see [Communication Management](communication-management-2e84a10.md).

6.  Choose a new *System ID* and click *Create*.

    > ### Note:  
    > The *System Name* is filled in automatically with the same name as the ID. We recommend leaving this as it is to prevent confusion.

7.  In the *General* section, mark the *Inbound Only* checkbox.

8.  Now scroll down to *Users for Inbound Communication* and click "+" to add a new communication user.

9.  Click on *New User*. Enter a username and a description. You can then choose to either enter a new password or upload a client certificate by clicking on *Upload*. Click *Create* to save the user, then click *OK*.

10. Save your communication system by clicking *Save* on the bottom right, then save your communication arrangement the same way.

11. Now, use the operations of communication scenario `0A86` mentioned below to create print queues.



<a name="loio3a7d4d7024af42b5a8ef16fd55a90572__section_olh_b5x_42c"/>

## Operations

**Operations for the print queue administrator integration**


<table>
<tr>
<th valign="top">

Operation

</th>
<th valign="top">

HTTP Method

</th>
<th valign="top">

Sample URL

</th>
</tr>
<tr>
<td valign="top">

Get Queues

</td>
<td valign="top">

GET

</td>
<td valign="top">

`<host>/sap/bc/http/sap/APS_OM_PQ/queues`

</td>
</tr>
<tr>
<td valign="top">

Get Queue Formats

</td>
<td valign="top">

GET

</td>
<td valign="top">

`<host>/sap/bc/http/sap/APS_OM_PQ/queue-formats`

</td>
</tr>
<tr>
<td valign="top">

Get Queue Context

</td>
<td valign="top">

GET

</td>
<td valign="top">

`<host>/sap/bc/http/sap/APS_OM_PQ/queue-context`

</td>
</tr>
<tr>
<td valign="top">

Create Queue

</td>
<td valign="top">

POST

</td>
<td valign="top">

`<host>/sap/bc/http/sap/APS_OM_PQ/queues`

</td>
</tr>
<tr>
<td valign="top">

Delete Queue

</td>
<td valign="top">

DELETE

</td>
<td valign="top">

`<host>/sap/bc/http/sap/APS_OM_PQ/queues/{QNAME}`

</td>
</tr>
<tr>
<td valign="top">

Set Status of Queues

</td>
<td valign="top">

POST

</td>
<td valign="top">

`<host>/sap/bc/http/sap/APS_OM_PQ`

</td>
</tr>
</table>



### Get Queues

Read existing queues in a tenant using the HTTP method `GET`.

**Request**: You can retrieve all print queues in tenant with one call: `GET` `/sap/bc/http/sap/APS_OM_PQ/queues`

**Response**: The operation returns a list of print queues.

**Examples**: If the request is `GET` `/sap/bc/http/sap/APS_OM_PQ/queues`, the response is:

> ### Sample Code:  
> ```
> [
> 							{
> 							"MANDT" : "100",
> 							"QNAME" : "ZTEST01",
> 							"QDESCRIPTION" : "",
> 							"QFORMAT" : "acrobat6.xdc",
> 							"QFORMAT_DESCRIPT" : "PDF",
> 							"TECH_USER_NAME" : "CC*",
> 							"QSTATUS" : "R",
> 							"CREATE_TIME" : 20250212162704,
> 							"LAST_RETRIEVE_TIME" : 20250214061838,
> 							"CLEANUP_PRD" : 1,
> 							"LOCATION_ID" : "",
> 							"LOCATION_ID_TYPE" : "",
> 							"OMS_TYPE" : 466,
> 							"QPARAMS" : "",
> 							"DESTINATION" : "",
> 							"NOTIFY_TYPE" : ""
> 							},
> 							{
> 							"MANDT" : "100",
> 							"QNAME" : "ZTEST02",
> 							"QDESCRIPTION" : "",
> 							"QFORMAT" : "acrobat6.xdc",
> 							"QFORMAT_DESCRIPT" : "PDF",
> 							"TECH_USER_NAME" : "CC*2",
> 							"QSTATUS" : "H",
> 							"CREATE_TIME" : 20241103110846,
> 							"LAST_RETRIEVE_TIME" : 20241103124912,
> 							"CLEANUP_PRD" : 0,
> 							"LOCATION_ID" : "",
> 							"LOCATION_ID_TYPE" : "",
> 							"OMS_TYPE" : 466,
> 							"QPARAMS" : "",
> 							"DESTINATION" : "",
> 							"NOTIFY_TYPE" : ""
> 							}
> 							]
> ```



### Get Queue Formats

Read existing queue formats in a tenant using the HTTP method `GET`. When a queue is created, the queue format should be part of the input.

**Request**: You can retrieve all print queue formats in tenant with one call: `GET``/sap/bc/http/sap/APS_OM_PQ/queue-formats`

**Response**: The operation returns a list of print queue formats.

**Examples**: If the request is `GET` `/sap/bc/http/sap/APS_OM_PQ/queue-formats`, then the response is:

> ### Sample Code:  
> ```
> [
> 							{
> 							"QFORMAT" : "acrobat6.xdc",
> 							"QFORMAT_DESC" : "PDF"
> 							},
> 							{
> 							"QFORMAT" : "cab203.xdc",
> 							"QFORMAT_DESC" : "CAB 203 dpi"
> 							}
> 							
> 							]
> ```



### Get Queue Context

Read the existing queue context in a tenant using the HTTP method `GET`. The queue context provides information on which users could be used as print queue owners, and in which queue type the users could be used \(such as queue type 466 or 467, for example\). When a queue is created, the queue owner should be part of the input.

**Request**: You can retrieve the entire print queue context \(which is the queue owner and the corresponding queue type\) in a tenant with one call: `GET` `/sap/bc/http/sap/APS_OM_PQ/queue-context`

**Response**: The operation returns a list of the entire print queue context.

**Examples**: If the request is `GET` `/sap/bc/http/sap/APS_OM_PQ/queue-context`, then the reponse is:

> ### Sample Code:  
> ```
> [
> 							{
> 							"MANDT" : "100",
> 							"OWNER" : "CC001",
> 							"DESCRIPTION" : "",
> 							"DESTINATION" : "",
> 							"USERALIAS" : "TEST466",
> 							"OMSTYPE" : 466
> 							},
> 							{
> 							"MANDT" : "100",
> 							"OWNER" : "CC002",
> 							"DESCRIPTION" : "",
> 							"DESTINATION" : "......",
> 							"USERALIAS" : "TEST467",
> 							"OMSTYPE" : 467
> 							}
> 							]
> ```



### Create Queue

Create a new print queue in a tenant using the HTTP method `POST`.

**Request**: You can create a new print queue in a tenant with one call: `POST` `/sap/bc/http/sap/APS_OM_PQ/queues`. The body is: `{"queuename":"", "queuedescription":"","queueformat":"","queueowner":"","queuetype":"","queueretention":"", "queuenotification":"", "queuelocation":"","queuelocationtype":""}`.

**Response**: The operation returns the status code `200`.

**Examples**: If the request is `POST` `/sap/bc/http/sap/APS_OM_PQ/queues` with the body `{"queuename":"ZTEST", "queuedescription":"TEST...","queueformat":"acrobat6.xdc","queueowner":"CC_PRINT_USER","queuetype":"466","queueretention":"2"}`, then the response is

> ### Sample Code:  
> ```
> ~status_code    200
> 							~status_reason    OK
> ```



### Delete Queue

Delete a print queue in a tenant using the HTTP method `DELETE`.

**Request**: You can delete a print queue in a tenant with one call: `DELETE` `/sap/bc/http/sap/APS_OM_PQ/queues/{QNAME}`.

**Response**: The operation returns the status code `200`.

**Examples**: If the request is `POST` `/sap/bc/http/sap/APS_OM_PQ/queues/ZTEST`, then the response is

> ### Sample Code:  
> ```
> ~status_code    200
> 							~status_reason    OK
> ```



### Set Status of Queues

Set the status of print queues in a tenant using the HTTP method `POST`.

**Request**: You can set the status *Resume* or *Hold* of print queues in a tenant with one call: `POST` `/sap/bc/http/sap/APS_OM_PQ` using the body `[{"queuename":"","queuestatus":""}...]`.

**Response**: The operation returns status code `200`.

**Examples**: If the request is `POST` `/sap/bc/http/sap/APS_OM_PQ` with the body `[{"queuename":"ZTEST2","queuestatus":"H"},{"queuename":"ZTEST3","queuestatus":"R"}]`, then the response is

> ### Sample Code:  
> ```
> ~status_code    200
> 							~status_reason    OK
> ```

