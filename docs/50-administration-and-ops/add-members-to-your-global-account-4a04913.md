<!-- loio4a0491330a164f5a873fa630c7f45f06 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Add Members to Your Global Account

Add users as global account members using the SAP BTP cockpit.



<a name="loio4a0491330a164f5a873fa630c7f45f06__prereq_hdd_wd2_nbb"/>

## Prerequisites

You have the Administrator role in the global account.



<a name="loio4a0491330a164f5a873fa630c7f45f06__steps_igf_mlf_knb"/>

## Procedure

1.  Find out which cloud management tools feature set your global account uses. For more information, see [Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md).

2.  Learn how to add members to your global account.

    -   [Add Members to Your Global Account \[Feature Set A\]](add-members-to-your-global-account-4a04913.md#loio4a0491330a164f5a873fa630c7f45f06__AddMembers-FSA) 
    -   [Add Members to Your Global Account \[Feature Set B\]](add-members-to-your-global-account-4a04913.md#loio4a0491330a164f5a873fa630c7f45f06__AddMembers-FSB)


**Related Information**  


[Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

[User and Member Management](../10-concepts/user-and-member-management-cc1c676.md "On SAP BTP, member management happens at all levels from global account to environment, while user management is done for business applications.")

<a name="AddMembers-FSA"/>

<!-- AddMembers-FSA -->

## Add Members to Your Global Account \[Feature Set A\]

Add users as global account members using the SAP BTP cockpit.



<a name="AddMembers-FSA__context_qpw_tkf_knb"/>

## Context

The users you add as members at global account level are automatically assigned the Administrator role.

All global account administrators can do the following:

-   View all the subaccounts in the global account, meaning all the subaccount tiles in the global account's *Subaccounts* page.
-   Edit general properties of the subaccounts in the global account from the *Edit* icon in the subaccount tile.
-   Create a new subaccount in the global account.
-   View, add, and remove global account members.
-   Manage entitlements for the global account.

On the *Members* page at the global account level in the cockpit, all global account members can view the global account administrators. If you're a subaccount member, you're also a member of the global account.



<a name="AddMembers-FSA__steps_spw_tkf_knb"/>

## Procedure

1.  Choose the global account to which you'd like to add members.

2.  In the navigation area, choose *Members*.

3.  Choose *Add Members*.

4.  Enter up to 100 user IDs. To separate them, you can use commas, spaces, semicolons, or line breaks.

5.  Choose *Add Members*.




<a name="AddMembers-FSA__postreq_tpw_tkf_knb"/>

## Next Steps

To delete members at global account level, choose :wastebasket: next to the user's ID.

<a name="AddMembers-FSB"/>

<!-- AddMembers-FSB -->

## Add Members to Your Global Account \[Feature Set B\]

Add members to your global account by assigning them a role collection.



<a name="AddMembers-FSB__prereq_sf4_3hg_klb"/>

## Prerequisites

-   You must be a global account administrator to add other global account members.

-   The users exist in a trusted platform identity provider.

    All users of SAP BTP are stored in identity providers, either in the default or in a custom identity provider. SAP BTP needs a copy of the user, sometimes called a shadow user. You assign the shadow user authorizations to access resources in SAP BTP. When a user authenticates, SAP BTP forwards the request to the identity provider.

    For more information, see [Trust and Federation with Identity Providers](trust-and-federation-with-identity-providers-cb1bc8f.md).




<a name="AddMembers-FSB__context_gr5_5kf_knb"/>

## Context

Assign predefined or custom role collections to users who need to manage or view the global account in SAP BTP cockpit. Examples of predefined role collections include the following:

-   *Global Account Administrator*

-   *Global Account Viewer*


For more information about these role collections, see [Role Collections and Roles in Global Accounts, Directories, and Subaccounts \[Feature Set B\]](../10-concepts/role-collections-and-roles-in-global-accounts-directories-and-subaccounts-feature-set-b-0039cf0.md).



<a name="AddMembers-FSB__steps_vqz_cjg_klb"/>

## Procedure

1.  Navigate to your global account.

2.  Add a user to your global account.

    For more information, see [Create Users](create-users-a3bc7e8.md).

3.  Assign a role collection to the user.

    For more information, see [Assign Users to Role Collections](assign-users-to-role-collections-c576676.md).




<a name="AddMembers-FSB__result_syg_v3g_klb"/>

## Results

The next time this user logs on to the SAP BTP cockpit, the user can access this global account.

