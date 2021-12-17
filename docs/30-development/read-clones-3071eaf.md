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

<a name="loio3071eafb3eef498d8d0d74742645d7e9__table_ssp_js4_bpb"/>


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
<tr>
<td valign="top">

uuid



</td>
<td valign="top">

yes



</td>
<td valign="top">

string



</td>
<td valign="top">

ID of the job



</td>
<td valign="top">

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

<a name="loio3071eafb3eef498d8d0d74742645d7e9__table_sjb_vs4_bpb"/>


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

Read clone succesfully



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

