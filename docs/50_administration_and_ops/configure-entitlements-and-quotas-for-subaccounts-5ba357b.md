<!-- loio5ba357b4fa1e4de4b9fcc4ae771609da -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Configure Entitlements and Quotas for Subaccounts

Assign entitlements to subaccounts by adding service plans and distribute the quotas available in your global account to your subaccounts using the SAP BTP cockpit.



<a name="loio5ba357b4fa1e4de4b9fcc4ae771609da__prereq_rzj_njy_dcb"/>

## Prerequisites

You must be a global account administrator to configure subaccount entitlements.



<a name="loio5ba357b4fa1e4de4b9fcc4ae771609da__context_oqd_ck3_vhb"/>

## Context

You can distribute entitlements and quotas across subaccounts within a global account from two places in the cockpit:

-   The *Entitlements* \> *Subaccount Assignments* page at global account level \(only visible to global account administrators\)
-   The *Entitlements* page at subaccount level \(visible to all subaccount members, but only editable by global account administrators\)

\[Feature Set A\] To get an overview of all the services and plans available in the global account, you can navigate to *Entitlements* \> *Service Assignments* using the left hand-side navigation. There you can see the global usage of each service plan, as well as the detailed assignments of each service across subaccounts, but you aren't able to make changes on this page.

For more information, see [Managing Entitlements and Quotas Using the Cockpit](managing-entitlements-and-quotas-using-the-cockpit-c824874.md).

> ### Note:  
> -   \[Feature Set B\] To subscribe to a multitenant application, you must first assign it to the specific subaccount using the same process explained below. If you remove a subaccount’s entitlement to a multitenant application, any subscriptions to it from that subaccount stop working.
> 
> -   \[Feature Set B\] Before a subaccount admin can enable a quota-based environment, such as Kyma, the subaccount admin must first assign the environment as an entitlement to the subaccount. Other non-quota-based environments, such as Cloud Foundry, are available by default to all subaccounts, and therefore aren’t available as entitlements.

 <a name="task_lzl_bpb_vhb"/>

<!-- task\_lzl\_bpb\_vhb -->

## Configure Entitlements and Quotas from Your Global Account



<a name="task_lzl_bpb_vhb__steps_jqt_vpb_vhb"/>

## Procedure

1.  Navigate to your global account.

2.  Choose *Entitlements* \> *Subaccount Assignments* from the left hand-side navigation.

    > ### Note:  
    > \[Feature Set B\] Choose *Entitlements* \> *Entity Assignments* from the left hand-side navigation.

3.  At the top of the page, select all the subaccounts for which you would like to configure or display entitlements.

    > ### Tip:  
    > If your global account contains more than 20 subaccounts, choose <span class="SAP-icons"></span> to open up the value help dialog. There you can filter subaccounts by role, environment, and region to make your selection easier and faster. You can only select a maximum of 50 subaccounts at once.

4.  Choose *Go* to apply the filter.

    You get a table for each of the subaccounts you selected, displaying the current entitlement and quota assignments.

5.  Choose *Configure Entitlements* to start editing entitlements for a particular subaccount.

    > ### Note:  
    > You can only edit entitlements for one subaccount at a time.

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

    **Add new service plans to the subaccount**


    
    </td>
    <td valign="top">

    Choose *Add Service Plans* and from the dialog select the services and the plans from each service that you would like to add to the subaccount.

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

    Use <span class="SAP-icons"></span> and <span class="SAP-icons"></span> to increase or decrease the quota for each service plan.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    **Assign quota to unlimited service plans in global accounts using the consumption-based commercial model.**


    
    </td>
    <td valign="top">

    Use the checkbox in the *Assign Quota* column to enable or disable the *Subaccount Assignment* column for editing.

    Now, you can increase or decrease the quota for this service plan by using <span class="SAP-icons"></span> and <span class="SAP-icons"></span>.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    **Delete a service plan and its quota from the subaccount**


    
    </td>
    <td valign="top">

    Choose <span class="SAP-icons"></span> from the *Actions* column.


    
    </td>
    </tr>
    </table>
    
7.  Once you're done, choose *Save* to save the changes and exit edit mode for that subaccount.

8.  Repeat steps 5 to 7 to configure entitlements for the other subaccounts selected.


**Related Information**  


[Entitlements and Quotas](../10_concepts/entitlements-and-quotas-00aa2c2.md "When you purchase an enterprise account, you’re entitled to use a specific set of resources, such as the amount of memory that can be allocated to your applications.")

[Cloud Management Tools — Feature Set Overview](../10_concepts/cloud-management-tools-feature-set-overview-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

 <a name="task_h3v_xmb_vhb"/>

<!-- task\_h3v\_xmb\_vhb -->

## Configure Entitlements and Quotas from Your Subaccount

If you’re working in a subaccount and realize you’re missing entitlements or quota, you can edit the entitlements directly from that subaccount.



<a name="task_h3v_xmb_vhb__prereq_dml_p3h_jhb"/>

## Prerequisites

In addition to being a global account administrator, you must also be a member of the subaccount to be able to access that subaccount.



<a name="task_h3v_xmb_vhb__steps_j1l_3nb_vhb"/>

## Procedure

1.  Navigate into the subaccount where you would like to configure the entitlements.

2.  Choose *Entitlements* from the left hand-side navigation to see the entitlements for your subaccount.

3.  Choose *Configure Entitlements*.

4.  You can now edit the entitlements table:


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

    **Add new service plans to the subaccount**


    
    </td>
    <td valign="top">

    Choose *Add Service Plans* and from the dialog select the services and the plans from each service that you would like to add to the subaccount.

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

    Use <span class="SAP-icons"></span> and <span class="SAP-icons"></span> to increase or decrease the quota for each service plan.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    **Delete a service plan and its quota from the subaccount**


    
    </td>
    <td valign="top">

    Choose <span class="SAP-icons"></span> from the *Actions* column.


    
    </td>
    </tr>
    </table>
    
5.  Once you're happy with the changes, choose *Save* to save and exit edit mode.


**Related Information**  


[Entitlements and Quotas](../10_concepts/entitlements-and-quotas-00aa2c2.md "When you purchase an enterprise account, you’re entitled to use a specific set of resources, such as the amount of memory that can be allocated to your applications.")

[Cloud Management Tools — Feature Set Overview](../10_concepts/cloud-management-tools-feature-set-overview-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

