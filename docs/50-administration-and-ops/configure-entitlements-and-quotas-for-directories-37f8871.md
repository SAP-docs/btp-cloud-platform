<!-- loio37f8871865114f44aebee3db6ac64b72 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Configure Entitlements and Quotas for Directories

> ### Note:  
> Directories are available only in \[Feature Set B\], and there is no equivalent in \[Feature Set A\]. For more information, see [Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md).

Distribute entitlements that are available in your global account to directories by adding service plans and their allowed quotas by using SAP BTP cockpit.

<a name="task_pxy_ph1_ryb"/>

<!-- task\_pxy\_ph1\_ryb -->

## Enable Entitlement Management for a Directory

Before you can assign plans and quotas to a directory so that they can be further distributed to the subaccounts in the directory, you must first enable the **entitlement management** feature for the directory. This configuration only needs to be done once for each directory. In this documentation, we'll refer to these types of directories as "managed directories".

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

-   In the *Account Explorer*, click the <span class="SAP-icons-V5"></span> Actions button for a specific directory and select *Edit*. In the *Edit Directory* dialog box, under *Advanced*, choose the *Enable entitlement management* option.

-   Navigate to the directory's *Entitlements* page and select *Enable Entitlement Management*.

-   Navigate to your global account and open the *Entitlements* \> *Entity Assignments* from the navigation panel. Select the <span class="SAP-icons-V5"></span> icon in the *Select Entity* dropdown menu.

    Then, in the *Select Entities* dialog box, choose the directory for which you want to manage assignments. Click *Select* and then *Enable Entitlement Management*.

    > ### Tip:  
    > To disable entitlement management for a directory, redo these steps from the global account's *Entitlements* \> *Entity Assignments* page, but choose *Disable Entitlement Management* at the end. When you disable entitlement management, any assignments and quota that are currently assigned to the directory are "returned" to the global account and are then available for distribution to other directories and subaccounts.




<a name="task_pxy_ph1_ryb__postreq_rmz_nng_ryb"/>

## Next Steps

Once you've enabled entitlement management for a directory, you can now configure its service plan and quota assignments as described below.

<a name="task_mtd_ssf_mqb"/>

<!-- task\_mtd\_ssf\_mqb -->

## Configure Assignments and Quotas for Managed Directories

Use this procedure to configure the service plan assignments and quotas for one or more managed directories.

> ### Note:  
> To get an overview of all the services and plans available in your global account, navigate to the *Entitlements* \> *Service Assignments* page. There you can see the global usage of each service plan in the *All Services* view, as well as the detailed assignments of each service across subaccounts and directories in the *Assignments by Service* view.
> 
> -   In the *All Services* view of this page, the *Assigned To* column shows you the total number of directories and subaccounts to which each service plan is assigned in your global account. You can click on the links in this column to quickly navigate to the selected service in the *Assignments by Service* view and display more details about these assignments.
> 
> -   You can turn on the *Show commercial info* toggle option in the *Service Assignments* page to display additional table columns that can help you to gain a better understanding of the relationship between contractual service entitlements and the technical assets \(services and plans\) in your global account; in other words, how each entitled plan was added to your global account.
> 
> -   The *Service Assignments* page is for viewing purposes only; you cannot make any assignment changes from it.
> 
> 
> You can also access the *Entitlements* \> *Service Assignments* page from the directory level \(only for directories that are configured to manage entitlements\) to display the directory's assignments.



<a name="task_mtd_ssf_mqb__prereq_ntd_ssf_mqb"/>

## Prerequisites

-   You are a global account administrator.

    Note that if the directory also has the user management feature enabled, then you must be either the directory administrator or a global administrator. See [Manage Users in Directories](manage-users-in-directories-ff4d4a4.md).

-   The service and applications that you intend to assign to your directories must be entitled to your global account.

    -   For enterprise accounts that use the subscription-based commercial model, your account receives only the services that you've already purchased and subscribed to according to your SAP BTP contract. To access additional services, at an extra cost, you can modify your contract via your sales representative or account executive.

    -   For enterprise accounts that use the consumption-based commercial model, your global account receives all pay-for-use and free services that are eligible for this commercial model.

    -   If you have a trial account, you'll receive a restricted set of free platform resources and services for a limited time period. To access additional services, you'll have to switch to an enterprise account.





<a name="task_mtd_ssf_mqb__steps_ptd_ssf_mqb"/>

## Procedure

1.  Navigate to your global account.

2.  Choose *Entitlements* \> *Entity Assignments* from the left hand-side navigation.

    Alternatively, you can navigate to a directory from the *Account Explorer*, and then access the *Entitlements* \> *Entity Assignments* page for that specific directory.

3.  Open the *Manage Assignments* view \(tab\).

    Skip this step if you have a trial account.

    > ### Tip:  
    > You can use the *View Commercial Information* view in this page to display comprehensive commercial information about the entitlements in your global account \(you cannot make assignments in this view\). Note that this view is not available for trial accounts.

4.  Select the <span class="SAP-icons-V5"></span> icon in the *Directories / Subaccounts* dropdown menu.

5.  In the *Select Subaccounts and Directories* dialog box, choose the directories for which you want to manage assignments.

6.  Click *Select*.

    > ### Note:  
    > If you select a directory for which entitlement management is not enabled, you can click *Enable Entitlement Management* to enable the feature. Remember that you can enable this feature only for a single directory in a path.

    You get a table for each of the directories you selected, displaying the current assignments and quotas. You can choose *Show subaccount assignments* next to the table title to see the assignments and quotas for the subaccounts in a specific directory.

    > ### Tip:  
    > Under the *Service Technical Name* column, click on the <span class="SAP-icons-V5"></span> \(Service Details\) icon of any service to access its service-related links to documentation, support information, and SAP Discovery Center.

7.  Choose *Edit* to start editing assignments for a particular directory.

    > ### Note:  
    > You can only edit assignments for one directory at a time.

8.  You can now edit the assignments table:


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
    
    Choose *Add Service Plans* and from the dialog box select the services and the plans from each service that you would like to add to the directory. Choose *Add <x\> Service Plans* in the dialog box to confirm.

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
    
    Use :heavy_plus_sign: and :heavy_minus_sign: in the *Quota Assignment* column to increase or decrease the quota for each service plan.

    Note some service plans do not have a numeric quota assignment. In other words, you do not assign a specific quantity but grant access to the plan by simply assigning it to the subaccount. See *Quotas* in [Managing Entitlements and Quotas Using the Cockpit](managing-entitlements-and-quotas-using-the-cockpit-c824874.md).

    > ### Tip:  
    > If you would like to have quota automatically assigned to subaccounts that are created or moved to the directory, select the *Auto-Assign to Subaccounts* checkbox and follow the same process to set the amount that should be auto-assigned to each subaccount.
    > 
    > -   The auto-assign feature doesn't apply to subaccounts that are already in the directory when the feature is enabled.
    > 
    > -   You cannot use the auto-assign feature with beta services and applications.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    **Set a quota limit to unlimited service plans that use the consumption-based commercial model**
    
    </td>
    <td valign="top">
    
    The usage of most service plans is unlimited by default in global accounts that use the consumption-based commercial model. To control costs of such plans, you can set a quota limit on the service plans for this directory by first selecting the checkbox in the *Set Quota Limit* column.

    Now, you can increase or decrease the quota for this service plan in the *Quota Assignment* column by using :heavy_plus_sign: and :heavy_minus_sign:.

    Note some service plans do not have a numeric quota assignment. In other words, you do not assign a specific quantity but grant access to the plan by simply assigning it to the directory \(and then subsequently to the subaccount\). See *Quotas* in [Managing Entitlements and Quotas Using the Cockpit](managing-entitlements-and-quotas-using-the-cockpit-c824874.md).
    
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
    
9.  Once you're done, choose *Save* to save the changes and exit edit mode for that directory.

10. **Optional:** Repeat steps 7 to 9 to configure assignments for the other selected directories.


**Related Information**  


[Entitlements and Quotas](../10-concepts/entitlements-and-quotas-00aa2c2.md "When you purchase an enterprise account, you’re entitled to use a specific set of resources, such as the amount of memory that can be allocated to your applications.")

[Directories](../10-concepts/account-model-8ed4a70.md#loioa92721fc75524ec09a7a7255997dbd94 "With directories, you can organize and manage your subaccounts according to your technical and business needs.")

[Manage Users in Directories](manage-users-in-directories-ff4d4a4.md "Manage members in your directory using the SAP BTP cockpit.")

[Create a Directory](create-a-directory-b8ef1c4.md "Create a directory using the SAP BTP cockpit to organize and manage your subaccounts. For example, you can group subaccounts by project, team, or department.")

[Managing Entitlements and Quotas Using the Cockpit](managing-entitlements-and-quotas-using-the-cockpit-c824874.md "When you purchase an enterprise account, you are entitled to use a specific set of resources, such as the amount of memory that can be allocated to your applications.")

[Configure Entitlements and Quotas for Subaccounts](configure-entitlements-and-quotas-for-subaccounts-5ba357b.md "Distribute the entitlements that are available in your global account by adding service plans and their allowed quotas to your subaccounts using SAP BTP cockpit.")

[Using Free Service Plans](../10-concepts/using-free-service-plans-524e108.md "The free tier model for SAP BTP lets you try out services in global accounts without any additional cost using the consumption-based commercial model and an enterprise account.")

[Trial Accounts and Free Tier](../10-concepts/trial-accounts-and-free-tier-046f127.md "Explore the different options for trying out SAP BTP.")

