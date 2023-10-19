<!-- loio15b28bb6d3574cfe9891023221372c0c -->

# Communication System – Inbound User Entity





Technical name: `CommSystemInboundUsers` 



<a name="loio15b28bb6d3574cfe9891023221372c0c__CommunicationSystemsInboundUser"/>

## Properties

****


<table>
<tr>
<th valign="top">

Property



</th>
<th valign="top">

Description



</th>
<th valign="top">

Necessity



</th>
</tr>
<tr>
<td valign="top">

CommunicationSystemID



</td>
<td valign="top">

Communication system ID



</td>
<td valign="top">

Mandatory \(Key\)



</td>
</tr>
<tr>
<td valign="top">

InboundUUID



</td>
<td valign="top">

Inbound UUID



</td>
<td valign="top">

Mandatory \(Key\)



</td>
</tr>
<tr>
<td valign="top">

UserID



</td>
<td valign="top">

User ID



</td>
<td valign="top">

Mandatory \(Key\)



</td>
</tr>
<tr>
<td valign="top">

UserName



</td>
<td valign="top">

User name



</td>
<td valign="top">

Optional



</td>
</tr>
<tr>
<td valign="top">

OAuth2ClientID



</td>
<td valign="top">

OAuth 2.0 client ID



</td>
<td valign="top">

Optional



</td>
</tr>
<tr>
<td valign="top">

OAuth2GrantType



</td>
<td valign="top">

OAuth 2.0 grant type



</td>
<td valign="top">

Optional



</td>
</tr>
<tr>
<td valign="top">

AuthMethod



</td>
<td valign="top">

`x509`: SSL Client Certificate

`basic`: User ID and Password

`none`: None

`oauth2`: OAuth 2.0

`oauth1`: OAuth 1.0

`princ_prop`: Principal Propagation

`oauth2_mtls`: OAuth 2.0 \(mTLS\)



</td>
<td valign="top">

Optional



</td>
</tr>
</table>

> ### Note:  
> To display more information about the properties on the SAP Business Accelerator Hub, choose **Schema View**.

