<!-- loio437e9d41d24349c3a2b363f726022677 -->

# Supported Protocols and Authentication Methods

Get an overview about supported protocols and authentication methods in the ABAP environment.



Each communication scenario defines which authentication methods can be used. The tables below gives you an overview of all the authentication methods.



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

Oauth2 Client Credentials

Oauth2 SAML Bearer Assertion

Oauth2 User Token Exchange



</td>
<td valign="top">

No Authentication

Basic Authentication

Client Certificate Authentication

Oauth2 Client Credentials



</td>
</tr>
<tr>
<td valign="top">

HTTP \(Cloud Connector\)



</td>
<td valign="top">

No Authentication

Basic Authentication

JWT Principal Propagation



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



</td>
<td valign="top">

No Authentication

Basic Authentication

Client Certficate Authentication



</td>
</tr>
<tr>
<td valign="top">

SOAP \(Cloud Connector\)



</td>
<td valign="top">

No Authentication

Basic Authentication



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

JWT Principal Propagation



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



</td>
</tr>
<tr>
<td valign="top">

SOAP



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

SQL-Service



</td>
<td valign="top">

Basic Authentication



</td>
</tr>
</table>

**Related Information**  


[Accessing ABAP-Managed Data from External ODBC-Based Clients](Accessing_ABAP-Managed_Data_from_External_ODBC-Based_Clients_4082fe1.md "As a developer in the ABAP environment, you can access CDS view entities in an ABAP system using SQL and the open database connectivity (ODBC), a standard API for accessing databases. As a result, you can use SQL statements in external analytical tools to access data in database tables that reside in the ABAP environment.")

