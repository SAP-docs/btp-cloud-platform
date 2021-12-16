<!-- loio77fef2fb104b4b1795e2e6cee790e8b8 -->

# Error Response Format

Describes the response format for the errors from the SAP Cloud Management service for SAP BTP.

Standard HTTP codes are used to indicate successful execution or if errors occur. The response includes additional information about the error, including an application error code and human readable error description. This example represents a common error response resulting from a failed API request.

```
HTTP/1.1 400 Bad Request
{
  "error": {
    "code": 11000,
    "message": "Request payload is invalid",
    "target": "/accounts/v1/subaccounts/125e2778-e457-4c24-9db8-e3e10a3a0ed5",
    "details": [
      {
        "code": 11001,
        "message": "description: length must be between 0 and 255"
      }
    ]
  }
}
```


<table>
<tr>
<th valign="top">

Parameter



</th>
<th valign="top">

Description



</th>
<th valign="top">

Type



</th>
</tr>
<tr>
<td valign="top">

`error.code`



</td>
<td valign="top">

A unique application error code. Common values are listed below.



</td>
<td valign="top">

Number



</td>
</tr>
<tr>
<td valign="top">

`error.message`



</td>
<td valign="top">

A description of the error.



</td>
<td valign="top">

String



</td>
</tr>
<tr>
<td valign="top">

`error.target`



</td>
<td valign="top">

The resource URL of the request.



</td>
<td valign="top">

String



</td>
</tr>
<tr>
<td valign="top">

`error.details`



</td>
<td valign="top">

An array of additional error codes and descriptions with further details about the error and its root cause. If this field exists, the array will contain at least one element.



</td>
<td valign="top">

Array



</td>
</tr>
</table>

An application error code is not necessarily coupled with a specific HTTP status code.



<a name="loio77fef2fb104b4b1795e2e6cee790e8b8__section_gh2_3gf_53b"/>

## Error Codes

Provides a list of error codes and the details of the errors.


<table>
<tr>
<th valign="top">

Error Code



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

10XXX



</td>
<td valign="top">

Server errors



</td>
</tr>
<tr>
<td valign="top">

11XXX



</td>
<td valign="top">

General request errors



</td>
</tr>
<tr>
<td valign="top">

12XXX



</td>
<td valign="top">

General operations failures



</td>
</tr>
<tr>
<td valign="top">

2XXXX



</td>
<td valign="top">

Accounts service errors



</td>
</tr>
<tr>
<td valign="top">

3XXXX



</td>
<td valign="top">

Entitlements service errors



</td>
</tr>
<tr>
<td valign="top">

40XXX



</td>
<td valign="top">

Tenants operations failures



</td>
</tr>
<tr>
<td valign="top">

41XXX



</td>
<td valign="top">

Environment instances operations failures



</td>
</tr>
<tr>
<td valign="top">

42XXX



</td>
<td valign="top">

Provisioning service errors



</td>
</tr>
<tr>
<td valign="top">

5XXXX



</td>
<td valign="top">

Service Management service proxy errors



</td>
</tr>
<tr>
<td valign="top">

6XXXX



</td>
<td valign="top">

Order Processing service errors



</td>
</tr>
<tr>
<td valign="top">

7XXXX



</td>
<td valign="top">

CLI backend errors



</td>
</tr>
<tr>
<td valign="top">

8XXXX



</td>
<td valign="top">

Asynchronous jobs failures



</td>
</tr>
<tr>
<td valign="top">

9XXXX



</td>
<td valign="top">

SaaS Provisioning service errors



</td>
</tr>
<tr>
<td valign="top">

10XXXX



</td>
<td valign="top">

Events service errors



</td>
</tr>
</table>

