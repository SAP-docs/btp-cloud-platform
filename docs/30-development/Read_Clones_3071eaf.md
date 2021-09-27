<!-- loio3071eafb3eef498d8d0d74742645d7e9 -->

# Read Clones

Read a clone job. The entity is only available after the job has finished. To track the status of the job, you can use the GET /Pull\(guid’UUID’\) request.



## Request

**URI:** /sap/opu/odata/sap/MANAGE\_GIT\_REPOSITORY/Clones

**Operation Type:** CRUD

**HTTP Method:**GET



### Request Headers

<a name="loio3071eafb3eef498d8d0d74742645d7e9__table_byq_jr4_bpb"/>


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

<a name="loio3071eafb3eef498d8d0d74742645d7e9__table_ssp_js4_bpb"/>


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
<tr>
<td>

uuid



</td>
<td>

yes



</td>
<td>

string



</td>
<td>

ID of the job



</td>
<td>

query string



</td>
</tr>
</table>



### Request Example

> ### Sample Code:  
> ```
> GET /sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Clones(uuid=02409ac8-dc6a-1edb-908e-31e4b44596d4’,branch_name=’main’,sc_name=’/DMO/GIT_REPOSITORY’) HTTP/1.1
> 
> Host: host.com
> Authentication: basicAuthentication
> Accept: application/json
> 
> ```



<a name="loio3071eafb3eef498d8d0d74742645d7e9__section_tbd_zq4_bpb"/>

## Response



### Response Headers

<a name="loio3071eafb3eef498d8d0d74742645d7e9__table_rlc_ss4_bpb"/>


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

<a name="loio3071eafb3eef498d8d0d74742645d7e9__table_sjb_vs4_bpb"/>


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

Read clone succesfully



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

Could not read the clone entity. Please check the parameters.



</td>
</tr>
</table>



### Request Payload Example

> ### Sample Code:  
> ```
> {
>     "d": {
>         "__metadata": {
>             "id": "https://4c7c0f11-da7c-43cf-b60c-e6e308144458.abap.stagingaws.hanavlab.ondemand.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Clones(uuid=guid'02409ac8-dc6a-1edb-908e-31e4b44596d4',sc_name='%2FDMO%2F GIT_REPOSITORY,branch_name='main')",
>             "uri": "https://4c7c0f11-da7c-43cf-b60c-e6e308144458.abap.stagingaws.hanavlab.ondemand.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Clones(uuid=guid'02409ac8-dc6a-1edb-908e-31e4b44596d4',sc_name='%2FDMO%2F GIT_REPOSITORY,branch_name='main')",
>             "type": "cds_sd_a4c_a2g_gha_sc_web_api.ClonesType"
>         },
>         "uuid": "02409ac8-dc6a-1edb-908e-31e4b44596d4",
>         "sc_name": "/DMO/GIT_REPOSITORY",
>         "branch_name": "main",
>         "commit_id": "",
>         "import_type": "Clone",
>         "namespace": "",
>         "status": "S",
>         "status_descr": "Success",
>         "criticality": 3,
>         "user_name": "CC0000000001",
>         "start_time": "/Date(1608214205000+0000)/",
>         "change_time": "/Date(1608214243000+0000)/"
>     }
> }
> 
> ```

