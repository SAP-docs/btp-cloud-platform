<!-- loio36214a93a8864662996a0d0814f3e1b7 -->

# Manual Trust Setup \(Optional\)

If you want to use Identity Authentication service as custom identity provider, you need to set up trust between the Cloud Foundry account and the Identity Authentication service.

> ### Note:  
> You only need to set up trust manually if you don't want to use the function to establish trust automatically \(see [Establish Trust Automatically](Establish_Trust_Automatically_b9f4b0d.md)\).

You need to configure how the Cloud Foundry account, which acts as local service provider, communicates with the identity provider. This includes, for example, setting a signing key and certificate to verify the service provider’s identity and encrypt data. This configuration is later needed for developer authentication.

-   **[Exporting SAML Identity Provider Metadata](Exporting_SAML_Identity_Provider_Metadata_5c1479e.md "Export the SAML metadata of the identity provider for the SAML trust setup on the service provider side.")**  
Export the SAML metadata of the identity provider for the SAML trust setup on the service provider side.
-   **[Exporting the SAML Service Provider Metadata from the Cloud Foundry Account](Exporting_the_SAML_Service_Provider_Metadata_from_the_Cloud_Foundry_Account_326c830.md "Get the local SAML service provider metadata from the Cloud Foundry account.")**  
Get the local SAML service provider metadata from the Cloud Foundry account.
-   **[Establishing Trust to the SAML Identity Provider for the Cloud Foundry Account](Establishing_Trust_to_the_SAML_Identity_Provider_for_the_Cloud_Foundry_Account_55e7d92.md "Import the SAML identity provider metadata to the Cloud Foundry account to configure SAML trust to the identity provider (that is, the
		Identity Authentication service tenant).")**  
Import the SAML identity provider metadata to the Cloud Foundry account to configure SAML trust to the identity provider \(that is, the Identity Authentication service tenant\).
-   **[Creating a Cloud Foundry Application as Trusted Service Provider](Creating_a_Cloud_Foundry_Application_as_Trusted_Service_Provider_bfc537a.md "Create and configure an application to represent the Cloud Foundry account in the Identity Authentication Service tenant as SAML 2.0
		service provider.")**  
Create and configure an application to represent the Cloud Foundry account in the Identity Authentication Service tenant as SAML 2.0 service provider.

