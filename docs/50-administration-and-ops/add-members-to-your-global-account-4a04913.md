<!-- loio4a0491330a164f5a873fa630c7f45f06 -->

# Add Members to Your Global Account

Add users as global account members using the SAP BTP cockpit.



<a name="loio4a0491330a164f5a873fa630c7f45f06__prereq_ukv_qjz_ncc"/>

## Prerequisites

-   You must be a global account administrator to add other global account members.

    If you don't have a global account administrator or one isn't available, there is a workaround using SAP for Me.

    For more information, see [2669325 - How to add a user as a Global Account administrator for SAP Business Technology Platform](https://me.sap.com/notes/0002669325).

-   The users exist in a trusted platform identity provider.

    All users of SAP BTP are stored in identity providers, either in the default or in a custom identity provider. SAP BTP needs a copy of the user, sometimes called a shadow user. You assign the shadow user authorizations to access resources in SAP BTP. When a user authenticates, SAP BTP forwards the request to the identity provider.

    For more information, see [Trust and Federation with Identity Providers](trust-and-federation-with-identity-providers-cb1bc8f.md).




<a name="loio4a0491330a164f5a873fa630c7f45f06__context_dlv_qjz_ncc"/>

## Context

Assign predefined or custom role collections to users who need to manage or view the global account in SAP BTP cockpit. Examples of predefined role collections include the following:

-   *Global Account Administrator*

-   *Global Account Viewer*


For more information about these role collections, see [Role Collections and Roles in Global Accounts, Directories, and Subaccounts](../10-concepts/role-collections-and-roles-in-global-accounts-directories-and-subaccounts-0039cf0.md).



<a name="loio4a0491330a164f5a873fa630c7f45f06__steps_flv_qjz_ncc"/>

## Procedure

1.  Navigate to your global account.

2.  Add a user to your global account.

    For more information, see [Create Users](create-users-a3bc7e8.md).

    > ### Note:  
    > If the user is already a user in a subaccount and has logged on to SAP BTP cockpit, SAP BTP adds the user at the global account level automatically, but without any role collections.

3.  Assign a role collection to the user.

    For more information, see [Assign Users to Role Collections](assign-users-to-role-collections-c576676.md).




<a name="loio4a0491330a164f5a873fa630c7f45f06__result_glv_qjz_ncc"/>

## Results

The next time this user logs on to the SAP BTP cockpit, the user can access this global account.

**Related Information**  


[User and Member Management](../10-concepts/user-and-member-management-cc1c676.md "On SAP BTP, member management takes place at all levels from global account to environment, while user management is relevant for business applications.")

