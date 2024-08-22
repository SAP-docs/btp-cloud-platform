<!-- loio437e9d41d24349c3a2b363f726022677 -->

# Supported Protocols and Authentication Methods

Get an overview about supported protocols and authentication methods in the ABAP environment.



Each communication scenario defines which authentication methods can be used. The tables below gives you an overview of all the authentication methods for communication management.

> ### Note:  
> -   The supported protocols and authentication methods only apply to communication scenarios that are managed by customers.
> -   Since OData is HTTP-based, the listed authentication methods for HTTP are also valid for OData.



## Outbound Communication


<table>
<tr>
<th valign="top">

Protocol

</th>
<th valign="top">

Available Authentication via Outbound Communication User

</th>
<th valign="top">

Available Authentication via Business Users \(Principal Propagation\)

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

</td>
</tr>
<tr>
<td valign="top">

HTTP \(Cloud Connector\)

</td>
<td valign="top">

No authentication

Basic authentication

Technical user propagation

</td>
<td valign="top">

Not supported. Use the destination service instead. For more information, see [Authentication Methods via Destination Service](authentication-methods-via-destination-service-2da17aa.md).

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

Technical user propagation

</td>
<td valign="top">

Not supported. Use the destination service instead. For more information, see [Authentication Methods via Destination Service](authentication-methods-via-destination-service-2da17aa.md).

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

Not supported. Use the destination service instead. For more information, see [Authentication Methods via Destination Service](authentication-methods-via-destination-service-2da17aa.md).

</td>
</tr>
<tr>
<td valign="top">

SQL service \(Internet\)

</td>
<td valign="top">

Basic authentication

</td>
<td valign="top">

Not supported

</td>
</tr>
</table>



<a name="loio437e9d41d24349c3a2b363f726022677__section_lgb_rc5_wmb"/>

## Inbound Communication

All API requests must be sent to the correct API host. Use the API hostname format: **<tenant\>.abap.<domain\>**.


<table>
<tr>
<th valign="top">

Protocol

</th>
<th valign="top">

Available Authentication via Inbound Communication User

</th>
<th valign="top">

Available Authentication via Business User \(Principal Propagation\)

</th>
</tr>
<tr>
<td valign="top">

HTTP

</td>
<td valign="top">

Basic authentication

Client certificate authentication

</td>
<td valign="top">

SAML assertion authentication

OpenID Connect Bearer token

OAuth 2.0 Authorization Code with Proof Key for Code Exchange \(PKCE\)

OAuth 2.0 SAML Bearer Assertion

</td>
</tr>
<tr>
<td valign="top">

RFC \(Internet\)

</td>
<td valign="top">

Basic Authentication

Client Certificate Authentication

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

Basic Authentication

</td>
<td valign="top">

Not supported

</td>
</tr>
<tr>
<td valign="top">

SQL service

</td>
<td valign="top">

Basic Authentication

Client Certificate Authentication

</td>
<td valign="top">

OpenID Connect Bearer token

</td>
</tr>
</table>

-   For more information about the SQL service, see [Accessing ABAP-Managed Data Using SQL Services for Data Integration Scenarios](accessing-abap-managed-data-using-sql-services-for-data-integration-scenarios-4082fe1.md).

-   For more information about SAML Assertion Authentication and OpenID Connect Bearer token, see [How to Create Communication Systems](https://help.sap.com/docs/btp/sap-business-technology-platform/how-to-create-communication-systems?version=Cloud).

    > ### Note:  
    > To use OpenID Connect Bearer token authentication, include the HTTP header **sap-icm-jwt-passthrough** with the value **TRUE** in the request sent to the API host.

-   For HTTP protocol: provided that the technical requirements are met, it is recommended to use security sessions. For more information, see [3201227](https://me.sap.com/notes/3201227).

    > ### Note:  
    > It is mandatory for the API caller to explicitly request security sessions and confirm that the prerequisites are fulfilled. For more information, see [3319136](https://me.sap.com/notes/3319136).

-   For all logon methods other than *Client certificate authentication*, it is recommended to instruct the server not to use mTLS for logon purposes. For more information, see [3455890](https://me.sap.com/notes/3455890).

    > ### Note:  
    > It is recommended that the API caller sends only one type of credential. The evaluation of an unintentionally transmitted client certificate should be deliberately prevented.


