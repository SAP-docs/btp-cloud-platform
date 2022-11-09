<!-- loio6771f668a83d463395c54a5c36319819 -->

# Read Entities from Tag

Read entities from tags.



<a name="loio6771f668a83d463395c54a5c36319819__section_y3t_354_bpb"/>

## Request

**URI:** /sap/opu/odata/sap/MANAGE\_GIT\_REPOSITORY/Tags

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

No parameters.



### Request Example

> ### Sample Code:  
> ```
> GET /sap/opu/odata/sap/Tags 
> 
> Host: host.com
> Authentication: basicAuthentication
> Accept: application/json
> 
> ```



<a name="loio6771f668a83d463395c54a5c36319819__section_tbd_zq4_bpb"/>

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

Branch was read successfully



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

Could not read branch; software component or branch may not exist..



</td>
</tr>
</table>



### Request Payload Example

> ### Sample Code:  
> ```
> 
> ```

