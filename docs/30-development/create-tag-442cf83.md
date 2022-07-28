<!-- loio442cf830e7a64287a31a15ea3b743cec -->

# Create Tag

Create a new tag.



<a name="loio442cf830e7a64287a31a15ea3b743cec__section_u2x_zs4_bpb"/>

## Request

**URI:** /sap/opu/odata/sap/MANAGE\_GIT\_REPOSITORY/Tags

**Operation Type:** CRUD

**HTTP Method:**POST



### Request Headers


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

No parameters.



### Request Body

<a name="loio442cf830e7a64287a31a15ea3b743cec__table_yv3_yb5_kqb"/>


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

commit\_id



</td>
<td valign="top">

yes



</td>
<td valign="top">

string



</td>
<td valign="top">

long commit id



</td>
<td valign="top">

Request body



</td>
</tr>
<tr>
<td valign="top">

tag\_name



</td>
<td valign="top">

yes



</td>
<td valign="top">

string



</td>
<td valign="top">

name of the tag



</td>
<td valign="top">

Request body



</td>
</tr>
</table>

> ### Sample Code:  
> ```
> POST/sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Tags
> HTTP/1.1
> Host: host.com
> Authentication: basicAuthentication
> X-csrf-token: xCsrfToken
> Content-Type: application/json
> Accept: application/json
> 	{
>   "sc_name": "string",
>   "commit_id": "string",
>   "tag_name": "string",
>   "tag_description": "string",
>   "tag_created_by": "string",
>   "tag_created_on": "/Date(1492098664000)/",
>   "short_commit_id": "string",
>   "message": "string",
>   "author": "string",
>   "author_mail": "string"
> }
> 
> 
> ```



<a name="loio442cf830e7a64287a31a15ea3b743cec__section_tbd_zq4_bpb"/>

## Response



### Response Status and Error Codes

<a name="loio442cf830e7a64287a31a15ea3b743cec__table_sjb_vs4_bpb"/>


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

Tag was created successfully



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

Could not create a tag due to the values passed in the request body.



</td>
</tr>
</table>



### Request Payload Example

> ### Sample Code:  
> ```
> 
> ```

