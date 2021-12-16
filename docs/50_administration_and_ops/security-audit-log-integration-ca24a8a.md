<!-- loioca24a8adb8c9440a9e7246fb615c306b -->

# Security Audit Log Integration

Service name: `RSAU_LOG_API`

This service enables you to retrieve the security audit log data from SAP S/4HANA Cloud. You can use the audit log data to integrate them into your Security and Event Management solution \(SIEM\) to detect security relevant event situations.

This is an OData version 4 service. This version aims to improve processing time and resource consumption of clients and servers and to reflect the complexity of the underlying business model. This includes a lightweight JSON format that reduces the size of every response. Business data can be retrieved in the exact amount, at the right time, and in appropriate mode by using new synchronization mechanisms. Calculations are made and data is aggregated by using the tiers best suited for this task. Sophisticated metadata artifacts enable a true-to-life modeling of business models.



<a name="loioca24a8adb8c9440a9e7246fb615c306b__section_technical_details"/>

## Technical Details

A service group contains services belonging to the same business object model and so it shares similar environment conditions. This means the configuration and administration of a service group apply to all services in a service group, that is, routing, authorization, and so on, so you only have to do them once.

In the OData version 4 \(V4\) runtime implementation of the SAP Gateway Foundation, framework services originate from repositories.


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

 `RSAU_LOG_API` 



</td>
<td valign="top">

 `SRVD_A2X` 



</td>
<td valign="top">

 `RSAU_LOG_API_SERVICE` 



</td>
<td valign="top">

 `0001` 



</td>
</tr>
</table>



<a name="loioca24a8adb8c9440a9e7246fb615c306b__section_service_structure"/>

## Service Structure

**Service Header \(optional\)**

The service header contains information about the service.

**Entities**

The entities contain the business data of the service.

<a name="loioca24a8adb8c9440a9e7246fb615c306b__table_thq_y5d_5y"/>


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

Security Audit Log



</td>
<td valign="top">

Security Audit Log



</td>
<td valign="top">

 



</td>
<td valign="top">

  



</td>
</tr>
</table>



<a name="loioca24a8adb8c9440a9e7246fb615c306b__section_service_response"/>

## Service Response

The details included in the response vary according to the type of operation. For more information, see Operation for Security Audit Log Integration.



<a name="loioca24a8adb8c9440a9e7246fb615c306b__section_additional_information"/>

## Additional Information

> ### Note:  
> For more details about Communication Management, see [Communication Management](communication-management-2e84a10.md).

