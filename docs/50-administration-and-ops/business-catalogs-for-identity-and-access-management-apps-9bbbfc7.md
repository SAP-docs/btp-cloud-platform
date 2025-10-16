<!-- loio9bbbfc78b74a45af9059da66a149e507 -->

# Business Catalogs for Identity and Access Management Apps

Get an overview of available business role catalogs and their restrictions.



You assign business catalogs to business roles that are assigned to business users. Business catalogs contain authorizations that define what a business user with a certain business role is allowed to do.

**Business Catalogs for Identity and Access Management Apps**


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
<td valign="top" rowspan="3">

*User Management*

`SAP_CORE_BC_IAM_UM`

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

`SAP_CORE_BC_IAM_RM`

</td>
<td valign="top">

Maintain Business Roles

</td>
<td valign="top">

Not possible to assign business roles to the business users.

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

`SAP_CORE_BC_IAM_RA`

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

Only possible to assign business roles to the business users. Not possible to change the business roles.

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
<td valign="top">

*Identity and Access Management - Role Management - Display* 

`SAP_CORE_BC_IAM_RM_DISP_PC`

</td>
<td valign="top">

This business catalog enables you to grant read-only access to the following apps related to identity and access management:

-   *Maintain Business Roles*

-   *IAM Information System*

-   *IAM Key Figures*

-   *Business Role Templates*

-   *Business Catalogs*

-   *Display Restriction Types*




</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*Identity and Access Management - User Management - Display*

`SAP_CORE_BC_IAM_UM_DISP_PC`

</td>
<td valign="top">

This business catalog enables you to grant read-only access to the following apps related to identity and access management:

-   *Maintain Business Users*

-   *IAM Information System*

-   *IAM Key Figures*

-   *Display Technical Users*




</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*Identity and Access Management - Group Management*

`SAP_CORE_BC_IAM_GRP_PC`

</td>
<td valign="top">

This business catalog enables users to create and maintain business user groups and business role groups.

</td>
<td valign="top">

None

</td>
</tr>
</table>

**Related Information**  


[What Are Cloud Identity Services?](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/what-is-identity-authentication?locale=en-US)

[User Guide](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/user-guide?locale=en-US)

[Corporate Identity Providers](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/corporate-identity-providers?locale=en-US)

