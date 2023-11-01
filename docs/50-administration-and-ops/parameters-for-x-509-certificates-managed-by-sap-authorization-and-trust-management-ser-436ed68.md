<!-- loio436ed684eadc4045881e59bd1048d98d -->

# Parameters for X.509 Certificates Managed by SAP Authorization and Trust Management Service 

Use the parameters to have the service generate X.509 certificates for you.



<a name="loio436ed684eadc4045881e59bd1048d98d__section_cr1_hhs_hsb"/>

## Prerequisites

You've enabled the service instance to use X.509 secrets.

For more information, see [Application Security Descriptor Configuration Syntax](../30-development/application-security-descriptor-configuration-syntax-517895a.md).



<a name="loio436ed684eadc4045881e59bd1048d98d__section_sc5_23s_hsb"/>

## Parameters for Certificates Managed by the Service

The *create-binding* or *create-service-key* commands expect a `parameters.json` in the following format.

```
{
  "credential-type": "x509",
  "x509": {
    "key-length": 2048,
    "validity": 8,
    "validity-type": "DAYS"
  }
}
```

The following table describes the supported parameters.

**Parameters for Service-Managed Certificates**


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

Specifies the byte length of the generated private key. The default length is 2048 bytes. You can also choose 4096 bytes or 8192 bytes.

</td>
</tr>
<tr>
<td valign="top">

`validity` 

</td>
<td valign="top">

Specifies the number of time units for `validity-type`. The default value is 7.

Together with the `validity-type` the range of validity runs from `1 DAYS` to `30 DAYS`.

</td>
</tr>
<tr>
<td valign="top">

`validity-type` 

</td>
<td valign="top">

Specifies the time unit for validity. Supported value is `DAYS`. The default value is `DAYS`.

</td>
</tr>
</table>

**Related Information**  


[Service Instance Secrets](service-instance-secrets-5578ec4.md "When an application consumes a service instance of the SAP Authorization and Trust Management service (XSUAA), the application identifies itself to the service instance with a client ID and a secret. The client ID and secret are the credentials with which an application authenticates itself to the service instance.")

