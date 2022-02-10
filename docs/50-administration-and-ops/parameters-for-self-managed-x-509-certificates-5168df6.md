<!-- loio5168df615064457eafe3e48e10a95665 -->

# Parameters for Self-Managed X.509 Certificates

Use these parameters to provide your own certificates for a binding or service key to service instances of the SAP Authorization and Trust Management service \(XSUAA\).



<a name="loio5168df615064457eafe3e48e10a95665__section_hvc_2ds_crb"/>

## Prerequisites

-   You've enabled the service instance to use X.509 secrets.

    For more information, see [Application Security Descriptor Configuration Syntax](../30-development/application-security-descriptor-configuration-syntax-517895a.md).

-   To use your own public key infrastructure \(PKI\), the certificates must be issued from one of the following certificate authorities \(CA\).

    For more information, see [Trusted Certificate Authorities for X.509 Secrets](trusted-certificate-authorities-for-x-509-secrets-edd5613.md).




<a name="loio5168df615064457eafe3e48e10a95665__section_lyy_fhs_crb"/>

## Parameters for Self-Managed Certificates

The create binding or create service key command expects a `parameters.json` in the following format.

```
{
  "credential-type": "x509",
  "x509": {
    "certificate": "-----BEGIN CERTIFICATE-----...-----END CERTIFICATE-----",
    "certificate-pinning": true
  }
}
```

<a name="loio5168df615064457eafe3e48e10a95665__table_byb_yjs_crb"/>Parameters for Self-Managed Certificates


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
> -   ***true***
> 
>     The certificate hash must be unique.
> 
> -   ***false***
> 
>     The combination of subject and issuer DN must be unique.



</td>
</tr>
<tr>
<td valign="top">

 `ensure-uniqueness` 



</td>
<td valign="top">

Ensures that the certificate is unique among all following clone instances. The default value is ***false***.

> ### Note:  
> This parameter only applies to the broker plan of the service.



</td>
</tr>
<tr>
<td valign="top">

 `certificate-pinning` 



</td>
<td valign="top">

Set to ***false*** for applications that are rarely updated or deployed. The incoming certificate's subject and issuer DN is compared to the subject and issuer of the stored certificate. If the values match and the certificate was issued on or after the stored issuer date, the authentication is accepted. Afterwards the incoming certificate's issuer date is stored for future authentication attempts.

**Exception:** Matching certificates with a `Valid from` parameter that is less than 10 minutes old are always accepted.

Set to ***true*** for blue and green deployments, where you deploy a new application or version of an application regularly and rotate the certificate in parallel. For this use case, you need a new certificate to use in the binding of the new application.

The default value is ***true***.



</td>
</tr>
</table>

**Related Information**  


[Service Instance Secrets](service-instance-secrets-5578ec4.md "When an application consumes a service instance of the SAP Authorization and Trust Management service (XSUAA), the application identifies itself to the service instance with a client ID and a secret. The client ID and secret are the credentials with which an application authenticates itself to the service instance.")

