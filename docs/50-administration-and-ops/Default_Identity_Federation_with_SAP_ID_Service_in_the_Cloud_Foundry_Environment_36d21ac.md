<!-- loio36d21ac25533495491059887201fe6a3 -->

# Default Identity Federation with SAP ID Service in the Cloud Foundry Environment

The default identity provider of SAP BTP is SAP ID service.



## Prerequisites

-   To see the default identity provider in *Security* \> *Trust Configuration*, you must have administrator permissions or you are a security administrator of this account. For more information, see the related links.




<a name="loio36d21ac25533495491059887201fe6a3__section_aw5_w2x_thb"/>

## SAP ID Service

SAP ID service is the place where you register to get initial access to SAP BTP. If you are a new user, you can use the self-service registration option of [SAP ID service](https://account.hanatrial.ondemand.com/cockpit).

Trust to SAP ID service in your subaccount is pre-configured in the Cloud Foundry environment of SAP BTP by default, so you can start using it without further configuration. Optionally, you can add additional trust settingsor set the default trust to inactive \(for cloud management tools feature set A, for example if you prefer to use another SAML 2.0 identity provider. Using the SAP BTP cockpit you can make changes by navigating to your respective subaccount and by choosing *Security* \> *Trust Configuration*.

> ### Note:  
> If you do not intend to use SAP ID service, you must establish trust to your custom SAML 2.0 identity provider. We describe a custom trust configuration using the example of SAP Cloud Identity Services - Identity Authentication.
> 
> For more information, see the related link.

**Related Information**  


[Trust and Federation with Identity Providers](Trust_and_Federation_with_Identity_Providers_cb1bc8f.md "When setting up accounts you need to assign users. While we provide you with your first users to get you started, your organization has its own user bases which you want to integrate.")

[Role Collections and Roles in Global Accounts, Directories, and Subaccounts \[Feature Set B\]](../10-concepts/Role_Collections_and_Roles_in_Global_Accounts,_Directories,_and_Subaccounts_Feature_Set_B_0039cf0.md "In the cloud management tools feature set B, SAP BTP provides a set of role collections to set up administrator access to your global account and subaccounts.")

[Managing Security Administrators in Your Subaccount \[Feature Set A\]](Managing_Security_Administrators_in_Your_Subaccount_Feature_Set_A_6752c4b.md "Running on the cloud management tools feature set A: When you create a subaccount, SAP BTP automatically grants your user the role for the administration of business users and their authorizations in the subaccount. Having this role, you can also add or remove other users who will then also be user and role administrators of this subaccount.")

