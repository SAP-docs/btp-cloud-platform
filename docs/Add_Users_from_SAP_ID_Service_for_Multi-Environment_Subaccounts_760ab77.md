<!-- loio760ab77e5afd4c15ae70ec7ff59e02ef -->

# Add Users from SAP ID Service for Multi-Environment Subaccounts

Before you can assign role collection to a user from SAP ID service, you've to ensure that this user exists in SAP ID service.



<a name="loio760ab77e5afd4c15ae70ec7ff59e02ef__prereq_mvk_fdf_bhb"/>

## Prerequisites

The user you want to add to SAP ID service must have an SAP user account \(for example, an S-user or P-user\). For more information, see [Create SAP User Accounts](Create_SAP_User_Accounts_ebe42f6.md).



## Context

When you create your own trial account, your SAP user is automatically created and assigned to SAP ID service. But when you onboard new members to your subscribed app, you must add them to your subaccount and ensure that they're also added to SAP ID service. Then you can assign a role collection to a user in SAP ID service.



<a name="loio760ab77e5afd4c15ae70ec7ff59e02ef__steps_unm_1rf_bhb"/>

## Procedure

1.  Create users and assign role collections to users in *Security* \> *Users* It's possible to create users in custom identity providers and in the SAP ID service. For more information, see [Working with Users](Working_with_Users_2c91f88.md).


**Related Information**  


[Platform Identity Provider](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/80edbe70b8f3478d8a59c21a91a47aa6.html "The platform identity provider is the user base for access to your SAP BTP subaccount in the Neo environment. The default user base is provided by SAP ID Service. You can switch to an Identity Authentication tenant if you want to use a custom user base.") :arrow_upper_right:

[Assigning Role Collections](Assigning_Role_Collections_9e1bf57.md "You have arranged roles in role collections, and now want to assign these role collections to business users.")

