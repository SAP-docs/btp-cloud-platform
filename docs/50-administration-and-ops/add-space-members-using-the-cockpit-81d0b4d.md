<!-- loio81d0b4dcfbc84016b6b3c1465d4272f4 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Add Space Members Using the Cockpit

You can add space members and assign roles to them at the space level in the cockpit.



<a name="loio81d0b4dcfbc84016b6b3c1465d4272f4__prereq_ryf_qsj_nbb"/>

## Prerequisites

-   You have the Space Manager or Org Manager role.

    If you only have the Space Manager role, the users you want to add to the space must already be members of the org.

    For more information, see the *Context* section.

-   The users exist in a trusted platform identity provider.

    For more information, see [About User Management in the Cloud Foundry Environment](about-user-management-in-the-cloud-foundry-environment-8e6ce96.md).




<a name="loio81d0b4dcfbc84016b6b3c1465d4272f4__context_rqw_csz_kjb"/>

## Context

Space members are organization members who have specific roles in a space.

Org members can only be added by an Org Manager. This means that if you only have the Space Manager role, you can’t add space members that aren’t known to the org. To do that, you must first ask your Org Manager to add the users as org members with no roles. Once this is done, you can add them as space members following the steps below.

If you’re the Org Manager, you don’t need to first add the users as org members with no roles. Since you have the permissions necessary to add users to the org, when you add a new user as a space member, that user automatically becomes part of the org as well.



<a name="loio81d0b4dcfbc84016b6b3c1465d4272f4__steps_jrg_wt4_zl"/>

## Procedure

1.  Navigate to the space to which you'd like to add members. For more information, see [Navigate to Orgs and Spaces](navigate-to-orgs-and-spaces-5bf8735.md).

2.  Choose a space.

3.  In the navigation area, choose *Members*.

    The screen displays all members currently assigned to the org in a list.

4.  Choose *Add Members*.

5.  Enter one or more e-mail addresses.

    Use commas \(`,`\), spaces \(``\), semicolons \(. The changes you make to the roles of a member take effect immediately.`;`\), or line breaks to separate members.

6.  Enter the *Origin* for the identity provider, which hosts the members you just added.

    The default identity provider is ***sap.ids***.

    For more information, see [Default Identity Provider](default-identity-provider-d6a8db7.md).

    If the new members are platform users from a custom identity provider, enter the origin.

    -   Feature Set A: Choose *Other* and then enter the corresponding origin of the Identity Authentication tenant.

        For more information about finding the origin, see [Establish Trust and Federation of Custom Identity Providers for Platform Users in Multi-Environment Subaccounts \[Feature Set A\]](establish-trust-and-federation-of-custom-identity-providers-for-platform-users-in-multi-8600afb.md).

    -   Feature Set B: Select the corresponding origin of the Identity Authentication tenant.

        For more information about finding the origin, see [Establish Trust and Federation of Custom Identity Providers for Platform Users \[Feature Set B\]](establish-trust-and-federation-of-custom-identity-providers-for-platform-users-feature-c368984.md).


7.  Select the roles for the users and save your changes.

    For more information, see [About Roles in the Cloud Foundry Environment](about-roles-in-the-cloud-foundry-environment-0907638.md).




<a name="loio81d0b4dcfbc84016b6b3c1465d4272f4__postreq_flp_dtj_nbb"/>

## Next Steps

You also have the following options:

-   To select or unselect roles for a member, choose :pencil2:
-   To remove all the roles of a member, choose :wastebasket:. This removes the member from the space.

**Related Information**  


[Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

[Add Org Members Using the Cockpit](add-org-members-using-the-cockpit-a4eeaf1.md "Add users as org members and assign roles to grant the users access to information, such as user and quota information in a Cloud Foundry org.")

