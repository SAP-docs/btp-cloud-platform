<!-- loio4a0491330a164f5a873fa630c7f45f06 -->

# Add Members to Your Global Account

Add users as global account members using the SAP BTP cockpit.



<a name="loio4a0491330a164f5a873fa630c7f45f06__prereq_hdd_wd2_nbb"/>

## Prerequisites

You have the Administrator role in the global account.



<a name="loio4a0491330a164f5a873fa630c7f45f06__steps_igf_mlf_knb"/>

## Procedure

1.  Find out which cloud management tools feature set your global account uses. For more information, see [Cloud Management Tools — Feature Set Overview](../10-concepts/Cloud_Management_Tools_—_Feature_Set_Overview_caf4e4e.md).

2.  Learn how to add members to your global account.

    -   [Add Members to Your Global Account \[Feature Set A\]](Add_Members_to_Your_Global_Account_4a04913.md#loio4a0491330a164f5a873fa630c7f45f06__AddMembers-FSA) 
    -   [Add Members to Your Global Account \[Feature Set B\]](Add_Members_to_Your_Global_Account_4a04913.md#loio4a0491330a164f5a873fa630c7f45f06__AddMembers-FSB)

**Related Information**  


[Cloud Management Tools — Feature Set Overview](../10-concepts/Cloud_Management_Tools_—_Feature_Set_Overview_caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

[User and Member Management](../10-concepts/User_and_Member_Management_cc1c676.md "On the cloud platform, member management happens at all levels from global account to space, while user management is done for deployed applications.")

 <a name="loio4a0491330a164f5a873fa630c7f45f06 AddMembers-FSA__AddMembers-FSA"/>

<!-- AddMembers-FSA -->

# Add Members to Your Global Account \[Feature Set A\]

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

On the *Members* page at the global account level in the cockpit, all global account members can view the global account administrators. If you are a subaccount member, you are also a member of the global account.



<a name="AddMembers-FSA__steps_spw_tkf_knb"/>

## Procedure

1.  Choose the global account to which you'd like to add members.

2.  In the navigation area, choose *Members*.

3.  Choose *Add Members*.

4.  Enter up to 100 user IDs. To separate them, you can use commas, spaces, semicolons, or line breaks.

5.  Choose *Add Members*.




<a name="AddMembers-FSA__postreq_tpw_tkf_knb"/>

## Next Steps

To delete members at global account level, choose   \(Delete\)  next to the user's ID.

 <a name="loio4a0491330a164f5a873fa630c7f45f06 AddMembers-FSB__AddMembers-FSB"/>

<!-- AddMembers-FSB -->

# Add Members to Your Global Account \[Feature Set B\]

Add members to your global account by assigning them a predefined role collection.



<a name="AddMembers-FSB__prereq_sf4_3hg_klb"/>

## Prerequisites

-   You must be a global account administrator in order to add other global account members.

-   You have defined role collections. For more information, see [Define a Role Collection](Define_a_Role_Collection_4b20383.md).




<a name="AddMembers-FSB__context_gr5_5kf_knb"/>

## Context

There are 2 predefined role collections that you can use when adding global account members:

-   Global Account Administrator
-   Global Account Viewer

For more information on the roles included in each of these role collections, see [Role Collections and Roles in Global Accounts, Directories, and Subaccounts \[Feature Set B\]](../10-concepts/Role_Collections_and_Roles_in_Global_Accounts,_Directories,_and_Subaccounts_Feature_Set_B_0039cf0.md).

> ### Restriction:  
> Adding members to global accounts is only possible in enterprise accounts, not in trial accounts.



<a name="AddMembers-FSB__steps_vqz_cjg_klb"/>

## Procedure

1.  Familiarize yourself with the concepts of [Working with Role Collections](Working_with_Role_Collections_393ea0b.md).

2.  Navigate to your global account.

3.  Assign a role collection to users. For more information, see [Assign Users to Role Collections](Assign_Users_to_Role_Collections_c576676.md).




<a name="AddMembers-FSB__result_syg_v3g_klb"/>

## Results

The new role collection assigned to the user is displayed in the table. The user is now a global account member.

