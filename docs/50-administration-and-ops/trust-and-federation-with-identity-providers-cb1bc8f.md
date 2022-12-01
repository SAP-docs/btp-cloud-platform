<!-- loiocb1bc8f1bd5c482e891063960d7acd78 -->

# Trust and Federation with Identity Providers

When setting up accounts you need to assign users. While we provide you with your first users to get you started, your organization has identity providers that you want to integrate.

SAP BTP supports identity federation, a concept of linking and reusing digital identities of a user base across loosely coupled systems. Identity federation frees applications on SAP BTP as well as the platform itself from the need to obtain and store the credentials of users and to authenticate them. Instead, the user base is reused from identity providers, which support the administration of digital user identities, authentication, and authorizations in a centralized and decoupled manner. To enable communication between SAP BTP and identity providers, you must cross-configure the communication endpoints of the involved systems, establishing a trust relationship between them.

> ### Recommendation:  
> We recommend that you always use SAP Cloud Identity Services - Identity Authentication as single identity provider for SAP BTP. If you use corporate identity providers, connect them to your Identity Authentication tenant, which then acts as a hub. We especially recommend this if you are using multiple corporate identity providers. For platform users, the use of SAP Cloud Identity Services - Identity Authentication is mandatory.
> 
> For more information, see [Corporate Identity Providers](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/19f3eca47db643b6aad448b5dc1075ad.html) and [Configure Conditional Authentication for an Application](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/0143dce88a604533ab5ab17e639fec09.html) in [What Is Identity Authentication](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/27882717f44b445fa287936c6f43dc1f.html) and [SAP Cloud Identity Services - Identity Authentication](https://help.sap.com/viewer/product/IDENTITY_AUTHENTICATION/Cloud/en-US)

   
  
**Identity Provider and XSUAA in SAP BTP Architecture**

 ![](images/CF_Trust_for_Identity_Providers_3663b18.png "Identity Provider and XSUAA in SAP BTP
                    Architecture") 

Identity Authentication is a multitenancy enabled identity provider and authentication service for all applications powered by SAP BTP and optionally on-premise applications. The service provides capabilities for authentication, single sign-on, and on-premise integration as well as self-services like self-registration or password reset — for both the employees and the partners and customers of your organization. For administrators, the service offers features for user management and reporting capabilities in the administration console.

SAP has its own Identity Authentication tenant, SAP ID service. SAP ID service is the default identity provider of SAP BTP and where you register to get initial access to SAP BTP. Trust to SAP ID service is preconfigured by default.

We recommend that you request your own Identity Authentication tenant \(see [Getting a Tenant](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/93160ebd2dcb40e98aadcbb9a970f2b9.html#getting-a-tenant)\), but you can also use any other identity provider, which supports the SAML 2.0 protocol. To establish trust with your identity provider, perform one of the following procedures.

For business users: [Business Users](business-users-3a3f0e1.md)

For platform users: [Platform Users](platform-users-9e5e635.md)

**Related Information**  


[Federation Attribute Settings of Any Identity Provider](federation-attribute-settings-of-any-identity-provider-6d07333.md "This table is supposed to display the attribute settings of the identity provider and the values administrators use to establish trust between the SAML 2.0 identity provider and a new subaccount.")

