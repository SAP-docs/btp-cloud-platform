<!-- loio875afe7dfd11469a92855a691730d0dd -->

# Content Security Policy - Read Integration



Service name: `ContentSecurityPolicy`

This service enables you to

-   Read Content Security Policy statuses

-   Read trusted sites


This service is published on the SAP Business Accelerator Hub. For more information about APIs, see the *Related Information* section.

This is an OData version 4 service. This version aims to improve processing time and resource consumption of clients and servers. This includes a lightweight JSON format that reduces the size of every response.



<a name="loio875afe7dfd11469a92855a691730d0dd__section_ozh_cvx_clb"/>

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

`aps_sec_api_csp_read`

</td>
<td valign="top">

`srvd_a2x`

</td>
<td valign="top">

`ContentSecurityPolicy`

</td>
<td valign="top">

`0001`

</td>
</tr>
</table>



<a name="loio875afe7dfd11469a92855a691730d0dd__section_ct2_xxx_clb"/>

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

ContentSecurityPolicyStatus

</td>
<td valign="top">

Contains the Content Security Policy statuses

</td>
<td valign="top">

Mandatory

</td>
<td valign="top">

For more information, see the *Related Information* section.

</td>
</tr>
<tr>
<td valign="top">

TrustedSites

</td>
<td valign="top">

Contains trusted sites

</td>
<td valign="top">

Mandatory

</td>
<td valign="top">

For more information, see the *Related Information* section.

</td>
</tr>
</table>



<a name="loio875afe7dfd11469a92855a691730d0dd__section_znk_jzx_clb"/>

## Additional Information



> ### Note:  
> For more information about Communication Management, see the *Related Information* section.

**Related Information**  


[Content Security Policy Status - Entity](content-security-policy-status-entity-8882336.md)

[Trusted Sites - Entity](trusted-sites-entity-0dbb5b3.md)

[**APIs on SAP Business Accelerator Hub**](https://help.sap.com/docs/SAP_S4HANA_CLOUD/0f69f8fb28ac4bf48d2b57b9637e81fa/1e60f14bdc224c2c975c8fa8bcfd7f3f.html?version=latest)

[Communication Management](../50-administration-and-ops/communication-management-2e84a10.md "The communication management apps allow you to integrate your system or solution with other systems to enable data exchange.")

