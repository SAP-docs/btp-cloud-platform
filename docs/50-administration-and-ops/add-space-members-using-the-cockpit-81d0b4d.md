<!-- loio81d0b4dcfbc84016b6b3c1465d4272f4 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Add Space Members Using the Cockpit

You can add space members and assign roles to them at the space level in the cockpit.



<a name="loio81d0b4dcfbc84016b6b3c1465d4272f4__prereq_ryf_qsj_nbb"/>

## Prerequisites

-   You have the Space Manager or Org Manager role.

    If you only have the Space Manager role, the users you want to add to the space must already be members of the org. For more details, see the *Context* section.

-   You have the e-mail addresses of the users that you want to add.

    > ### Note:  
    > You must add e-mail addresses of registered members who have an S-user or a P-user \(normally used for trial accounts\). Administrators can request S-user IDs on the SAP ONE Support Launchpad *User Management* application: [1271482](https://launchpad.support.sap.com/#/notes/1271482).
    > 
    > If users don’t have a registered S-user ID, they can register for a P-user on [sap.com](https://www.sap.com/).




<a name="loio81d0b4dcfbc84016b6b3c1465d4272f4__context_rqw_csz_kjb"/>

## Context

Space members are organization members who have specific roles in a space.

Org members can only be added by an Org Manager. This means that if you only have the Space Manager role, you can’t add space members that aren’t known to the org. To do that, you must first ask your Org Manager to add the users as org members with no roles. Once this is done, you can add them as space members following the steps below.

If you’re the Org Manager, you don’t need to first add the users as org members with no roles. Since you have the permissions necessary to add users to the org, when you add a new user as a space member, that user automatically becomes part of the org as well.



<a name="loio81d0b4dcfbc84016b6b3c1465d4272f4__steps_jrg_wt4_zl"/>

## Procedure

1.  Navigate to the space to which you'd like to add members. For more information, see [Navigate to Orgs and Spaces](navigate-to-orgs-and-spaces-5bf8735.md).

2.  In the navigation area, choose *Cloud Foundry* \> *Members*.

    All members currently assigned to the space are shown in a list.

3.  Choose *Add Members*.

4.  Enter one or more e-mail addresses.

    You can use commas, spaces, semicolons, or line breaks to separate members.

5.  Feature Set A: Choose the *Origin*.

    If you want to use a custom user base, choose *Other* for *Origin* and then enter the corresponding Identity Authentication tenant name. For more information, see [Establish Trust and Federation of Custom Identity Providers for Platform Users in Multi-Environment Subaccounts \[Feature Set A\]](Establish_Trust_and_Federation_of_Custom_Identity_Providers_8600afb.md).

6.  Select the roles for the users and save your changes.




<a name="loio81d0b4dcfbc84016b6b3c1465d4272f4__postreq_flp_dtj_nbb"/>

## Next Steps

You also have the following options:

-   To select or unselect roles for a member, choose <span class="SAP-icons"></span> \(Edit\). The changes you make to the roles of a member take effect immediately.
-   To remove all the roles of a member, choose <span class="SAP-icons"></span>. This removes the member from the space.

**Related Information**  


[Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

[Add Org Members Using the Cockpit](add-org-members-using-the-cockpit-a4eeaf1.md "You can add org members and assign roles to them at the subaccount level in the cockpit.")

