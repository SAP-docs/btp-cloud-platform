<!-- loio4333dc97ea0d42bd8fe13eebd4382a9b -->

# Extended Cloud Foundry Commands of Custom Domains

The Custom Domain plugin includes commands that you can use to configure and manage your custom domains.



**Commands for the Custom Domain CLI Plugin**


<table>
<tr>
<th valign="top">

Command

</th>
<th valign="top">

Alias

</th>
<th valign="top">

Usage

</th>
<th valign="top">

Options

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`cf custom-domain-create-key`

</td>
<td valign="top">

`cdck`

</td>
<td valign="top">

`cf custom-domain-create-key KEY SUBJECT DOMAIN [DOMAIN ...] [options]`

</td>
<td valign="top">


<table>
<tr>
<td valign="top">

`-skip-ssl-validation`

</td>
<td valign="top">

Do not attempt to validate SSL certificate.

</td>
</tr>
<tr>
<td valign="top">

`-verbose`

</td>
<td valign="top">

Show verbose information.

</td>
</tr>
<tr>
<td valign="top">

`-force`

</td>
<td valign="top">

Force key creation without confirmation.

</td>
</tr>
</table>



</td>
<td valign="top">

Generate a new private and public key pair.

</td>
</tr>
<tr>
<td valign="top">

`cf custom-domain-get-csr`

</td>
<td valign="top">

`cdgc`

</td>
<td valign="top">

`cf custom-domain-get-csr KEY [FILE] [options]`

</td>
<td valign="top">


<table>
<tr>
<td valign="top">

`-skip-ssl-validation`

</td>
<td valign="top">

Do not attempt to validate SSL certificate.

</td>
</tr>
<tr>
<td valign="top">

`-verbose`

</td>
<td valign="top">

Show verbose information.

</td>
</tr>
</table>



</td>
<td valign="top">

Download the certificate signing request corresponding to a new key.

</td>
</tr>
<tr>
<td valign="top">

`cf custom-domain-upload-certificate-chain`

</td>
<td valign="top">

`cducc`

</td>
<td valign="top">

`cf custom-domain-upload-certificate-chain KEY FILE [options]`

</td>
<td valign="top">


<table>
<tr>
<td valign="top">

`-skip-ssl-validation`

</td>
<td valign="top">

Do not attempt to validate SSL certificate.

</td>
</tr>
<tr>
<td valign="top">

`-verbose`

</td>
<td valign="top">

Show verbose information.

</td>
</tr>
<tr>
<td valign="top">

`-force`

</td>
<td valign="top">

Force uploading the certificate chain without confirmation.

</td>
</tr>
</table>



</td>
<td valign="top">

Upload a certificate chain for a given key.

</td>
</tr>
<tr>
<td valign="top">

`cf custom-domain-activate`

</td>
<td valign="top">

`cda`

</td>
<td valign="top">

`cf custom-domain-activate KEY DOMAIN [DOMAIN ...] [options]`

</td>
<td valign="top">


<table>
<tr>
<td valign="top">

`-skip-ssl-validation`

</td>
<td valign="top">

Do not attempt to validate SSL certificate.

</td>
</tr>
<tr>
<td valign="top">

`-verbose`

</td>
<td valign="top">

Show verbose information.

</td>
</tr>
</table>



</td>
<td valign="top">

Activate the server certificate for specified domains.

</td>
</tr>
<tr>
<td valign="top">

`cf custom-domain-list`

</td>
<td valign="top">

`cdl`

</td>
<td valign="top">

`cf custom-domain-list`

</td>
<td valign="top">


<table>
<tr>
<td valign="top">

`-skip-ssl-validation`

</td>
<td valign="top">

Do not attempt to validate SSL certificate.

</td>
</tr>
<tr>
<td valign="top">

`-verbose`

</td>
<td valign="top">

Show verbose information.

</td>
</tr>
</table>



</td>
<td valign="top">

List domains and their configuration status.

</td>
</tr>
<tr>
<td valign="top">

`cf custom-domain-show-certificates`

</td>
<td valign="top">

`cdsc`

</td>
<td valign="top">

`cf custom-domain-show-certificates KEY [FILE] [options]`

</td>
<td valign="top">


<table>
<tr>
<td valign="top">

`-dump`

</td>
<td valign="top">

Dump the certificates in PEM format.

</td>
</tr>
<tr>
<td valign="top">

`-skip-ssl-validation`

</td>
<td valign="top">

Do not attempt to validate SSL certificate.

</td>
</tr>
<tr>
<td valign="top">

`-verbose`

</td>
<td valign="top">

Show verbose information.

</td>
</tr>
</table>



</td>
<td valign="top">

Show certificates for a specified key.

</td>
</tr>
<tr>
<td valign="top">

`cf custom-domain-enable-client-authentication`

</td>
<td valign="top">

`cdeca`

</td>
<td valign="top">

`cf custom-domain-enable-client-authentication FILE DOMAIN [DOMAIN ...] [options]`

</td>
<td valign="top">


<table>
<tr>
<td valign="top">

`-skip-ssl-validation`

</td>
<td valign="top">

Do not attempt to validate SSL certificate.

</td>
</tr>
<tr>
<td valign="top">

`-verbose`

</td>
<td valign="top">

Show verbose information.

</td>
</tr>
</table>



</td>
<td valign="top">

Activate client authentication for specified domains.

</td>
</tr>
<tr>
<td valign="top">

`cf custom-domain-disable-client-authentication`

</td>
<td valign="top">

`cddca`

</td>
<td valign="top">

`cf custom-domain-disable-client-authentication DOMAIN [options]`

</td>
<td valign="top">


<table>
<tr>
<td valign="top">

`-skip-ssl-validation`

</td>
<td valign="top">

Do not attempt to validate SSL certificate.

</td>
</tr>
<tr>
<td valign="top">

`-verbose`

</td>
<td valign="top">

Show verbose information.

</td>
</tr>
<tr>
<td valign="top">

`-force`

</td>
<td valign="top">

Force deactivation of client authentication without confirmation.

</td>
</tr>
</table>



</td>
<td valign="top">

Disable client authentication for a domain.

</td>
</tr>
<tr>
<td valign="top">

`cf custom-domain-show-trusted-certificates`

</td>
<td valign="top">

`cdstc`

</td>
<td valign="top">

`cf custom-domain-show-trusted-certificates DOMAIN [FILE] [options]`

</td>
<td valign="top">


<table>
<tr>
<td valign="top">

`-dump`

</td>
<td valign="top">

Dump the certificates in PEM format.

</td>
</tr>
<tr>
<td valign="top">

`-skip-ssl-validation`

</td>
<td valign="top">

Do not attempt to validate SSL certificate.

</td>
</tr>
<tr>
<td valign="top">

`-verbose`

</td>
<td valign="top">

Show verbose information.

</td>
</tr>
</table>



</td>
<td valign="top">

Show the trusted certificates for a domain.

</td>
</tr>
<tr>
<td valign="top">

`cf custom-domain-deactivate`

</td>
<td valign="top">

`cdd`

</td>
<td valign="top">

`cf custom-domain-deactivate DOMAIN [options]`

</td>
<td valign="top">


<table>
<tr>
<td valign="top">

`-skip-ssl-validation`

</td>
<td valign="top">

Do not attempt to validate SSL certificate.

</td>
</tr>
<tr>
<td valign="top">

`-verbose`

</td>
<td valign="top">

Show verbose information.

</td>
</tr>
<tr>
<td valign="top">

`-force`

</td>
<td valign="top">

Force deactivation without confirmation.

</td>
</tr>
</table>



</td>
<td valign="top">

Deactivate the certificate for a specified domain.

</td>
</tr>
<tr>
<td valign="top">

`cf custom-domain-delete-key`

</td>
<td valign="top">

`cddk`

</td>
<td valign="top">

`cf custom-domain-delete-key KEY [options]`

</td>
<td valign="top">


<table>
<tr>
<td valign="top">

`-skip-ssl-validation`

</td>
<td valign="top">

Do not attempt to validate SSL certificate.

</td>
</tr>
<tr>
<td valign="top">

`-verbose`

</td>
<td valign="top">

Show verbose information.

</td>
</tr>
<tr>
<td valign="top">

`-force`

</td>
<td valign="top">

Force key deletion without confirmation.

</td>
</tr>
</table>



</td>
<td valign="top">

Delete the private key and its certificates.

</td>
</tr>
<tr>
<td valign="top">

`cf custom-domain-version`

</td>
<td valign="top">

`cdv`

</td>
<td valign="top">

`cf custom-domain-version`

</td>
<td valign="top">


<table>
<tr>
<td valign="top">

`-skip-ssl-validation`

</td>
<td valign="top">

Do not attempt to validate SSL certificate.

</td>
</tr>
<tr>
<td valign="top">

`-verbose`

</td>
<td valign="top">

Show verbose information.

</td>
</tr>
</table>



</td>
<td valign="top">

Show the Custom Domain plugin version.

</td>
</tr>
<tr>
<td valign="top">

`cf custom-domain-map-route`

</td>
<td valign="top">

`cdmr`

</td>
<td valign="top">

`cf custom-domain-map-route STANDARD_ROUTE CUSTOM_ROUTE`

</td>
<td valign="top">


<table>
<tr>
<td valign="top">

`-skip-ssl-validation`

</td>
<td valign="top">

Do not attempt to validate SSL certificate.

</td>
</tr>
<tr>
<td valign="top">

`-verbose`

</td>
<td valign="top">

Show verbose information.

</td>
</tr>
</table>



</td>
<td valign="top">

Map a custom domain route to a SaaS application.

</td>
</tr>
<tr>
<td valign="top">

`cf custom-domain-unmap-route`

</td>
<td valign="top">

`cdur`

</td>
<td valign="top">

`cf custom-domain-unmap-route CUSTOM_ROUTE`

</td>
<td valign="top">


<table>
<tr>
<td valign="top">

`-skip-ssl-validation`

</td>
<td valign="top">

Do not attempt to validate SSL certificate.

</td>
</tr>
<tr>
<td valign="top">

`-verbose`

</td>
<td valign="top">

Show verbose information.

</td>
</tr>
</table>



</td>
<td valign="top">

Unmap a custom domain route from a SaaS application.

</td>
</tr>
<tr>
<td valign="top">

`cf custom-domain-routes`

</td>
<td valign="top">

`cdr`

</td>
<td valign="top">

`cf custom-domain-routes`

</td>
<td valign="top">


<table>
<tr>
<td valign="top">

`-skip-ssl-validation`

</td>
<td valign="top">

Do not attempt to validate SSL certificate.

</td>
</tr>
<tr>
<td valign="top">

`-verbose`

</td>
<td valign="top">

Show verbose information.

</td>
</tr>
</table>



</td>
<td valign="top">

List all configured routes of SaaS applications with custom domains.

</td>
</tr>
</table>

**Related Information**  


[Configuring Custom Domains](https://help.sap.com/viewer/74af813c7ee2457cb5eddca0cc70a0c1/Cloud/en-US/1c6c729595f144d9a0bec1b4e2ef1299.html "To make sure that your domain is trusted and all application data is protected, you must first set up secure TLS/SSL communication. Then, make your application reachable via the custom domain and route traffic to it.") :arrow_upper_right:

[Managing Custom Domains](https://help.sap.com/viewer/74af813c7ee2457cb5eddca0cc70a0c1/Cloud/en-US/4651cdc79a1c49878e340e0448e5d0e6.html "Use the Cloud Foundry CLI to manage your custom domains and complete tasks like updating a certificate.") :arrow_upper_right:

