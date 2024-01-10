<!-- loio2e2a5b67f5ba4782a9070534148e8426 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Manage the Account Explorer Hierarchy \[Feature Set B\]

Create an account structure by creating a hierarchy of directories and subaccounts using the SAP BTP cockpit. Add, move, and delete subaccounts and directories in your structure.



<a name="loio2e2a5b67f5ba4782a9070534148e8426__context_rns_xdt_1qb"/>

## Context

Here, you'll learn how to:

-   Add directories and subaccounts to a directory

-   Move directories and subaccounts in the account structure

-   Delete directories and subaccounts from the account structure

-   Export the account structure to Microsoft Excel format.


A subaccount moves with its assigned service plans and quota. The entitlements of the source and target directories are adjusted accordingly.

If any entitlement for a plan in the target directory is configured with the auto-assign option, it is then automatically applied to the moved subaccount. Automatic quota assignments are subject to available quota in the target directory.

You can create a hierarchical structure that is up to 7 levels deep. The highest level of a given path is always the global account and the lowest is a subaccount, which means that you can have up to 5 levels of directories between the global account and the lowest level subaccount.



<a name="loio2e2a5b67f5ba4782a9070534148e8426__steps-unordered_nvj_ppn_szb"/>

## Procedure

-   Add directories and subaccounts to a directory.

    -   In the *Create* dropdown, choose *Directory*.

        When creating the new directory, you choose its location in the account structure by selecting its parent directory or the global account directly in the creation dialog box.

    -   You can also create a directory by selecting *Create Directory* from the <span class="SAP-icons"></span> Actions menu button for the global account or a specific parent directory.


-   Move subaccounts in the account structure.

    -   Click <span class="SAP-icons"></span> Actions and select *Edit*. Then select a new parent.

    -   Click <span class="SAP-icons"></span> Actions and select *Move*. Then select a new parent.

    -   Click <span class="SAP-icons"></span> Move to move subaccounts by drag and dropping.


-   Delete directories and subaccounts from the account structure.

    -   Click <span class="SAP-icons"></span> Actions and select *Delete*.

    -   To delete a subaccount, you can also navigate into the subaccount and click *Delete Subaccount*.


-   Export the account structure to Microsoft Excel format.

    -   Click <span class="SAP-icons"></span> Export.

        The exported Microsoft Excel file contains a sheet \(tab\) called *Account Structure*, which lists all the subaccounts and directories in the account structure, and includes information about each entity. Each subaccount and directory displays its name, ID, description, path, creation/change dates, and the user that created it.

        Subaccounts also display information about their environment, provider, region, used for production setting, and whether the beta feature option is enabled. Directories also display whether they are configured to manage users and entitlements.



**Related Information**  


[Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

[Directories \[Feature Set B\]](../10-concepts/account-model-8ed4a70.md#loioa92721fc75524ec09a7a7255997dbd94 "Directories allow you to organize and manage your subaccounts according to your technical and business needs.")

[Create a Directory \[Feature Set B\]](create-a-directory-feature-set-b-b8ef1c4.md "Create a directory using the SAP BTP cockpit to organize and manage your subaccounts. For example, you can group subaccounts by project, team, or department.")

[Create a Subaccount](create-a-subaccount-05280a1.md "Create subaccounts in your global account using the SAP BTP cockpit.")

[Delete a Subaccount](delete-a-subaccount-419dc3d.md "Delete subaccounts using the SAP BTP cockpit to clean up your account hierarchy, free up quota used by services in your subaccounts, and to reduce overall costs.")

