<!-- loio81d0b4dcfbc84016b6b3c1465d4272f4 -->

# Add Space Members

You can add space members and assign roles to them at the space level in the SAP BTP cockpit.



<a name="loio81d0b4dcfbc84016b6b3c1465d4272f4__prereq_ryf_qsj_nbb"/>

## Prerequisites

-   You have the Space Manager or Org Manager role.

    If you only have the Space Manager role, the users you want to add to the space must already have the Org User role.

    If you have the Org Manager role, you can assign space roles to users even if they're not members of the org yet.

    > ### Note:  
    > When you add users who aren't yet members of an org to a space in that org, they get the Org User role by default. This makes them members of the org as well.

-   The users exist in a trusted platform identity provider.

    For more information, see [About User Management in the Cloud Foundry Environment](about-user-management-in-the-cloud-foundry-environment-8e6ce96.md).




<a name="loio81d0b4dcfbc84016b6b3c1465d4272f4__steps_jrg_wt4_zl"/>

## Procedure

1.  Navigate to *Cloud Foundry* \> *Spaces* in the SAP BTP cockpit. For more information, see [Navigate to Orgs and Spaces](navigate-to-orgs-and-spaces-5bf8735.md).

2.  Choose a space to which you'd like to add members. For more information, see [Navigate to Orgs and Spaces](navigate-to-orgs-and-spaces-5bf8735.md).

3.  In the navigation area, choose *Space Members*.

    The screen displays all members currently assigned to the space in a list.

4.  Choose *Add Members*.

5.  Enter one or more e-mail addresses.

    Use commas \(`,`\), spaces \(``\), semicolons \(`;`\), or line breaks to separate members. The changes you make to the roles of a member take effect immediately.

6.  Enter the *Origin* for the identity provider, which hosts the members you just added.

    The default identity provider is ***sap.ids***.

    For more information, see [Default Identity Provider](default-identity-provider-d6a8db7.md).

    If the new members are platform users from a custom identity provider, enter the origin.

    Select the corresponding origin of the Identity Authentication tenant.

    For more information about finding the origin, see [Establish Trust and Federation of Custom Identity Providers for Platform Users](establish-trust-and-federation-of-custom-identity-providers-for-platform-users-c368984.md).

7.  Select the space roles you want to assign.

    For more information, see [About Roles in the Cloud Foundry Environment](about-roles-in-the-cloud-foundry-environment-0907638.md).

8.  Choose *Add*.




<a name="loio81d0b4dcfbc84016b6b3c1465d4272f4__postreq_flp_dtj_nbb"/>

## Next Steps

You also have the following options:

-   [Edit Space Members](edit-space-members-d9e1a15.md)

-   [Delete Space Members](delete-space-members-78b20cf.md)


**Related Information**  


[Cloud Management Tools](../10-concepts/cloud-management-tools-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

[Add Org Members Using the Cockpit](add-org-members-a4eeaf1.md "In the SAP BTP cockpit, add users as org members and assign roles to grant the users access to information, such as user and quota information in a Cloud Foundry org.")

[Add Space Members Using the Cloud Foundry Command Line Interface](add-space-members-using-the-cloud-foundry-command-line-interface-d23ea8b.md "You can use the Cloud Foundry Command Line Interface (cf CLI) to add space members and assign roles to them.")

