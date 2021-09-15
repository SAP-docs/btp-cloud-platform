<!-- loio5de83f9069454973af95d87984cfd5f0 -->

# Read Pull

Read a pull jon.



<a name="loio5de83f9069454973af95d87984cfd5f0__section_y3t_354_bpb"/>

## Request

**URI:** /sap/opu/odata/sap/MANAGE\_GIT\_REPOSITORY/Pull

**Operation Type:** CRUD

**HTTP Method:**GET



### Request Headers

<a name="loio5de83f9069454973af95d87984cfd5f0__table_byq_jr4_bpb"/>


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

<a name="loio5de83f9069454973af95d87984cfd5f0__table_ssp_js4_bpb"/>


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
> GET /sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Pull(uuid=02409ac8-dc6a-1edb-908e-31e4b44596d4’) HTTP/1.1
> 
> Host: host.com
> Authentication: basicAuthentication
> Accept: application/json
> 
> ```



<a name="loio5de83f9069454973af95d87984cfd5f0__section_tbd_zq4_bpb"/>

## Response



### Response Headers

<a name="loio5de83f9069454973af95d87984cfd5f0__table_rlc_ss4_bpb"/>


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

<a name="loio5de83f9069454973af95d87984cfd5f0__table_sjb_vs4_bpb"/>


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

Read pull succesfully



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

Could not find a pull entity with the specified UUID.



</td>
</tr>
</table>



### Request Payload Example

> ### Sample Code:  
> ```
> {
>     "d": {
>         "__metadata": {
>             "id": "https://host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Pull(guid’UUID’)", "uri": "https://host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Pull(guid’UUID’)", "type": "cds_sd_a4c_a2g_gha_sc_web_api.PullType"
>         }
>         ,
>         "uuid": "UUID ",
>         "sc_name": "/DMO/GIT_REPOSITORY ",
>         "namespace": "",
>         "status": "R",
>         "status_descr": "Running",
>         "start_time": "/Date(1571227437000+0000)/",
>         "change_time": "/Date(1571227472000+0000)/",
>         "criticality": 2,
>         "user_name": "CC0000000001",
>         "to_Execution_log": {
>             "__deferred": {
>                 "uri": "https://host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Pull(guid’UUID’)/to_Execution_log"
>             }
>         }
>         ,
>         "to_Transport_log": {
>             "__deferred": {
>                 "uri": "https://host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Pull(guid’UUID’)/to_Transport_log"
>             }
>         }
>     }
> }
> 
> ```

