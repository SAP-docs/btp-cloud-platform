<!-- loio1e1b7b60bb1b4764a2d4bb96bd73182d -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Add Members to Your Subaccount

Add members to your subaccount to enable users to access resources available there. Platform users manage subaccounts with cloud management tools, while business users consume applications and services.



<a name="loio1e1b7b60bb1b4764a2d4bb96bd73182d__prereq_sf4_3hg_klb"/>

## Prerequisites

-   You’re managing a multi-environment subaccount.

    For more information about adding members to Neo subaccounts, see [Add Members to Your Neo Subaccount](https://help.sap.com/docs/btp/sap-btp-neo-environment/add-members-to-your-neo-subaccount?version=Cloud).

-   You must be a subaccount administrator to add other subaccount members.

-   The users exist in a trusted identity provider.

    All users of SAP BTP are stored in identity providers, either in the default or in a custom identity provider. SAP BTP needs a copy of the user, sometimes called a shadow user. You assign the shadow user authorizations to access resources in SAP BTP. When a user authenticates, SAP BTP forwards the request to the identity provider.

    For more information, see [Trust and Federation with Identity Providers](trust-and-federation-with-identity-providers-cb1bc8f.md).




<a name="loio1e1b7b60bb1b4764a2d4bb96bd73182d__context_uqz_cjg_klb"/>

## Context

There are two types of users in subaccounts:

-   Platform users

    These users are members of your team. Platform users manage the subaccount with the cloud management tools.

    Assign predefined or custom role collections to users who need to manage or view the subaccount in SAP BTP cockpit. Examples of predefined role collections include the following:

    -   *Subaccount Administrator*

    -   *Subaccount Viewer*


    For more information about the available role collections, see [Role Collections and Roles in Global Accounts, Directories, and Subaccounts](../10-concepts/role-collections-and-roles-in-global-accounts-directories-and-subaccounts-0039cf0.md).

    To work in the Cloud Foundry, ABAP, Kyma, and Neo environments, your team members need additional authorizations.

    For more information, see [Giving Access Rights to Platform Users](https://help.sap.com/docs/btp/best-practices/giving-access-rights-to-platform-users) in the *SAP BTP Best Practices Guide*.

    > ### Note:  
    > If the subaccount has a Cloud Foundry environment, SAP BTP checks Cloud Foundry users with org or space roles. If there's no corresponding user at the subaccount level, SAP BTP creates one automatically.
    > 
    > For more information, see [About User Management in the Cloud Foundry Environment](about-user-management-in-the-cloud-foundry-environment-8e6ce96.md).

-   Business users

    These users consume applications and services. Business users don't access cloud management tools like the SAP BTP cockpit. Assign role collections required by the applications and services that the business users consume.




<a name="loio1e1b7b60bb1b4764a2d4bb96bd73182d__steps_vqz_cjg_klb"/>

## Procedure

> ### Tip:  
> If you're a global account administrator, you can quickly assign yourself as an administrator of a subaccount by going to the *Account Explorer* page and then choosing the *Add Me as Admin* option in the *Actions* \(<span class="SAP-icons-V5"></span>\) context menu of the subaccount. To assign other users, use the following instructions.
> 
> This feature isn't available if it has been disabled for your global account.
> 
> To disable this feature, send an opt-out request using the component BC-NEO-CIS-OPS. See [Getting Support](../70-getting-support/getting-support-5dd7398.md) for information about opening a case and getting technical assistance.

1.  Navigate to your subaccount.

2.  Add a user to your subaccount.

    For more information, see [Create Users](create-users-a3bc7e8.md).

3.  Assign role collections to the user.

    For more information, see [Assign Users to Role Collections](assign-users-to-role-collections-c576676.md).




<a name="loio1e1b7b60bb1b4764a2d4bb96bd73182d__result_syg_v3g_klb"/>

## Results

The user can log on to SAP BTP and access resources according to the role collections you've assigned to the user.

> ### Note:  
> If the new subaccount platform user logs on to SAP BTP cockpit and there's no corresponding platform user at the global account level, SAP BTP creates one automatically.

**Related Information**  


[User and Member Management](../10-concepts/user-and-member-management-cc1c676.md "On SAP BTP, member management takes place at all levels from global account to environment, while user management is relevant for business applications.")

[Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md "Learn how to navigate to your global accounts, directories, and subaccounts in the SAP BTP cockpit.")

