<!-- loio269f4efd61834c419517df223dcbc035 -->

# Retrieving Read Access Log

With `Read Access Log` you can retrieve the Read Access Log by using the HTTP method `GET`.



<a name="loio269f4efd61834c419517df223dcbc035__section_zgh_vbj_12c"/>

## Request

You have to include the following properties in the URL of the request:

****


<table>
<tr>
<th valign="top">

Property

</th>
<th valign="top">

Property

</th>
<th valign="top">

Comment

</th>
</tr>
<tr>
<td valign="top">

`LogID` 

</td>
<td valign="top">

Optional

</td>
<td valign="top">

Unique identfier of each logt

-   String\($uuid\)

    Example: `01234567-89ab-cdef-0123-456789abcdef`




</td>
</tr>
<tr>
<td valign="top">

`LogTimestamp` 

</td>
<td valign="top">

Optional

</td>
<td valign="top">

Timestamp of the read access log event

-   String\($date-time\)

    Example: `2017-04-13T15:51:04`




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

    Example: YI3




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

-   String <=20 characters

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



<a name="loio269f4efd61834c419517df223dcbc035__section_cd2_dpw_12c"/>

## Response

The operation returns the Read Access Log.



<a name="loio269f4efd61834c419517df223dcbc035__section_wfv_fpw_12c"/>

## Example



### Get events within a specific timeframe:

```
GET <host>/sap/opu/odata4/sap/rsau_log_api/srvd_a2x/sap/rsau_log_api/0001/ReadAccessLog?$filter=(log_tstmp%20ge%202021-05-08T10%3A25%3A09Z%20and%20log_tstmp%20le%202021-05-09T10%3A25%3A09Z)
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

