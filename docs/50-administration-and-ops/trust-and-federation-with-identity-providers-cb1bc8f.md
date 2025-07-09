<!-- loiocb1bc8f1bd5c482e891063960d7acd78 -->

# Trust and Federation with Identity Providers

When setting up accounts you need to assign users. While we provide you with your first users from the default identity provider to get you started, your organization has identity providers that you want to integrate.

SAP BTP supports identity federation, a concept of linking and reusing digital identities of a user base across loosely coupled systems. Identity federation frees applications on SAP BTP as well as the platform itself from the need to obtain and store the credentials of users and to authenticate them. Instead, the user base is reused from identity providers, which support the administration of digital user identities, authentication, and authorizations in a centralized and decoupled manner. To enable communication between SAP BTP and identity providers, you must cross-configure the communication endpoints of the involved systems, establishing a trust relationship between them.

> ### Recommendation:  
> We strongly recommend that you use a custom tenant of SAP Cloud Identity Services. Using SAP Cloud Identity Services eases integration with other SAP solutions. When setting up accounts you need to assign users. We provide you with your first users from the default identity provider. By using SAP Cloud Identity Services as a proxy to your corporate identity provider and hosting your users there, you gain a number of advantages:
> 
> -   Integrate the management of these users with your broader identity management strategy, hosted on your own identity providers. You control your own user lifecycle and single sign-on strategies throughout the entire landscape.
> 
> -   Enforce your own password and authentication policies, such as stronger passwords or multifactor authentication.
> 
> 
> For platform users, the use of SAP Cloud Identity Services is mandatory. If you don't have a tenant yet, check [Getting a Tenant](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/93160ebd2dcb40e98aadcbb9a970f2b9.html#getting-a-tenant).
> 
> To connect your corporate identity provider to SAP Cloud Identity Services, see [Corporate Identity Providers](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/19f3eca47db643b6aad448b5dc1075ad.html) and [Configure Conditional Authentication for an Application](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/0143dce88a604533ab5ab17e639fec09.html) in [What Is Identity Authentication](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/27882717f44b445fa287936c6f43dc1f.html) and [SAP Cloud Identity Services](https://help.sap.com/viewer/product/IDENTITY_AUTHENTICATION/Cloud/en-US)

  
  
**Identity Provider and the SAP Authorization and Trust Management Service in SAP BTP Architecture**



SAP Cloud Identity Services is a multitenancy-enabled identity provider for all SAP cloud applications and optionally on-premise applications. The service provides capabilities for authentication, single sign-on, authorizations, identity lifecycle management, and on-premise integration as well as self-services like self-registration or password reset.

SAP has its own SAP Cloud Identity Services tenant, SAP ID service. SAP ID service is the default identity provider of SAP BTP and where you register to get initial access to SAP BTP. Trust to SAP ID service is preconfigured by default.

We recommend that you request your own SAP Cloud Identity Services tenant \(see [Getting a Tenant](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/93160ebd2dcb40e98aadcbb9a970f2b9.html#getting-a-tenant)\). To establish trust with your identity provider, proceed as follows.

For business users: [Business Users](business-users-3a3f0e1.md)

For platform users: [Platform Users](platform-users-9e5e635.md)

**Related Information**  


[Map User Attributes from a Corporate Identity Provider for Business Users](map-user-attributes-from-a-corporate-identity-provider-for-business-users-bbb4a8a.md "When you enable trust with a tenant of SAP Cloud Identity Services, you get an OpenID Connect (OIDC) application in SAP Cloud Identity Services to represent your subaccount, in the context of business users. When SAP Cloud Identity Services authenticates users using a corporate identity provider, map the user attributes provided by the corporate identity provider to the attributes required by your applications.")

[Map User Attributes from a Corporate Identity Provider for Platform Users](map-user-attributes-from-a-corporate-identity-provider-for-platform-users-40c2e54.md "When you enable trust with a tenant of SAP Cloud Identity Services, you get an OpenID Connect (OIDC) application in SAP Cloud Identity Services to represent SAP BTP, in the context of platform users. When you authenticate users using a corporate identity provider, map the user attributes provided by the corporate identity provider to the attributes required by SAP BTP. The following information explains which attributes SAP BTP needs for which purpose, and how you can map those attributes.")

[Settings for Default SAML Federation Attributes of Identity Providers for Business Users](establish-trust-and-federation-with-uaa-using-any-saml-identity-provider-2ce3938.md#loio6d073332bc5743fdb7f7f06bde499ab7 "This table shows the attribute settings of the identity provider and the values administrators use to establish trust between the SAML 2.0 identity provider and a subaccount.")

