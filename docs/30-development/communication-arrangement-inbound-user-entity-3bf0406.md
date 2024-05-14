<!-- loio3bf0406c50a949a19851f288211cdd2e -->

# Communication Arrangement – Inbound User Entity





Technical name: `CommArrangementsInboundUsers` 



<a name="loio3bf0406c50a949a19851f288211cdd2e__CommunicationArrangementInboundUser"/>

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

CommunicationArrangementUUID

</td>
<td valign="top">

Communication arrangement UUID

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

princ\_prop: Principal Propagation

oauth2\_mtls: OAuth 2.0 \(mTLS\)

</td>
<td valign="top">

Optional

</td>
</tr>
</table>



> ### Note:  
> To display more information about the properties on the SAP Business Accelerator Hub, choose *Schema View*.

