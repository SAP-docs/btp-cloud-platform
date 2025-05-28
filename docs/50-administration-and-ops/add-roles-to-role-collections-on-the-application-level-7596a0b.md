<!-- loio7596a0bdab4649ac8a6f6721dc72db19 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Add Roles to Role Collections on the Application Level

Roles are used to define the type of access granted to an application.



<a name="loio7596a0bdab4649ac8a6f6721dc72db19__context_fkg_xk2_5jb"/>

## Context

A role is an instance of a role template; you can build a role based on a role template and assign the role to a role collection. Role collections are then assigned to SAML 2.0 groups or users. The role template defines the type of access permitted for an application, for example: the authorization scope, and any attributes that need to be applied. Attributes define information that comes with the respective user, for example 'cost center' or 'country' \(see the related link\). This information can only be resolved at run time.

> ### Note:  
> The User Account and Authentication service automatically creates default roles for all role templates that do not include attribute references. They have the same name as the role template. You can't delete them. You can recognize them because their description contains *Default Instance*.



<a name="loio7596a0bdab4649ac8a6f6721dc72db19__steps_emy_b51_d5"/>

## Procedure

1.  Open the SAP BTP cockpit.

2.  Go to your global account and subaccount \(see [Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md)\).

3.  Choose *Security* in the navigation pane or go to *Cloud Foundry* \> *Spaces* \> *<your\_space\>* \> *<your\_application\>*.

4.  Choose *Security* \> *Roles* in the navigation pane.

    Here you see a complete list of all roles sorted by role templates. It also contains information about attributes used in this role and about the role collections the role has been added to. On the right side, you find the action buttons.

    > ### Note:  
    > You cannot edit or delete predefined roles for default role collections. For this reason, the action buttons are grayed out. For more information, see the related link.

5.  To directly assign a role to role collections, choose the action button :heavy_plus_sign: \(Add to role collection\) in the same row.

    A new window shows all role collections that are available in your global account orsubaccount.

6.  Select the role collections to which you want to add your role.

7.  Choose *Add*.

    The number in the role collections column counts up. You have now assigned this role to the role collections you selected earlier.


**Related Information**  


[Attributes](attributes-713f52a.md "Attributes use information that is specific to the user, for example the user's country. If the application developer in the Cloud Foundry environment of SAP BTP has created a country attribute to a role, this restricts the data a business user can see based on this attribute.")

[Role Collections and Roles in Global Accounts, Directories, and Subaccounts](../10-concepts/role-collections-and-roles-in-global-accounts-directories-and-subaccounts-0039cf0.md "SAP BTP provides a set of role collections to set up administrator access to your global account and subaccounts.")

[Cloud Management Tools](../10-concepts/cloud-management-tools-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

