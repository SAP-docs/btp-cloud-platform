<!-- copye6aa861c1f5e4baa93cba69fa0565353 -->

# Retrieving Security Audit Log

With `SecurityAuditLog` you can retrieve the Security Audit Log by using the HTTP method `GET`.



<a name="copye6aa861c1f5e4baa93cba69fa0565353__section_jzq_tvt_zhb"/>

## Request

You have to include the following properties in the URL of the request:


<table>
<tr>
<th valign="top">

Property

</th>
<th valign="top">

Necessity

</th>
<th valign="top">

Comment

</th>
</tr>
<tr>
<td valign="top">

`eventID` 

</td>
<td valign="top">

Optional

</td>
<td valign="top">

Security Audit Log Event

-   String <= 3 characters

    Example: AU1, AU2




</td>
</tr>
<tr>
<td valign="top">

`log_tstmp` 

</td>
<td valign="top">

Optional

</td>
<td valign="top">

Timestamp of the security audit log event

-   String\($date-time\)

    Example: 2017-04-13T15:51:04Z




</td>
</tr>
<tr>
<td valign="top">

`slgmand` 

</td>
<td valign="top">

Optional

</td>
<td valign="top">

Client within the SAP System

-   String <=3 characters

    Example: 100




</td>
</tr>
<tr>
<td valign="top">

`sid` 

</td>
<td valign="top">

Optional

</td>
<td valign="top">

System ID

-   String <=3 characters
-   Example: YI3



</td>
</tr>
<tr>
<td valign="top">

`counter` 

</td>
<td valign="top">

Optional

</td>
<td valign="top">

Message counter

-   integer\($int16\)



</td>
</tr>
<tr>
<td valign="top">

`slgtc` 

</td>
<td valign="top">

Optional

</td>
<td valign="top">

Transaction Code

-   String <= 20 characters

    Example: VA01




</td>
</tr>
<tr>
<td valign="top">

`slgrepna` 

</td>
<td valign="top">

Optional

</td>
<td valign="top">

Program Name

-   String <= 40 characters

    Example: SAPMSSY8




</td>
</tr>
</table>



<a name="copye6aa861c1f5e4baa93cba69fa0565353__section_ztj_5wt_zhb"/>

## Response

The operation returns the Security Audit Log.



<a name="copye6aa861c1f5e4baa93cba69fa0565353__section_mwv_vwt_zhb"/>

## Examples



### Get events within a specific timeframe:

```
GET <host>/sap/opu/odata4/sap/rsau_log_api/srvd_a2x/sap/rsau_log_api/0001/SecurityAuditLog?$filter=(log_tstmp%20ge%202021-05-08T10%3A25%3A09Z%20and%20log_tstmp%20le%202021-05-09T10%3A25%3A09Z)
```



### Response

```
{
"eventID": "AU1",
"log_tstmp": "2021-05-08T10:26:22.740611Z",
"slgmand": "100",
"sid": "ABC",
"counter": 0,
"terminal_name": "",
"user_fullname": "Example Administrator",
"slgtc": "S000",
"slgrepna": "RSBTCRTE",
"rsau_text": "Logon successful (type=B, method=A)",
"UserDescription": "Example Administrator"
},
{
"eventID": "AU1",
"log_tstmp": "2021-05-08T10:28:22.924215Z",
"slgmand": "100",
"sid": "ABC",
"counter": 0,
"terminal_name": "",
"user_fullname": "Example Administrator",
"slgtc": "S000",
"slgrepna": "RSBTCRTE",
"rsau_text": "Logon successful (type=B, method=A)",
"UserDescription": "Example Administrator"
},

```

