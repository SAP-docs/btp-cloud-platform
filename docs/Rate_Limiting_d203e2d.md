<!-- loiod203e2d41df1455d8fdc2334844a60d4 -->

# Rate Limiting

This section provides information on the rate limiting in the SAP Authorization and Trust Management service.

The SAP Authorization and Trust Management service acts as an OAuth authorization server and issues access tokens with a long validity. These tokens are meant to be reused. However, some OAuth clients don't reuse them and thus cause a high load. The SAP Authorization and Trust Management service is scaled per landscape to handle the load.

To protect the SAP Authorization and Trust Management service from overload of misbehaving OAuth clients, rate limiting has been introduced. The limit is per subaccount.

-   Requests sent at a lower rate are processed directly.

-   When the limit for a subaccount is slightly exceeded, the requests are queued and sent to the SAP Authorization and Trust Management service at a maximum rate \(see table\). The response times increase due to the queuing.

-   If too many requests are queued so that the response time due to queuing exceeds about 5 seconds, the service sends an HTTP 429 response code. This response also contains the http `Retry-After` header, which indicates to the client how long the service is expected to be unavailable.


> ### Note:  
> Since rate limiting is per subaccount, SaaS applications probably don't notice rate limiting because the load is distributed across different SaaS subaccounts.

<a name="loiod203e2d41df1455d8fdc2334844a60d4__table_ykc_csf_bqb"/>Maximum Rate


<table>
<tr>
<th>

Endpoint



</th>
<th>

Subaccount Limit



</th>
<th>

Effect



</th>
</tr>
<tr>
<td>

https//*<subdomain\>*.authentication.*<landscape\>*/oauth/token



</td>
<td>

Up to 60 request per second



</td>
<td>

The requests are executed at once



</td>
</tr>
<tr>
<td>

https//*<subdomain\>*.authentication.*<landscape\>*/oauth/token



</td>
<td>

Slightly exceeding 60 request per second



</td>
<td>

The requests are being queued and then executed.



</td>
</tr>
<tr>
<td>

https//*<subdomain\>*.authentication.*<landscape\>*/oauth/token



</td>
<td>

Significantly exceeding 60 request per second



</td>
<td>

An `HTTP 429 Too Many Requests` response status code is sent.



</td>
</tr>
</table>

**Related Information**  


[Application Security Descriptor Configuration Syntax](Application_Security_Descriptor_Configuration_Syntax_517895a.md "The syntax required to set the properties and values defined in the xs-security.json application security descriptor file.")

