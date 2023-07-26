<!-- loio15fb03d11bea4f9d93b6ebad6e96265b -->

# Restrictions and App Behavior



<a name="loio15fb03d11bea4f9d93b6ebad6e96265b__section_qxg_15x_ntb"/>

## Restrictions Required to Be Maintained by the Administrative User

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

> ### Note:  
> When maintaining restrictions, set the *Write, Read, Value Help* restriction to **No Access**.



<a name="loio15fb03d11bea4f9d93b6ebad6e96265b__section_cj1_cwx_ntb"/>

## App Behavior in Response to Administrative Restrictions

Refer to the restriction matrix below to understand the expected behavior of the application.

****


<table>
<tr>
<th valign="top" colspan="3">

Restrictions Set By the Administrator



</th>
<th valign="top" colspan="5">

Display Behavior in Customer Data Browser App



</th>
</tr>
<tr>
<td valign="top">

**For Object Name**



</td>
<td valign="top">

**For Object Field** 



</td>
<td valign="top">

**For Object Record** 



</td>
<td valign="top">

**Objects**



</td>
<td valign="top">

**CDS Views**



</td>
<td valign="top">

**Database Tables**



</td>
<td valign="top">

**Fields**



</td>
<td valign="top">

**Records**



</td>
</tr>
<tr>
<td valign="top">

Unrestricted access



</td>
<td valign="top">

Unrestricted



</td>
<td valign="top">

Unrestricted



</td>
<td valign="top">

Displays all objects



</td>
<td valign="top">

Displays data that is authorized for the user. Note that the user is explicitly required to obtain the necessary authorizations.



</td>
<td valign="top">

No data displayed



</td>
<td valign="top">

Displays general \(GE\) and sensitive personal \(SP\) fields



</td>
<td valign="top">

Displays records that fulfill access controls \(AC\)



</td>
</tr>
<tr>
<td valign="top">

Restrictions not maintained



</td>
<td valign="top">

Restrictions not maintained



</td>
<td valign="top">

Restrictions not maintained



</td>
<td valign="top">

Displays no objects



</td>
<td valign="top">

No data displayed



</td>
<td valign="top">

No data displayed



</td>
<td valign="top">

No data displayed



</td>
<td valign="top">

No data displayed



</td>
</tr>
<tr>
<td valign="top">

Restricted access



</td>
<td valign="top">

Access to general fields \(GE\)



</td>
<td valign="top">

Access to records that fulfill access controls \(AC\)



</td>
<td valign="top">

Displays objects with access



</td>
<td valign="top">

Displays data that is authorized for the user. Note that the user is explicitly required to obtain the necessary authorizations.



</td>
<td valign="top">

No data displayed



</td>
<td valign="top">

Displays general fields \(GE\)



</td>
<td valign="top">

Displays records that fulfill access controls \(AC\)



</td>
</tr>
<tr>
<td valign="top">

Restricted access



</td>
<td valign="top">

Access to sensitive personal fields \(SP\)



</td>
<td valign="top">

Access to records that fulfill access controls \(AC\)



</td>
<td valign="top">

Displays objects with access



</td>
<td valign="top">

Displays data that is authorized for the user. Note that the user is explicitly required to obtain the necessary authorizations.



</td>
<td valign="top">

No data displayed



</td>
<td valign="top">

Displays sensitive personal fields \(SP\)



</td>
<td valign="top">

Displays records that fulfill access controls \(AC\)



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

Access to general \(GE\) and sensitive personal \(SP\) fields



</td>
<td valign="top">

Access to records that fulfill access controls \(AC\)



</td>
<td valign="top">

Displays objects with access



</td>
<td valign="top">

Displays data that is authorized for the user. Note that the user is explicitly required to obtain the necessary authorizations.



</td>
<td valign="top">

No data displayed



</td>
<td valign="top">

Displays general \(GE\) and sensitive personal \(SP\) fields



</td>
<td valign="top">

Displays records that fulfill access controls \(AC\)



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

Access to general fields \(GE\)



</td>
<td valign="top">

Access to records with bypassed access controls \(OV\)



</td>
<td valign="top">

Displays objects with access



</td>
<td valign="top">

Displays all data



</td>
<td valign="top">

Displays all data



</td>
<td valign="top">

Displays general fields \(GE\)



</td>
<td valign="top">

Displays all records



</td>
</tr>
<tr>
<td valign="top">

Restricted Read Access



</td>
<td valign="top">

Access to sensitive personal fields \(SP\)



</td>
<td valign="top">

Access to records with bypassed access controls \(OV\)



</td>
<td valign="top">

Displays objects with access



</td>
<td valign="top">

Displays all data



</td>
<td valign="top">

Displays all data



</td>
<td valign="top">

Displays sensitive personal fields \(SP\)



</td>
<td valign="top">

Displays all records



</td>
</tr>
<tr>
<td valign="top">

Restricted access



</td>
<td valign="top">

Access to general \(GE\) and sensitive personal \(SP\) fields



</td>
<td valign="top">

Access to records with bypassed access controls \(OV\)



</td>
<td valign="top">

Displays objects with access



</td>
<td valign="top">

Displays all data



</td>
<td valign="top">

Displays all data



</td>
<td valign="top">

Displays general \(GE\) and sensitive personal \(SP\) fields



</td>
<td valign="top">

Displays all records



</td>
</tr>
</table>



<a name="loio15fb03d11bea4f9d93b6ebad6e96265b__section_ymh_jyx_ntb"/>

## Summary of User Access

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

[Using the App](using-the-app-c222a96.md "")

