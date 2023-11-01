<!-- loioe8e40c2d3fd1431a86c7bf324d70ba7d -->

# Read Branches

Read one or multiple branches .



<a name="loioe8e40c2d3fd1431a86c7bf324d70ba7d__section_y3t_354_bpb"/>

## Request

**URI:** /sap/opu/odata/sap/MANAGE\_GIT\_REPOSITORY/Branches

**Operation Type:** CRUD

**HTTP Method:**GET



### Request Headers

****


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

x-csrf-token

</td>
<td valign="top">

no

</td>
<td valign="top">

fetch

</td>
</tr>
</table>



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

****


<table>
<tr>
<th valign="top">

Header

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

x-csrf-token

</td>
<td valign="top">

Token, which can be used for POST requests

</td>
</tr>
</table>



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

200

</td>
<td valign="top">

OK

</td>
<td valign="top">

Branch was read successfully

</td>
</tr>
<tr>
<td valign="top">

404

</td>
<td valign="top">

Not foumd

</td>
<td valign="top">

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

