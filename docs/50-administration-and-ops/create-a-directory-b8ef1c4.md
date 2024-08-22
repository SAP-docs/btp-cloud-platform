<!-- loiob8ef1c48499a49e9a2dc1d1c8de0a85a -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Create a Directory

Create a directory using the SAP BTP cockpit to organize and manage your subaccounts. For example, you can group subaccounts by project, team, or department.



## Context

> ### Recommendation:  
> Before creating your subaccounts, we recommend you learn more about [Setting Up Your Account Model](https://help.sap.com/viewer/df50977d8bfa4c9a8a063ddb37113c43/Cloud/en-US/2db81f42f5194454beecde6cd4994dda.html "The hierarchical structure between global accounts, directories, and subaccounts lets you define an account model that accurately fits your business and development needs.") :arrow_upper_right:.

For more information about directories, see [Directories](../10-concepts/account-model-8ed4a70.md#loioa92721fc75524ec09a7a7255997dbd94).



## Procedure

1.  In your global account, navigate to the *Account Explorer* page.

2.  In the *Create* dropdown, choose *Directory*.

    > ### Tip:  
    > You can also create a directory by selecting *Create Directory* from the <span class="SAP-icons-V5"></span> Actions menu button of the global account or an existing directory.

3.  In the *Create Directory* dialog box, enter a display name for your new directory and choose a parent. The parent can be the global account or another directory.

4.  **Optional:** Under *Advanced*, choose the *Enable entitlement management* option if you want to manage the entitlements that are used by the subaccounts under this directory. This allows you to reserve quota for service plans so that they cannot be assigned to other subaccounts or directories. For more information, see [Entitlements and Quotas](../10-concepts/entitlements-and-quotas-00aa2c2.md) and [Configure Entitlements and Quotas for Directories](configure-entitlements-and-quotas-for-directories-37f8871.md).

    You can enable this feature later from the *Entitlements* \> *Entity Entitlements* page or by editing the directory in the *Account Explorer* page.

    If you don't enable this feature, then subaccounts in this directory use the entitlements and quota from the global account level.

    > ### Note:  
    > Only a single directory in any given directory path can have the user management \(see next option\) and/or entitlement management features enabled.
    > 
    > For example, if you have 3 stacked directories in your account hierarchy and the middle directory has both the user and entitlement management features enabled, then neither of these features can be enabled for its parent or child directory since these two directories are in the same direct path as the middle directory.

5.  **Optional:** Under *Advanced*, choose the *Enable user management* option if you want to assign specific users as administrators or viewers of this directory. For more information, see [Manage Users in Directories](manage-users-in-directories-ff4d4a4.md).

    You can enable this feature later from the directory's *Users* page or by editing the directory in the *Account Explorer* page.

    If you don't enable this feature, then any user that has access to the directory in the account hierarchy can view and work in it.

    > ### Note:  
    > -   The user management feature can be enabled only in combination with the entitlement management feature on the same directory in given path.
    > 
    > -   Only a single directory in any given directory path can have the user management and/or entitlement management features enabled.
    > 
    >     For example, if you have 3 stacked directories in your account hierarchy and the middle directory has both the user and entitlement management features enabled, then neither of these features can be enabled for its parent or child directory since these two directories are in the same direct path as the middle directory.

6.  **Optional:** Under *Advanced* \> *Labels*, assign labels to the directory to make organizing and filtering your directories and their subaccounts easier. For more information, see [Labels](../10-concepts/account-model-8ed4a70.md#loioe8663c08ead648faa673b0d63c5b478e).

    > ### Tip:  
    > -   When adding multiple values to a label, press [Enter\] after each value.
    > -   When you start typing, any matching label names and values that are already assigned to other directories in your global account are offered as suggestions.

    > ### Note:  
    > All subaccounts in the path of this directory also inherit all labels that are assigned to this directory.

7.  Review the details of your directory and choose *Create* to finalize the process.




<a name="loiob8ef1c48499a49e9a2dc1d1c8de0a85a__result_cfq_gxk_kkb"/>

## Results

Your directory is created.



<a name="loiob8ef1c48499a49e9a2dc1d1c8de0a85a__postreq_xpr_bxk_kkb"/>

## Next Steps

Once you've created a directory, you can perform the following actions:

-   Edit the directory - you can edit the name, description, entitlements, and labels of the directory.
-   Add subaccounts to the directory - [Manage the Account Explorer Hierarchy](manage-the-account-explorer-hierarchy-2e2a5b6.md).
-   Assign users and entitlements to the directory \(if you've enabled the user and entitlement management features, respectively\).
-   Delete the directory - you can only delete a directory that does not contain any subaccounts or subdirectories.

**Related Information**  


[Directories](../10-concepts/account-model-8ed4a70.md#loioa92721fc75524ec09a7a7255997dbd94 "With directories, you can organize and manage your subaccounts according to your technical and business needs.")

[Manage the Account Explorer Hierarchy](manage-the-account-explorer-hierarchy-2e2a5b6.md "Create an account structure by creating a hierarchy of directories and subaccounts using the SAP BTP cockpit. Add, move, and delete subaccounts and directories in your structure.")

[Manage Users in Directories](manage-users-in-directories-ff4d4a4.md "Manage members in your directory using the SAP BTP cockpit.")

[Configure Entitlements and Quotas for Directories](configure-entitlements-and-quotas-for-directories-37f8871.md "Distribute entitlements that are available in your global account to directories by adding service plans and their allowed quotas by using SAP BTP cockpit.")

[View Directory Usage Analytics](view-directory-usage-analytics-a287782.md "You can explore, compare, and analyze all your actual usage data for the services and applications that are available in your directory.")

[Labels](../10-concepts/account-model-8ed4a70.md#loioe8663c08ead648faa673b0d63c5b478e "Labels are user-defined words or phrases that you can assign to various entities in SAP BTP to categorize them in your global account, to identify them more easily.")

