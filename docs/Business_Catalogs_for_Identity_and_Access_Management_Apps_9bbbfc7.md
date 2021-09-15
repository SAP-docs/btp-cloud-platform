<!-- loio9bbbfc78b74a45af9059da66a149e507 -->

# Business Catalogs for Identity and Access Management Apps

Get an overview of available business role catalogs and their restrictions.



You assign business catalogs to business roles that are assigned to business users. Business catalogs contain authorizations that define what a business user with a certain business role is allowed to do. Currently, four business catalogs are supported.

<a name="loio9bbbfc78b74a45af9059da66a149e507__table_igc_jnw_dw"/>Business Catalogs for Identity and Access Management Apps


<table>
<tr>
<th>

Business Role Catalog



</th>
<th>

Authorizations



</th>
<th>

Restrictions



</th>
</tr>
<tr>
<td>

*Identity and Access Management*

SAP\_CORE\_BC\_IAM



</td>
<td>

All authorizations for the IAM apps



</td>
<td>

Business catalog was set to obsolete due to potential SoD \(segregation of duties\) conflicts. Please use the other three catalogs listed below.



</td>
</tr>
<tr>
<td rowspan="3">

*User Management*

SAP\_CORE\_BC\_IAM\_UM



</td>
<td>

Maintain Business Users



</td>
<td>

Not possible to assign business roles to the business users



</td>
</tr>
<tr>
<td>

Display Technical Users



</td>
<td>

None



</td>
</tr>
<tr>
<td>

IAM Information System



</td>
<td>

None



</td>
</tr>
<tr>
<td rowspan="4">

*Role Management*

SAP\_CORE\_BC\_IAM\_RM



</td>
<td>

Maintain Business Roles



</td>
<td>

Not possible to assign business roles to the business users



</td>
</tr>
<tr>
<td>

Business Role Templates



</td>
<td>

None



</td>
</tr>
<tr>
<td>

Business Catalogs



</td>
<td>

None



</td>
</tr>
<tr>
<td>

IAM Information System



</td>
<td>

None



</td>
</tr>
<tr>
<td rowspan="3">

*Role Assignment*

SAP\_CORE\_BC\_IAM\_RA



</td>
<td>

Maintain Business Users



</td>
<td>

Only possible to assign business roles to the business users. Not possible to change the user data.



</td>
</tr>
<tr>
<td>

Maintain Business Roles



</td>
<td>

Only possible to assign business roles to the business users. Not possible to change the business roles



</td>
</tr>
<tr>
<td>

IAM Information System



</td>
<td>

None



</td>
</tr>
</table>

