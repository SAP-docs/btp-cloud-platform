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
<th valign="top">

Header



</th>
<th valign="top">

Required



</th>
<th valign="top">

Values



</th>
</tr>
<tr>
<td valign="top">

Accept



</td>
<td valign="top">

no



</td>
<td valign="top">

application/json

application/xml



</td>
</tr>
<tr>
<td valign="top">

Content-Type



</td>
<td valign="top">

no



</td>
<td valign="top">

application/json

application/xml



</td>
</tr>
<tr>
<td valign="top">

x-csrf-token



</td>
<td valign="top">

yes



</td>
<td valign="top">

Value of x-csrf-token



</td>
</tr>
</table>



### Request Parameters

<a name="loioa9ce22e685144dc88894067ead3b2778__table_ssp_js4_bpb"/>


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

Request body



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

Request body



</td>
</tr>
<tr>
<td valign="top">

derived\_from



</td>
<td valign="top">

yes



</td>
<td valign="top">

string



</td>
<td valign="top">

name of the original branch form which the branch was derived



</td>
<td valign="top">

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

201



</td>
<td valign="top">

Created



</td>
<td valign="top">

Branch was created successfully



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

