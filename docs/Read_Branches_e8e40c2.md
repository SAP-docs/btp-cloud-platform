<!-- loioe8e40c2d3fd1431a86c7bf324d70ba7d -->

# Read Branches

Read one or multiple branches .



<a name="loioe8e40c2d3fd1431a86c7bf324d70ba7d__section_y3t_354_bpb"/>

## Request

**URI:** /sap/opu/odata/sap/MANAGE\_GIT\_REPOSITORY/Branches

**Operation Type:** CRUD

**HTTP Method:**GET



### Request Headers

<a name="loioe8e40c2d3fd1431a86c7bf324d70ba7d__table_byq_jr4_bpb"/>


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

x-csrf-token



</td>
<td>

no



</td>
<td>

fetch



</td>
</tr>
</table>



### Request Parameters

<a name="loioe8e40c2d3fd1431a86c7bf324d70ba7d__table_ssp_js4_bpb"/>


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
> GET /sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Branches(branch_name=’newBranch’,sc_name=’/DMO/GIT_REPOSITORY’ HTTP/1.1
> 
> Host: host.com
> Authentication: basicAuthentication
> Accept: application/json
> 
> ```



<a name="loioe8e40c2d3fd1431a86c7bf324d70ba7d__section_tbd_zq4_bpb"/>

## Response



### Response Headers

<a name="loioe8e40c2d3fd1431a86c7bf324d70ba7d__table_rlc_ss4_bpb"/>


<table>
<tr>
<th>

Header



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

x-csrf-token



</td>
<td>

Token, which can be used for POST requests



</td>
</tr>
</table>



### Response Status and Error Codes

<a name="loioe8e40c2d3fd1431a86c7bf324d70ba7d__table_sjb_vs4_bpb"/>


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

200



</td>
<td>

OK



</td>
<td>

Branch was read successfully



</td>
</tr>
<tr>
<td>

404



</td>
<td>

Not foumd



</td>
<td>

Could not read branch; software component or branch may not exist..



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
> 		"derived_from": "main",
> 		"created_by": "CC0000000001",
> 		"created_on": "/Date(1584967657000+0000)/",
> 		"last_commit_on": "/Date(1584634658000+0000)/"
> 	}
> }
> 
> ```

