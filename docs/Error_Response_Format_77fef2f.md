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
<th>

Parameter



</th>
<th>

Description



</th>
<th>

Type



</th>
</tr>
<tr>
<td>

`error.code`



</td>
<td>

A unique application error code. Common values are listed below.



</td>
<td>

Number



</td>
</tr>
<tr>
<td>

`error.message`



</td>
<td>

A description of the error.



</td>
<td>

String



</td>
</tr>
<tr>
<td>

`error.target`



</td>
<td>

The resource URL of the request.



</td>
<td>

String



</td>
</tr>
<tr>
<td>

`error.details`



</td>
<td>

An array of additional error codes and descriptions with further details about the error and its root cause. If this field exists, the array will contain at least one element.



</td>
<td>

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
<th>

Error Code



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

10XXX



</td>
<td>

Server errors



</td>
</tr>
<tr>
<td>

11XXX



</td>
<td>

General request errors



</td>
</tr>
<tr>
<td>

12XXX



</td>
<td>

General operations failures



</td>
</tr>
<tr>
<td>

2XXXX



</td>
<td>

Accounts service errors



</td>
</tr>
<tr>
<td>

3XXXX



</td>
<td>

Entitlements service errors



</td>
</tr>
<tr>
<td>

40XXX



</td>
<td>

Tenants operations failures



</td>
</tr>
<tr>
<td>

41XXX



</td>
<td>

Environment instances operations failures



</td>
</tr>
<tr>
<td>

42XXX



</td>
<td>

Provisioning service errors



</td>
</tr>
<tr>
<td>

5XXXX



</td>
<td>

Service Management service proxy errors



</td>
</tr>
<tr>
<td>

6XXXX



</td>
<td>

Order Processing service errors



</td>
</tr>
<tr>
<td>

7XXXX



</td>
<td>

CLI backend errors



</td>
</tr>
<tr>
<td>

8XXXX



</td>
<td>

Asynchronous jobs failures



</td>
</tr>
<tr>
<td>

9XXXX



</td>
<td>

SaaS Provisioning service errors



</td>
</tr>
<tr>
<td>

10XXXX



</td>
<td>

Events service errors



</td>
</tr>
</table>

