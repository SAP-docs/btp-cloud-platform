<!-- loio37f8871865114f44aebee3db6ac64b72 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Configure Entitlements and Quotas for Directories \[Feature Set B\]

> ### Note:  
> This feature is new in Feature Set B so there is no equivalent in Feature Set A. For more information, see [Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md).

Assign entitlements to directories by adding service plans and distribute the quotas available in your global account to your directories using the SAP BTP cockpit.

 <a name="task_amv_krf_mqb"/>

<!-- task\_amv\_krf\_mqb -->

## Configure Entitlements and Quotas for a Single Directory \[Feature Set B\]



<a name="task_amv_krf_mqb__prereq_bmv_krf_mqb"/>

## Prerequisites

-   You are a global account administrator.

-   The service and applications that you intend to assign to your directory must be entitled to your global account.

    -   For enterprise accounts that use the subscription-based commercial model, your account receives only the services that you've already purchased and subscribed to according to your SAP BTP contract. To access additional services, at an extra cost, you can modify your contract via your sales representative or account executive.

    -   For enterprise accounts that use the consumption-based commercial model, your global account receives all pay-for-use and free services that are eligible for this commercial model.

    -   If you have a trial account, you'll receive a restricted set of free platform resources and services for a limited time period. To access additional services, you'll have to switch to an enterprise account.





<a name="task_amv_krf_mqb__steps_dmv_krf_mqb"/>

## Procedure

1.  In the *Account Explorer*, navigate to the directory for which you want to manage entitlements.

2.  If entitlement management is not yet enabled for this directory yet, navigate to the directory's *Entitlements* page and select *Enable Entitlement Management*.

    > ### Tip:  
    > You can quickly tell if the entitlement management has enabled if the directory's *Entitlements* page in the navigation panel has two subpages, *Entity Assignments* and *Service Assignments*. Also the directory's *Overview* page will have the *Disable Entitlement Management* button.

    > ### Note:  
    > Any given directory path in the account hierarchy can have only one directory that is enabled with the entitlement management feature \(or with the authorization management feature\). If such a directory exists, other directories in that path can only have the default directory features enabled.

3.  Navigate to *Entitlements* \> *Entity Assignments*.

4.  Click *Configure Entitlements*.

5.  You can now edit the entitlements table:


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

    Once you've added new service plans, you can also change the quota for those plans as described in the following row and enable the option to auto-assign quota to subaccounts. For service plans where quota can be increased or decreased, you can also specify what amount should be auto-assigned to each subaccount that is created or added to the directory.

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
    
6.  Once you're done, choose *Save* to save the changes and exit edit mode for that directory.


 <a name="task_mtd_ssf_mqb"/>

<!-- task\_mtd\_ssf\_mqb -->

## Configure Entitlements and Quotas for Multiple Directories \[Feature Set B\]



<a name="task_mtd_ssf_mqb__prereq_ntd_ssf_mqb"/>

## Prerequisites

-   You are a global account administrator.

-   Your directories have the entitlement management feature enabled. To do that, navigate to the directory and on the *Entitlements* page, click *Enable Entitlement Management*.

    > ### Tip:  
    > You can quickly tell if the entitlement management has enabled if the directory's *Entitlements* page in the navigation panel has two subpages, *Entity Assignments* and *Service Assignments*. Also the directory's *Overview* page will have the *Disable Entitlement Management*button.

    > ### Note:  
    > Any given directory path in the account hierarchy can have only one directory that is enabled with the entitlement management feature \(or with the authorization management feature\). If such a directory exists, other directories in that path can only have the default directory features enabled.

-   The service and applications that you intend to assign to your directories must be entitled to your global account.

    -   For enterprise accounts that use the subscription-based commercial model, your account receives only the services that you've already purchased and subscribed to according to your SAP BTP contract. To access additional services, at an extra cost, you can modify your contract via your sales representative or account executive.

    -   For enterprise accounts that use the consumption-based commercial model, your global account receives all pay-for-use and free services that are eligible for this commercial model.

    -   If you have a trial account, you'll receive a restricted set of free platform resources and services for a limited time period. To access additional services, you'll have to switch to an enterprise account.





<a name="task_mtd_ssf_mqb__steps_ptd_ssf_mqb"/>

## Procedure

1.  Navigate to your global account.

2.  Choose *Entitlements* \> *Entity Assignments* from the left hand-side navigation.

3.  At the top of the page, choose *Show: Directories* and then select all the directories for which you would like to configure or display entitlements.

4.  Choose *Go* to apply the filter.

    You get a table for each of the directories you selected, displaying the current entitlement and quota assignments. You can choose *Show subaccount assignments* next to the table title to see the entitlement and quota assignments for the subaccounts in a specific directory.

5.  Choose *Configure Entitlements* to start editing entitlements for a particular directory.

    > ### Note:  
    > You can only edit entitlements for one directory at a time.

6.  You can now edit the entitlements table:


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

    Once you've added new service plans, you can also change the quota for those plans as described in the following row and enable the option to auto-assign quota to subaccounts. For service plans where quota can be increased or decreased, you can also specify what amount should be auto-assigned to each subaccount that is created or added to the directory.

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
    
7.  Once you're done, choose *Save* to save the changes and exit edit mode for that directory.

8.  **Optional:** Repeat steps 5 to 7 to configure entitlements for the other directories selected.


**Related Information**  


[Entitlements and Quotas](../10-concepts/entitlements-and-quotas-00aa2c2.md "When you purchase an enterprise account, you’re entitled to use a specific set of resources, such as the amount of memory that can be allocated to your applications.")

[Directories \[Feature Set B\]](../10-concepts/account-model-8ed4a70.md#loioa92721fc75524ec09a7a7255997dbd94 "Directories allow you to organize and manage your subaccounts according to your technical and business needs.")

[Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

