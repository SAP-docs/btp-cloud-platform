<!-- loiobfaaf02f429f47e89edfead24b370d27 -->

# RoleCategoryDependentMetaData



<a name="loiobfaaf02f429f47e89edfead24b370d27__section_m53_np5_qcb"/>

## Nodes and Fields

> ### Note:  
> In the following table, field attributes are marked in blue.

**RoleCategoryDependentMetaData**


<table>
<tr>
<th valign="top" colspan="5">

Node or Field



</th>
<th valign="top">

Description



</th>
<th valign="top">

Cardinality



</th>
</tr>
<tr>
<td valign="top" rowspan="5">

`BusinessPartnerRoleCategory`

Cardinality: 1..1



</td>
<td valign="top" colspan="4">

`BusinessPartnerRoleCategoryCode`



</td>
<td valign="top">

For example: `BUP003` 



</td>
<td valign="top">

1..1



</td>
</tr>
<tr>
<td valign="top">

`Description`



</td>
<td valign="top" colspan="3">

`languageCode`



</td>
<td valign="top">

For example: Employee



</td>
<td valign="top">

0..unbounded



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

`BusinessPartnerRole`

Cardinality: 1..1



</td>
<td valign="top" colspan="3">

`BusinessPartnerRoleCode`



</td>
<td valign="top">

For example: `BBP005`



</td>
<td valign="top">

1..1



</td>
</tr>
<tr>
<td valign="top">

`Description`



</td>
<td valign="top" colspan="2">

`languageCode`



</td>
<td valign="top">

 



</td>
<td valign="top">

0..unbounded



</td>
</tr>
<tr>
<td valign="top" colspan="3">

`DefaultIndicator`



</td>
<td valign="top">

Can be *true* or *false*



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top" rowspan="5">

`BusinessPartnerExternalIDCategory`

Cardinality: 0..1



</td>
<td valign="top" colspan="4">

`BusinessPartnerExternalIDCategoryCode`



</td>
<td valign="top">

For example: `HCM030`



</td>
<td valign="top">

1..1



</td>
</tr>
<tr>
<td valign="top">

`Description`



</td>
<td valign="top" colspan="3">

`languageCode`



</td>
<td valign="top">

 



</td>
<td valign="top">

0..unbounded



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

`BusinessPartnerExternalID`

Cardinality: 0..unbounded



</td>
<td valign="top" colspan="3">

`BusinessPartnerExternalIDCode`



</td>
<td valign="top">

For example: `HCM030`



</td>
<td valign="top">

1..1



</td>
</tr>
<tr>
<td valign="top">

`Description`



</td>
<td valign="top" colspan="2">

`languageCode`



</td>
<td valign="top">

 



</td>
<td valign="top">

0..unbounded



</td>
</tr>
<tr>
<td valign="top" colspan="3">

`DefaultIndicator`



</td>
<td valign="top">

The value can be either*true* or *false*



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top" rowspan="6">

`BusinessPartnerRelationshipCategory`

Cardinality: 0..1



</td>
<td valign="top" colspan="4">

`BusinessPartnerRelationshipCategoryCode`



</td>
<td valign="top">

For example: `BUR025`



</td>
<td valign="top">

1..1



</td>
</tr>
<tr>
<td valign="top" colspan="2">

`Description`



</td>
<td valign="top" colspan="2">

`languageCode`



</td>
<td valign="top">

 



</td>
<td valign="top">

0..unbounded



</td>
</tr>
<tr>
<td valign="top" rowspan="2" colspan="2">

`Partner1_BusinessPartnerCategory`

Cardinality: 0..unbounded



</td>
<td valign="top" colspan="2">

`BusinessPartnerCategoryCode`



</td>
<td valign="top">

Can be:

-   2 - Organization

-   3 - Group




</td>
<td valign="top">

1..1



</td>
</tr>
<tr>
<td valign="top">

`Description`



</td>
<td valign="top">

`languageCode`



</td>
<td valign="top">

 



</td>
<td valign="top">

0..unbounded



</td>
</tr>
<tr>
<td valign="top" rowspan="2" colspan="2">

`Partner2_BusinessPartnerCategory`

Cardinality: 0..unbounded



</td>
<td valign="top" colspan="2">

`BusinessPartnerCategoryCode`



</td>
<td valign="top">

Can be:

-   1 - Person




</td>
<td valign="top">

1..1



</td>
</tr>
<tr>
<td valign="top">

`Description`



</td>
<td valign="top">

`languageCode`



</td>
<td valign="top">

 



</td>
<td valign="top">

0..unbounded



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

`NodeProperties`

Cardinality: 0..unbounded



</td>
<td valign="top" colspan="4">

`NodePath`



</td>
<td valign="top">

For example: `BUSINESS_USER`



</td>
<td valign="top">

1..1



</td>
</tr>
<tr>
<td valign="top" rowspan="2" colspan="2">

`NodeProperty`

Cardinality: 0..unbounded



</td>
<td valign="top" colspan="2">

`NodePropertyCode`



</td>
<td valign="top" rowspan="2">

Node property codes are:

-   01 - enabled

-   02 - disabled

-   03 - read only




</td>
<td valign="top">

1..1



</td>
</tr>
<tr>
<td valign="top">

`Description`



</td>
<td valign="top">

`languageCode`



</td>
<td valign="top">

0..unbounded



</td>
</tr>
<tr>
<td valign="top" rowspan="4">

`FieldProperties`

0..unbounded



</td>
<td valign="top" colspan="4">

`NodePath`



</td>
<td valign="top">

For example:

-   `BUSINESS_USER-USER-ROLE`
-   `BUSINESS_USER-USER-VALIDITY_PERIOD`
-   `BUSINESS_USER-USER_ASSIGNMENT`



</td>
<td valign="top">

1..1



</td>
</tr>
<tr>
<td valign="top" colspan="4">

`Fieldname`



</td>
<td valign="top">

Name of a field.



</td>
<td valign="top">

1..1



</td>
</tr>
<tr>
<td valign="top" rowspan="2" colspan="2">

`FieldProperty`

Cardinality: 0..unbounded



</td>
<td valign="top" colspan="2">

`FieldPropertyCode`



</td>
<td valign="top">

Node property codes are:

-   01 - enabled

-   02 - disabled

-   03 - read only

-   04 - mandatory

-   05 - enabled, read only for update

-   06 - mandatory, read only for update




</td>
<td valign="top">

1..1



</td>
</tr>
<tr>
<td valign="top">

`Description`



</td>
<td valign="top">

`languageCode`



</td>
<td valign="top">

 



</td>
<td valign="top">

0..unbounded



</td>
</tr>
</table>

> ### Note:  
> To display more information about the service node on the SAP API Business Hub, choose *API References* and select the operation.

