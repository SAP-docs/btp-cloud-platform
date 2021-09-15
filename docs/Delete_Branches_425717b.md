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

<a name="loio425717b1f53941d7b90428fc53e51d14__table_ssp_js4_bpb"/>


<table>
<tr>
<th>

Parameter



</th>
<th>

Required



</th>
<th>

Data Type



</th>
<th>

Description



</th>
<th>

Parameter Type



</th>
</tr>
<tr>
<td>

sc\_name



</td>
<td>

yes



</td>
<td>

string



</td>
<td>

name of the software component



</td>
<td>

query string



</td>
</tr>
<tr>
<td>

branch\_name



</td>
<td>

yes



</td>
<td>

string



</td>
<td>

name of the branch



</td>
<td>

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

<a name="loio425717b1f53941d7b90428fc53e51d14__table_sjb_vs4_bpb"/>


<table>
<tr>
<th>

Code



</th>
<th>

Reason



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

204



</td>
<td>

No content



</td>
<td>

Branch was deleted successfully



</td>
</tr>
<tr>
<td>

400



</td>
<td>

Bad Request



</td>
<td>

Could not delete branch due to the values passed in the request body.



</td>
</tr>
</table>

