<!-- loio1fa7273fc4c54e98aa051f9ad46fab2c -->

# Configuration of Identity Authentication After Migration from SAML to OIDC

You replaced an SAML trust configuration to your custom identity provider with an OIDC trust configuration to Identity Authentication. Now, you need to make sure that the subaccount gets the same user attributes \(names and values\) as before.

How you proceed depends on which architecture you're trying to achieve. We provide guidance for the configuration according to your target architecture.

-   Business users authenticate directly with Identity Authentication

    See [Identity Authentication Without Corporate Identity Provider](identity-authentication-without-corporate-identity-provider-8c37725.md).

-   Business users authenticate with a corporate identity provider. Identity Authentication is a proxy:

    -   Identity federation is disabled \(default flow\)

    -   Identity federation is enabled \(advanced\)


    See [Identity Authentication with Corporate Identity Provider](identity-authentication-with-corporate-identity-provider-036126c.md).


**Related Information**  


[Migration from SAML Trust to OpenID Connect Trust with Identity Authentication](migration-from-saml-trust-to-openid-connect-trust-with-identity-authentication-d097ce2.md "To use or get the most out of some applications, such as SAP Build Work Zone and SAP Build Apps, your subaccount must use Identity Authentication with OpenID Connect (OIDC) as the custom identity provider. This process helps you change an SAML trust configuration to an OIDC configuration with as little impact to your application users as possible, especially in productive subaccounts.")

[Restore SAML Trust Configuration](restore-saml-trust-configuration-21d86cf.md "You replaced an SAML trust configuration to your custom identity provider to OpenID Connect (OIDC) and the authentication of application users in the subaccount isn't working as you expected. Restore your SAML configuration to get your application working again.")

[Map User Attributes from a Corporate Identity Provider for Business Users](map-user-attributes-from-a-corporate-identity-provider-for-business-users-bbb4a8a.md "When you enable trust with a tenant of SAP Cloud Identity Services - Identity Authentication, you get an OpenID Connect (OIDC) application in Identity Authentication to represent your subaccount, in the context of business users. When Identity Authentication authenticates users using a corporate identity provider, map the user attributes provided by the corporate identity provider to the attributes required by your applications.")

