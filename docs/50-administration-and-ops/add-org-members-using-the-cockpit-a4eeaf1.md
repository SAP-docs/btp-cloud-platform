<!-- loioa4eeaf179ee646b99558f27c0bae7b3e -->

# Add Org Members Using the Cockpit

Add users as org members and assign roles to grant the users access to information, such as user and quota information in a Cloud Foundry org.



## Prerequisites

-   You have the Org Manager role for the org in question.

    > ### Note:  
    > When you enable Cloud Foundry and the org is created, the Org Manager role is assigned automatically to you.

    For more information, see [About Roles in the Cloud Foundry Environment](about-roles-in-the-cloud-foundry-environment-0907638.md).

-   The users exist in a trusted platform identity provider.

    For more information, see [About User Management in the Cloud Foundry Environment](about-user-management-in-the-cloud-foundry-environment-8e6ce96.md).




<a name="loioa4eeaf179ee646b99558f27c0bae7b3e__steps_jrg_wt4_zl"/>

## Procedure

1.  Navigate to your subaccount. Make sure that Cloud Foundry is enabled. For more information, see [Navigate to Orgs and Spaces](navigate-to-orgs-and-spaces-5bf8735.md).

2.  In the navigation area, choose *Cloud Foundry* \> *Org Members*.

    The screen displays all members currently assigned to the org in a list.

3.  Choose *Add Members*.

4.  Enter one or more e-mail addresses.

    Use commas \(`,`\), spaces \(``\), semicolons \(`;`\), or line breaks to separate members.

5.  Enter the *Origin* for the identity provider, which hosts the members you just added.

    The default identity provider is ***sap.ids***. For more information, see [Default Identity Provider](default-identity-provider-d6a8db7.md).

    If the new members are platform users from a custom identity provider, enter the origin.

    -   Feature Set A: Choose *Other* and then enter the corresponding origin of the Identity Authentication tenant.

        For more information about finding the origin, see [Establish Trust and Federation of Custom Identity Providers for Platform Users in Multi-Environment Subaccounts \[Feature Set A\]](establish-trust-and-federation-of-custom-identity-providers-for-platform-users-in-multi-8600afb.md).

    -   Feature Set B: Select the corresponding origin of the Identity Authentication tenant.

        > ### Note:  
        > The option to select an origin appears only if you have two or more identity providers.

        For more information about finding the origin, see [Establish Trust and Federation of Custom Identity Providers for Platform Users \[Feature Set B\]](establish-trust-and-federation-of-custom-identity-providers-for-platform-users-feature-c368984.md).


6.  Select roles for the members and save your entries.

    For more information, see [About Roles in the Cloud Foundry Environment](about-roles-in-the-cloud-foundry-environment-0907638.md).




<a name="loioa4eeaf179ee646b99558f27c0bae7b3e__postreq_ocr_wj2_nbb"/>

## Next Steps

-   To select or unselect roles for a member, see [Edit Org Members Using the Cockpit](edit-org-members-using-the-cockpit-fdbeabb.md).

-   To remove all the roles of a member, see [Delete Org Members Using the Cockpit](delete-org-members-using-the-cockpit-35a720c.md).

    This action removes the member from the organization and any spaces in the org.

-   If the users need to view or manage applications in spaces, add the users to the relevant spaces, too.

    For more information, see [Add Space Members Using the Cockpit](add-space-members-using-the-cockpit-81d0b4d.md).


**Related Information**  


[Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

[Add Organization Members Using the Cloud Foundry Command Line Interface](add-organization-members-using-the-cloud-foundry-command-line-interface-1422a5d.md "You can use the Cloud Foundry Command Line Interface (cf CLI) to add organization members and assign roles to them.")

