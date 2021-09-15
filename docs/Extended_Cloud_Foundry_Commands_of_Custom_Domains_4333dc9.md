<!-- loio4333dc97ea0d42bd8fe13eebd4382a9b -->

# Extended Cloud Foundry Commands of Custom Domains

The Custom Domain plugin includes commands that you can use to configure and manage your custom domains.



<a name="loio4333dc97ea0d42bd8fe13eebd4382a9b__table_b4y_spl_3gb"/>Commands for the Custom Domain CLI Plugin


<table>
<tr>
<th>

Command



</th>
<th>

Alias



</th>
<th>

Usage



</th>
<th>

Options



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

`cf custom-domain-create-key`



</td>
<td>

`cdck`



</td>
<td>

`cf custom-domain-create-key KEY SUBJECT DOMAIN [DOMAIN ...] [options]`



</td>
<td>


<table>
<tr>
<td>

`-skip-ssl-validation`



</td>
<td>

Do not attempt to validate SSL certificate.



</td>
</tr>
<tr>
<td>

`-verbose`



</td>
<td>

Show verbose information.



</td>
</tr>
<tr>
<td>

`-force`



</td>
<td>

Force key creation without confirmation.



</td>
</tr>
</table>



</td>
<td>

Generate a new private and public key pair.



</td>
</tr>
<tr>
<td>

`cf custom-domain-get-csr`



</td>
<td>

`cdgc`



</td>
<td>

`cf custom-domain-get-csr KEY [FILE] [options]`



</td>
<td>


<table>
<tr>
<td>

`-skip-ssl-validation`



</td>
<td>

Do not attempt to validate SSL certificate.



</td>
</tr>
<tr>
<td>

`-verbose`



</td>
<td>

Show verbose information.



</td>
</tr>
</table>



</td>
<td>

Download the certificate signing request corresponding to a new key.



</td>
</tr>
<tr>
<td>

`cf custom-domain-upload-certificate-chain`



</td>
<td>

`cducc`



</td>
<td>

`cf custom-domain-upload-certificate-chain KEY FILE [options]`



</td>
<td>


<table>
<tr>
<td>

`-skip-ssl-validation`



</td>
<td>

Do not attempt to validate SSL certificate.



</td>
</tr>
<tr>
<td>

`-verbose`



</td>
<td>

Show verbose information.



</td>
</tr>
<tr>
<td>

`-force`



</td>
<td>

Force uploading the certificate chain without confirmation.



</td>
</tr>
</table>



</td>
<td>

Upload a certificate chain for a given key.



</td>
</tr>
<tr>
<td>

`cf custom-domain-activate`



</td>
<td>

`cda`



</td>
<td>

`cf custom-domain-activate KEY DOMAIN [DOMAIN ...] [options]`



</td>
<td>


<table>
<tr>
<td>

`-skip-ssl-validation`



</td>
<td>

Do not attempt to validate SSL certificate.



</td>
</tr>
<tr>
<td>

`-verbose`



</td>
<td>

Show verbose information.



</td>
</tr>
</table>



</td>
<td>

Activate the server certificate for specified domains.



</td>
</tr>
<tr>
<td>

`cf custom-domain-list`



</td>
<td>

`cdl`



</td>
<td>

`cf custom-domain-list`



</td>
<td>


<table>
<tr>
<td>

`-skip-ssl-validation`



</td>
<td>

Do not attempt to validate SSL certificate.



</td>
</tr>
<tr>
<td>

`-verbose`



</td>
<td>

Show verbose information.



</td>
</tr>
</table>



</td>
<td>

List domains and their configuration status.



</td>
</tr>
<tr>
<td>

`cf custom-domain-show-certificates`



</td>
<td>

`cdsc`



</td>
<td>

`cf custom-domain-show-certificates KEY [FILE] [options]`



</td>
<td>


<table>
<tr>
<td>

`-dump`



</td>
<td>

Dump the certificates in PEM format.



</td>
</tr>
<tr>
<td>

`-skip-ssl-validation`



</td>
<td>

Do not attempt to validate SSL certificate.



</td>
</tr>
<tr>
<td>

`-verbose`



</td>
<td>

Show verbose information.



</td>
</tr>
</table>



</td>
<td>

Show certificates for a specified key.



</td>
</tr>
<tr>
<td>

`cf custom-domain-enable-client-authentication`



</td>
<td>

`cdeca`



</td>
<td>

`cf custom-domain-enable-client-authentication FILE DOMAIN [DOMAIN ...] [options]`



</td>
<td>


<table>
<tr>
<td>

`-skip-ssl-validation`



</td>
<td>

Do not attempt to validate SSL certificate.



</td>
</tr>
<tr>
<td>

`-verbose`



</td>
<td>

Show verbose information.



</td>
</tr>
</table>



</td>
<td>

Activate client authentication for specified domains.



</td>
</tr>
<tr>
<td>

`cf custom-domain-disable-client-authentication`



</td>
<td>

`cddca`



</td>
<td>

`cf custom-domain-disable-client-authentication DOMAIN [options]`



</td>
<td>


<table>
<tr>
<td>

`-skip-ssl-validation`



</td>
<td>

Do not attempt to validate SSL certificate.



</td>
</tr>
<tr>
<td>

`-verbose`



</td>
<td>

Show verbose information.



</td>
</tr>
<tr>
<td>

`-force`



</td>
<td>

Force deactivation of client authentication without confirmation.



</td>
</tr>
</table>



</td>
<td>

Disable client authentication for a domain.



</td>
</tr>
<tr>
<td>

`cf custom-domain-show-trusted-certificates`



</td>
<td>

`cdstc`



</td>
<td>

`cf custom-domain-show-trusted-certificates DOMAIN [FILE] [options]`



</td>
<td>


<table>
<tr>
<td>

`-dump`



</td>
<td>

Dump the certificates in PEM format.



</td>
</tr>
<tr>
<td>

`-skip-ssl-validation`



</td>
<td>

Do not attempt to validate SSL certificate.



</td>
</tr>
<tr>
<td>

`-verbose`



</td>
<td>

Show verbose information.



</td>
</tr>
</table>



</td>
<td>

Show the trusted certificates for a domain.



</td>
</tr>
<tr>
<td>

`cf custom-domain-deactivate`



</td>
<td>

`cdd`



</td>
<td>

`cf custom-domain-deactivate DOMAIN [options]`



</td>
<td>


<table>
<tr>
<td>

`-skip-ssl-validation`



</td>
<td>

Do not attempt to validate SSL certificate.



</td>
</tr>
<tr>
<td>

`-verbose`



</td>
<td>

Show verbose information.



</td>
</tr>
<tr>
<td>

`-force`



</td>
<td>

Force deactivation without confirmation.



</td>
</tr>
</table>



</td>
<td>

Deactivate the certificate for a specified domain.



</td>
</tr>
<tr>
<td>

`cf custom-domain-delete-key`



</td>
<td>

`cddk`



</td>
<td>

`cf custom-domain-delete-key KEY [options]`



</td>
<td>


<table>
<tr>
<td>

`-skip-ssl-validation`



</td>
<td>

Do not attempt to validate SSL certificate.



</td>
</tr>
<tr>
<td>

`-verbose`



</td>
<td>

Show verbose information.



</td>
</tr>
<tr>
<td>

`-force`



</td>
<td>

Force key deletion without confirmation.



</td>
</tr>
</table>



</td>
<td>

Delete the private key and its certificates.



</td>
</tr>
<tr>
<td>

`cf custom-domain-version`



</td>
<td>

`cdv`



</td>
<td>

`cf custom-domain-version`



</td>
<td>


<table>
<tr>
<td>

`-skip-ssl-validation`



</td>
<td>

Do not attempt to validate SSL certificate.



</td>
</tr>
<tr>
<td>

`-verbose`



</td>
<td>

Show verbose information.



</td>
</tr>
</table>



</td>
<td>

Show the Custom Domain plugin version.



</td>
</tr>
<tr>
<td>

`cf custom-domain-map-route`



</td>
<td>

`cdmr`



</td>
<td>

`cf custom-domain-map-route STANDARD_ROUTE CUSTOM_ROUTE`



</td>
<td>


<table>
<tr>
<td>

`-skip-ssl-validation`



</td>
<td>

Do not attempt to validate SSL certificate.



</td>
</tr>
<tr>
<td>

`-verbose`



</td>
<td>

Show verbose information.



</td>
</tr>
</table>



</td>
<td>

Map a custom domain route to a SaaS application.



</td>
</tr>
<tr>
<td>

`cf custom-domain-unmap-route`



</td>
<td>

`cdur`



</td>
<td>

`cf custom-domain-unmap-route CUSTOM_ROUTE`



</td>
<td>


<table>
<tr>
<td>

`-skip-ssl-validation`



</td>
<td>

Do not attempt to validate SSL certificate.



</td>
</tr>
<tr>
<td>

`-verbose`



</td>
<td>

Show verbose information.



</td>
</tr>
</table>



</td>
<td>

Unmap a custom domain route from a SaaS application.



</td>
</tr>
<tr>
<td>

`cf custom-domain-routes`



</td>
<td>

`cdr`



</td>
<td>

`cf custom-domain-routes`



</td>
<td>


<table>
<tr>
<td>

`-skip-ssl-validation`



</td>
<td>

Do not attempt to validate SSL certificate.



</td>
</tr>
<tr>
<td>

`-verbose`



</td>
<td>

Show verbose information.



</td>
</tr>
</table>



</td>
<td>

List all configured routes of SaaS applications with custom domains.



</td>
</tr>
</table>

**Related Information**  


[Configuring Custom Domains](https://help.sap.com/viewer/74af813c7ee2457cb5eddca0cc70a0c1/Cloud/en-US/1c6c729595f144d9a0bec1b4e2ef1299.html "To make sure that your domain is trusted and all application data is protected, you must first set up secure TLS/SSL communication. Then, make your application reachable via the custom domain and route traffic to it.") :arrow_upper_right:

[Managing Custom Domains](https://help.sap.com/viewer/74af813c7ee2457cb5eddca0cc70a0c1/Cloud/en-US/4651cdc79a1c49878e340e0448e5d0e6.html "Use the Cloud Foundry CLI to manage your custom domains and complete tasks like updating a certificate.") :arrow_upper_right:

