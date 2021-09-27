<!-- loiobfaaf02f429f47e89edfead24b370d27 -->

# RoleCategoryDependentMetaData



<a name="loiobfaaf02f429f47e89edfead24b370d27__section_m53_np5_qcb"/>

## Nodes and Fields

> ### Note:  
> In the following table, field attributes are marked in blue.

<a name="loiobfaaf02f429f47e89edfead24b370d27__table_rzl_pp5_qcb"/>RoleCategoryDependentMetaData


<table>
<tr>
<th colspan="5">

Node or Field



</th>
<th>

Description



</th>
<th>

Cardinality



</th>
</tr>
<tr>
<td rowspan="5">

`BusinessPartnerRoleCategory`

Cardinality: 1..1



</td>
<td colspan="4">

`BusinessPartnerRoleCategoryCode`



</td>
<td>

For example: `BUP003` 



</td>
<td>

1..1



</td>
</tr>
<tr>
<td>

`Description`



</td>
<td colspan="3">

`languageCode`



</td>
<td>

For example: Employee



</td>
<td>

0..unbounded



</td>
</tr>
<tr>
<td rowspan="3">

`BusinessPartnerRole`

Cardinality: 1..1



</td>
<td colspan="3">

`BusinessPartnerRoleCode`



</td>
<td>

For example: `BBP005`



</td>
<td>

1..1



</td>
</tr>
<tr>
<td>

`Description`



</td>
<td colspan="2">

`languageCode`



</td>
<td>

 



</td>
<td>

0..unbounded



</td>
</tr>
<tr>
<td colspan="3">

`DefaultIndicator`



</td>
<td>

Can be *true* or *false*



</td>
<td>

 



</td>
</tr>
<tr>
<td rowspan="5">

`BusinessPartnerExternalIDCategory`

Cardinality: 0..1



</td>
<td colspan="4">

`BusinessPartnerExternalIDCategoryCode`



</td>
<td>

For example: `HCM030`



</td>
<td>

1..1



</td>
</tr>
<tr>
<td>

`Description`



</td>
<td colspan="3">

`languageCode`



</td>
<td>

 



</td>
<td>

0..unbounded



</td>
</tr>
<tr>
<td rowspan="3">

`BusinessPartnerExternalID`

Cardinality: 0..unbounded



</td>
<td colspan="3">

`BusinessPartnerExternalIDCode`



</td>
<td>

For example: `HCM030`



</td>
<td>

1..1



</td>
</tr>
<tr>
<td>

`Description`



</td>
<td colspan="2">

`languageCode`



</td>
<td>

 



</td>
<td>

0..unbounded



</td>
</tr>
<tr>
<td colspan="3">

`DefaultIndicator`



</td>
<td>

The value can be either*true* or *false*



</td>
<td>

 



</td>
</tr>
<tr>
<td rowspan="6">

`BusinessPartnerRelationshipCategory`

Cardinality: 0..1



</td>
<td colspan="4">

`BusinessPartnerRelationshipCategoryCode`



</td>
<td>

For example: `BUR025`



</td>
<td>

1..1



</td>
</tr>
<tr>
<td colspan="2">

`Description`



</td>
<td colspan="2">

`languageCode`



</td>
<td>

 



</td>
<td>

0..unbounded



</td>
</tr>
<tr>
<td rowspan="2" colspan="2">

`Partner1_BusinessPartnerCategory`

Cardinality: 0..unbounded



</td>
<td colspan="2">

`BusinessPartnerCategoryCode`



</td>
<td>

Can be:

-   2 - Organization

-   3 - Group




</td>
<td>

1..1



</td>
</tr>
<tr>
<td>

`Description`



</td>
<td>

`languageCode`



</td>
<td>

 



</td>
<td>

0..unbounded



</td>
</tr>
<tr>
<td rowspan="2" colspan="2">

`Partner2_BusinessPartnerCategory`

Cardinality: 0..unbounded



</td>
<td colspan="2">

`BusinessPartnerCategoryCode`



</td>
<td>

Can be:

-   1 - Person




</td>
<td>

1..1



</td>
</tr>
<tr>
<td>

`Description`



</td>
<td>

`languageCode`



</td>
<td>

 



</td>
<td>

0..unbounded



</td>
</tr>
<tr>
<td rowspan="3">

`NodeProperties`

Cardinality: 0..unbounded



</td>
<td colspan="4">

`NodePath`



</td>
<td>

For example: `BUSINESS_USER`



</td>
<td>

1..1



</td>
</tr>
<tr>
<td rowspan="2" colspan="2">

`NodeProperty`

Cardinality: 0..unbounded



</td>
<td colspan="2">

`NodePropertyCode`



</td>
<td rowspan="2">

Node property codes are:

-   01 - enabled

-   02 - disabled

-   03 - read only




</td>
<td>

1..1



</td>
</tr>
<tr>
<td>

`Description`



</td>
<td>

`languageCode`



</td>
<td>

0..unbounded



</td>
</tr>
<tr>
<td rowspan="4">

`FieldProperties`

0..unbounded



</td>
<td colspan="4">

`NodePath`



</td>
<td>

For example:

-   `BUSINESS_USER-USER-ROLE`
-   `BUSINESS_USER-USER-VALIDITY_PERIOD`
-   `BUSINESS_USER-USER_ASSIGNMENT`



</td>
<td>

1..1



</td>
</tr>
<tr>
<td colspan="4">

`Fieldname`



</td>
<td>

Name of a field.



</td>
<td>

1..1



</td>
</tr>
<tr>
<td rowspan="2" colspan="2">

`FieldProperty`

Cardinality: 0..unbounded



</td>
<td colspan="2">

`FieldPropertyCode`



</td>
<td>

Node property codes are:

-   01 - enabled

-   02 - disabled

-   03 - read only

-   04 - mandatory

-   05 - enabled, read only for update

-   06 - mandatory, read only for update




</td>
<td>

1..1



</td>
</tr>
<tr>
<td>

`Description`



</td>
<td>

`languageCode`



</td>
<td>

 



</td>
<td>

0..unbounded



</td>
</tr>
</table>

> ### Note:  
> To display more information about the service node on the SAP API Business Hub, select the operation.

