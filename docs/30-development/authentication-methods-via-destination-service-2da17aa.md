<!-- loio2da17aa7ba9e463c8e9bfaaeffc71448 -->

# Authentication Methods via Destination Service

Get an overview about supported protocols and authentication methods via the destination service in the ABAP environment.



## Outbound Communication

The following table gives you an overview of supported authentication methods for communication management when using the destination service.


<table>
<tr>
<th valign="top">

Protocol

</th>
<th valign="top">

Available Authentication Methods via Technical User

</th>
<th valign="top">

Available Authentication Methods via Business User \(Principal Propagation\)

</th>
</tr>
<tr>
<td valign="top">

HTTP \(Internet\)

</td>
<td valign="top">

No authentication

Basic authentication

Client certificate authentication

OAuth 2.0 Client Credentials grant

</td>
<td valign="top">

OAuth 2.0 SAML Bearer Assertion

OAuth 2.0 User Token Exchange

</td>
</tr>
<tr>
<td valign="top">

HTTP \(Cloud Connector\)

</td>
<td valign="top">

No authentication

Basic authentication

</td>
<td valign="top">

Principal propagation

</td>
</tr>
<tr>
<td valign="top">

SOAP \(Internet\)

</td>
<td valign="top">

No authentication

Basic authentication

Client certificate authentication

OAuth 2.0 Client Credentials grant

</td>
<td valign="top">

Not supported

</td>
</tr>
<tr>
<td valign="top">

SOAP \(Cloud Connector\)

</td>
<td valign="top">

No authentication

Basic authentication

</td>
<td valign="top">

Principal propagation

</td>
</tr>
<tr>
<td valign="top">

RFC \(Internet\)

</td>
<td valign="top">

Basic authentication

Client certificate authentication

</td>
<td valign="top">

Not supported

</td>
</tr>
<tr>
<td valign="top">

RFC \(Cloud Connector\)

</td>
<td valign="top">

Basic authentication

</td>
<td valign="top">

Principal propagation

</td>
</tr>
</table>

> ### Note:  
> The use of principal propagation isn't supported in the ADT class runner \(`if_oo_adt_classrun`\) and application jobs. It can only be used during processing of an OData or HTTP service, and only if you execute the service as a business user.

**Related Information**  


[Supported Protocols and Authentication Methods](supported-protocols-and-authentication-methods-437e9d4.md "Get an overview about supported protocols and authentication methods in the ABAP environment.")

