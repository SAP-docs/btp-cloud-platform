<!-- loio1e1b7b60bb1b4764a2d4bb96bd73182d -->

# Add Members to Your Subaccount \[Feature Set B\]

Add members to your subaccount to enable users to access resources available there. Platform users manage subaccounts with cloud management tools, while business users consume applications and services.



<a name="loio1e1b7b60bb1b4764a2d4bb96bd73182d__prereq_sf4_3hg_klb"/>

## Prerequisites

-   You’re managing a multi-environment subaccount.

    For more information about adding members to Neo subaccounts, see [Add Members to Your Subaccount \[Feature Set B\]](add-members-to-your-subaccount-feature-set-b-1e1b7b6.md).

-   You must be a subaccount administrator to add other subaccount members.

-   The users exist in a trusted identity provider.

    All users of SAP BTP are stored in identity providers, either in the default or in a custom identity provider. SAP BTP needs a copy of the user, sometimes called a shadow user. You assign the shadow user authorizations to access resources in SAP BTP. When a user authenticates, SAP BTP forwards the request to the identity provider.

    For more information, see [Trust and Federation with Identity Providers](trust-and-federation-with-identity-providers-cb1bc8f.md).




<a name="loio1e1b7b60bb1b4764a2d4bb96bd73182d__context_uqz_cjg_klb"/>

## Context

> ### Note:  
> The content in this section is only relevant for cloud management tools feature set B. For more information, see [Cloud Management Tools - Feature Set Overview](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/caf4e4e23aef4666ad8f125af393dfb2.html).

There are two types of users in subaccounts:

-   Platform users

    These users are members of your team. Platform users manage the subaccount with the cloud management tools.

    Assign predefined or custom role collections to users who need to manage or view the subaccount in SAP BTP cockpit. Examples of predefined role collections include the following:

    -   *Subaccount Administrator*

    -   *Subaccount Viewer*


    For more information about the available role collections, see [Role Collections and Roles in Global Accounts, Directories, and Subaccounts \[Feature Set B\]](../10-concepts/role-collections-and-roles-in-global-accounts-directories-and-subaccounts-feature-set-b-0039cf0.md).

    To work in the Cloud Foundry environment add users and authorizations at the org and space level.

    For more information, see [About User Management in the Cloud Foundry Environment](about-user-management-in-the-cloud-foundry-environment-8e6ce96.md).

-   Business users

    These users consume applications and services. Business users don't access cloud management tools like the SAP BTP cockpit. Assign role collections required by the applications and services the business users consume.




<a name="loio1e1b7b60bb1b4764a2d4bb96bd73182d__steps_vqz_cjg_klb"/>

## Procedure

1.  Navigate to your subaccount account.

2.  Add a user to your subaccount.

    For more information, see [Create Users](create-users-a3bc7e8.md).

3.  Assign role collections to the user.

    For more information, see [Assign Users to Role Collections](assign-users-to-role-collections-c576676.md).




<a name="loio1e1b7b60bb1b4764a2d4bb96bd73182d__result_syg_v3g_klb"/>

## Results

The user can log on to SAP BTP and access resources according to the role collections you've assigned to the user.

**Related Information**  


[User and Member Management](../10-concepts/user-and-member-management-cc1c676.md "On SAP BTP, member management happens at all levels from global account to environment, while user management is done for business applications.")

