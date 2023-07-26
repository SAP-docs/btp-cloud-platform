<!-- loio823ed3ef605640d6a08192d1b5e7ae11 -->

# CloudEvents Context Attributes

Events published through the enterprise event enablement are compliant with the CloudEvents specification. Context attributes contained in events are listed in this topic.



The following table lists required and optional context attributes of the CloudEvents specification \([https://cloudevents.io](https://cloudevents.io)\).


<table>
<tr>
<th valign="top">

Context Attribute



</th>
<th valign="top">

Requirement



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

`id`



</td>
<td valign="top">

required



</td>
<td valign="top">

identifies the event instance



</td>
</tr>
<tr>
<td valign="top">

`source`



</td>
<td valign="top">

required



</td>
<td valign="top">

identifies the issuer of the event

containing:

-   `region` 
    -   the region where the application service is located
    -   value: `default`

-   `applicationNamespace` 
    -   the registered namespace of the application, which emits the event
    -   value
        -   `sap.s4.beh` for SAP released events
        -   `sap.abap.custom` for events created by customers


-   `instanceID` 
    -   identifier of the application instance issuing the event
    -   value: represented through the cloud landscape directory \(CLD\) tenant ID of the SAP S/4HANA Cloud tenant.


> ### Note:  
> All contained values are set for events published in SAP S/4HANA Cloud.



</td>
</tr>
<tr>
<td valign="top">

`specversion`



</td>
<td valign="top">

required



</td>
<td valign="top">

specifies the version of the CloudEvents specification, which the event uses

currently: 1.0



</td>
</tr>
<tr>
<td valign="top">

`type`



</td>
<td valign="top">

required



</td>
<td valign="top">

specifies the type of event



</td>
</tr>
<tr>
<td valign="top">

`datacontenttype`



</td>
<td valign="top">

optional



</td>
<td valign="top">

content type of the event



</td>
</tr>
<tr>
<td valign="top">

`time`



</td>
<td valign="top">

optional



</td>
<td valign="top">

timestamp of the occurrence of the event



</td>
</tr>
<tr>
<td valign="top">

`data`



</td>
<td valign="top">

optional



</td>
<td valign="top">

business payload of the event



</td>
</tr>
</table>

