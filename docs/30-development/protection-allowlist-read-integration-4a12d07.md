<!-- loio4a12d077b7df494abe2da3018643805e -->

# Protection Allowlist - Read Integration



Service name: `ProtectionAllowlist`

This service enables you to:

-   Read clickjacking protection data

-   Read trusted network zones

-   Read trusted CSS Style Sheets

-   Read Cross-Origin Resource Sharing


This service is published on the SAP Business Accelerator Hub. For more information about APIs, see the *Related Information* section.

This is an OData version 4 service. This version aims to improve processing time and resource consumption of clients and servers. This includes a lightweight JSON format that reduces the size of every response.



<a name="loio4a12d077b7df494abe2da3018643805e__section_ozh_cvx_clb"/>

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

`aps_sec_api_pal_read`

</td>
<td valign="top">

`srvd_a2`

</td>
<td valign="top">

`ProtectionAllowlist`

</td>
<td valign="top">

`0001`

</td>
</tr>
</table>



<a name="loio4a12d077b7df494abe2da3018643805e__section_ct2_xxx_clb"/>

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

ClickjackingProtection

</td>
<td valign="top">

Contains trusted hosts for Clickjacking Protection

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

TrustedNetworkZones

</td>
<td valign="top">

Contains trusted hosts for trusted network zones

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

TrustedCSSStyleSheets

</td>
<td valign="top">

Contains trusted hosts CSS Style Sheets

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

CrossOriginResourceSharing

</td>
<td valign="top">

Contains trusted hosts for Cross-Origin Resource sharing

</td>
<td valign="top">

Mandatory

</td>
<td valign="top">

For more information, see the *Related Information* section.

</td>
</tr>
</table>



<a name="loio4a12d077b7df494abe2da3018643805e__section_znk_jzx_clb"/>

## Additional Information



> ### Note:  
> For more information about Communication Management, see the *Related Information* section.

**Related Information**  


[Clickjacking Protection - Entity](clickjacking-protection-entity-5b78b73.md)

[CORS - Entity](cors-entity-0539e1d.md)

[**APIs on SAP Business Accelerator Hub**](https://help.sap.com/docs/SAP_S4HANA_CLOUD/0f69f8fb28ac4bf48d2b57b9637e81fa/1e60f14bdc224c2c975c8fa8bcfd7f3f.html?version=2308.500)

[Communication Management](../50-administration-and-ops/communication-management-2e84a10.md "The communication management apps allow you to integrate your system or solution with other systems to enable data exchange.")

