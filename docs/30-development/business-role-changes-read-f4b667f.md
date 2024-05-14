<!-- loiof4b667f2fa8041d5b5ac2e63393d0225 -->

# Business Role Changes - Read



Technical name: `APS_IAM_API_BROLE_CDOC_0001_IWSG`

This service enables you to to read the change documents of business roles.



This service is published on the SAP Business Accelerator Hub. For more information about APIs, see the **Related Information** section.



<a name="loiof4b667f2fa8041d5b5ac2e63393d0225__BusinessRoleChangesServiceSturcture"/>

## Service Structure

**Service Header \(optional\)**

The service header contains information about the service.

**Entities**

The entities contain the service's business data.

****


<table>
<tr>
<th valign="top">

Entity

</th>
<th valign="top">

Description

</th>
<th valign="top">

Necessity

</th>
</tr>
<tr>
<td valign="top">

`BusinessRoleID`

</td>
<td valign="top">

Business Role ID

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

`ChangedOn`

</td>
<td valign="top">

Change on Date/Time

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

`ChangeCategory`

</td>
<td valign="top">

Category of change

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

`ChangeCategoryText`

</td>
<td valign="top">

Category of change description \(such as *Business catalog added*\)

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

`Attribute`

</td>
<td valign="top">

Name of changed attribute

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

`ValueChangedFrom`

</td>
<td valign="top">

Old value

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

`ValueChangedTo`

</td>
<td valign="top">

New value

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

`ChangedByUserName`

</td>
<td valign="top">

Changed by user identified by user name

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

`ChangedByUserID`

</td>
<td valign="top">

Changed by user identified by user ID

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

`ChangedByUserEmailAddress`

</td>
<td valign="top">

Changed by user identified by email address

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

`ChangedByGlobalUserID`

</td>
<td valign="top">

Changed by user identified by *Global User ID*

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

`Action`

</td>
<td valign="top">

Action

</td>
<td valign="top">

Optional

</td>
</tr>
</table>



## Service Response

The details of an API response are according to the operation types that are supported. For more information, see [Operation for Business Role Changes - Read](operation-for-business-role-changes-read-276b1b0.md).

****


<table>
<tr>
<th valign="top">

Entity

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

200

</td>
<td valign="top">

OK

</td>
</tr>
<tr>
<td valign="top">

400

</td>
<td valign="top">

Bad Request

</td>
</tr>
<tr>
<td valign="top">

403

</td>
<td valign="top">

Forbidden

</td>
</tr>
</table>



<a name="loiof4b667f2fa8041d5b5ac2e63393d0225__section_xwc_t4f_zkb"/>

## Additional Information



For more information about Communication Management, see the **Related Information** section.



**Related Information**  


[**APIs on SAP Business Accelerator Hub**](https://help.sap.com/docs/SAP_S4HANA_CLOUD/0f69f8fb28ac4bf48d2b57b9637e81fa/1e60f14bdc224c2c975c8fa8bcfd7f3f.html?version=latest)

[Communication Management](../50-administration-and-ops/communication-management-2e84a10.md "The communication management apps allow you to integrate your system or solution with other systems to enable data exchange.")

