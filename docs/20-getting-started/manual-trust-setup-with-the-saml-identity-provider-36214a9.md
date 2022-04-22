<!-- loio36214a93a8864662996a0d0814f3e1b7 -->

# Manual Trust Setup with the SAML Identity Provider

Learn how you can set up the Identity Authentication service as SAML identity provider for the ABAP environment.



<a name="loio36214a93a8864662996a0d0814f3e1b7__section_ifw_bmp_btb"/>

## Process Overview

If you want to use Identity Authentication service as custom identity provider, you need to set up trust between the Cloud Foundry account and the Identity Authentication service.

You configure how the Cloud Foundry account, which acts as local service provider, communicates with the identity provider. This configuration includes, for example, setting a signing key and certificate to verify the service provider’s identity and encrypt data. This configuration is later needed for developer authentication.

