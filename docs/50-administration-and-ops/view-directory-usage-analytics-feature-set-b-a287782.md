<!-- loioa2877827b9f644a29e508a4d2864b2e8 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# View Directory Usage Analytics \[Feature Set B\]

You can explore, compare, and analyze all your actual usage data for the services and applications that are available in your directory.

To monitor and track usage in a directory, open your directory from the *Account Explorer* in the SAP BTP cockpit, and then go to the *Usage Analytics* page in the navigation area.

> ### Note:  
> This cockpit page is available only for directories that have user management enabled.
> 
> You must also be assigned as an admin of the directory. For the more information, see [Create a Directory \[Feature Set B\]](create-a-directory-feature-set-b-b8ef1c4.md) and [Manage Users in Directories \[Feature Set B\]](manage-users-in-directories-feature-set-b-ff4d4a4.md).



<a name="loioa2877827b9f644a29e508a4d2864b2e8__section_xyh_sjc_tdb"/>

## Views in the Directory 'Usage Analytics' Page

The directory *Usage Analytics* page contains two views that display the same usage information; however, your entry point is different – either from a service/subscription or a directory/subaccount:


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

 **Service Usage** 



</td>
<td valign="top">

Displays high-level usage information for a selected service or business application subscriptions according to the directory from which you accessed the *Usage Analytics* page. You can also drill down and view usage data for specific subdirectories and subaccounts that are located in this directory.



</td>
</tr>
<tr>
<td valign="top">

 **Directory/Subaccount Usage** 



</td>
<td valign="top">

Displays high-level usage information for all services and business application subscriptions according to the directory from which you accessed the *Usage Analytics* page. You can also drill down and view usage data for specific subdirectories and subaccounts that are located in this directory.



</td>
</tr>
</table>

Information is shown only for those services and subscriptions whose metered consumption in the directory is greater than zero.

Usage values are updated every 24 hours. Usage data displayed in this cockpit page refers to actual usage, not billed usage.

The *Space* filter is available only when you've selected a subaccount and the subaccount has the Cloud Foundry environment enabled.

> ### Tip:  
> -   If your directory is in a global account that uses the consumption-based commercial model, you can view information about your billed usage for billable services in your global acccount's *Usage Analytics* page. The global account's *Usage Analytics* page also provides information about cloud-credit usage. For more information, see [Monitoring Usage and Consumption Costs in Your Global Account](monitoring-usage-and-consumption-costs-in-your-global-account-de6f0db.md).
> -   You can also view usage information by subaccount directly in a subaccount's *Usage Analytics* page. For more information, see [View Subaccount Usage Analytics](view-subaccount-usage-analytics-8f4d9db.md).



<a name="loioa2877827b9f644a29e508a4d2864b2e8__section_ynm_hd4_tdb"/>

## Working with the Tables and Charts

Both the *Service Usage* and *Directory/Subaccount Usage* views display the usage information in tabular and chart formats.

-   The tables present accumulated usage values based on the aggregation logic of each service plan and its metric over the selected time period. The usage values are broken down by resource.
-   The charts present usage values for one or more service plans that you select in the adjacent tables.

Select a table row to display the usage information in the chart. You can also compare usage between service plans in the same service by selecting multiple rows. To compare usage, the rows items must also share the same metric.

In the charts, you can view the data as a column chart or as a line chart.

To display a larger view of a chart, choose the <span style="font-size:16px;"><span class="SAP-icons"></span></span> \(Zoom\) button.

Some rounding or shortening is applied to large values. You can mouse over values in the table to view the exact values as tooltips.

**Related Information**  


[Org Administration Using the Cockpit](org-administration-using-the-cockpit-c4c25cc.md "In the Cloud Foundry enviroment, manage orgs, spaces and space quota plans using the SAP BTP cockpit.")

[Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

[Monitoring Usage and Consumption Costs in Your Global Account](monitoring-usage-and-consumption-costs-in-your-global-account-de6f0db.md "In a global account that uses the consumption-based commercial model, you can monitor the usage of billed services and your consumption costs in the SAP BTP cockpit.")

[What Is the Consumption-Based Commercial Model?](../10-concepts/what-is-the-consumption-based-commercial-model-7047eb4.md "With the consumption-based model, your organization purchases an entitlement to all current and future SAP BTP services that are eligible for this model. Throughout the duration of your contract, you have complete flexibility to turn services on and off and to switch between services as your business requires.")

[View Subaccount Usage Analytics](view-subaccount-usage-analytics-8f4d9db.md "You can explore, compare, and analyze all your actual usage data for the services and applications that are available in your subaccount.")

[Monitoring Usage Information Using APIs of the SAP Usage Data Management Service \[Feature Set B\]](Monitoring_Usage_Information_Using_APIs_bf2b304.md "Provides information about using the Resource Consumption APIs of the SAP Usage Data Management service for SAP BTP for gathering, storing, and making usage information available for all services and applications in all regions in a cloud deployment. This information is for the purpose of central analysis, reporting, and license auditing.")

[Manage Users in Directories \[Feature Set B\]](manage-users-in-directories-feature-set-b-ff4d4a4.md "Manage members in your directory using the SAP BTP cockpit.")

