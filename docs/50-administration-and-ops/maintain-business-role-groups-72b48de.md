<!-- loio72b48dea7743487c952fa13fbdb6d23c -->

# Maintain Business Role Groups



With this app you can create business role groups and assign multiple business roles to them. This helps you to organize your area and easily search for all business roles of a certain category \(for example to assign business users to them\). Grouping also facilitates maintenance of authorizations. If you are the super administrator for all areas, you can delegate this task to administrators for the relevant areas, such as Financials. In this case, you would create a business role group for Financials and allow to assign these business roles only to particular user groups.

Please note that the name of business role group is created automatically in namespace *ZCB*.



## Key Features

You can use this app to:



-   Create business role groups and assign the required business roles to them

-   Reassign or remove business roles to or from business role groups

    Note: You can also use drag and drop to move business roles from one group to another.

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

SAP\_CORE\_BC\_IAM\_RM

</td>
<td valign="top">

*Business Role* \(S\_BRL\)

</td>
</tr>
<tr>
<td valign="top">

SAP\_CORE\_BC\_IAM\_UM

</td>
<td valign="top">

*Business User*\(CLASS\)

*Business Role* \(S\_BRL\)

</td>
</tr>
<tr>
<td valign="top">

SAP\_CORE\_BC\_IAM\_RA

</td>
<td valign="top">

*Business Role* \(S\_BRL\)

*Business Role User Assignment* \(S\_BRL\_ASG\)

*Business User* \(CLASS\)

</td>
</tr>
<tr>
<td valign="top">

SAP\_CORE\_BC\_IAM\_RM\_DISP\_PC

</td>
<td valign="top">

*Business Role* \(S\_BRL\)

</td>
</tr>
<tr>
<td valign="top">

SAP\_CORE\_BC\_IAM\_UM\_DISP\_PC

</td>
<td valign="top">

*Business User* \(CLASS\)

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

