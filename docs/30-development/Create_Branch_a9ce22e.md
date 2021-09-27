<!-- loioa9ce22e685144dc88894067ead3b2778 -->

# Create Branch

Create a new branch.



<a name="loioa9ce22e685144dc88894067ead3b2778__section_u2x_zs4_bpb"/>

## Request

**URI:** /sap/opu/odata/sap/MANAGE\_GIT\_REPOSITORY/Branches

**Operation Type:** CRUD

**HTTP Method:**POST



### Request Headers

<a name="loioa9ce22e685144dc88894067ead3b2778__table_byq_jr4_bpb"/>


<table>
<tr>
<th>

Header



</th>
<th>

Required



</th>
<th>

Values



</th>
</tr>
<tr>
<td>

Accept



</td>
<td>

no



</td>
<td>

application/json

application/xml



</td>
</tr>
<tr>
<td>

Content-Type



</td>
<td>

no



</td>
<td>

application/json

application/xml



</td>
</tr>
<tr>
<td>

x-csrf-token



</td>
<td>

yes



</td>
<td>

Value of x-csrf-token



</td>
</tr>
</table>



### Request Parameters

<a name="loioa9ce22e685144dc88894067ead3b2778__table_ssp_js4_bpb"/>


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

Request body



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

Request body



</td>
</tr>
<tr>
<td>

derived\_from



</td>
<td>

yes



</td>
<td>

string



</td>
<td>

name of the original branch form which the branch was derived



</td>
<td>

Request body



</td>
</tr>
</table>



### Request Example

> ### Sample Code:  
> ```
> POST/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Branches HTTP/1.1
> Host: host.com
> Authentication: basicAuthentication
> X-csrf-token: xCsrfToken
> Content-Type: application/json
> Accept: application/json
> 	{
> "sc_name" : "/DMO/GIT_REPOSITORY",
> "derived_from" : "main",
> "branch_name" : "newBranch"
> 	}
> 
> ```



<a name="loioa9ce22e685144dc88894067ead3b2778__section_tbd_zq4_bpb"/>

## Response



### Response Status and Error Codes

<a name="loioa9ce22e685144dc88894067ead3b2778__table_sjb_vs4_bpb"/>


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

201



</td>
<td>

Created



</td>
<td>

Branch was created successfully



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

Could not create a branch due to the values passed in the request body.



</td>
</tr>
</table>



### Request Payload Example

> ### Sample Code:  
> ```
> {
> 	"d": {
> 		"__metadata": {
> 			"id": "https://host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Branches(branch_name='newBranch',sc_name='/DMO/GIT_REPOSITORY')",
> 			"uri": "https://host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Branches(branch_name='newBranch',sc_name='/DMO/GIT_REPOSITORY')",
> 			"type": "cds_sd_a4c_a2g_gha_sc_web_api.BranchesType"
> 		},
> 		"branch_name": "newBranch",
> 		"sc_name": "/DMO/GIT_REPOSITORY",
> 		"is_active": false,
> 		"criticality": 0,
> 		"derived_from": "master",
> 		"created_by": "CC0000000001",
> 		"created_on": "/Date(1584967657000+0000)/",
> 		"last_commit_on": "/Date(1584634658000+0000)/"
> 	}
> }
> 
> ```

