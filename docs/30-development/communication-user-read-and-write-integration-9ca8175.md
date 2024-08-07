<!-- loio9ca817560dcb4b2e8c1f5ce1d3c6b8aa -->

# Communication User - Read and Write Integration



This service enables you to:

-   Read and write communication users

-   Read and write assigned certificates, communication systems and communication arrangements


This service is published on the SAP Business Accelerator Hub. For more information about APIs, see the *Related Information* section.

This is an OData version 4 service. This version aims to improve processing time and resource consumption of clients and servers. This includes a lightweight JSON format that reduces the size of every response.



<a name="loio9ca817560dcb4b2e8c1f5ce1d3c6b8aa__section_TechnicalDetails_CommunicationUser_RW"/>

## Technical Details


<table>
<tr>
<th valign="top">

Service Group \(incl. Namespace if It Exists\)

</th>
<th valign="top">

Repository ID

</th>
<th valign="top">

Service Name \(incl. Namespace if It Exists\)

</th>
<th valign="top">

Version

</th>
</tr>
<tr>
<td valign="top">

`aps_com_cu_a4c_odata`

</td>
<td valign="top">

`srvd_a2x`

</td>
<td valign="top">

`aps_com_cu_a4c_odata`

</td>
<td valign="top">

`0001`

</td>
</tr>
</table>



<a name="loio9ca817560dcb4b2e8c1f5ce1d3c6b8aa__section_ServiceStructureCommunicationUserRW"/>

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
</tr>
<tr>
<td valign="top">

CommunicationUsers

</td>
<td valign="top">

Contains communication user root data

</td>
<td valign="top">

Mandatory

</td>
</tr>
<tr>
<td valign="top">

Certificates

</td>
<td valign="top">

Contains the assigned certificates

</td>
<td valign="top">

Optional

</td>
</tr>
</table>



<a name="loio9ca817560dcb4b2e8c1f5ce1d3c6b8aa__section_AdditionalInformation_CommunicationUserRW"/>

## Additional Information



> ### Note:  
> For more information about Communication Management, see the *Related Information* section.

**Related Information**  


[Communication Arrangements - Entity](communication-arrangements-entity-26253af.md)

[**APIs on SAP Business Accelerator Hub**](https://help.sap.com/docs/SAP_S4HANA_CLOUD/0f69f8fb28ac4bf48d2b57b9637e81fa/1e60f14bdc224c2c975c8fa8bcfd7f3f.html?version=latest)

[Communication Management](../50-administration-and-ops/communication-management-2e84a10.md "The communication management apps allow you to integrate your system or solution with other systems to enable data exchange.")

