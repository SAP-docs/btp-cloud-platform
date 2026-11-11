<!-- loio72b48dea7743487c952fa13fbdb6d23c -->

# Maintain Business Role Groups

**App ID:** F6461



With this app you can bundle related business roles together by functional department, business process, or project phase. Once grouped, you can search and filter roles by category, assign them to business users more efficiently, and keep a clear picture of your role landscape at any time.

Grouping brings practical benefits across three areas:

-   It simplifies authorization maintenance when you need to review or update business roles across an entire functional domain.

-   It speeds up audit and compliance reviews: you can pull all business roles tied to Procurement or Supply Chain instantly, without hunting through individual assignments.

-   It also streamlines transport management, letting you move custom business roles in logical functional blocks rather than transporting dozens of standalone business roles one by one.


Delegated administration is built into the concept. Rather than giving an administrator access to all business roles, you can scope their responsibility to a specific business role group, for example, a **Finance** group and restrict which business user groups those business roles can be assigned to.

> ### Example:  
> You can create a `ZCB_FINANCE` business role group containing the Accounts Payable Accountant, Accounts Receivable Accountant, and General Ledger Accountant business roles and hand its management over to the **Finance** area administrator. Or you can bundle regional variants like US Accounts Payable and EU Accounts Payable into a `FIN_AP_GLOBAL` business role group to monitor or transport all sub-ledger functions at once.

> ### Note:  
> The system automatically creates the business role group name in namespace *ZCB*.



## Key Features

You can use this app to:



-   Create business role groups and assign the required business roles to them

-   Reassign or remove business roles to or from business role groups

    > ### Note:  
    > You can also use drag and drop to move business roles from one group to another.

-   Upload business role assignments

-   Add business role groups to transports

-   Export business role groups to a spreadsheet \(including description and number of business roles\)




<a name="loio72b48dea7743487c952fa13fbdb6d23c__section_a5z_k4w_nvb"/>

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



<a name="loio72b48dea7743487c952fa13fbdb6d23c__supported_devices"/>

## Supported Device Types

-   Desktop

-   Tablet




<a name="loio72b48dea7743487c952fa13fbdb6d23c__customer_component"/>

## Component for Customer Incidents

If you need support or experience issues, please report an incident under component `BC-SRV-APS-IAM`.

