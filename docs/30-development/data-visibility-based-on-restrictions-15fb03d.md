<!-- loio15fb03d11bea4f9d93b6ebad6e96265b -->

# Data Visibility Based on Restrictions



<a name="loio15fb03d11bea4f9d93b6ebad6e96265b__section_qxg_15x_ntb"/>

## Restriction Fields in the Maintain Business Roles App

The administrator can set restrictions on restriction fields in the [Maintain Business Roles](https://help.sap.com/docs/SAP_S4HANA_CLOUD/53e36b5493804bcdb3f6f14de8b487dd/8980ad05330b4585ab96a8e09cef4688.html?locale=en-US) app. The restrictions set appear in the *Read/Value Help* restriction type in the Maintain Business Roles app.

> ### Note:  
> When maintaining restrictions, set the *Write, Read, Value Help* restriction to **No Access**.

The user can view objects in the Customer Data Browser app based on the restrictions set by the administrator.

The*Read/Value Help*restriction type for the Customer Data Browser app consists of the following restriction fields:

****


<table>
<tr>
<th valign="top">

Restriction Field

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Object Group

</td>
<td valign="top">

Logically groups Customer Data Browser objects.

Note that this field is not active.

</td>
</tr>
<tr>
<td valign="top">

Object Name

</td>
<td valign="top">

Displays a list of Customer Data Browser objects and their descriptions.

</td>
</tr>
<tr>
<td valign="top">

Object Fields

</td>
<td valign="top">

Provides access to the following categories of fields in Customer Data Browser objects:

-   GE: General fields that do not contain sensitive personal information
-   SP: Sensitive personal information fields that contain key fields and fields with sensitive personal information
-   Unrestricted: All fields containing general and sensitive personal information

Note that the field categories are determined by internal SAP classifications.

</td>
</tr>
<tr>
<td valign="top">

Object Records

</td>
<td valign="top">

Provides access to the following categories of data records in Customer Data Browser objects:

-   OV: Records with bypassed access controls \(privileged access\)
-   AC: Records that fulfill access controls \(unprivileged access\)
-   Unrestricted: Records that fulfill access controls \(unprivileged access\)



</td>
</tr>
</table>



<a name="loio15fb03d11bea4f9d93b6ebad6e96265b__section_cj1_cwx_ntb"/>

## Display Behavior in the Customer Data Browser App

See the restriction categories and visibility scenarios below to understand what you can view in the Customer Data Browser application.



### Restriction Category: Bypassing Access Controls

**Scenario 1: View the data of all CDS views and all database tables**

If you want to view the data of all CDS views and database tables, the administrator needs to set the following restrictions in the Maintain Business Roles app:


<table>
<tr>
<th valign="top">

Object

</th>
<th valign="top">

Required Restriction

</th>
</tr>
<tr>
<td valign="top">

Object Name

</td>
<td valign="top">

Unrestricted

</td>
</tr>
<tr>
<td valign="top">

Object Fields

</td>
<td valign="top">

General fields \(GE\) <or\> Sensitive personal fields \(SP\) <or\> Both

</td>
</tr>
<tr>
<td valign="top">

Object Records

</td>
<td valign="top">

Access to records with bypassed access controls \(OV\)

</td>
</tr>
</table>

**Scenario 2: View the data of only CDS views** 

If you want to view the data of only CDS views, the administrator needs to set the following restrictions in the Maintain Business Roles app:


<table>
<tr>
<th valign="top">

Object

</th>
<th valign="top">

Required Restriction

</th>
</tr>
<tr>
<td valign="top">

Object Name

</td>
<td valign="top">

Restricted - Select all CDS views

</td>
</tr>
<tr>
<td valign="top">

Object Fields

</td>
<td valign="top">

General fields \(GE\) <or\> Sensitive personal fields \(SP\) <or\> Both

</td>
</tr>
<tr>
<td valign="top">

Object Records

</td>
<td valign="top">

Access to records with bypassed access controls \(OV\)

</td>
</tr>
</table>

**Scenario 3: View the data of only database tables** 

If you want to view the data of only database tables, the administrator needs to set the following restrictions in the Maintain Business Roles app:


<table>
<tr>
<th valign="top">

Object

</th>
<th valign="top">

Required Restriction

</th>
</tr>
<tr>
<td valign="top">

Object Name

</td>
<td valign="top">

Restricted - Select all database tables

</td>
</tr>
<tr>
<td valign="top">

Object Fields

</td>
<td valign="top">

General fields \(GE\) <or\> Sensitive personal fields \(SP\) <or\> Both

</td>
</tr>
<tr>
<td valign="top">

Object Records

</td>
<td valign="top">

Access to records with bypassed access controls \(OV\)

</td>
</tr>
</table>

**Scenario 4: View the data of specific CDS views and specific database tables** 

If you want to view the data of specific CDS views and specific database tables, the administrator needs to set the following restrictions in the Maintain Business Roles app:


<table>
<tr>
<th valign="top">

Object

</th>
<th valign="top">

Required Restriction

</th>
</tr>
<tr>
<td valign="top">

Object Name

</td>
<td valign="top">

Restricted - Select specific CDS views and specific database tables

</td>
</tr>
<tr>
<td valign="top">

Object Fields

</td>
<td valign="top">

General fields \(GE\) <or\> Sensitive personal fields \(SP\) <or\> Both

</td>
</tr>
<tr>
<td valign="top">

Object Records

</td>
<td valign="top">

Access to records with bypassed access controls \(OV\)

</td>
</tr>
</table>

**Scenario 5: View the data of a group of objects created with SSCUI** 

If you want to view the data of objects created with SSCUI, the administrator needs to set the following restrictions in the Maintain Business Roles app:


<table>
<tr>
<th valign="top">

Object

</th>
<th valign="top">

Required Restriction

</th>
</tr>
<tr>
<td valign="top">

Object Name

</td>
<td valign="top">

Optional - Restricted <or\> Unrestricted <or\> Not maintained

</td>
</tr>
<tr>
<td valign="top">

Object Fields

</td>
<td valign="top">

General fields \(GE\) <or\> Sensitive personal fields \(SP\) <or\> Both

</td>
</tr>
<tr>
<td valign="top">

Object Records

</td>
<td valign="top">

Access to records with bypassed access controls \(OV\)

</td>
</tr>
</table>



### Restriction Category: Retaining Access Controls

**Scenario 1: View the data of only CDS views** 

If you want to view the data of only CDS views, the administrator needs to set the following restrictions in the Maintain Business Roles app


<table>
<tr>
<th valign="top">

Object

</th>
<th valign="top">

Required Restriction

</th>
</tr>
<tr>
<td valign="top">

Object Name

</td>
<td valign="top">

Unrestricted <or\> Restricted

</td>
</tr>
<tr>
<td valign="top">

Object Fields

</td>
<td valign="top">

General fields \(GE\) <or\> Sensitive personal fields \(SP\) <or\> Both

</td>
</tr>
<tr>
<td valign="top">

Object Records

</td>
<td valign="top">

Access to records that fulfill access controls \(AC\)

</td>
</tr>
</table>

**Scenario 2: View the data of only database tables**

This is not possible.



<a name="loio15fb03d11bea4f9d93b6ebad6e96265b__section_ymh_jyx_ntb"/>

## Restriction Permissions by User Role

**Business Users**


<table>
<tr>
<th valign="top">

You can access…

</th>
<th valign="top">

If…

</th>
<th valign="top">

Even if…

</th>
</tr>
<tr>
<td valign="top">

Data in CDS views

</td>
<td valign="top">

You have the required CDS view-specific access controls

</td>
<td valign="top">

You have Customer Data Browser-specific access to bypass access controls \(Object Records: OV\)

</td>
</tr>
<tr>
<td valign="top">

Data in database tables

</td>
<td valign="top">

You have Customer Data Browser-specific access to bypass access controls \(Object Records: OV\)

</td>
<td valign="top">

 

</td>
</tr>
</table>

**Administrators**

You can restrict access to Customer Data Browser objects by providing a list of object names in the *Object Name* restriction field.:

**Related Information**  


[Customer Data Browser](customer-data-browser-c570bf8.md)

[Working wtih the App](working-wtih-the-app-c222a96.md "")

[Accessing the App](accessing-the-app-dce4f9a.md "")

