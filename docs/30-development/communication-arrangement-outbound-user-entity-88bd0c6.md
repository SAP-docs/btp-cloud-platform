<!-- loio88bd0c67e22540d6ac380dd64076b830 -->

# Communication Arrangement – Outbound User Entity





Technical name: `CommArrangementsOutboundUsers` 



<a name="loio88bd0c67e22540d6ac380dd64076b830__CommunicationArrangementOutboundUser"/>

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

UserName

</td>
<td valign="top">

User name

</td>
<td valign="top">

Mandatory \(Key\)

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

Mandatory \(Key\)

</td>
</tr>
<tr>
<td valign="top">

CertificateID

</td>
<td valign="top">

Certificate ID

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

\- `oauth1`: OAuth 1.0

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

