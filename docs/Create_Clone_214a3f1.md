<!-- loio214a3f1fd2b34bed9f9a627ffeaa98c3 -->

# Create Clone

Create a clone job.



<a name="loio214a3f1fd2b34bed9f9a627ffeaa98c3__section_u2x_zs4_bpb"/>

## Request

**URI:** /sap/opu/odata/sap/MANAGE\_GIT\_REPOSITORY/Clones

**Operation Type:** CRUD

**HTTP Method:**POST



### Request Headers

<a name="loio214a3f1fd2b34bed9f9a627ffeaa98c3__table_byq_jr4_bpb"/>


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

Contentt-Type



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

<a name="loio214a3f1fd2b34bed9f9a627ffeaa98c3__table_ssp_js4_bpb"/>


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

no



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

commit\_id



</td>
<td>

no



</td>
<td>

string



</td>
<td>

commit ID



</td>
<td>

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

<a name="loio214a3f1fd2b34bed9f9a627ffeaa98c3__table_sjb_vs4_bpb"/>


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

Created a clone job



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

