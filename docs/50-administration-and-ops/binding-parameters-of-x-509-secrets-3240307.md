<!-- loio3240307e513e4bceaa75e4134d337fab -->

# Binding Parameters of X.509 Secrets

When binding applications or creating service keys for services instances of the SAP Authorization and Trust Management service \(XSUAA\) you can configure what kinds of X.509 certificates to use for secrets. The service can generate certificates for you or, if you already have your own public key infrastructure \(PKI\), you can use your own.



<a name="loio3240307e513e4bceaa75e4134d337fab__section_hvc_2ds_crb"/>

## Prerequisites

-   You've enabled the service instance to use X.509 secrets.

-   To use your own PKI infrastructure, the certificates must be issued from one of the following certificate authorities \(CA\).

    <a name="loio3240307e513e4bceaa75e4134d337fab__table_gnh_wds_crb"/>Supported CAs for X.509 Secrets


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
    



## Parameters for Certificates Managed by SAP Authorization and Trust Management Service 

The create binding or create service key command expects a `parameters.json` in the following format.

```
{
  "credential-type": "x509",
  "x509": {
    "key-length": 2048,
    "validity": 7,
    "validity-type": "DAYS"
  }
}
```

<a name="loio3240307e513e4bceaa75e4134d337fab__table_iyc_qhs_crb"/>Parameters for SAP Authorization and Trust Management Service-Managed Certificates


<table>
<tr>
<th valign="top">

Parameter



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `credential-type` 



</td>
<td valign="top">

Only required to use X.509 when X.509 isn't specified as default in the application security descriptor \(`xs-security.json`\).

For more information, see [Application Security Descriptor Configuration Syntax](../30-development/application-security-descriptor-configuration-syntax-517895a.md).



</td>
</tr>
<tr>
<td valign="top">

 `x509` 



</td>
<td valign="top">

In this parameter, you define the certificate options of key length, validity period, and unit of length. This parameter is optional.



</td>
</tr>
<tr>
<td valign="top">

 `key-length` 



</td>
<td valign="top">

Specifies the byte length of the generated private key. The default length is 2048 bytes. You can also choose 4096 or 8192 bytes.



</td>
</tr>
<tr>
<td valign="top">

 `validity` 



</td>
<td valign="top">

Specifies the number of time units for `validity-type`. The default value is 7.

Together with the `validity-type` the range of validity runs from `1 DAYS` to `1 YEARS`.



</td>
</tr>
<tr>
<td valign="top">

 `validity-type` 



</td>
<td valign="top">

Specifies the time unit for validity. Supported values are `DAYS`, `MONTHS`, and `YEARS`. The default value is `DAYS`.



</td>
</tr>
</table>



<a name="loio3240307e513e4bceaa75e4134d337fab__section_lyy_fhs_crb"/>

## Parameters for Certificates Managed by Customers

The create binding or create service key command expects a `parameters.json` in the following format.

```
{
  "credential-type": "x509",
  "x509": {
    "certificate": "-----BEGIN CERTIFICATE-----...-----END CERTIFICATE-----",
    "ensure-uniqueness": false,
    "certificate-pinning": true
  }
}
```

<a name="loio3240307e513e4bceaa75e4134d337fab__table_byb_yjs_crb"/>Parameters for Self-Managed Certificates


<table>
<tr>
<th valign="top">

Parameter



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `credential-type` 



</td>
<td valign="top">

Only required to use X.509 when X.509 isn't specified as default in the application security descriptor \(`xs-security.json`\).

For more information, see [Application Security Descriptor Configuration Syntax](../30-development/application-security-descriptor-configuration-syntax-517895a.md).



</td>
</tr>
<tr>
<td valign="top">

 `x509` 



</td>
<td valign="top">

In this parameter, you include the certificate and the options of uniqueness and pinning. This parameter is required.



</td>
</tr>
<tr>
<td valign="top">

 `certificate` 



</td>
<td valign="top">

Provide the certificate string in privacy-enhanced mail \(PEM\) format. This parameter is required.

> ### Restriction:  
> You can only use each certificate once per service instance. The uniqueness of the certificate among all bindings and keys of a service instance is dependent on the value of `certificate-pinning`:
> 
> -   true
> 
>     The certificate hash must be unique.
> 
> -   false
> 
>     The combination of subject and issuer DN must be unique.



</td>
</tr>
<tr>
<td valign="top">

 `ensure-uniqueness` 



</td>
<td valign="top">

Ensures that the certificate is unique among all following instances. The default value is `false`.



</td>
</tr>
<tr>
<td valign="top">

 `certificate-pinning` 



</td>
<td valign="top">

Set to false for applications that are rarely updated or deployed. The incoming certificate's subject and issuer DN is compared to the subject and issuer of the stored certificate. If the values match and the certificate was issued on or after the stored issuer date, the authentication is accepted. Afterwards the incoming certificate's issuer date is stored for future authentication attempts.

Set to true for blue and green deployments, where you deploy a new application or version of an application regularly and rotate the certificate in parallel. For this use case, you need a new certificate to use in the binding of the new application.

The default value is `true`.



</td>
</tr>
</table>

