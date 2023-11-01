<!-- loio1c042caa1d7142da8de5260bee663864 -->

# Business User Changes - Read



Technical name: `APS_IAM_API_BUSER_CDOC_0001_IWSG`

This service enables you to read the change documents of business users.

This service is published on the SAP Business Accelerator Hub. For more information about APIs, see  <?sap-ot O2O class="- topic/xref " href="1e60f14bdc224c2c975c8fa8bcfd7f3f.xml" text="" desc="" xtrc="xref:2" xtrf="file:/home/builder/src/dita-all/jjq1673438782153/loio2080d0faf9d84ce6aa14caa4caa32935_en-US/src/content/localization/en-us/6f3c2e18174047a49596401780e54132.xml" ?> .



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

`BusinessUserID` 

</td>
<td valign="top">

Business User ID

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

The following values are available

-   *GE* = General changes to the business user attributes, such as the description



    • *BR* = Business role assignments




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

Changed by user identified by*Global User ID*

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

The details of an API response are according to the operation types that are supported. For more information, see  <?sap-ot O2O class="- topic/xref " href="c85065d6a1884b9e92d19b85b39e1219.xml" text="" desc="" xtrc="xref:2" xtrf="file:/home/builder/src/dita-all/jjq1673438782153/loio2080d0faf9d84ce6aa14caa4caa32935_en-US/src/content/localization/en-us/1c042caa1d7142da8de5260bee663864.xml" ?> .

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



<a name="loio1c042caa1d7142da8de5260bee663864__section_xwc_t4f_zkb"/>

## Additional Information

https://api.sap.com/api/APS\_IAM\_API\_BUSER\_CDOC\_0001\_IWSG/overview

> ### Note:  
> For more details about Communication Management, see [Communication Management](../50-administration-and-ops/communication-management-2e84a10.md).

