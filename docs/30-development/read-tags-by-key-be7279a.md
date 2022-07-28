<!-- loiobe7279a64db440e7844e1010ff9826cc -->

# Read Tags by Key

Read entities from tags.



<a name="loiobe7279a64db440e7844e1010ff9826cc__section_y3t_354_bpb"/>

## Request

**URI:** : /sap/opu/odata/sap/MANAGE\_GIT\_REPOSITORY/Tags\(sc\_name='\{sc\_name\}',commit\_id='\{commit\_id\}',tag\_name='\{tag\_name\}'\)

**Operation Type:** CRUD

**HTTP Method:**GET



### Request Headers

<a name="loiobe7279a64db440e7844e1010ff9826cc__table_byq_jr4_bpb"/>


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

<a name="loiobe7279a64db440e7844e1010ff9826cc__table_ssp_js4_bpb"/>


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

query string



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

query string



</td>
</tr>
</table>



### Request Example

> ### Sample Code:  
> ```
> GET /sap/opu/odata/sap/MANAGE_GIT_REPOSITORY/Tags(sc_name='{sc_name}',commit_id='{commit_id}',tag_name='{tag_name}') 
> HTTP/1.1
> Host: host.com
> Authentication: basicAuthentication
> Accept: application/json
> 
> ```



<a name="loiobe7279a64db440e7844e1010ff9826cc__section_tbd_zq4_bpb"/>

## Response



### Response Headers

<a name="loiobe7279a64db440e7844e1010ff9826cc__table_rlc_ss4_bpb"/>


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

<a name="loiobe7279a64db440e7844e1010ff9826cc__table_sjb_vs4_bpb"/>


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

Tag was read successfully



</td>
</tr>
<tr>
<td valign="top">

404



</td>
<td valign="top">

Not foumd



</td>
<td valign="top">

Could not read tag; software component or commit id may not exist..



</td>
</tr>
</table>



### Request Payload Example

> ### Sample Code:  
> ```
> 
> ```

