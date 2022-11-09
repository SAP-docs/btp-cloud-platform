<!-- loio974ac87d61ee4a9ca490208cfabfccaf -->

# Parameters for Suppressing Client Secrets

When binding or creating a service key for an `xsuaa` service instance, you can pass some parameters in JSON format or in a JSON file \(see ***cf bind-service*** and ***cf create-service-key*** in the related links\). The `"hide-secret"` element enables you to suppress the client secret when binding or creating a service key. It's useful if some applications only want to bind the `xsuaa` service for authorization purposes.



<a name="loio974ac87d61ee4a9ca490208cfabfccaf__section_cr1_hhs_hsb"/>

## Prerequisites

-   In the application security descriptor file \(`xs-security.json`\), you've included the “credential-type” key with `"instance-secret"` and/or `"binding-secret"` when you created or updated the service instance. The `"hide-secret"` element is only taken into account if the credential type is `"instance-secret"` or `"binding-secret"`.


> ### Note:  
> If the `"credential-type"` element isn't defined in the binding descriptor, it defaults to the first value of the array passed as `"credential-types"` in `xs-security.json` for the service instance or for the first value of the default list.

For more information, see [Application Security Descriptor Configuration Syntax](../30-development/application-security-descriptor-configuration-syntax-517895a.md).



<a name="loio974ac87d61ee4a9ca490208cfabfccaf__section_sc5_23s_hsb"/>

## Parameters for Suppressing Client Secrets

The ***cf create-binding*** or ***cf create-service-key*** commands expect a valid `parameters.json` file containing the service-specific configuration parameters in the following format.

> ### Sample Code:  
> ```
> {
>   "credential-type": "instance-secret",
>   "hide-secret": "true"
> }
> ```

> ### Sample Code:  
> ```
> {
>   "credential-type": "binding-secret",
>   "hide-secret": "true"
> }
> ```

The `hide-secret` element defines whether the client secret is omitted.

**Element for Suppressing Client Secrets**


<table>
<tr>
<th valign="top">

Element



</th>
<th valign="top">

Value



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top" rowspan="2">

hide-secret



</td>
<td valign="top">

 `true` 



</td>
<td valign="top">

The client secret is omitted in the binding information.



</td>
</tr>
<tr>
<td valign="top">

 `false` \(default\)



</td>
<td valign="top">

The client secret is included in the binding information.



</td>
</tr>
</table>

**Related Information**  


[Cloud Foundry CLI Reference](https://cli.cloudfoundry.org/en-US/)

