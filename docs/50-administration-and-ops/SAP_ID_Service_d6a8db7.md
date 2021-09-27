<!-- loiod6a8db70bdde459f92f2837349f95090 -->

# SAP ID Service

The default platform identity provider and application identity provider of SAP BTP is SAP ID service.



## Context

Trust to SAP ID service in your subaccount is pre-configured in both the Neo and the Cloud Foundry environment of SAP BTP by default, so you can start using it without further configuration. Optionally, you can add additional trust settings or set the default trust to inactive, for example if you prefer to use another identity provider. Using the SAP BTP cockpit, you can make changes by navigating to your respective subaccount and by choosing *Security* \> *Trust Configuration* for multi-environment subaccounts, and *Security* \> *Authorization* for Neo.

If you want to add new users to a subscribed app, or if you want to add users to a service, such as Web IDE, you can add those users to SAP ID service in your subaccount. See [Add Users from SAP ID Service for Multi-Environment Subaccounts](Add_Users_from_SAP_ID_Service_for_Multi-Environment_Subaccounts_760ab77.md)

> ### Note:  
> If you want to use a custom IdP, you must establish trust to your custom identity provider. We describe a custom trust configuration using the example of SAP Cloud Identity Services - Identity Authentication.
> 
> For more information, see [Trust and Federation with Identity Providers](Trust_and_Federation_with_Identity_Providers_cb1bc8f.md).

-   **[Create SAP User Accounts](Create_SAP_User_Accounts_ebe42f6.md "If you want to grant authorizations to users from SAP ID service in your subaccount, you
		must ensure that they have a user account in SAP ID service.")**  
If you want to grant authorizations to users from SAP ID service in your subaccount, you must ensure that they have a user account in SAP ID service.
-   **[Add Users from SAP ID Service for Multi-Environment Subaccounts](Add_Users_from_SAP_ID_Service_for_Multi-Environment_Subaccounts_760ab77.md "Before you can assign role collection to a user from SAP ID service, you've to ensure that
		this user exists in SAP ID service.")**  
Before you can assign role collection to a user from SAP ID service, you've to ensure that this user exists in SAP ID service.

**Related Information**  


[Security](../60-security/Security_e129aa2.md "Use the security features and functions of SAP BTP to support the security policies of your organization.")

[Platform Identity Provider](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/80edbe70b8f3478d8a59c21a91a47aa6.html "The platform identity provider is the user base for access to your SAP BTP subaccount in the Neo environment. The default user base is provided by SAP ID Service. You can switch to an Identity Authentication tenant if you want to use a custom user base.") :arrow_upper_right:



[Working with Users](Working_with_Users_2c91f88.md "In the SAP BTP cockpit, you can see the users of your global account or subaccount, user-related identity provider information, and their authorizations. In a user's overview, you can create and delete users, and assign role collections. You can also display an overview of the role collections, where you can drill down all the way to the role, and see the application that the role is belongs to.")

