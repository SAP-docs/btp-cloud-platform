<!-- loio5de83f9069454973af95d87984cfd5f0 -->

# Read Pull

Read a pull jon.



<a name="loio5de83f9069454973af95d87984cfd5f0__section_y3t_354_bpb"/>

## Request

**URI:** /sap/opu/odata/sap/MANAGE\_GIT\_REPOSITORY/Pull

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

Read pull succesfully

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

