<!-- loio37f8871865114f44aebee3db6ac64b72 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Configure Entitlements and Quotas for Directories \[Feature Set B\]

> ### Note:  
> This feature is new in Feature Set B so there is no equivalent in Feature Set A. For more information, see [Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md).

Distribute entitlements that are available in your global account to directories by adding service plans and their allowed quotas by using the SAP BTP cockpit.

<a name="task_pxy_ph1_ryb"/>

<!-- task\_pxy\_ph1\_ryb -->

## Enable Entitlement Management for a Directory

Before you can assign plans and quotas to a directory so that they can be further distributed to the directory's subaccounts, you must first enable the **entitlement management** feature for the directory. This configuration only needs to be done once for each directory.

> ### Note:  
> -   In the account hierarchy, each directory path can have only one directory enabled with the entitlement management feature \(or the user management feature\). Consequently, if a directory in the path already has one of these features enabled, it is not possible to enable either of them for other parent or child directories within the same path as this directory.
> 
> -   Enabling entitlement management for a directory that already contains subaccounts will result in the automatic assignment of any existing assignments and quotas \(for the subaccounts\) to the directory.



<a name="task_pxy_ph1_ryb__prereq_qxy_ph1_ryb"/>

## Prerequisites

-   You are a global account administrator.




<a name="task_pxy_ph1_ryb__steps-unordered_xxj_1j1_ryb"/>

## Procedure

There are several ways you can enable the entitlement management feature for a directory:

-   In the *Account Explorer*, click the <span class="SAP-icons"></span> Actions button for a specific directory and select *Edit*. In the *Edit Directory* dialog box, under *Advanced*, choose the *Enable entitlement management* option.

-   Navigate to the directory's *Entitlements* page and select *Enable Entitlement Management*.

-   Navigate to your global account and open the *Entitlements* \> *Entity Assignments* from the navigation panel. Select the <span class="SAP-icons"></span> icon in the *Select Entity* dropdown menu.

    Then, in the *Select Entities* dialog box, choose the directory for which you want to manage assignments. Click *Select* and then *Enable Entitlement Management*.

    > ### Tip:  
    > To disable entitlement management for a directory, redo these steps from the global account's *Entitlements* \> *Entity Assignments* page, but choose *Disable Entitlement Management* at then end. When you disable entitlement management, any assignments and quota that are currently assigned to the directory are "returned" to the global account and are then available for distribution to other directories and subaccounts.




<a name="task_pxy_ph1_ryb__postreq_rmz_nng_ryb"/>

## Next Steps

Once you've enabled entitlement management for a directory, you can now configure its entitlement and quota assignments as described below.

<a name="task_amv_krf_mqb"/>

<!-- task\_amv\_krf\_mqb -->

## Configure Assignments and Quotas for a Single Directory



<a name="task_amv_krf_mqb__prereq_bmv_krf_mqb"/>

## Prerequisites

-   You are a global account administrator.

    > ### Note:  
    > If the directory has user management enabled, then you must be an admininstrator of the directory. See [Manage Users in Directories \[Feature Set B\]](manage-users-in-directories-feature-set-b-ff4d4a4.md).

-   The service and applications that you intend to assign to your directory must be entitled to your global account.

    -   For enterprise accounts that use the subscription-based commercial model, your account receives only the services that you've already purchased and subscribed to according to your SAP BTP contract. To access additional services, at an extra cost, you can modify your contract via your sales representative or account executive.

    -   For enterprise accounts that use the consumption-based commercial model, your global account receives all pay-for-use and free services that are eligible for this commercial model.

    -   If you have a trial account, you'll receive a restricted set of free platform resources and services for a limited time period. To access additional services, you'll have to switch to an enterprise account.





<a name="task_amv_krf_mqb__steps_dmv_krf_mqb"/>

## Procedure

1.  In the *Account Explorer*, navigate to the directory for which you want to manage assignments.

2.  Navigate to *Entitlements* \> *Entity Assignments*.

    > ### Note:  
    > If your directory does not have the entitlement management feature enabled yet, it won't have a *Entity Assignments* child page. To enable the feature for that directory, in the directory's *Entitlements* page, select *Enable Entitlement Management*.

3.  Click *Configure Entitlements*.

4.  You can now edit the assignments table:


    <table>
    <tr>
    <th valign="top">

    Action
    
    </th>
    <th valign="top">

    Steps
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    **Add new service plans to the directory**
    
    </td>
    <td valign="top">
    
    Choose *Add Service Plans* and from the dialog select the services and the plans from each service that you would like to add to the directory. Choose *Add <x\> Service Plans* in the dialog to confirm.

    Remember, the services that you see depend on the type of global account you have and your contract details \(see the prerequisites above for more information\).

    Once you've added new service plans, you can also change the quota for those plans as described in the following row and enable the option to auto-assign quota to new subaccounts that are added to the directory. For service plans where quota can be increased or decreased, you can also specify what amount should be auto-assigned to each subaccount that is created or added to the directory.

    > ### Note:  
    > To subscribe a subaccount to a multitenant application, you must first assign the application to the specific subaccount using the process described in [Configure Entitlements and Quotas for Subaccounts](configure-entitlements-and-quotas-for-subaccounts-5ba357b.md).

    > ### Tip:  
    > If your global account is configured to consume remote services from a non-SAP cloud vendor \(resource provider\), an additional dropdown list is displayed in the *Service Details* pane, where you can choose a configured resource provider. You can then choose the required service plans that are available for the selected resource provider to add them to the subaccount.
    > 
    > For more information, see [Managing Resource Providers](managing-resource-providers-e2c250d.md).


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Edit the quota for one or more service plans**
    
    </td>
    <td valign="top">
    
    Use :heavy_plus_sign: and :heavy_minus_sign: to increase or decrease the quota for each service plan.

    If you would like to have quota automatically assigned to subaccounts that are created or moved to the directory, follow the same process to set the amount that should be auto-assigned to each subaccount.

    > ### Note:  
    > -   The auto-assign feature doesn't apply to subaccounts that are already in the directory when the feature is enabled.
    > 
    > -   You cannot use the auto-assign feature with beta services and applications.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Delete a service plan and its quota from the directory**
    
    </td>
    <td valign="top">
    
    Choose :wastebasket: from the *Actions* column.
    
    </td>
    </tr>
    </table>
    
5.  Once you're done, choose *Save* to save the changes and exit edit mode for that directory.


<a name="task_mtd_ssf_mqb"/>

<!-- task\_mtd\_ssf\_mqb -->

## Configure Assignments and Quotas for Multiple Directories

You can also use this method to configure assignments and quotas for a single directory.



<a name="task_mtd_ssf_mqb__prereq_ntd_ssf_mqb"/>

## Prerequisites

-   You are a global account administrator.

    > ### Note:  
    > If a directory has user management enabled, then you must be an admininstrator of the directory. See [Manage Users in Directories \[Feature Set B\]](manage-users-in-directories-feature-set-b-ff4d4a4.md).

-   The service and applications that you intend to assign to your directories must be entitled to your global account.

    -   For enterprise accounts that use the subscription-based commercial model, your account receives only the services that you've already purchased and subscribed to according to your SAP BTP contract. To access additional services, at an extra cost, you can modify your contract via your sales representative or account executive.

    -   For enterprise accounts that use the consumption-based commercial model, your global account receives all pay-for-use and free services that are eligible for this commercial model.

    -   If you have a trial account, you'll receive a restricted set of free platform resources and services for a limited time period. To access additional services, you'll have to switch to an enterprise account.





<a name="task_mtd_ssf_mqb__steps_ptd_ssf_mqb"/>

## Procedure

1.  Navigate to your global account.

2.  Choose *Entitlements* \> *Entity Assignments* from the left hand-side navigation.

3.  Select the <span class="SAP-icons"></span> icon in the *Select Entity* dropdown menu.

4.  In the *Select Entities* dialog box, choose the directories for which you want to manage assignments.

5.  Click *Select*.

    > ### Note:  
    > If you select a directory for which entitlement management is not enabled, you can click *Enable Entitlement Management* to enable the feature. Remember that you can enable this feature only for a single directory in a path.

    You get a table for each of the directories you selected, displaying the current assignments and quotas. You can choose *Show subaccount assignments* next to the table title to see the assignments and quotas for the subaccounts in a specific directory.

6.  Choose *Configure Entitlements* to start editing assignments for a particular directory.

    > ### Note:  
    > You can only edit assignments for one directory at a time.

7.  You can now edit the assignments table:


    <table>
    <tr>
    <th valign="top">

    Action
    
    </th>
    <th valign="top">

    Steps
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    **Add new service plans to the directory**
    
    </td>
    <td valign="top">
    
    Choose *Add Service Plans* and from the dialog select the services and the plans from each service that you would like to add to the directory. Choose *Add <x\> Service Plans* in the dialog to confirm.

    Remember, the services that you see depend on the type of global account you have and your contract details \(see the prerequisites above for more information\).

    Once you've added new service plans, you can also change the quota for those plans as described in the following row and enable the option to auto-assign quota to new subaccounts that are added to the directory. For service plans where quota can be increased or decreased, you can also specify what amount should be auto-assigned to each subaccount that is created or added to the directory.

    > ### Note:  
    > To subscribe a subaccount to a multitenant application, you must first assign the application to the specific subaccount using the process described in [Configure Entitlements and Quotas for Subaccounts](configure-entitlements-and-quotas-for-subaccounts-5ba357b.md).

    > ### Tip:  
    > If your global account is configured to consume remote services from a non-SAP cloud vendor \(resource provider\), an additional dropdown list is displayed in the *Service Details* pane, where you can choose a configured resource provider. You can then choose the required service plans that are available for the selected resource provider to add them to the subaccount.
    > 
    > For more information, see [Managing Resource Providers](managing-resource-providers-e2c250d.md).


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Edit the quota for one or more service plans**
    
    </td>
    <td valign="top">
    
    Use :heavy_plus_sign: and :heavy_minus_sign: to increase or decrease the quota for each service plan.

    If you would like to have quota automatically assigned to subaccounts that are created or moved to the directory, follow the same process to set the amount that should be auto-assigned to each subaccount.

    > ### Note:  
    > -   The auto-assign feature doesn't apply to subaccounts that are already in the directory when the feature is enabled.
    > 
    > -   You cannot use the auto-assign feature with beta services and applications.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Delete a service plan and its quota from the directory**
    
    </td>
    <td valign="top">
    
    Choose :wastebasket: from the *Actions* column.
    
    </td>
    </tr>
    </table>
    
8.  Once you're done, choose *Save* to save the changes and exit edit mode for that directory.

9.  **Optional:** Repeat steps 6 to 7 to configure assignments for the other selected directories.


**Related Information**  


[Entitlements and Quotas](../10-concepts/entitlements-and-quotas-00aa2c2.md "When you purchase an enterprise account, you’re entitled to use a specific set of resources, such as the amount of memory that can be allocated to your applications.")

[Directories \[Feature Set B\]](../10-concepts/account-model-8ed4a70.md#loioa92721fc75524ec09a7a7255997dbd94 "Directories allow you to organize and manage your subaccounts according to your technical and business needs.")

[Manage Users in Directories \[Feature Set B\]](manage-users-in-directories-feature-set-b-ff4d4a4.md "Manage members in your directory using the SAP BTP cockpit.")

[Create a Directory \[Feature Set B\]](create-a-directory-feature-set-b-b8ef1c4.md "Create a directory using the SAP BTP cockpit to organize and manage your subaccounts. For example, you can group subaccounts by project, team, or department.")

[Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

