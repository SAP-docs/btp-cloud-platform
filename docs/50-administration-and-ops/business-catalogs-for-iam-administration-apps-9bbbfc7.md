<!-- loio9bbbfc78b74a45af9059da66a149e507 -->

# Business Catalogs for IAM Administration Apps

Get an overview of available business catalogs and their restrictions.



You assign business catalogs to business roles that are assigned to business users.

The following two types of business catalogs are available:

-   Business catalogs that directly include authorizations specifying the actions a business user with a specific business role is permitted to perform.
-   Business catalogs that serve as containers for IAM apps, which manage authorizations. These business catalogs are designated by the *Supports IAM Apps* checkbox.

    > ### Note:  
    > You can also directly assign IAM apps to business roles in the *Maintain Business Roles* app.


**Business Catalogs for Identity and Access Management Apps**


<table>
<tr>
<th valign="top">

Business Role Catalog

</th>
<th valign="top">

IAM App

</th>
<th valign="top">

IAM App ID

</th>
<th valign="top">

Transaction

</th>
<th valign="top">

Transaction Code

</th>
<th valign="top">

Restrictions

</th>
</tr>
<tr>
<td valign="top">

*User Management*

`SAP_CORE_BC_IAM_UM`

</td>
<td valign="top">

*Display Technical Users* 

</td>
<td valign="top">

`F1301_TRAN`

</td>
<td valign="top">

Display Technical Users

</td>
<td valign="top">

`F1301`

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*User Management*

`SAP_CORE_BC_IAM_UM`

</td>
<td valign="top">

*Maintain Business Users* 

</td>
<td valign="top">

`F1303_TRAN`

</td>
<td valign="top">

Maintain Business Users

</td>
<td valign="top">

`F1303`

</td>
<td valign="top">

Not possible to assign business roles to the business users

</td>
</tr>
<tr>
<td valign="top">

*User Management*

`SAP_CORE_BC_IAM_UM`

</td>
<td valign="top">

*Display Business Roles*

</td>
<td valign="top">

`F1492_03_TRAN`

</td>
<td valign="top">

Maintain Business Roles

</td>
<td valign="top">

`F1492`

</td>
<td valign="top">

Not possible to assign business roles to the business users.

</td>
</tr>
<tr>
<td valign="top">

*User Management*

`SAP_CORE_BC_IAM_UM`

</td>
<td valign="top">

*IAM Information System* 

</td>
<td valign="top">

`F2450_TRAN`

</td>
<td valign="top">

IAM Information System

</td>
<td valign="top">

`F2450`

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*User Management*

`SAP_CORE_BC_IAM_UM`

</td>
<td valign="top">

*Display Restriction Types*

</td>
<td valign="top">

`F3816_TRAN` 

</td>
<td valign="top">

Display Restriction Types

</td>
<td valign="top">

`F3816`

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*User Management*

`SAP_CORE_BC_IAM_UM`

</td>
<td valign="top">

*IAM Key Figures*

</td>
<td valign="top">

`F4474_TRAN`

</td>
<td valign="top">

IAM Key Figures

</td>
<td valign="top">

`F4474`

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*User Management*

`SAP_CORE_BC_IAM_UM`

</td>
<td valign="top">

*Schedule Locks for Unused Business Users*

</td>
<td valign="top">

`F6288_TRAN`

</td>
<td valign="top">

Schedule Lock for Unused Business Users

</td>
<td valign="top">

`F6288`

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*Role Management*

`SAP_CORE_BC_IAM_RM`

</td>
<td valign="top">

*Maintain Business Roles* 

</td>
<td valign="top">

`F1492_02_TRAN`

</td>
<td valign="top">

Maintain Business Roles

</td>
<td valign="top">

`F1492`

</td>
<td valign="top">

Not possible to assign business roles to the business users.

</td>
</tr>
<tr>
<td valign="top">

*Role Management*

`SAP_CORE_BC_IAM_RM`

</td>
<td valign="top">

*IAM Information System* 

</td>
<td valign="top">

`F2450_TRAN`

</td>
<td valign="top">

IAM Information System

</td>
<td valign="top">

`F2450`

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*Role Management*

`SAP_CORE_BC_IAM_RM`

</td>
<td valign="top">

*Business Catalogs* 

</td>
<td valign="top">

`F2471_TRAN`

</td>
<td valign="top">

Business Catalogs

</td>
<td valign="top">

`F2471`

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*Role Management*

`SAP_CORE_BC_IAM_RM`

</td>
<td valign="top">

*Business Role Templates* 

</td>
<td valign="top">

`F2820_TRAN`

</td>
<td valign="top">

Business Role Templates

</td>
<td valign="top">

`F2820`

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*Role Management*

`SAP_CORE_BC_IAM_RM`

</td>
<td valign="top">

*Display Restriction Types*

</td>
<td valign="top">

`F3816_TRAN`

</td>
<td valign="top">

Display Restriction Types

</td>
<td valign="top">

`F3816`

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*Role Management*

`SAP_CORE_BC_IAM_RM`

</td>
<td valign="top">

*Display Authorization Trace*

</td>
<td valign="top">

`F4106_TRAN`

</td>
<td valign="top">

Display Authorization Trace

</td>
<td valign="top">

`F4106`

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*Role Management*

`SAP_CORE_BC_IAM_RM`

</td>
<td valign="top">

*IAM Key Figures*

</td>
<td valign="top">

`F4474_TRAN`

</td>
<td valign="top">

IAM Key Figures

</td>
<td valign="top">

`F4474`

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*Role Management*

`SAP_CORE_BC_IAM_RM`

</td>
<td valign="top">

*Display IAM Apps*

</td>
<td valign="top">

`F7500_TRAN`

</td>
<td valign="top">

Display IAM Apps

</td>
<td valign="top">

`F7500`

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*Role Assignment*

`SAP_CORE_BC_IAM_RA`

</td>
<td valign="top">

*Assign Business Users to Business Roles* 

</td>
<td valign="top">

`F1303_22_TRAN`

</td>
<td valign="top">

Maintain Business Users

</td>
<td valign="top">

`F1303`

</td>
<td valign="top">

Only possible to assign business roles to the business users. Not possible to change the business roles.

</td>
</tr>
<tr>
<td valign="top">

*Role Assignment*

`SAP_CORE_BC_IAM_RA`

</td>
<td valign="top">

*Assign Business Roles to Business Users* 

</td>
<td valign="top">

`F1492_22_TRAN` 

</td>
<td valign="top">

Maintain Business Roles

</td>
<td valign="top">

`F1492`

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*Role Assignment*

`SAP_CORE_BC_IAM_RA`

</td>
<td valign="top">

*IAM Information System*

</td>
<td valign="top">

`F2450_TRAN` 

</td>
<td valign="top">

IAM Information System

</td>
<td valign="top">

`F2450`

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*Role Assignment*

`SAP_CORE_BC_IAM_RA`

</td>
<td valign="top">

*Display Business Catalogs* 

</td>
<td valign="top">

`F2471_TRAN`

</td>
<td valign="top">

Business Catalogs

</td>
<td valign="top">

`F2471`

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*Role Assignment*

`SAP_CORE_BC_IAM_RA`

</td>
<td valign="top">

*Display Restriction Types*

</td>
<td valign="top">

`F3816_TRAN` 

</td>
<td valign="top">

Display Restriction Types

</td>
<td valign="top">

`F3816` 

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*Role Assignment*

`SAP_CORE_BC_IAM_RA`

</td>
<td valign="top">

*Display Authorization Trace*

</td>
<td valign="top">

`F4106_TRAN`

</td>
<td valign="top">

Display Authorization Trace

</td>
<td valign="top">

`F4106`

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*Role Assignment*

`SAP_CORE_BC_IAM_RA`

</td>
<td valign="top">

*IAM Key Figures*

</td>
<td valign="top">

`F4474_TRAN`

</td>
<td valign="top">

IAM Key Figures

</td>
<td valign="top">

`F4474`

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*Role Assignment*

`SAP_CORE_BC_IAM_RA`

</td>
<td valign="top">

*Display IAM Apps*

</td>
<td valign="top">

`F7500_TRAN`

</td>
<td valign="top">

Display IAM Apps

</td>
<td valign="top">

`F7500`

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*Role Management - Display*

`SAP_CORE_BC_IAM_RM_DISP_PC`

</td>
<td valign="top">

*Display Business Roles*

</td>
<td valign="top">

`F1492_03_TRAN` 

</td>
<td valign="top">

Maintain Business Roles

</td>
<td valign="top">

*F1492*

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*Role Management - Display*

`SAP_CORE_BC_IAM_RM_DISP_PC`

</td>
<td valign="top">

*IAM Information System*

</td>
<td valign="top">

`F2450_TRAN`

</td>
<td valign="top">

IAM Information System

</td>
<td valign="top">

*F2450*

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*Role Management - Display*

`SAP_CORE_BC_IAM_RM_DISP_PC`

</td>
<td valign="top">

*Display Business Catalogs*

</td>
<td valign="top">

`F2471_TRAN` 

</td>
<td valign="top">

Business Catalogs

</td>
<td valign="top">

F2471

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*Role Management - Display*

`SAP_CORE_BC_IAM_RM_DISP_PC`

</td>
<td valign="top">

*Business Role Templates*

</td>
<td valign="top">

`F2820_TRAN` 

</td>
<td valign="top">

Business Role Templates

</td>
<td valign="top">

F2820

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*Role Management - Display*

`SAP_CORE_BC_IAM_RM_DISP_PC`

</td>
<td valign="top">

*Display Restriction Types*

</td>
<td valign="top">

`F3816_TRAN`

</td>
<td valign="top">

Display Restriction Types

</td>
<td valign="top">

F3816

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*Role Management - Display*

`SAP_CORE_BC_IAM_RM_DISP_PC`

</td>
<td valign="top">

*IAM Key Figures*

</td>
<td valign="top">

`F4474_TRAN`

</td>
<td valign="top">

IAM Key Figures

</td>
<td valign="top">

F4474

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*Role Management - Display*

`SAP_CORE_BC_IAM_RM_DISP_PC`

</td>
<td valign="top">

*Display IAM Apps*

</td>
<td valign="top">

`F7500_TRAN` 

</td>
<td valign="top">

Display IAM Apps

</td>
<td valign="top">

F7500

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*User Management - Display*

`SAP_CORE_BC_IAM_UM_DISP_PC`

</td>
<td valign="top">

*Display Technical Users*

</td>
<td valign="top">

`F1301_TRAN` 

</td>
<td valign="top">

Display Technical Users

</td>
<td valign="top">

F1301

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*User Management - Display*

`SAP_CORE_BC_IAM_UM_DISP_PC`

</td>
<td valign="top">

*Display Business User*s

</td>
<td valign="top">

`F1303_03_TRAN` 

</td>
<td valign="top">

Maintain Business Users

</td>
<td valign="top">

F1303

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*User Management - Display*

`SAP_CORE_BC_IAM_UM_DISP_PC`

</td>
<td valign="top">

*IAM Information System*

</td>
<td valign="top">

`F2450_TRAN` 

</td>
<td valign="top">

IAM Information System

</td>
<td valign="top">

F2405

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*User Management - Display*

`SAP_CORE_BC_IAM_UM_DISP_PC`

</td>
<td valign="top">

*Display Restriction Types* 

</td>
<td valign="top">

`F3816_TRAN`

</td>
<td valign="top">

Display Restriction Types

</td>
<td valign="top">

F3816

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*User Management - Display*

`SAP_CORE_BC_IAM_UM_DISP_PC`

</td>
<td valign="top">

*IAM Key Figures*

</td>
<td valign="top">

`F4474_TRAN` 

</td>
<td valign="top">

IAM Key Figures

</td>
<td valign="top">

F4474

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*Group Management* 

`SAP_CORE_BC_IAM_GRP_PC`

</td>
<td valign="top">

*Maintain Business User Groups*

</td>
<td valign="top">

`F6399_TRAN` 

</td>
<td valign="top">

Maintain Business User Groups

</td>
<td valign="top">

`F6399`

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

*Group Management* 

`SAP_CORE_BC_IAM_GRP_PC`

</td>
<td valign="top">

*Maintain Business Role Groups*

</td>
<td valign="top">

`F6461_TRAN` 

</td>
<td valign="top">

Maintain Business Role Groups

</td>
<td valign="top">

`F6461`

</td>
<td valign="top">

None

</td>
</tr>
</table>

