<!-- loio069b979e4c304bf69ac8bdf034d3ee22 -->

# Checkout Branches

Checkout a branch.



<a name="loio069b979e4c304bf69ac8bdf034d3ee22__section_u2x_zs4_bpb"/>

## Request

**URI:** /sap/opu/odata/sap/MANAGE\_GIT\_REPOSITORY/Branches

**Operation Type:** CRUD

**HTTP Method:**POST



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

yes

</td>
<td valign="top">

Value of x-csrf-token

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
> POST/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/checkout_branch?branch_name='newBranch'&sc_name="'/DMO/GIT_REPOSITORY' HTTP/1.1
> 
> Host: host.com
> Authentication: basicAuthentication
> X-csrf-token: xCsrfToken
> Content-Type: application/json
> Accept: application/json
> 
> ```



<a name="loio069b979e4c304bf69ac8bdf034d3ee22__section_tbd_zq4_bpb"/>

## Response



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

Branch was checked out successfully

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

Could not check out a branch due to the values passed in the request body

</td>
</tr>
</table>



### Response Payload Example

> ### Sample Code:  
> ```
> {
> 
> 	"d": {
> 		"__metadata": {
> 			"id": "https://host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Pull(guid’UUID’)", 
> 			"uri": "https://host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Pull(guid’UUID’)", 
> 			"type": "cds_sd_a4c_a2g_gha_sc_web_api.PullType"
> 		},
> 		"uuid": "UUID ",
> 		"sc_name": "/DMO/GIT_REPOSITORY ",
> 		"namespace": "",
> 		"status": "R",
> 		"status_descr": "Running",
> 		"start_time": "/Date(1571227437000+0000)/",
> 		"change_time": "/Date(1571227472000+0000)/",
> 		"criticality": 2,
> 		"user_name": "CC0000000001",
> 		"to_Execution_log": {
> 			"__deferred": {
> 				"uri": "https://host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Pull(guid’UUID’)/to_Execution_log"
> 			}
> 		},
> 
> 		"to_Transport_log": {
> 			"__deferred": {
> 				"uri": "https://host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Pull(guid’UUID’)/to_Transport_log"
> 			}
> 		}
> 	}
> }
> 
> ```

