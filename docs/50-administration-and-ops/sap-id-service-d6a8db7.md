<!-- loiod6a8db70bdde459f92f2837349f95090 -->

# SAP ID Service

The default platform identity provider and application identity provider of SAP BTP is SAP ID service.



## Context

Trust to SAP ID service in your subaccount is pre-configured in both the Neo and the Cloud Foundry environment of SAP BTP by default, so you can start using it without further configuration. Optionally, you can add additional trust settings. Using the SAP BTP cockpit, you can make changes by navigating to your respective subaccount and by choosing *Security* \> *Trust Configuration* for multi-environment subaccounts, and *Security* \> *Authorization* for Neo.

In cloud management tools feature set A, you can set the default trust to inactive, for example if you prefer to use another identity provider.

In cloud management tools feature set B, you can hide the default trust. For more information, see [Hide Logon Link for Default Identity Provider](hide-logon-link-for-default-identity-provider-9e3d457.md).

If you want to add new users to a subscribed app, or if you want to add users to a service, such as Web IDE, you can add those users to SAP ID service in your subaccount. See [Add Users from SAP ID Service for Multi-Environment Subaccounts](add-users-from-sap-id-service-for-multi-environment-subaccounts-760ab77.md)

> ### Note:  
> If you want to use a custom IdP, you must establish trust to your custom identity provider. We describe a custom trust configuration using the example of SAP Cloud Identity Services - Identity Authentication.
> 
> For more information, see [Trust and Federation with Identity Providers](trust-and-federation-with-identity-providers-cb1bc8f.md).

**Related Information**  


[Security](../60-security/security-e129aa2.md "Use the security features and functions of SAP BTP to support the security policies of your organization.")

[Platform Identity Provider](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/80edbe70b8f3478d8a59c21a91a47aa6.html "The platform identity provider is the user base for access to your SAP BTP subaccount in the Neo environment. The default user base is provided by SAP ID Service. You can switch to an Identity Authentication tenant if you want to use a custom user base.") :arrow_upper_right:



[Working with Users](working-with-users-2c91f88.md "In the SAP BTP cockpit, you can see the users of your global account or subaccount, user-related identity provider information, and their authorizations. In a user's overview, you can create and delete users, and assign role collections. You can also display an overview of the role collections, where you can drill down all the way to the role, and see the application that the role is belongs to.")

[Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

