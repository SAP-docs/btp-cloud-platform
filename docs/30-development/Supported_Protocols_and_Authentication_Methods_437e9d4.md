<!-- loio437e9d41d24349c3a2b363f726022677 -->

# Supported Protocols and Authentication Methods

Get an overview about supported protocols and authentication methods in the ABAP environment.



Each communication scenario defines which authentication methods can be used. The tables below gives you an overview of all the authentication methods for communication management.



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

Client Certficate Authentication

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

Principal Propagation \(only via service destination\)



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
</tr>
<tr>
<td valign="top">

HTTP



</td>
<td valign="top">

Basic Authentication

Client Certificate Authentication

SAML Assertion Authentication

OpenID Connect Bearer Token



</td>
</tr>
<tr>
<td valign="top">

SOAP

> ### Note:  
> You can only use it in communication scenarios delivered by SAP.



</td>
<td valign="top">

Basic Authentication

Client Certificate Authentication



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
</tr>
<tr>
<td valign="top">

RFC \(Cloud Connector\)



</td>
<td valign="top">

Basic Authentication



</td>
</tr>
<tr>
<td valign="top">

SQL service



</td>
<td valign="top">

Basic Authentication

OpenID Connect Bearer Token



</td>
</tr>
</table>

-   For more information about the SQL service, see [Accessing ABAP-Managed Data from External ODBC-Based Clients](Accessing_ABAP-Managed_Data_from_External_ODBC-Based_Clients_4082fe1.md).

-   For more information about the OpenID Connect Bearer Token, see [How to Create Communication Systems](https://help.sap.com/viewer/0f69f8fb28ac4bf48d2b57b9637e81fa/latest/en-US/1bfe32ae08074b7186e375ab425fb114.html).

