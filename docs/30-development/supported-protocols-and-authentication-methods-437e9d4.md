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

Available Authentication Methods via Destination Service

</th>
<th valign="top">

Available Authentication via Outbound Communication User

</th>
</tr>
<tr>
<td valign="top">

HTTP \(Internet\)

</td>
<td valign="top">

No Authentication

Basic Authentication

Client Certificate Authentication

OAuth 2.0 Client Credentials Grant

OAuth 2.0 SAML Bearer Assertion

OAuth 2.0 User Token Exchange

</td>
<td valign="top">

No Authentication

Basic Authentication

Client Certificate Authentication

OAuth 2.0 Client Credentials Grant

OAuth 2.0 SAML Bearer Assertion

</td>
</tr>
<tr>
<td valign="top">

HTTP \(Cloud Connector\)

</td>
<td valign="top">

No Authentication

Basic Authentication

Principal Propagation

</td>
<td valign="top">

No Authentication

Basic Authentication

</td>
</tr>
<tr>
<td valign="top">

SOAP \(Internet\)

</td>
<td valign="top">

No Authentication

Basic Authentication

Client Certificate Authentication

OAuth 2.0 Client Credentials Grant

</td>
<td valign="top">

No Authentication

Basic Authentication

Client Certificate Authentication

OAuth 2.0 Client Credentials Grant

</td>
</tr>
<tr>
<td valign="top">

SOAP \(Cloud Connector\)

</td>
<td valign="top">

No Authentication

Basic Authentication

Principal Propagation

</td>
<td valign="top">

No Authentication

Basic Authentication

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

Basic Authentication

Client Certificate Authentication

</td>
</tr>
<tr>
<td valign="top">

RFC \(Cloud Connector\)

</td>
<td valign="top">

Basic Authentication

Principal Propagation

</td>
<td valign="top">

Basic Authentication

</td>
</tr>
</table>

> ### Note:  
> The use of Principal Propagation, OAuth 2.0 SAML Bearer Assertion, and OAuth 2.0 User Token Exchange isn't supported in the ADT class runner \(`if_oo_adt_classrun`\) and application jobs. It can only be used during processing of an OData or HTTP service, and only if you execute the service as a business user.



<a name="loio437e9d41d24349c3a2b363f726022677__section_lgb_rc5_wmb"/>

## Inbound Communication


<table>
<tr>
<th valign="top">

Protocol

</th>
<th valign="top">

Available Authentication via Inbound Communication User

</th>
<th valign="top">

Available Authentication via Business User

</th>
</tr>
<tr>
<td valign="top">

HTTP

</td>
<td valign="top">

Basic Authentication

Client Certificate Authentication

</td>
<td valign="top">

SAML Assertion Authentication

OpenID Connect Bearer Token

OAuth 2.0 Authorization Code with Proof Key for Code Exchange \(PKCE\)

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

OpenID Connect Bearer Token

</td>
</tr>
</table>

-   For more information about the SQL service, see [Accessing ABAP-Managed Data Using SQL Services for Data Integration Scenarios](accessing-abap-managed-data-using-sql-services-for-data-integration-scenarios-4082fe1.md).

-   For more information about SAML Assertion Authentication and OpenID Connect Bearer Token, see [How to Create Communication Systems](https://help.sap.com/docs/btp/sap-business-technology-platform/how-to-create-communication-systems?version=Cloud).

