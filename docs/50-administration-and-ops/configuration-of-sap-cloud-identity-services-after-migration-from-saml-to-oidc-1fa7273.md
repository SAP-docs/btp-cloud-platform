<!-- loio1fa7273fc4c54e98aa051f9ad46fab2c -->

# Configuration of SAP Cloud Identity Services After Migration from SAML to OIDC

You replaced an SAML trust configuration to your custom identity provider with an OIDC trust configuration to SAP Cloud Identity Services. Now, you need to make sure that the subaccount gets the same user attributes \(names and values\) as before.

How you proceed depends on which architecture you're trying to achieve. We provide guidance for the configuration according to your target architecture.

-   Business users authenticate directly with SAP Cloud Identity Services

    See [SAP Cloud Identity Services Without Corporate Identity Provider](sap-cloud-identity-services-without-corporate-identity-provider-8c37725.md).

-   Business users authenticate with a corporate identity provider. SAP Cloud Identity Services is a proxy:

    -   Identity federation is disabled \(default flow\)

    -   Identity federation is enabled \(advanced\)


    See [SAP Cloud Identity Services with Corporate Identity Provider](sap-cloud-identity-services-with-corporate-identity-provider-036126c.md).


**Related Information**  


[Migration from SAML Trust to OpenID Connect Trust with SAP Cloud Identity Services](migration-from-saml-trust-to-openid-connect-trust-with-sap-cloud-identity-services-d097ce2.md "To use or get the most out of some applications, such as SAP Build Work Zone and SAP Build Apps, your subaccount must use SAP Cloud Identity Services with OpenID Connect (OIDC) as the custom identity provider. This process helps you change an SAML trust configuration to an OIDC configuration with as little impact to your application users as possible, especially in productive subaccounts.")

[Restore SAML Trust Configuration](restore-saml-trust-configuration-21d86cf.md "You replaced a SAML trust configuration to your custom identity provider with an OpenID Connect (OIDC) trust configuration to SAP Cloud Identity Services, and the authentication of application users in the subaccount isn't working as you expected. Restore your SAML configuration to get your applications working again.")

[Map User Attributes from a Corporate Identity Provider for Business Users](map-user-attributes-from-a-corporate-identity-provider-for-business-users-bbb4a8a.md "When you enable trust with a tenant of SAP Cloud Identity Services, you get an OpenID Connect (OIDC) application in SAP Cloud Identity Services to represent your subaccount, in the context of business users. When SAP Cloud Identity Services authenticates users using a corporate identity provider, map the user attributes provided by the corporate identity provider to the attributes required by your applications.")

