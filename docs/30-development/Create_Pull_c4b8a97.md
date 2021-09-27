<!-- loioc4b8a978ff4a4953bad243599e5e4892 -->

# Create Pull

Create a pull job.



<a name="loioc4b8a978ff4a4953bad243599e5e4892__section_u2x_zs4_bpb"/>

## Request

**URI:** /sap/opu/odata/sap/MANAGE\_GIT\_REPOSITORY/Pull

**Operation Type:** CRUD

**HTTP Method:**POST



### Request Headers

<a name="loioc4b8a978ff4a4953bad243599e5e4892__table_byq_jr4_bpb"/>


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

Content-Type



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

yes



</td>
<td>

Value of x-csrf-token



</td>
</tr>
</table>



### Request Parameters

<a name="loioc4b8a978ff4a4953bad243599e5e4892__table_ssp_js4_bpb"/>


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
> POST/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Pull HTTP/1.1
> Host: host.com
> Authentication: basicAuthentication
> X-csrf-token: xCsrfToken
> Content-Type: application/json
> Accept: application/json
> 
> {
> 	“sc_name” : “/DMO/GIT_REPOSITORY”
> }
> 
> ```



<a name="loioc4b8a978ff4a4953bad243599e5e4892__section_tbd_zq4_bpb"/>

## Response



### Response Status and Error Codes

<a name="loioc4b8a978ff4a4953bad243599e5e4892__table_sjb_vs4_bpb"/>


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

Created a pull job



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

Could not read the pull job. Please check the parameters.



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

