<!-- loio452c5200c9d44b109e5d574bbd7ea37d -->

# Integrating Read Access Logs

Service name: `SRAL_API_RAW_LOG`

This service enables you to retrieve the raw Read Access Logs. You can use the log data to integrate them into your Security and Event Management solution \(SIEM\) to detect security relevant event situations.



<a name="loio452c5200c9d44b109e5d574bbd7ea37d__section_technical_details"/>

## Technical Details


<table>
<tr>
<th valign="top">

Service Group \(incl. Namespace if Existent\)

</th>
<th valign="top">

Repository ID

</th>
<th valign="top">

Service Name \(incl. Namespace if Existent\)

</th>
<th valign="top">

Version

</th>
</tr>
<tr>
<td valign="top">

`SRAL_API_RAW_LOG` 

</td>
<td valign="top">

`SRVD_A2X` 

</td>
<td valign="top">

`SRAL_API_RAW_LOG` 

</td>
<td valign="top">

`0001` 

</td>
</tr>
</table>



<a name="loio452c5200c9d44b109e5d574bbd7ea37d__section_service_structure"/>

## Service Structure

**Service Header \(optional\)**

The service header contains information about the service.

**Entities**

The entities contain the business data of the service.

****


<table>
<tr>
<th valign="top">

Entity

</th>
<th valign="top">

Description

</th>
<th valign="top">

Necessity

</th>
<th valign="top">

Link to Details

</th>
</tr>
<tr>
<td valign="top">

ReadAccessLogRAW

</td>
<td valign="top">

Read Access Log in RAW format

</td>
<td valign="top">

 

</td>
<td valign="top">

[Retrieving Security Audit Log](retrieving-security-audit-log-ce39470.md) 

</td>
</tr>
</table>



<a name="loio452c5200c9d44b109e5d574bbd7ea37d__section_service_response"/>

## Service Response

The details included in the response vary according to the type of operation. For more information, see Operation for Read Access Log Integration.



<a name="loio452c5200c9d44b109e5d574bbd7ea37d__section_crs_psc_lwb"/>

## Integration with SIEM Solution

Service name: ***SRAL\_API\_RAW\_LOG***

Communication scenario: ***SAP\_COM\_0915***

This service enables you to retrieve the Read Access Log data. This service enables you to retrieve the raw Read Access Logs. You can use the log data to integrate them into your Security and Event Management solution \(SIEM\) to detect security relevant event situations.

