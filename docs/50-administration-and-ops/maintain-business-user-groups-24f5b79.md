<!-- loio24f5b79256f64990af35b22ea87ea020 -->

# Maintain Business User Groups

**App ID:** F6399



With this app you can organize users into logical groups based on organizational areas, project teams, or location. Once grouped, you can search within those groups independently, review all members at once, and apply actions to the entire group in one step, such as assigning business roles.

You can create and manage business user groups manually, or synchronize them automatically from an external corporate identity provider via System for Cross-domain Identity Management \(SCIM\) integration. This keeps your SAP user structure aligned with your company's central directory.

Beyond organization, business user groups are the foundation of delegated administration. Rather than granting an administrator access to your entire user base, you can scope their authorization to a specific group. This keeps overall control with the super administrator while distributing day-to-day maintenance to the right people.

> ### Example:  
> You can create a **Finance** business user group and hand management over to the **Finance** area administrator without exposing any other users. You can set up a dedicated business user group for a go-live team to control access during a specific implementation phase. Or you can bundle all external consultants into a business user group so their team lead can handle only their basic details, without access to internal employee records.

> ### Note:  
> The system automatically creates the business user group name in namespace *ZCB*.



## Key Features

You can use this app to:



-   Create business user groups and assign the required business users to them

-   Reassign or remove business users to or from business user groups

    > ### Note:  
    > You can also use drag and drop to move business users from one group to another.

-   Upload business user assignments

-   Add business user groups to transports

-   Export business user groups to a spreadsheet \(including description and number of business users\)




<a name="loio24f5b79256f64990af35b22ea87ea020__section_a5z_k4w_nvb"/>

## Prerequisites

The following restriction types \(in the following business catalogs\) are required for maintaining or displaying business role groups and business user groups:


<table>
<tr>
<th valign="top">

Business Catalogs

</th>
<th valign="top">

Restriction Types

</th>
</tr>
<tr>
<td valign="top">

`SAP_CORE_BC_IAM_RM` 

</td>
<td valign="top">

*Business Role* \(`S_BRL`\)

</td>
</tr>
<tr>
<td valign="top">

`SAP_CORE_BC_IAM_UM`

</td>
<td valign="top">

*Business User*\(`CLASS`\)

*Business Role* \(`S_BRL`\)

</td>
</tr>
<tr>
<td valign="top">

`SAP_CORE_BC_IAM_RA`

</td>
<td valign="top">

*Business Role* \(`S_BRL`\)

*Business Role User Assignment* \(`S_BRL_ASG`\)

*Business User* \(`CLASS`\)

</td>
</tr>
<tr>
<td valign="top">

`SAP_CORE_BC_IAM_RM_DISP_PC`

</td>
<td valign="top">

*Business Role* \(`S_BRL`\)

</td>
</tr>
<tr>
<td valign="top">

`SAP_CORE_BC_IAM_UM_DISP_PC`

</td>
<td valign="top">

*Business User* \(`CLASS`\)

</td>
</tr>
</table>



<a name="loio24f5b79256f64990af35b22ea87ea020__supported_devices"/>

## Supported Device Types

-   Desktop

-   Tablet




<a name="loio24f5b79256f64990af35b22ea87ea020__customer_component"/>

## Component for Customer Incidents

If you need support or experience issues, please report an incident under component `BC-SRV-APS-IAM`.

