<!-- loiod203e2d41df1455d8fdc2334844a60d4 -->

# Rate Limiting

This section provides information on the rate limiting in the SAP Authorization and Trust Management service.

The SAP Authorization and Trust Management service acts as an OAuth authorization server and issues access tokens with a long validity. These tokens are meant to be reused. However, some OAuth clients don't reuse them and thus cause a high load. The SAP Authorization and Trust Management service is scaled per landscape to handle the load.

To protect the SAP Authorization and Trust Management service from overload of misbehaving OAuth clients, rate limiting has been introduced. The limit is per subaccount.

-   Requests sent at a lower rate are processed directly.

-   When the limit for a subaccount is exceeded, the requests are queued and sent to the SAP Authorization and Trust Management service at a maximum rate \(see table\). The response times increase because of the queuing.

-   If too many requests are queued so that the response time due to queuing exceeds a certain time, the service sends an HTTP 429 response code. This response also contains the http `Retry-After` header, which indicates when the client can retry.


> ### Note:  
> Since rate limiting is per subaccount, SaaS applications probably don't notice rate limiting because the load is distributed across different SaaS subaccounts.

> ### Restriction:  
> The following table lists sizing restrictions when using APIs.
> 
> **Sizing Restrictions**
> 
> 
> <table>
> <tr>
> <th valign="top">
> 
> Element
> 
> 
> 
> </th>
> <th valign="top">
> 
> Maximum Size
> 
> 
> 
> </th>
> </tr>
> <tr>
> <td valign="top">
> 
> HTTP header
> 
> 
> 
> </td>
> <td valign="top">
> 
> 16 KB
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> POST body
> 
> 
> 
> </td>
> <td valign="top">
> 
> 1 MB
> 
> 
> 
> </td>
> </tr>
> </table>



<a name="loiod203e2d41df1455d8fdc2334844a60d4__section_dhs_hgl_15b"/>

## Token Endpoint

The token endpoint enables you to authenticate with OAuth 2.0.

**Token Endpoint**


<table>
<tr>
<th valign="top">

Endpoint



</th>
<th valign="top">

Subaccount Limit



</th>
<th valign="top">

Effect



</th>
</tr>
<tr>
<td valign="top">

 <code>https://<i class="varname">&lt;subdomain&gt;</i>.authentication.<i class="varname">&lt;landscape&gt;</i>/oauth/token</code> 



</td>
<td valign="top">

Up to 60 requests per second



</td>
<td valign="top">

The requests are executed at once.



</td>
</tr>
<tr>
<td valign="top">

 <code>https://<i class="varname">&lt;subdomain&gt;</i>.authentication.<i class="varname">&lt;landscape&gt;</i>/oauth/token</code> 



</td>
<td valign="top">

Exceeding 60 requests per second



</td>
<td valign="top">

The requests are queued and then executed.



</td>
</tr>
<tr>
<td valign="top">

 <code>https://<i class="varname">&lt;subdomain&gt;</i>.authentication.<i class="varname">&lt;landscape&gt;</i>/oauth/token</code> 



</td>
<td valign="top">

Significantly exceeding 60 requests per second



</td>
<td valign="top">

An `HTTP 429 Too Many Requests` response status code is sent.



</td>
</tr>
<tr>
<td valign="top">

 <code>https://<i class="varname">&lt;subdomain&gt;</i>.authentication.cert.<i class="varname">&lt;landscape&gt;</i>/oauth/token</code> 



</td>
<td valign="top">

Up to 60 requests per second



</td>
<td valign="top">

The requests are executed at once.



</td>
</tr>
<tr>
<td valign="top">

 <code>https://<i class="varname">&lt;subdomain&gt;</i>.authentication.cert.<i class="varname">&lt;landscape&gt;</i>/oauth/token</code> 



</td>
<td valign="top">

Exceeding 60 requests per second



</td>
<td valign="top">

The requests are queued and then executed.



</td>
</tr>
<tr>
<td valign="top">

 <code>https://<i class="varname">&lt;subdomain&gt;</i>.authentication.cert.<i class="varname">&lt;landscape&gt;</i>/oauth/token</code> 



</td>
<td valign="top">

Significantly exceeding 60 requests per second



</td>
<td valign="top">

An `HTTP 429 Too Many Requests` response status code is sent.



</td>
</tr>
</table>



<a name="loiod203e2d41df1455d8fdc2334844a60d4__section_h4z_cfl_15b"/>

## Authorization, Security Settings, and Identity Provider Management APIs

The authorization, security settings, and identity provider management APIs enable you to manage service instances, roles, role templates, role collections, and identity providers. You find the APIs of SAP Authorization and Trust Management service and of the security settings in the [SAP Business Accelerator Hub](https://api.sap.com/package/authtrustmgmnt?section=Artifacts).

**Authorization, Security Settings, and Identity Provider APIs**


<table>
<tr>
<th valign="top">

Endpoint



</th>
<th valign="top">

Subaccount Limit



</th>
<th valign="top">

Effect



</th>
</tr>
<tr>
<td valign="top">

<code>https://api.authentication.<i class="varname">&lt;landscape&gt;</i>/sap/rest/authorization/v2</code>

\(Including all APIs with subpaths, for example `sap/rest/authorization/v2/apps`\)



</td>
<td valign="top">

Up to 30 requests per second



</td>
<td valign="top">

The requests are executed at once.



</td>
</tr>
<tr>
<td valign="top">

<code>https://api.authentication.<i class="varname">&lt;landscape&gt;</i>/sap/rest/authorization/v2</code>

\(Including all APIs with subpaths, for example `sap/rest/authorization/v2/apps`\)



</td>
<td valign="top">

Exceeding 30 requests per second



</td>
<td valign="top">

The requests are queued and then executed.



</td>
</tr>
<tr>
<td valign="top">

<code>https://api.authentication.<i class="varname">&lt;landscape&gt;</i>/sap/rest/authorization/v2</code>

\(Including all APIs with subpaths, for example `sap/rest/authorization/v2/apps`\)



</td>
<td valign="top">

Significantly exceeding 30 requests per second



</td>
<td valign="top">

An `HTTP 429 Too Many Requests` response status code is sent.



</td>
</tr>
<tr>
<td valign="top">

<code>https://api.authentication.<i class="varname">&lt;landscape&gt;</i>/sap/rest/identity-providers</code>

\(Including all APIs with subpaths, for example `sap/rest/identity-providers/{id}`\)



</td>
<td valign="top">

Up to 30 requests per second



</td>
<td valign="top">

The requests are executed at once.



</td>
</tr>
<tr>
<td valign="top">

<code>https://api.authentication.<i class="varname">&lt;landscape&gt;</i>/sap/rest/identity-providers</code>

\(Including all APIs with subpaths, for example `sap/rest/identity-providers/{id}`\)



</td>
<td valign="top">

Exceeding 30 requests per second



</td>
<td valign="top">

The requests are queued and then executed.



</td>
</tr>
<tr>
<td valign="top">

<code>https://api.authentication.<i class="varname">&lt;landscape&gt;</i>/sap/rest/identity-providers</code>

\(Including all APIs with subpaths, for example `sap/rest/identity-providers/{id}`\)



</td>
<td valign="top">

Significantly exceeding 30 requests per second



</td>
<td valign="top">

An `HTTP 429 Too Many Requests` response status code is sent.



</td>
</tr>
</table>



<a name="loiod203e2d41df1455d8fdc2334844a60d4__section_xcj_hfl_15b"/>

## User Management \(SCIM\) APIs

The user management \(SCIM\) APIs enable you to manage shadow users and role collections. You find the APIs of SAP Authorization and Trust Management service in the [SAP API Business Hub](https://api.sap.com/package/authtrustmgmnt/rest).

**User Management \(SCIM\) APIs**


<table>
<tr>
<th valign="top">

Endpoint



</th>
<th valign="top">

Subaccount Limit



</th>
<th valign="top">

Effect



</th>
</tr>
<tr>
<td valign="top">

<code>https://api.authentication.<i class="varname">&lt;landscape&gt;</i>/groups</code>

\(Including all APIs with subpaths, for example `sap/rest/groups/{id}`\)



</td>
<td valign="top">

Up to 3 requests per second



</td>
<td valign="top">

The requests are executed at once.



</td>
</tr>
<tr>
<td valign="top">

<code>https://api.authentication.<i class="varname">&lt;landscape&gt;</i>/groups</code>

\(Including all APIs with subpaths, for example `sap/rest/groups/{id}`\)



</td>
<td valign="top">

Exceeding 3 requests per second



</td>
<td valign="top">

The requests are queued and then executed.



</td>
</tr>
<tr>
<td valign="top">

<code>https://api.authentication.<i class="varname">&lt;landscape&gt;</i>/groups</code>

\(Including all APIs with subpaths, for example `sap/rest/groups/{id}`\)



</td>
<td valign="top">

Significantly exceeding 3 requests per second



</td>
<td valign="top">

An `HTTP 429 Too Many Requests` response status code is sent.



</td>
</tr>
<tr>
<td valign="top">

<code>https://api.authentication.<i class="varname">&lt;landscape&gt;</i>/users</code>

\(Including all APIs with subpaths, for example `sap/rest/users/{id}`\)



</td>
<td valign="top">

Up to 3 requests per second



</td>
<td valign="top">

The requests are executed at once.



</td>
</tr>
<tr>
<td valign="top">

<code>https://api.authentication.<i class="varname">&lt;landscape&gt;</i>/users</code>

\(Including all APIs with subpaths, for example `sap/rest/users/{id}`\)



</td>
<td valign="top">

Exceeding 3 requests per second



</td>
<td valign="top">

The requests are queued and then executed.



</td>
</tr>
<tr>
<td valign="top">

<code>https://api.authentication.<i class="varname">&lt;landscape&gt;</i>/users</code>

\(Including all APIs with subpaths, for example `sap/rest/users/{id}`\)



</td>
<td valign="top">

Significantly exceeding 3 requests per second



</td>
<td valign="top">

An `HTTP 429 Too Many Requests` response status code is sent.



</td>
</tr>
</table>

**Related Information**  


[Application Security Descriptor Configuration Syntax](../30-development/application-security-descriptor-configuration-syntax-517895a.md "The syntax required to set the properties and values defined in the xs-security.json application security descriptor file.")

[Access Administration Using APIs of the SAP Authorization and Trust Management Service](../50-administration-and-ops/access-administration-using-apis-of-the-sap-authorization-and-trust-management-service-dcb3bfd.md "The REST services of the SAP Authorization and Trust Management service (XSUAA) provide APIs that enable you to manage entities, such as roles, shadow users, and access tokens in SAP BTP, subaccounts.")

