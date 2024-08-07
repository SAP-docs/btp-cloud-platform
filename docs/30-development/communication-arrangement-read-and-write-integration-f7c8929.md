<!-- loiof7c8929df1234eb6bd221a41ad6feac8 -->

# Communication Arrangement - Read and Write Integration



This service enables you to:

-   Read and write communication arrangements

-   Read and write assigned inbound users, outbound users, inbound services and outbound services


This service is published on the SAP Business Accelerator Hub. For more information about APIs, see the *Related Information* section.

This is an OData version 4 service. This version aims to improve processing time and resource consumption of clients and servers. This includes a lightweight JSON format that reduces the size of every response.



<a name="loiof7c8929df1234eb6bd221a41ad6feac8__section_TechnicalDetails_CommunicationArrangement_RW"/>

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

`aps_com_ca_a4c_odata`

</td>
<td valign="top">

`srvd_a2x`

</td>
<td valign="top">

`aps_com_ca_a4c_odata`

</td>
<td valign="top">

`0001`

</td>
</tr>
</table>



<a name="loiof7c8929df1234eb6bd221a41ad6feac8__section_ServiceStructureCommunicationArrangementRW"/>

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

CommunicationArrangements

</td>
<td valign="top">

Contains communication arrangement root data

</td>
<td valign="top">

Mandatory

</td>
</tr>
<tr>
<td valign="top">

Properties

</td>
<td valign="top">

Contains communication arrangement root property names

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

PropertyValues

</td>
<td valign="top">

Contains communication arrangement root property values

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

InboundUsers

</td>
<td valign="top">

Contains the reference to the communication system inbound user

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

InboundServices

</td>
<td valign="top">

Contains the communication arrangement inbound service data

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

InboundServiceProperties

</td>
<td valign="top">

Contains communication arrangement inbound service property names

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

InboundServicePropertyValues

</td>
<td valign="top">

Contains communication arrangement inbound service property values

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

OutboundUsers

</td>
<td valign="top">

Contains the reference to the communication system outbound user

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

OutboundUserAuthScopes

</td>
<td valign="top">

Contains additional scopes for outbound users

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

OutboundServices

</td>
<td valign="top">

Contains the communication arrangement outbound service data

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

OutboundServiceProperties

</td>
<td valign="top">

Contains communication arrangement outbound service property names

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

OutboundServicePropertyValues

</td>
<td valign="top">

Contains communication arrangement outbound service property values

</td>
<td valign="top">

Optional

</td>
</tr>
</table>



<a name="loiof7c8929df1234eb6bd221a41ad6feac8__section_AdditionalInformation_CommunicationArrangementRW"/>

## Additional Information



> ### Note:  
> For more information about Communication Management, see the *Related Information* section.

**Related Information**  


[Communication Arrangements - Entity](communication-arrangements-entity-26253af.md)

[**APIs on SAP Business Accelerator Hub**](https://help.sap.com/docs/SAP_S4HANA_CLOUD/0f69f8fb28ac4bf48d2b57b9637e81fa/1e60f14bdc224c2c975c8fa8bcfd7f3f.html?version=latest)

[Communication Management](../50-administration-and-ops/communication-management-2e84a10.md "The communication management apps allow you to integrate your system or solution with other systems to enable data exchange.")

