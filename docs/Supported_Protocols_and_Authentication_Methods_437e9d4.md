<!-- loio437e9d41d24349c3a2b363f726022677 -->

# Supported Protocols and Authentication Methods

Get an overview about supported protocols and authentication methods in the ABAP environment.



Each communication scenario defines which authentication methods can be used. The tables below gives you an overview of all the authentication methods.



## Outbound Communication


<table>
<tr>
<th>

Protocol



</th>
<th>

Available Authentication Methods via Destination Service



</th>
<th>

Available Authentication via Outbound Communication User



</th>
</tr>
<tr>
<td>

HTTP \(Internet\)



</td>
<td>

No Authentication

Basic Authentication

Client Certificate Authentication

Oauth2 Client Credentials

Oauth2 SAML Bearer Assertion

Oauth2 User Token Exchange



</td>
<td>

No Authentication

Basic Authentication

Client Certificate Authentication

Oauth2 Client Credentials



</td>
</tr>
<tr>
<td>

HTTP \(Cloud Connector\)



</td>
<td>

No Authentication

Basic Authentication

JWT Principal Propagation



</td>
<td>

No Authentication

Basic Authentication



</td>
</tr>
<tr>
<td>

SOAP \(Internet\)



</td>
<td>

No Authentication

Basic Authentication

Client Certificate Authentication



</td>
<td>

No Authentication

Basic Authentication

Client Certficate Authentication



</td>
</tr>
<tr>
<td>

SOAP \(Cloud Connector\)



</td>
<td>

No Authentication

Basic Authentication



</td>
<td>

No Authentication

Basic Authentication



</td>
</tr>
<tr>
<td>

RFC \(Internet\)



</td>
<td>

Basic Authentication

Client Certificate Authentication



</td>
<td>

Basic Authentication

Client Certificate Authentication



</td>
</tr>
<tr>
<td>

RFC \(Cloud Connector\)



</td>
<td>

Basic Authentication

JWT Principal Propagation



</td>
<td>

Basic Authentication



</td>
</tr>
</table>



<a name="loio437e9d41d24349c3a2b363f726022677__section_lgb_rc5_wmb"/>

## Inbound Communication


<table>
<tr>
<th>

Protocol



</th>
<th>

Available Authentication via Inbound Communication User



</th>
</tr>
<tr>
<td>

HTTP



</td>
<td>

Basic Authentication

Client Certificate Authentication



</td>
</tr>
<tr>
<td>

SOAP



</td>
<td>

Basic Authentication

Client Certificate Authentication



</td>
</tr>
<tr>
<td>

RFC \(Internet\)



</td>
<td>

Basic Authentication

Client Certificate Authentication



</td>
</tr>
<tr>
<td>

RFC \(Cloud Connector\)



</td>
<td>

Basic Authentication



</td>
</tr>
</table>

