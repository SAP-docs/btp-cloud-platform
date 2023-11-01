<!-- loio425717b1f53941d7b90428fc53e51d14 -->

# Delete Branches

Delete a branch.



<a name="loio425717b1f53941d7b90428fc53e51d14__section_u2x_zs4_bpb"/>

## Request

**URI:** /sap/opu/odata/sap/MANAGE\_GIT\_REPOSITORY/Branches

**Operation Type:** CRUD

**HTTP Method:**DELETE



### Request Headers



### Request Parameters

****


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Required

</th>
<th valign="top">

Data Type

</th>
<th valign="top">

Description

</th>
<th valign="top">

Parameter Type

</th>
</tr>
<tr>
<td valign="top">

sc\_name

</td>
<td valign="top">

yes

</td>
<td valign="top">

string

</td>
<td valign="top">

name of the software component

</td>
<td valign="top">

query string

</td>
</tr>
<tr>
<td valign="top">

branch\_name

</td>
<td valign="top">

yes

</td>
<td valign="top">

string

</td>
<td valign="top">

name of the branch

</td>
<td valign="top">

query string

</td>
</tr>
</table>



### Request Example

> ### Sample Code:  
> ```
> DELETE /sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Branches(branch_name='my-to-be-deleted-branch',sc_name='/DMO/GIT_REPOSITORY') HTTP/1.1
> Host: host.com
> Authentication: basicAuthentication
> Accept: application/json
> 
> ```



<a name="loio425717b1f53941d7b90428fc53e51d14__section_tbd_zq4_bpb"/>

## Response



### Response Headers

> ### Sample Code:  
> ```
> HTTP/1.1 204 No Content
> ```



### Response Status and Error Codes

****


<table>
<tr>
<th valign="top">

Code

</th>
<th valign="top">

Reason

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

204

</td>
<td valign="top">

No content

</td>
<td valign="top">

Branch was deleted successfully

</td>
</tr>
<tr>
<td valign="top">

400

</td>
<td valign="top">

Bad Request

</td>
<td valign="top">

Could not delete branch due to the values passed in the request body.

</td>
</tr>
</table>

