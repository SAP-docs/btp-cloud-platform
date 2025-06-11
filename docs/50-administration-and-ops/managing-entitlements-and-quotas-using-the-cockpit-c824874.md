<!-- loioc8248745dde24afb91479361de336111 -->

# Managing Entitlements and Quotas Using the Cockpit

When you purchase an enterprise account, you are entitled to use a specific set of resources, such as the amount of memory that can be allocated to your applications.

An entitlement equals your right to provision and consume a resource. A quota represents the numeric quantity that defines the maximum allowed consumption of that resource.

Entitlements are managed at the global account level, where services plans and their allowed quota are distributed to subaccounts, and then consumed by the subaccounts. When quota is freed at the subaccount level, it becomes available again at the global account level.

Optionally, you can assign service plans and quota from the global account to directories, and from there distribute these assignments to subaccounts under the directory. Before you can assign plans and quota to a directory, the directory must first be configured to manage entitlements. See [Configure Entitlements and Quotas for Directories](configure-entitlements-and-quotas-for-directories-37f8871.md). When quota is freed at the subaccount level, it becomes available again at the directory level.

> ### Note:  
> Only global account administrators can configure entitlements and quotas for subaccounts and managed directories.
> 
> Note that if you're assigning plans to a subaccount that is under a managed directory that also has the user management feature enabled, then you must be either the directory administrator or a global account administrator.

There are two places in the SAP BTP cockpit where you can view entitlements and assign service plans and quotas for subaccounts - at the global account level and at the subaccount level. Depending on your permissions, you may only have access to one of these pages. You can find more details below:

**Entitlements Pages**


<table>
<tr>
<th valign="top">

Page in cockpit

</th>
<th valign="top">

Navigation Level

</th>
<th valign="top">

Visible to

</th>
<th valign="top">

Permissions

</th>
</tr>
<tr>
<td valign="top">

*Entitlements* \> *Entity Assignments*

</td>
<td valign="top">

Global account level

</td>
<td valign="top">

Global account administrators only

</td>
<td valign="top">

-   View & Edit - Global account administrators



</td>
</tr>
<tr>
<td valign="top">

*Entitlements* \> *Service Assignments*

</td>
<td valign="top">

Global account level

</td>
<td valign="top">

Global account administrators only

</td>
<td valign="top">

-   View - Global account administrators \(you cannot make changes to entitlements or quota assignments from this page\)



</td>
</tr>
<tr>
<td valign="top">

*Entitlements*

</td>
<td valign="top">

Subaccount level

</td>
<td valign="top">

Subaccount members \(regardless of whether they are also global account administrators or not\)

</td>
<td valign="top">

-   View - Subaccount members who are not global account administrators
-   View & Edit - Global account administrators who are also subaccount members



</td>
</tr>
</table>

The *Entitlements* \> *Entity Assignments* is where you view and edit assignments and quota from the perspective of subaccounts and directories. This page contains these views \(tabs\):


<table>
<tr>
<th valign="top">

View

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

*Manage Assignments*

</td>
<td valign="top">

Allows global account admins to distribute the entitled service plans of their global account to subaccounts and directories.

</td>
</tr>
<tr>
<td valign="top">

*View Commercial Information*

</td>
<td valign="top">

Allows global account admins and viewers to view the commercial source of their service entitlements. This feature is not available for trial accounts.

</td>
</tr>
</table>

For information about setting assignments and quota, see:

-   [Configure Entitlements and Quotas for Directories](configure-entitlements-and-quotas-for-directories-37f8871.md)
-   [Configure Entitlements and Quotas for Subaccounts](configure-entitlements-and-quotas-for-subaccounts-5ba357b.md)

The *Entitlements* \> *Service Assignments* is where you view assignments and quota from the perspective of services. This page contains these views \(tabs\):


<table>
<tr>
<th valign="top">

View

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

*All Services*

</td>
<td valign="top">

Provides an overview of all available service entitlements of your global account.

> ### Tip:  
> The *Assigned To* column in this view shows you the total number of directories and subaccounts to which each service plan is assigned in your global account. You can click on the links in this column to quickly navigate to the selected service in the *Assignments by Service* view and display more details about these assignments.
> 
> Turn on the *Show commercial info* option to display additional columns in the main table. These columns can help you to gain a better understanding of the relationship between contractual service entitlements and the technical assets \(services and plans\) in your global account.



</td>
</tr>
<tr>
<td valign="top">

*Assignments by Service*

</td>
<td valign="top">

Allows you to choose specific services and see how their service plans are assigned to subaccounts and directories within your global account.

> ### Tip:  
> Turn on the *Show commercial info* option to display additional columns in the main table. These columns can help you to gain a better understanding of the relationship between contractual service entitlements and the technical assets \(services and plans\) in your global account.



</td>
</tr>
</table>

> ### Note:  
> -   To subscribe to a multitenant application, you must first assign its plan to the specific subaccount \(in one of the *Entitlements* pages\). If you remove a subaccount’s entitlement to a multitenant application, any subscriptions to it from that subaccount will stop working.
> 
> -   Before a subaccount admin can enable a quota-based environment, such as Kyma, the subaccount admin must first assign the environment's plan to the subaccount \(in one of the *Entitlements* pages\). Other non-quota-based environments, such as Cloud Foundry, are available by default to all subaccounts, and therefore are not available as entitlements.

In the Cloud Foundry environment, you can further distribute the quotas that are allocated to a subaccount. This is done by creating space quota plans and assigning them to the spaces. For more information on space quota plans in the Cloud Foundry environment, see:

-   [Managing Space Quotas](managing-space-quotas-4e5f0ee.md)
-   [https://docs.cloudfoundry.org/adminguide/quota-plans.html](https://docs.cloudfoundry.org/adminguide/quota-plans.html)

> ### Tip:  
> Optionally, you can configure assignments and quotas for supported services that you own or subscribe to from supported non-SAP cloud vendors. These services can be consumed in SAP BTP in your subaccounts alongside your self-developed services and those provided by SAP. This functionality requires first setting up a resource provider instance for your provider account in the cockpit. For more information, see [Managing Resource Providers](managing-resource-providers-e2c250d.md).

> ### Note:  
> In global accounts that use the consumption-based commercial model, a default runtime memory quota of 200 GB for the standard plan is automatically assigned to every subaccount. This quota represents a limit on how much runtime memory the applications in the subaccount can use at any given time. When you use the standard plan for SAP BTP, Cloud Foundry runtime in the consumption-based commercial model, you're billed based on the amount of runtime memory that has actually been consumed. For more information, see [Service Plans and Metering for Cloud Foundry Runtime](https://help.sap.com/docs/cf-runtime/cloud-foundry-runtime/service-plans-and-metering-for-cloud-foundry-runtime?version=Cloud) and [Consumption Monitoring](https://help.sap.com/docs/cf-runtime/cloud-foundry-runtime/monitoring-and-troubleshooting#consumption-monitoring).
> 
> A global account administrator can change the default quota as described in [\(optional\) Adjusting Runtime Memory Quota for Cloud Foundry Runtime \(Consumption-Based\)](https://help.sap.com/docs/cf-runtime/cloud-foundry-runtime/optional-adjusting-runtime-memory-quota-for-cloud-foundry-runtime?version=Cloud). For regions where this functionality is still unavailable, you can create a case on the [SAP Support Portal](https://support.sap.com) using the `BC-NEO-CIS` component if you need to increase the default quota.

**Related Information**  


[Entitlements and Quotas](../10-concepts/entitlements-and-quotas-00aa2c2.md "When you purchase an enterprise account, you’re entitled to use a specific set of resources, such as the amount of memory that can be allocated to your applications.")

[Configure Entitlements and Quotas for Subaccounts](configure-entitlements-and-quotas-for-subaccounts-5ba357b.md "Distribute the entitlements that are available in your global account by adding service plans and their allowed quotas to your subaccounts using SAP BTP cockpit.")

[Configure Entitlements and Quotas for Directories](configure-entitlements-and-quotas-for-directories-37f8871.md "Distribute entitlements that are available in your global account to directories by adding service plans and their allowed quotas by using SAP BTP cockpit.")

[Create Space Quotas](create-space-quotas-b13c4a2.md "You can use the SAP BTP cockpit to create space quotas.")

[Create Space Quota Plans Using the Cloud Foundry Command Line Interface](create-space-quota-plans-using-the-cloud-foundry-command-line-interface-504fde9.md "You can use the Cloud Foundry Command Line Interface to create space quota plans.")

[**Tutorial**: Manage Entitlements on SAP BTP Trial](https://developers.sap.com/tutorials/cp-trial-entitlements.html)

[**Troubleshooting**: Entitlement and Quota Problems](https://ga.support.sap.com/dtp/viewer/index.html#/tree/2065/actions/26547:27066)

