<!-- loiocb1bc8f1bd5c482e891063960d7acd78 -->

# Trust and Federation with Identity Providers

When setting up accounts you need to assign users. While we provide you with your first users to get you started, your organization has its own user bases which you want to integrate.

SAP BTP supports identity federation, a concept of linking and reusing digital identities of a user base across loosely coupled systems. Identity federation frees applications on SAP BTP from the need to obtain and store the credentials of users to can authenticate them. Instead, the application user base is reused from identity providers, which support the administration of digital user identities, authentication, and authorizations in a centralized and decoupled manner. To enable communication between SAP BTP and identity providers, you must cross-configure the communication endpoints of the involved systems, establishing a trust relationship between them.

> ### Recommendation:  
> We recommend that you use SAP Cloud Identity Services - Identity Authentication as a hub, especially if your business users are stored in multiple corporate identity providers.
> 
> For this scenario, connect Identity Authentication as single custom identity provider to SAP BTP. Next use Identity Authentication to integrate your corporate identity providers.
> 
> For more information, see [Corporate Identity Providers](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/19f3eca47db643b6aad448b5dc1075ad.html) and [Configure Conditional Authentication for an Application](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/0143dce88a604533ab5ab17e639fec09.html) in [What Is Identity Authentication](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/27882717f44b445fa287936c6f43dc1f.html) and [SAP Cloud Identity Services - Identity Authentication](https://help.sap.com/viewer/product/IDENTITY_AUTHENTICATION/Cloud/en-US)

   
  
Identity Provider and XSUAA in SAP BTP Architecture

 ![](images/CF_Trust_for_Identity_Providers_3663b18.png "Identity Provider and XSUAA in SAP BTP
                    Architecture") 

Identity Authentication is a multitenancy enabled identity management service for all applications powered by SAP BTP and optionally on-premise applications. The service provides capabilities for authentication, single sign-on, user provisioning, and on-premise integration as well as self-services like registration or password reset — for both the employees and the partners and customers of your organization. For administrators, the service offers features for user lifecycle management and reporting capabilities in the administration console.

SAP BTP has its own Identity Authentication tenant, SAP ID Service. SAP ID Service is the default identity provider of SAP BTP and where you register to get initial access to SAP BTP. Trust to SAP ID service is preconfigured by default.

We recommend that you request your own Identity Authentication tenant, but you can also use any other identity provider, which supports the SAML 2.0 protocol. To establish trust with your identity provider, perform one of the following procedures.

For business users:

-   [Establish Trust and Federation Between UAA and Identity Authentication](establish-trust-and-federation-between-uaa-and-identity-authentication-161f8f0.md)

-   [Manually Establish Trust and Federation Between UAA and Identity Authentication](manually-establish-trust-and-federation-between-uaa-and-identity-authentication-7c6aa87.md#loio7c6aa87459764b179aeccadccd4f91f3)

-   [Establish Trust and Federation with UAA Using Any SAML Identity Provider](establish-trust-and-federation-with-uaa-using-any-saml-identity-provider-2ce3938.md#loio2ce3938c66d94479848bff3090999027)


For platform users:

-   [Establish Trust and Federation of Custom Identity Providers for Platform Users in Multi-Environment Subaccounts \[Feature Set A\]](establish-trust-and-federation-of-custom-identity-providers-for-platform-users-in-multi-e-8600afb.md)


For default identity provider:

-   [Default Identity Federation with SAP ID Service in the Cloud Foundry Environment](default-identity-federation-with-sap-id-service-in-the-cloud-foundry-environment-36d21ac.md)

    > ### Note:  
    > How you assign users to their authorizations depends on the type of trust configuration. If you’re using the default trust configuration via SAP ID service, you can assign users directly to role collections. For more information, see [Default Identity Federation with SAP ID Service in the Cloud Foundry Environment](default-identity-federation-with-sap-id-service-in-the-cloud-foundry-environment-36d21ac.md).
    > 
    > However, if you’re using a custom trust configuration as described in this topic, you can assign individual users or groups to role collections. Assigning users to their authorizations is part of application administration, which is described here. For more information, see [Mapping Role Collections in the Subaccount](mapping-role-collections-in-the-subaccount-9e1bf57.md).

    The identity provider hosts the business users, who belong to user groups. It’s efficient to use federation by assigning role collections to one or more user groups. The role collection contains all the authorizations that are necessary for this user group. This method saves time when you add a new business user. Simply add the users to the respective user groups and the new business users automatically get all the authorizations that are included in the role collection.


**Related Information**  


[Federation Attribute Settings of Any Identity Provider](federation-attribute-settings-of-any-identity-provider-6d07333.md "This table is supposed to display the attribute settings of the identity provider and the values administrators use to establish trust between the SAML 2.0 identity provider and a new subaccount.")

