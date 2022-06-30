<!-- loioa4eeaf179ee646b99558f27c0bae7b3e -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Add Org Members Using the Cockpit

Add users as org members and assign roles to grant the users access to user and quota information in a Cloud Foundry org.



## Prerequisites

-   You have the Org Manager role for the org in question.

    > ### Note:  
    > You automatically have the Org Manager role in a subaccount that you created.

-   The users exist in a trusted platform identity provider.

    All users of SAP BTP are stored in identity providers, either in the default or in a custom identity provider. SAP BTP needs a copy of the user, sometimes called a shadow user. You assign the shadow user authorizations to access resources in SAP BTP. When a user authenticates, SAP BTP forwards the request to the identity provider.

    For more information, see [Trust and Federation with Identity Providers](trust-and-federation-with-identity-providers-cb1bc8f.md).




<a name="loioa4eeaf179ee646b99558f27c0bae7b3e__steps_jrg_wt4_zl"/>

## Procedure

1.  Choose the subaccount that contains the org to which you'd like to add members.

2.  In the navigation area, choose *Cloud Foundry* \> *Org Members*.

    All members currently assigned to the org are shown in a list.

3.  Choose *Add Members*.

4.  Enter one or more e-mail addresses.

    Use commas \(`,`\), spaces \(` `\), semicolons \(`;`\), or line breaks to separate members.

    > ### Restriction:  
    > Each time you add members, all entries must be from the same identity provider.

5.  Enter the *Origin* for the identity provider, which hosts the members you just added.

    The default identity provider is ***sap.ids***.

    For more information, see [Default Identity Provider](default-identity-provider-d6a8db7.md).

    If the new members are platform users in a custom identity provider, enter the origin.

    Feature Set A: Choose *Other* and then enter the corresponding Identity Authentication tenant name.

    For more information about finding the tenant name, see [Establish Trust and Federation of Custom Identity Providers for Platform Users in Multi-Environment Subaccounts \[Feature Set A\]](establish-trust-and-federation-of-custom-identity-providers-for-platform-users-in-multi-8600afb.md).

6.  Select roles for the members and save your entries.

    For more information, see [Add Org Members Using the Cockpit](add-org-members-using-the-cockpit-a4eeaf1.md).




<a name="loioa4eeaf179ee646b99558f27c0bae7b3e__postreq_ocr_wj2_nbb"/>

## Next Steps

-   To select or unselect roles for a member, choose <span class="SAP-icons"></span> \(Edit\). The changes you make to the roles of a member take effect immediately.
-   To remove all the roles of a member, choose <span class="SAP-icons"></span> \(Delete\). This action removes the member from the organization.

    > ### Note:  
    > You can only remove org members who are no longer assigned to any space in the org.

-   If the users need to view or manage applications in spaces, add the users to the relevant spaces, too.

    For more information, see [Add Space Members Using the Cockpit](add-space-members-using-the-cockpit-81d0b4d.md).


**Related Information**  


[Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

[Log On to Your Global Account](log-on-to-your-global-account-77be288.md "Use the SAP BTP cockpit to log on to your global account and start working in SAP BTP.")

[Navigate to Orgs and Spaces](navigate-to-orgs-and-spaces-5bf8735.md "To administer your Cloud Foundry environment, navigate to orgs, and spaces in the SAP BTP cockpit.")

