<!-- loio214a3f1fd2b34bed9f9a627ffeaa98c3 -->

# Create Clone

Create a clone job.



<a name="loio214a3f1fd2b34bed9f9a627ffeaa98c3__section_u2x_zs4_bpb"/>

## Request

**URI:** /sap/opu/odata/sap/MANAGE\_GIT\_REPOSITORY/Clones

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

Contentt-Type

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

Request body

</td>
</tr>
<tr>
<td valign="top">

branch\_name

</td>
<td valign="top">

no

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

commit\_id

</td>
<td valign="top">

no

</td>
<td valign="top">

string

</td>
<td valign="top">

commit ID

</td>
<td valign="top">

Request body

</td>
</tr>
</table>



### Request Example

> ### Sample Code:  
> ```
> POST/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Clones HTTP/1.1
> Host: host.com
> Authentication: basicAuthentication
> X-csrf-token: xCsrfToken
> Content-Type: application/json
> Accept: application/json
>  
> {
>         "sc_name" : "/DMO/GIT_REPOSITORY"
>         "branch_name": "main"
> }
> 
> ```



<a name="loio214a3f1fd2b34bed9f9a627ffeaa98c3__section_tbd_zq4_bpb"/>

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

201

</td>
<td valign="top">

Created

</td>
<td valign="top">

Created a clone job

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

Could not read the clone job. Please check the parameters.

</td>
</tr>
</table>



### Request Payload Example

> ### Sample Code:  
> ```
> {
>     "d": {
>             {
>                 "__metadata": {
>                     "id": "host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Clones(uuid=guid'02ceab7d-ff04-1eda-b1ea-eb7fdbf28bc4',sc_name='ZHM_INITIAL_TEST',branch_name='')",
>                     "uri": "host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Clones(uuid=guid'02ceab7d-ff04-1eda-b1ea-eb7fdbf28bc4',sc_name='ZHM_INITIAL_TEST',branch_name='')",
>                     "type": "cds_sd_a4c_a2g_gha_sc_web_api.ClonesType"
>                 },
>                 "uuid": "02ceab7d-ff04-1eda-b1ea-eb7fdbf28bc4",
>                 "sc_name": "/DMO/GIT_REPOSITORY",
>                 "branch_name": "",
>                 "import_type": "Clone",
>                 "namespace": "",
>                 "status": "S",
>                 "status_descr": "Success",
>                 "criticality": 3,
>                 "user_name": "administrator@example.com",
>                 "start_time": "/Date(1594898863000+0000)/",
>                 "change_time": "/Date(1594898891000+0000)/"
>             }
>        
>     }
> }
> 
> ```

