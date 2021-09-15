<!-- loio4446ee47a04648668f1a4a604d08b0d2 -->

# Read Transport Log



<a name="loio4446ee47a04648668f1a4a604d08b0d2__section_y3t_354_bpb"/>

## Request

**URI:** /sap/opu/odata/sap/MANAGE\_GIT\_REPOSITORY/to\_Transport\_log

**Operation Type:** CRUD

**HTTP Method:**GET



### Request Headers

<a name="loio4446ee47a04648668f1a4a604d08b0d2__table_byq_jr4_bpb"/>


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

<a name="loio4446ee47a04648668f1a4a604d08b0d2__table_ssp_js4_bpb"/>


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
> GET /sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Pull(uuid=02409ac8-dc6a-1edb-908e-31e4b44596d4’)/to_Transport_log HTTP/1.1
> 
> Host: host.com
> Authentication: basicAuthentication
> Accept: application/json
> 
> ```



<a name="loio4446ee47a04648668f1a4a604d08b0d2__section_tbd_zq4_bpb"/>

## Response



### Response Headers

<a name="loio4446ee47a04648668f1a4a604d08b0d2__table_rlc_ss4_bpb"/>


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

<a name="loio4446ee47a04648668f1a4a604d08b0d2__table_sjb_vs4_bpb"/>


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

Read transport log succesfully



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

Could not find a transport log with the specified UUID.



</td>
</tr>
</table>



### Request Payload Example

> ### Sample Code:  
> ```
> { {
>     "d": {
>         "results": [ {
>             "__metadata": {
>                 "id": "host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/ExecutionLogs(index_no=1m,uuid=guid'UUID')", "uri": "host.com/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/ExecutionLogs(index_no=1m,uuid=guid'UUID')", "type": "cds_sd_a4c_a2g_gha_sc_web_api.ExecutionLogsType"
>             }
>             ,
>             "index_no": "1",
>             "uuid": "UUID",
>             "type": "Information",
>             "descr": "Step X: Message",
>             "timestamp": "/Date(1571227438000+0000)/",
>             "criticality": 0,
>         }
>         ]
>     }
> }
> 
> ```

