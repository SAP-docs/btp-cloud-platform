<!-- loioedd5613fe3354373b0a0de4c90bcdb59 -->

# Trusted Certificate Authorities for X.509 Secrets

Service instances of the SAP Authorization and Trust Management service \(XSUAA\) trust the following certificate authorities \(CA\). To use your own public key infrastructure \(PKI\) for bindings, the certificates must be issued from one of these CAs.

<a name="loioedd5613fe3354373b0a0de4c90bcdb59__table_gnh_wds_crb"/>Supported CAs for X.509 Secrets


<table>
<tr>
<th valign="top">

Subject



</th>
<th valign="top">

Issuer



</th>
<th valign="top">

Validity



</th>
</tr>
<tr>
<td valign="top">

 `C=US, O=DigiCert Inc, OU=www.digicert.com, CN=DigiCert Global Root G2` 



</td>
<td valign="top">

 `C=US, O=DigiCert Inc, OU=www.digicert.com, CN=DigiCert Global Root G2` 



</td>
<td valign="top">

Jan 15 12:00:00 2038 GMT



</td>
</tr>
<tr>
<td valign="top">

 `C=US, O=DigiCert Inc, OU=www.digicert.com, CN=DigiCert Global Root CA` 



</td>
<td valign="top">

 `C=US, O=DigiCert Inc, OU=www.digicert.com, CN=DigiCert Global Root CA` 



</td>
<td valign="top">

Nov 10 00:00:00 2031 GMT



</td>
</tr>
<tr>
<td valign="top">

 `C=US, O=DigiCert Inc, OU=www.digicert.com, CN=DigiCert Global Root CA` 



</td>
<td valign="top">

 `C=US, O=DigiCert Inc, CN=DigiCert SHA2 Secure Server CA` 



</td>
<td valign="top">

Mar 8 12:00:00 2023 GMT



</td>
</tr>
<tr>
<td valign="top">

 `C=IE, O=Baltimore, OU=CyberTrust, CN=Baltimore CyberTrust Root` 



</td>
<td valign="top">

 `C=IE, O=Baltimore, OU=CyberTrust, CN=Baltimore CyberTrust Root` 



</td>
<td valign="top">

May 12 23:59:00 2025 GMT



</td>
</tr>
</table>

**Related Information**  


[Parameters for Self-Managed X.509 Certificates](parameters-for-self-managed-x-509-certificates-5168df6.md "Use these parameters to provide your own certificates for a binding or service key to service instances of the SAP Authorization and Trust Management service (XSUAA).")

[Service Instance Secrets](service-instance-secrets-5578ec4.md "When an application consumes a service instance of the SAP Authorization and Trust Management service (XSUAA), the application identifies itself to the service instance with a client ID and a secret. The client ID and secret are the credentials with which an application authenticates itself to the service instance.")

