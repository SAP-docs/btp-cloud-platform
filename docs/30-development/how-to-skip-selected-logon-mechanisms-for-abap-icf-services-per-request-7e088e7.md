<!-- loio7e088e7bf9c4441a8337f8fb3bb199c7 -->

# How to Skip Selected Logon Mechanisms for ABAP ICF Services per Request



<a name="loio7e088e7bf9c4441a8337f8fb3bb199c7__section_xys_nyq_5bc"/>

## Prerequisites

Typically, the order of the logon mechanism configuration of the called ICF External Alias or ICF Service dictates which mechanism to execute. However, there are cases when the alias or service configuration contains logon mechanisms that are not suitable for a certain HTTP client, such as when a logon mechanism requires interaction with a Trusted Third Party \(TTP\). Selected logon mechanisms can be skipped per request from the client side without having to adjust the logon order configuration at the ABAP backend side.



<a name="loio7e088e7bf9c4441a8337f8fb3bb199c7__section_xrg_pyq_5bc"/>

## Solution

A client can instruct the ABAP server to not use a certain logon mechanism by adding an HTTP header or HTTP URL parameter. The following table shows the available parameters and the corresponding SAP Note providing the skipping option \(if the SAP Note cell is empty, the skipping option is already available with the initial delivery of the logon mechanism\).


<table>
<tr>
<th valign="top">

Logon mechanism

</th>
<th valign="top">

URL parameter

</th>
<th valign="top">

HTTP header

</th>
<th valign="top">

Required SAP Note

</th>
</tr>
<tr>
<td valign="top">

Client Certificate

</td>
<td valign="top">

name: sap-certlogon

value: disabled

</td>
<td valign="top">

name: sap-certlogon

value: disabled

</td>
<td valign="top">

[3455890](https://me.sap.com/notes/3455890)

</td>
</tr>
<tr>
<td valign="top">

OAuth

</td>
<td valign="top">

name: oauth

value: disabled

</td>
<td valign="top">

name: x-sap-oauth

value: disabled

</td>
<td valign="top">

since SAP\_BASIS 7.56

</td>
</tr>
<tr>
<td valign="top">

Interactive OIDC/OIDC Logon

</td>
<td valign="top">

name: oidc

value: disabled

</td>
<td valign="top">

name: x-sap-oidc

value: disabled

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

SAML

</td>
<td valign="top">

name: saml2

value: disabled

</td>
<td valign="top">

name: x-sap-saml2

value: disabled

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

SPNego

</td>
<td valign="top">

name: spnego

value: disabled

</td>
<td valign="top">

name: x-sap-spnego

value: disabled

</td>
<td valign="top">

[2565845](https://me.sap.com/notes/2565845)

</td>
</tr>
</table>

> ### Note:  
> Ideally the HTTP client should control which credentials to attach to the HTTP request. For example, instead of adding an OAuth token and simultaneously instructing the ABAP backend via URL parameter or HTTP header to ignore that same token, the client should selectively manage the credentials.



<a name="loio7e088e7bf9c4441a8337f8fb3bb199c7__section_h2g_kzq_5bc"/>

## Related Information

For more detailed information on how to skip the respective logon mechanism, please consult the referenced SAP Notes:

1.  Client Certificate: [3455890](https://me.sap.com/notes/3455890).

2.  Interactive OpenID Connect \(OIDC\): [3111813](https://me.sap.com/notes/3111813), *Section 4.2. De-Activating Interactive OIDC for Certain Calls*.

3.  SPNego: [1732610](https://me.sap.com/notes/1732610), *Section 6. Skipping SPNego authentication in certain cases*.


