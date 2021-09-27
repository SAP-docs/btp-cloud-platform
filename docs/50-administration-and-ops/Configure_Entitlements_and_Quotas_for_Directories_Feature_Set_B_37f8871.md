<!-- loio37f8871865114f44aebee3db6ac64b72 -->

# Configure Entitlements and Quotas for Directories \[Feature Set B\]

> ### Note:  
> This feature is new in Feature Set B so there is no equivalent in Feature Set A. For more information, see [Cloud Management Tools — Feature Set Overview](../10-concepts/Cloud_Management_Tools_—_Feature_Set_Overview_caf4e4e.md).

Assign entitlements to directories by adding service plans and distribute the quotas available in your global account to your directories using the SAP BTP cockpit.

 <a name="loio37f8871865114f44aebee3db6ac64b72 task_amv_krf_mqb__task_amv_krf_mqb"/>

<!-- task\_amv\_krf\_mqb -->

# Configure Entitlements and Quotas for a Single Directory \[Feature Set B\]



<a name="task_amv_krf_mqb__prereq_bmv_krf_mqb"/>

## Prerequisites

-   You are a global account administrator



<a name="task_amv_krf_mqb__steps_dmv_krf_mqb"/>

## Procedure

1.  Navigate to the directory for which you want to manage entitlements.

2.  If entitlement mangement is not enabled for a directory in this path yet, navigate to the *Entitlements* page and select *Enable Entitlement Management*.

3.  Navigate to *Entitlements* \> *Entity Assignments*.

4.  Click *Configure Entitlements*.

5.  You can now edit the entitlements table:


    <table>
    <tr>
    <th>

    Action


    
    </th>
    <th>

    Steps


    
    </th>
    </tr>
    <tr>
    <td>

    **Add new service plans to the directory**


    
    </td>
    <td>

    Choose *Add Service Plans* and from the dialog select the services and the plans from each service that you would like to add to the directory. Choose *Add <x\> Service Plans* in the dialog to confirm.

    Once you've added new service plans, you can also change the quota for those plans as described in the following row and enable the option to auto-assign quota to subaccounts. For service plans where quota can be increased or decreased, you can also specify what amount should be auto-assigned to each subaccount that is created or added to the directory.

    > ### Note:  
    > To subscribe a subaccount to a multitenant application, you must first assign the application to the specific subaccount using the process described in [Configure Entitlements and Quotas for Subaccounts](Configure_Entitlements_and_Quotas_for_Subaccounts_5ba357b.md).

    > ### Tip:  
    > If your global account is configured to consume remote services from a non-SAP cloud vendor \(resource provider\), an additional dropdown list is displayed in the *Service Details* pane, where you can choose a configured resource provider. You can then choose the required service plans that are available for the selected resource provider to add them to the subaccount.
    > 
    > For more information, see [Managing Resource Providers](Managing_Resource_Providers_e2c250d.md).


    
    </td>
    </tr>
    <tr>
    <td>

    **Edit the quota for one or more service plans**


    
    </td>
    <td>

    Use     and     to increase or decrease the quota for each service plan.

    If you would like to have quota automatically assigned to subaccounts that are created or moved to the directory, follow the same process to set the amount that should be auto-assigned to each subaccount.

    > ### Note:  
    > -   The auto-assign feature doesn't apply to subaccounts that are already in the directory when the feature is enabled.
    > 
    > -   You cannot use the auto-assign feature with beta services and applications.


    
    </td>
    </tr>
    <tr>
    <td>

    **Delete a service plan and its quota from the directory**


    
    </td>
    <td>

    Choose     from the *Actions* column.


    
    </td>
    </tr>
    </table>
    
6.  Once you're done, choose *Save* to save the changes and exit edit mode for that directory.


 <a name="loio37f8871865114f44aebee3db6ac64b72 task_mtd_ssf_mqb__task_mtd_ssf_mqb"/>

<!-- task\_mtd\_ssf\_mqb -->

# Configure Entitlements and Quotas for Multiple Directories \[Feature Set B\]



<a name="task_mtd_ssf_mqb__prereq_ntd_ssf_mqb"/>

## Prerequisites

-   You are a global account administrator.
-   Your directory has the manage entitlements feature enabled. To do that, navigate to the directory and on the *Entitlements* page, click *Enable Entitlement Management*.



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
    <th>

    Action


    
    </th>
    <th>

    Steps


    
    </th>
    </tr>
    <tr>
    <td>

    **Add new service plans to the directory**


    
    </td>
    <td>

    Choose *Add Service Plans* and from the dialog select the services and the plans from each service that you would like to add to the directory. Choose *Add <x\> Service Plans* in the dialog to confirm.

    Once you've added new service plans, you can also change the quota for those plans as described in the following row and enable the option to auto-assign quota to subaccounts. For service plans where quota can be increased or decreased, you can also specify what amount should be auto-assigned to each subaccount that is created or added to the directory.

    > ### Note:  
    > To subscribe a subaccount to a multitenant application, you must first assign the application to the specific subaccount using the process described in [Configure Entitlements and Quotas for Subaccounts](Configure_Entitlements_and_Quotas_for_Subaccounts_5ba357b.md).

    > ### Tip:  
    > If your global account is configured to consume remote services from a non-SAP cloud vendor \(resource provider\), an additional dropdown list is displayed in the *Service Details* pane, where you can choose a configured resource provider. You can then choose the required service plans that are available for the selected resource provider to add them to the subaccount.
    > 
    > For more information, see [Managing Resource Providers](Managing_Resource_Providers_e2c250d.md).


    
    </td>
    </tr>
    <tr>
    <td>

    **Edit the quota for one or more service plans**


    
    </td>
    <td>

    Use     and     to increase or decrease the quota for each service plan.

    If you would like to have quota automatically assigned to subaccounts that are created or moved to the directory, follow the same process to set the amount that should be auto-assigned to each subaccount.

    > ### Note:  
    > -   The auto-assign feature doesn't apply to subaccounts that are already in the directory when the feature is enabled.
    > 
    > -   You cannot use the auto-assign feature with beta services and applications.


    
    </td>
    </tr>
    <tr>
    <td>

    **Delete a service plan and its quota from the directory**


    
    </td>
    <td>

    Choose     from the *Actions* column.


    
    </td>
    </tr>
    </table>
    
7.  Once you're done, choose *Save* to save the changes and exit edit mode for that directory.

8.  Repeat steps 5 to 7 to configure entitlements for the other directories selected.


**Related Information**  


[Entitlements and Quotas](../10-concepts/Entitlements_and_Quotas_00aa2c2.md "When you purchase an enterprise account, you’re entitled to use a specific set of resources, such as the amount of memory that can be allocated to your applications.")

[Directories \[Feature Set B\]](../10-concepts/Account_Model_8ed4a70.md#loioa92721fc75524ec09a7a7255997dbd94 "Directories allow you to organize and manage your subaccounts according to your technical and business needs.")

[Cloud Management Tools — Feature Set Overview](../10-concepts/Cloud_Management_Tools_—_Feature_Set_Overview_caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

