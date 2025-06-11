<!-- loioa4eeaf179ee646b99558f27c0bae7b3e -->

# Add Org Members

In the SAP BTP cockpit, add users as org members and assign roles to grant the users access to information, such as user and quota information in a Cloud Foundry org.



## Prerequisites

-   You have the Org Manager role for the org in question.

    > ### Note:  
    > When you enable Cloud Foundry and the org is created, the Org Manager role is assigned automatically to you.

    For more information, see [About Roles in the Cloud Foundry Environment](about-roles-in-the-cloud-foundry-environment-0907638.md).

-   The users exist in a trusted platform identity provider.

    For more information, see [About User Management in the Cloud Foundry Environment](about-user-management-in-the-cloud-foundry-environment-8e6ce96.md).




<a name="loioa4eeaf179ee646b99558f27c0bae7b3e__steps_jrg_wt4_zl"/>

## Procedure

1.  Navigate to your subaccount in the cockpit. Make sure that Cloud Foundry is enabled. For more information, see [Navigate to Orgs and Spaces](navigate-to-orgs-and-spaces-5bf8735.md).

2.  In the navigation area, choose *Cloud Foundry* \> *Org Members*.

    The screen displays all members currently assigned to the org in a list.

3.  Choose *Add Members*.

4.  Enter one or more e-mail addresses.

    Use commas \(`,`\), spaces \(``\), semicolons \(`;`\), or line breaks to separate members.

5.  Enter the *Origin* for the identity provider, which hosts the members you just added.

    The default identity provider is ***sap.ids***. For more information, see [Default Identity Provider](default-identity-provider-d6a8db7.md).

    If the new members are platform users from a custom identity provider, enter the origin.

    Select the corresponding origin of the Identity Authentication tenant.

    > ### Note:  
    > The option to select an origin appears only if you have two or more identity providers.

    For more information about finding the origin, see [Establish Trust and Federation of Custom Identity Providers for Platform Users](establish-trust-and-federation-of-custom-identity-providers-for-platform-users-c368984.md).

6.  Select the org roles you want to assign.

    For more information, see [About Roles in the Cloud Foundry Environment](about-roles-in-the-cloud-foundry-environment-0907638.md).

7.  Choose *Add*.




<a name="loioa4eeaf179ee646b99558f27c0bae7b3e__postreq_ocr_wj2_nbb"/>

## Next Steps

-   To change the roles of a member, see [Edit Org Members](edit-org-members-fdbeabb.md).

-   To remove all the roles of a member, see [Delete Org Members](delete-org-members-35a720c.md).

    This action removes the member from the organization and any spaces in the org.

-   If the users need to view or manage applications in spaces, add the users to the relevant spaces, too.

    For more information, see [Add Space Members](add-space-members-81d0b4d.md).


**Related Information**  


[Add Organization Members Using the Cloud Foundry Command Line Interface](add-organization-members-using-the-cloud-foundry-command-line-interface-1422a5d.md "You can use the Cloud Foundry Command Line Interface (cf CLI) to add organization members and assign roles to them.")

