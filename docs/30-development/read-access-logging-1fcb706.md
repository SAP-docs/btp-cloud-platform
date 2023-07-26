<!-- loio1fcb7069716a4e6cb17b312189c79b0c -->

# Read Access Logging



<a name="loio1fcb7069716a4e6cb17b312189c79b0c__section_ewl_nsk_byb"/>

## Use

In Read Access Logging \(RAL\), you can configure which read-access information to log and under which conditions.

SAP delivers sample configurations for applications.

The **BC/BC-SRV-APS-CDB/Template for Preview Access** captures information related to viewing and accessing data.

In the following configurations, fields are logged in combination with additional fields, in the following business contexts:


<table>
<tr>
<th valign="top">

Channel



</th>
<th valign="top">

Configuration



</th>
<th valign="top">

Fields Logged



</th>
<th valign="top">

Business Context



</th>
</tr>
<tr>
<td valign="top">

SAP Gateway \(OData\)



</td>
<td valign="top">

`BC/BC-SRV-APS-CDB/Template for Preview Access` 



</td>
<td valign="top">

Username \(`SY-UNAME`\)

Request URL \(`:Request URL`\)\>



</td>
<td valign="top">

Log viewing and accessing data along with the search filter criteria



</td>
</tr>
</table>

> ### Note:  
> See SAP Note [3351781](https://launchpad.support.sap.com/#/notes/3351781) for information about the template RAL configuration file for Customer Data Browser.

**Related Information**  


[Customer Data Browser](customer-data-browser-c570bf8.md)

[Security Audit Log](security-audit-log-d2167ac.md "")

