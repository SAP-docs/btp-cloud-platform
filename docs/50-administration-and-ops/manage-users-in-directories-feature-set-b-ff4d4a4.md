<!-- loioff4d4a4caff94b0486b6427eaa8a0b91 -->

# Manage Users in Directories \[Feature Set B\]

Manage members in your directory using the SAP BTP cockpit.



<a name="loioff4d4a4caff94b0486b6427eaa8a0b91__prereq_egz_33d_cqb"/>

## Prerequisites

-   You're a directory administrator.

-   User management is enabled for this directory.

    Choose *Enable User Management* to enable the user management capabilities for this directory if the feature isn't enabled already.

    > ### Note:  
    > Only one directory in a path can manage entitlements or users.

-   Your platform user exists in a trusted identity provider.

    All users of SAP BTP are stored in identity providers, either in the default or in a custom identity provider. SAP BTP needs a copy of the user, sometimes called a shadow user. You assign the shadow user authorizations to access resources in SAP BTP. When a user authenticates, SAP BTP forwards the request to the identity provider.

    For more information, see [Trust and Federation with Identity Providers](trust-and-federation-with-identity-providers-cb1bc8f.md).




<a name="loioff4d4a4caff94b0486b6427eaa8a0b91__context_nw4_4fx_stb"/>

## Context

You manage directory members by assigning role collections to platform users. Use the following predefined role collections:

-   *Directory Administrator*
-   *Directory Viewer*

For more information about these role collections, see [Role Collections and Roles in Global Accounts, Directories, and Subaccounts \[Feature Set B\]](../10-concepts/role-collections-and-roles-in-global-accounts-directories-and-subaccounts-feature-set-b-0039cf0.md).



## Procedure

1.  Navigate to your directory.

2.  Add a user to your directory.

    For more information, see [Create Users](create-users-a3bc7e8.md).

3.  Assign a role collection to the user.

    For more information, see [Assign Users to Role Collections](assign-users-to-role-collections-c576676.md).




<a name="loioff4d4a4caff94b0486b6427eaa8a0b91__result_t5w_zfx_stb"/>

## Results

The next time this user logs on to the SAP BTP cockpit, the user can access this directory.

**Related Information**  


[Working with Users](working-with-users-2c91f88.md "In the SAP BTP cockpit, you can see the users of your global account or subaccount, user-related identity provider information, and their authorizations. In a user's overview, you can create and delete users, and assign role collections. You can also display an overview of the role collections, where you can drill down all the way to the role, and see the application that the role is belongs to.")

[Role Collections and Roles in Global Accounts, Directories, and Subaccounts \[Feature Set B\]](../10-concepts/role-collections-and-roles-in-global-accounts-directories-and-subaccounts-feature-set-b-0039cf0.md "In the cloud management tools feature set B, SAP BTP provides a set of role collections to set up administrator access to your global account and subaccounts.")

