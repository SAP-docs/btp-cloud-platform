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

-   [Establish Trust and Federation Between UAA and Identity Authentication](Establish_Trust_and_Federation_Between_UAA_and_Identity_Authentication_161f8f0.md#loio161f8f0cfac64c4fa2d973bc5f08a894)

-   [Manually Establish Trust and Federation Between UAA and Identity Authentication](Manually_Establish_Trust_and_Federation_Between_UAA_and_Identity_Authentication_7c6aa87.md#loio7c6aa87459764b179aeccadccd4f91f3)

-   [Establish Trust and Federation with UAA Using Any SAML Identity Provider](Establish_Trust_and_Federation_with_UAA_Using_Any_SAML_Identity_Provider_2ce3938.md#loio2ce3938c66d94479848bff3090999027)


For platform users:

-   [Establish Trust and Federation of Custom Identity Providers for Platform Users in Multi-Environment Subaccounts \[Feature Set A\]](Establish_Trust_and_Federation_of_Custom_Identity_Providers_for_Platform_Users_in_Multi-Environment_Subaccounts_Feature_Set_A_8600afb.md)


For default identity provider:

-   [Default Identity Federation with SAP ID Service in the Cloud Foundry Environment](Default_Identity_Federation_with_SAP_ID_Service_in_the_Cloud_Foundry_Environment_36d21ac.md)

    > ### Note:  
    > How you assign users to their authorizations depends on the type of trust configuration. If you’re using the default trust configuration via SAP ID service, you can assign users directly to role collections. For more information, see [Default Identity Federation with SAP ID Service in the Cloud Foundry Environment](Default_Identity_Federation_with_SAP_ID_Service_in_the_Cloud_Foundry_Environment_36d21ac.md).
    > 
    > However, if you’re using a custom trust configuration as described in this topic, you can assign individual users or groups to role collections. Assigning users to their authorizations is part of application administration, which is described here. For more information, see [Assigning Role Collections](Assigning_Role_Collections_9e1bf57.md).

    The identity provider hosts the business users, who belong to user groups. It’s efficient to use federation by assigning role collections to one or more user groups. The role collection contains all the authorizations that are necessary for this user group. This method saves time when you add a new business user. Simply add the users to the respective user groups and the new business users automatically get all the authorizations that are included in the role collection.


-   **[Establish Trust and Federation Between UAA and Identity Authentication](Establish_Trust_and_Federation_Between_UAA_and_Identity_Authentication_161f8f0.md#loio161f8f0cfac64c4fa2d973bc5f08a894 "Use your SAP Cloud Identity Services - Identity
                                    Authentication tenant as an identity provider or a proxy to your own
		identity provider hosting your business users. This method avoids the upload and download of SAML meta data by using Open ID Connect (OIDC) to
		establish trust.")**  
Use your SAP Cloud Identity Services - Identity Authentication tenant as an identity provider or a proxy to your own identity provider hosting your business users. This method avoids the upload and download of SAML meta data by using Open ID Connect \(OIDC\) to establish trust.
-   **[Manually Establish Trust and Federation Between UAA and Identity Authentication](Manually_Establish_Trust_and_Federation_Between_UAA_and_Identity_Authentication_7c6aa87.md#loio7c6aa87459764b179aeccadccd4f91f3 "Use your SAP Cloud Identity Services - Identity
                                    Authentication tenant as an identity provider or a proxy to your own
		identity provider hosting your business users. Exchange SAML metadata to establish trust with the Identity
                                Authentication tenant and then register your subaccount with the tenant. To complete
		federation, maintain the federation attributes of the user groups.")**  
Use your SAP Cloud Identity Services - Identity Authentication tenant as an identity provider or a proxy to your own identity provider hosting your business users. Exchange SAML metadata to establish trust with the Identity Authentication tenant and then register your subaccount with the tenant. To complete federation, maintain the federation attributes of the user groups.
-   **[Establish Trust and Federation with UAA Using Any SAML Identity Provider](Establish_Trust_and_Federation_with_UAA_Using_Any_SAML_Identity_Provider_2ce3938.md#loio2ce3938c66d94479848bff3090999027 "To establish trust, configure the trust configuration of the SAML 2.0 identity provider
		in your subaccount using the SAP BTP
                                    cockpit. Next, register your
		subaccount in User Account and Authentication service using the
		administration console of your SAML 2.0 identity provider. To complete federation, maintain
		the federation attributes of the SAML 2.0 user groups. This makes sure that you can assign
		authorizations to user groups.")**  
To establish trust, configure the trust configuration of the SAML 2.0 identity provider in your subaccount using the SAP BTP cockpit. Next, register your subaccount in User Account and Authentication service using the administration console of your SAML 2.0 identity provider. To complete federation, maintain the federation attributes of the SAML 2.0 user groups. This makes sure that you can assign authorizations to user groups.
-   **[Establish Trust and Federation of Custom Identity Providers for Platform Users in Multi-Environment Subaccounts \[Feature Set A\]](Establish_Trust_and_Federation_of_Custom_Identity_Providers_for_Platform_Users_in_Multi-Environment_Subaccounts_Feature_Set_A_8600afb.md "By default, platform users in multi-environment subaccounts are users in SAP ID service. The use of your own identity provider requires integration between the
			user bases of  multi-environment and Neo subaccounts.")**  
By default, platform users in multi-environment subaccounts are users in SAP ID service. The use of your own identity provider requires integration between the user bases of multi-environment and Neo subaccounts.
-   **[Default Identity Federation with SAP ID Service in the Cloud Foundry Environment](Default_Identity_Federation_with_SAP_ID_Service_in_the_Cloud_Foundry_Environment_36d21ac.md "The default identity provider of SAP BTP is SAP ID service.")**  
The default identity provider of SAP BTP is SAP ID service.
-   **[Federation Attribute Settings of Any Identity Provider](Federation_Attribute_Settings_of_Any_Identity_Provider_6d07333.md "This table is supposed to display the attribute settings of the identity provider and
		the values administrators use to establish trust between the SAML 2.0 identity provider and
		a new subaccount.")**  
This table is supposed to display the attribute settings of the identity provider and the values administrators use to establish trust between the SAML 2.0 identity provider and a new subaccount.
-   **[Provide Logon Link Help to Identity Provider for Business Users](Provide_Logon_Link_Help_to_Identity_Provider_for_Business_Users_b8c0aac.md "You have configured trust configurations for multiple identity providers. You want to
		provide an understandable link on the logon page so that business users know where to log
		on.")**  
You have configured trust configurations for multiple identity providers. You want to provide an understandable link on the logon page so that business users know where to log on.
-   **[Switch Off Automatic Creation of Shadow Users](Switch_Off_Automatic_Creation_of_Shadow_Users_d852567.md "To switch off the creation of shadow users in the trust configuration of custom
		identity providers, administrators must explicitly allow users to log on. Administrators
		then have full control over who is allowed to log on.")**  
To switch off the creation of shadow users in the trust configuration of custom identity providers, administrators must explicitly allow users to log on. Administrators then have full control over who is allowed to log on.

**Related Information**  


[Federation Attribute Settings of Any Identity Provider](Federation_Attribute_Settings_of_Any_Identity_Provider_6d07333.md "This table is supposed to display the attribute settings of the identity provider and the values administrators use to establish trust between the SAML 2.0 identity provider and a new subaccount.")

