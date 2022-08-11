<!-- loio9bbbfc78b74a45af9059da66a149e507 -->

# Business Catalogs for Identity and Access Management Apps

Get an overview of available business role catalogs and their restrictions.



You assign business catalogs to business roles that are assigned to business users. Business catalogs contain authorizations that define what a business user with a certain business role is allowed to do.

<a name="loio9bbbfc78b74a45af9059da66a149e507__table_igc_jnw_dw"/>Business Catalogs for Identity and Access Management Apps


<table>
<tr>
<th valign="top">

Business Role Catalog



</th>
<th valign="top">

Authorizations



</th>
<th valign="top">

Restrictions



</th>
</tr>
<tr>
<td valign="top">

*Identity and Access Management*

SAP\_CORE\_BC\_IAM



</td>
<td valign="top">

All authorizations for the IAM apps



</td>
<td valign="top">

Business catalog was set to obsolete due to potential SoD \(segregation of duties\) conflicts. Please use the other three catalogs listed below.



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

*User Management*

SAP\_CORE\_BC\_IAM\_UM



</td>
<td valign="top">

Maintain Business Users



</td>
<td valign="top">

Not possible to assign business roles to the business users



</td>
</tr>
<tr>
<td valign="top">

Display Technical Users



</td>
<td valign="top">

None



</td>
</tr>
<tr>
<td valign="top">

IAM Information System



</td>
<td valign="top">

None



</td>
</tr>
<tr>
<td valign="top" rowspan="4">

*Role Management*

SAP\_CORE\_BC\_IAM\_RM



</td>
<td valign="top">

Maintain Business Roles



</td>
<td valign="top">

Not possible to assign business roles to the business users



</td>
</tr>
<tr>
<td valign="top">

Business Role Templates



</td>
<td valign="top">

None



</td>
</tr>
<tr>
<td valign="top">

Business Catalogs



</td>
<td valign="top">

None



</td>
</tr>
<tr>
<td valign="top">

IAM Information System



</td>
<td valign="top">

None



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

*Role Assignment*

SAP\_CORE\_BC\_IAM\_RA



</td>
<td valign="top">

Maintain Business Users



</td>
<td valign="top">

Only possible to assign business roles to the business users. Not possible to change the user data.



</td>
</tr>
<tr>
<td valign="top">

Maintain Business Roles



</td>
<td valign="top">

Only possible to assign business roles to the business users. Not possible to change the business roles



</td>
</tr>
<tr>
<td valign="top">

IAM Information System



</td>
<td valign="top">

None



</td>
</tr>
</table>

**Related Information**  


[Identity Authentication](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/d17a116432d24470930ebea41977a888.html?version=Cloud)

[What Is Identity Authentication?](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/27882717f44b445fa287936c6f43dc1f.html?version=Cloud)

[User Guide](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/d4c3811a58c44982bce09e9fdcbb5c64.html?version=Cloud)

[Corporate Identity Providers](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/19f3eca47db643b6aad448b5dc1075ad.html?version=Cloud)

