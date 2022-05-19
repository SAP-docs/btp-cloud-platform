<!-- loiod6a8db70bdde459f92f2837349f95090 -->

# Default Identity Provider

The default platform identity provider and application identity provider of SAP BTP is SAP ID service.



<a name="loiod6a8db70bdde459f92f2837349f95090__section_hpw_zlg_fsb"/>

## Managing Users

To add users to a subaccount, the users must exist in an identity provider.

For more information about adding users to SAP ID service, see [Create SAP User Accounts](create-sap-user-accounts-ebe42f6.md).

To add new users to a subscribed app or service, such as Web IDE, add those users to your subaccount.

For more information, see [Add Users from SAP ID Service for Multi-Environment Subaccounts](add-users-from-sap-id-service-for-multi-environment-subaccounts-760ab77.md).



<a name="loiod6a8db70bdde459f92f2837349f95090__section_e34_mmg_fsb"/>

## Multifactor Authentication

As a self-service, users can enable multifactor authentication for SAP ID service.

For more information, see [How to Enable Multi-Factor Authentication \(MFA\)](https://support.sap.com/en/my-support/mfa.html) on the *SAP Support Portal*.

> ### Note:  
> Some user interfaces don't offer an interactive way to support multifactor authentication, such as time-based one time passwords \(TOTP\). Instead, such tools offer fixed logon ID and password fields. For such tools, enter your password directly followed, without any spaces or dividers, by the TOTP offered by your multifactor device.
> 
> <code>User ID: <b><i>MylogoniD</i></b></code>
> 
> <code>Password: <b><i>MystrongpassworDMytotppasscodE</i></b></code>
> 
> For some tools, this behavior affects log on to the tool itself:
> 
> -   Cloud Foundry command-line interface \(cf CLI\)
> 
>     Alternatively, you can log on through a browser instead. For more information, see [Log On Manually With a Custom Identity Provider](log-on-manually-with-a-custom-identity-provider-e1009b4.md).
> 
> -   SAP Business Technology Platform command-line interface \(btp CLI\)
> 
>     Alternatively, you can log on through a browser instead. For more information, see [Log In Through a Browser](log-in-through-a-browser-b2a56a8.md).
> 
> 
> For other tools, this behavior doesn't affect log on to the tool itself, but log on to the platform when establishing connections or deploying software and such. For example:
> 
> -   Cloud Connector
> 
> -   SAP Business Application Studio
> 
> -   SAP Web IDE



<a name="loiod6a8db70bdde459f92f2837349f95090__section_fmj_mbp_ktb"/>

## SAP Universal ID

SAP ID Service acts as a proxy for SAP Universal ID, when users log on with their e-mail addresses. Users can log on with and manage all their SAP accounts with SAP Universal ID.



<a name="loiod6a8db70bdde459f92f2837349f95090__section_ifv_xlg_fsb"/>

## Trust and Identity Providers

Trust between your subaccount and SAP ID service is preconfigured by default, so you can start using it without further configuration.

In cloud management tools feature set A, you can set the default trust to inactive, for example if you prefer to use another identity provider.

In cloud management tools feature set B, you can hide the default trust.

For more information, see [Hide Logon Link for Default Identity Provider](hide-logon-link-for-default-identity-provider-9e3d457.md).

To use a custom identity provider, establish trust to your custom identity provider. We describe a custom trust configuration using the example of SAP Cloud Identity Services - Identity Authentication.

For more information, see [Trust and Federation with Identity Providers](trust-and-federation-with-identity-providers-cb1bc8f.md).

**Related Information**  


[Security](../60-security/security-e129aa2.md "Use the security features and functions of SAP BTP to support the security policies of your organization.")

[Platform Identity Provider](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/80edbe70b8f3478d8a59c21a91a47aa6.html "The platform identity provider is the user base for access to your SAP BTP subaccount in the Neo environment. The default user base is provided by SAP ID Service. You can switch to an Identity Authentication tenant if you want to use a custom user base.") :arrow_upper_right:



[Working with Users](working-with-users-2c91f88.md "In the SAP BTP cockpit, you can see the users of your global account or subaccount, user-related identity provider information, and their authorizations. In a user's overview, you can create and delete users, and assign role collections. You can also display an overview of the role collections, where you can drill down all the way to the role, and see the application that the role is belongs to.")

[Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

