<!-- loiodce4f9ac42d043ffbe50dbabc30d7a33 -->

# Accessing the App

Customer Data Browser is a self-service application that you can use to view data that belongs to specific CDS views and database tables that are allowed for user access by SAP or by the customer.

> ### Note:  
> The CDS views and database tables that are allowed for user access by SAP or by the customer in the Customer Data Browser app are called Customer Data Browser objects.



<a name="loiodce4f9ac42d043ffbe50dbabc30d7a33__section_g1v_trg_ntb"/>

## Viewing Fiori Tiles

This application is available on the SAP Fiori launchpad screen as a customer self-service.

Based on your assigned business role catalog, you can view the SAP Fiori launchpad tile *Customer Data Browser*.



<a name="loiodce4f9ac42d043ffbe50dbabc30d7a33__section_w5t_lcd_cqb"/>

## Required Users

The required user and the respective business catalog role and business role template for the **Customer Data Browser** app are described below.


<table>
<tr>
<th valign="top">

Required User

</th>
<th valign="top">

User Task

</th>
<th valign="top">

Business Catalog Role

</th>
<th valign="top">

Business Role Template

</th>
<th valign="top">

Application

</th>
</tr>
<tr>
<td valign="top">

Business User

</td>
<td valign="top">

Access application

</td>
<td valign="top">

SAP\_CORE\_BC\_CDB\_PC

</td>
<td valign="top">

SAP\_BR\_ADMINISTRATOR\_DANA

\(Administrator - Data Analysis\)

</td>
<td valign="top">

Customer Data Browser

</td>
</tr>
<tr>
<td valign="top">

Admin User

</td>
<td valign="top">

Maintain authorization restrictions

</td>
<td valign="top">

Not relevant

</td>
<td valign="top">

SAP\_BR\_ADMINISTRATOR

\(Administrator\)

</td>
<td valign="top">

Maintain Business Roles

</td>
</tr>
</table>



<a name="loiodce4f9ac42d043ffbe50dbabc30d7a33__section_iqy_lbg_ktb"/>

## Role Purpose

For each role, the table below shows information about access, purpose and assignments.

****


<table>
<tr>
<th valign="top">

User Role

</th>
<th valign="top">

Purpose

</th>
<th valign="top">

Access

</th>
<th valign="top">

Recommendations

</th>
</tr>
<tr>
<td valign="top">

Administrator

`SAP_BR_ADMINISTRATOR`

</td>
<td valign="top">

With this role, you can maintain authorization restrictions using the [Maintain Business Roles](https://help.sap.com/docs/SAP_S4HANA_CLOUD/53e36b5493804bcdb3f6f14de8b487dd/8980ad05330b4585ab96a8e09cef4688.html?locale=en-US) app.For more information about maintaining restrictions for Customer Data Browser, see [How to Define Authorizations Based on Restrictions](../50-administration-and-ops/how-to-define-authorizations-based-on-restrictions-c926d69.md). .

</td>
<td valign="top">

Access the Maintain Business Roles app in the Fiori Apps Library using the Fiori ID: F1492.

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

Administrator – Data Analysis

SAP\_BR\_ADMINISTRATOR

</td>
<td valign="top">

With this role, you can access the Customer Data Browser application.

</td>
<td valign="top">

Access the Customer Data Browser application in the Fiori apps Library using the Fiori ID: F5746.

</td>
<td valign="top">

-   Assign the`SAP_BR_ADMINISTRATOR_DANA` role to a business user who does not have the`SAP_BR_ADMINISTRATOR` role.

-   Make sure that the user with the`SAP_BR_ADMINISTRATOR_DANA` role is assigned to a single copy of the`SAP_BR_ADMINISTRATOR_DANA` role.


> ### Note:  
> Assigning the user to multiple copies of the`SAP_BR_ADMINISTRATOR_DANA` role may cause authorization issues when you access the Customer Data Browser app.



</td>
</tr>
</table>

**Related Information**  


[Customer Data Browser](customer-data-browser-c570bf8.md)

[Data Visibility Based on Restrictions](data-visibility-based-on-restrictions-15fb03d.md "")

