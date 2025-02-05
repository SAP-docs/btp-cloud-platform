<!-- loio65b70bfbd5ad438b9a3d778b677b7d4d -->

# Business Catalogs for Key User Tasks

Get an overview of available business role catalogs and their restrictions.



You assign business catalogs to business roles that are assigned to business users. Business catalogs contain authorizations that define what a business user with a certain business role is allowed to do.

Certain business catalogs are only available in tenants of specific [Tenant Business Types](../30-development/tenant-business-types-018e8bd.md).

**Business Catalogs for Key User Tasks**


<table>
<tr>
<th valign="top">

Business Catalog

</th>
<th valign="top">

Authorizations

</th>
<th valign="top">

Restrictions

</th>
<th valign="top">

Availability

</th>
</tr>
<tr>
<td valign="top">

*Extensibility - Key User Adaptation*

SAP\_CORE\_BC\_EXT\_FLX\_CUS\_PC

</td>
<td valign="top">

Key user adaptation

</td>
<td valign="top">

 

</td>
<td valign="top">

All tenant business types

</td>
</tr>
<tr>
<td valign="top">

SAP\_CORE\_BC\_EXT\_FDT

</td>
<td valign="top">

Maintain `Business Role Framework+` applications

</td>
<td valign="top">

 

</td>
<td valign="top">

All tenant business types

</td>
</tr>
<tr>
<td valign="top">

SAP\_CORE\_BC\_EXT\_PCF\_PC

</td>
<td valign="top">

Configuration of custom fields

</td>
<td valign="top">

 

</td>
<td valign="top">

Test tenant, partner customer test tenant, partner customer production tenant

</td>
</tr>
<tr>
<td valign="top">

SAP\_CORE\_BC\_EXT\_BLE

</td>
<td valign="top">

Implementation of custom logic

</td>
<td valign="top">

 

</td>
<td valign="top">

Test tenant, partner customer test tenant, partner customer production tenant

</td>
</tr>
<tr>
<td valign="top">

*Extensibility - Custom Apps and Services*

SAP\_CORE\_BC\_EXT\_TST

</td>
<td valign="top">

Testing of custom apps and custom services

</td>
<td valign="top">

Only services that have their original in the current system

</td>
<td valign="top">

Partner development tenant

</td>
</tr>
</table>

