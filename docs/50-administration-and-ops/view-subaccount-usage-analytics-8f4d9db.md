<!-- loio8f4d9db9ecb34b08865c2c7a61d7719f -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# View Subaccount Usage Analytics

You can explore, compare, and analyze all your actual usage data for the services and applications that are available in your subaccount.

To monitor and track usage in a subaccount, open the subaccount in the SAP BTP cockpit and choose *Usage Analytics* in the navigation area.



<a name="loio8f4d9db9ecb34b08865c2c7a61d7719f__section_xyh_sjc_tdb"/>

## Views in the Subaccount 'Usage Analytics' Page

The subaccount *Usage Analytics* page contains views that display usage at different levels of detail:


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

 **Subaccount** 



</td>
<td valign="top">

Displays high-level usage information for your subaccount relating to services, business application subscriptions, and Cloud Foundry org spaces.

Some information in this view is displayed only for global account admins.



</td>
</tr>
<tr>
<td valign="top">

 **Services** 



</td>
<td valign="top">

Displays usage per service plan for the region of the subaccount, and the selected metric and period. Information is shown for all services whose metered consumption in the subaccount is greater than zero.



</td>
</tr>
<tr>
<td valign="top">

 **Spaces** 



</td>
<td valign="top">

\(Cloud Foundry environment only\) Displays service plan usage per space for the services shown in the *Services* view.



</td>
</tr>
</table>

> ### Note:  
> The information displayed in this page depends on the environments that are enabled for your subaccount. For example, information about spaces is displayed only for subaccounts in the Cloud Foundry environment.

Usage values are updated every 24 hours.

Usage data displayed in this cockpit page refers to actual usage, not billed usage.

> ### Tip:  
> -   \[Feature Set A\] If your subaccount is in a global account that uses the consumption-based commercial model, you can view information about your billed usage for billable services in your global acccount's *Overview* and subaccount's *Overview* pages. The global account's *Overview* page also provides information about cloud-credit usage.
> -   \[Feature Set B\] If your subaccount is in a global account that uses the consumption-based commercial model, you can view information about your billed usage for billable services in your global acccount's *Usage Analytics* page. The global account's *Usage Analytics* page also provides information about cloud-credit usage. A directory's *Usage Analytics* page also allows you to view usage information for each subaccount that is located in the directory.
> -   \[Feature Set B\] If you use directories to group your subaccounts, you can view usage information by directory in your global account's *Usage Analytics* page or directly in the directory's *Usage Analytics* page.
> 
> For more information, see [Monitoring Usage and Consumption Costs in Your Global Account](monitoring-usage-and-consumption-costs-in-your-global-account-de6f0db.md) and [View Directory Usage Analytics \[Feature Set B\]](view-directory-usage-analytics-feature-set-b-a287782.md).



<a name="loio8f4d9db9ecb34b08865c2c7a61d7719f__section_ynm_hd4_tdb"/>

## Working with the Tables and Charts

In the *Services* and *Spaces* views, the usage information is displayed in both tabular and chart formats.

-   The tables present accumulated usage values based on the aggregation logic of each service plan and its metric over the selected time period. The usage values are broken down by resource.
-   The charts present usage values for one or more service plans or spaces that you select in the adjacent tables. The resolution of the charts is automatically set to days, weeks, or months, depending on the range of the selected time period.

You can perform various actions within the tables and charts:

-   In the *Services* and *Spaces* views, select a table row to display the usage information in the chart. You can also select multiple rows to compare usage in the following ways:
    -   In the *Services* view, you can compare usage between service plans in the same service. Multi-row selection in the table is possible only when you have selected a single service in the *Service* filter and the row items share the same metric.
    -   In the *Spaces* view, you can compare usage between spaces for the same service and service plan. Multi-row selection in the table is possible only when you have selected a single service plan in the *Service Plan* filter.

-   In the charts, you can view the data as a column chart or as a line chart.
-   To display a larger view of a chart, choose the <span style="font-size:16px;"><span class="SAP-icons"></span></span> \(Zoom\) button.
-   Some rounding or shortening is applied to large values. You can mouse over values in the table to view the exact values as tooltips.



<a name="loio8f4d9db9ecb34b08865c2c7a61d7719f__section_bqr_pd4_tdb"/>

## Using the Filters

Use the filters in the *Services* and *Spaces* views to choose which usage information to display.

The *Spaces* view inherits the filter settings, except for the *Period*, from the *Services* view above it. In other words, when you modify filters in the *Services* view, it affects the information that is displayed in the *Spaces* view. You can apply the *Period* filter independently to each view.

In the *Services* view, you can apply the *Metric* filter only when you have selected a service with more than one metric.

Click the <span style="font-size:16px;"><span class="SAP-icons"></span></span> \(Reset\) icon in each view to reset the filters to their default settings. If you reset the filters in the *Services* view, the filters in the *Spaces* are also reset.

**Related Information**  


[Org Administration Using the Cockpit](org-administration-using-the-cockpit-c4c25cc.md "In the Cloud Foundry enviroment, manage orgs, spaces and space quota plans using the SAP BTP cockpit.")

[Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

[Monitoring Usage and Consumption Costs in Your Global Account](monitoring-usage-and-consumption-costs-in-your-global-account-de6f0db.md "In a global account that uses the consumption-based commercial model, you can monitor the usage of billed services and your consumption costs in the SAP BTP cockpit.")

[What Is the Consumption-Based Commercial Model?](../10-concepts/what-is-the-consumption-based-commercial-model-7047eb4.md "With the consumption-based model, your organization purchases an entitlement to all current and future SAP BTP services that are eligible for this model. Throughout the duration of your contract, you have complete flexibility to turn services on and off and to switch between services as your business requires.")

[View Directory Usage Analytics \[Feature Set B\]](view-directory-usage-analytics-feature-set-b-a287782.md "You can explore, compare, and analyze all your actual usage data for the services and applications that are available in your directory.")

[Monitoring Usage Information Using APIs of the SAP Usage Data Management Service \[Feature Set B\]](Monitoring_Usage_Information_Using_APIs_bf2b304.md "Provides information about using the Resource Consumption APIs of the SAP Usage Data Management service for SAP BTP for gathering, storing, and making usage information available for all services and applications in all regions in a cloud deployment. This information is for the purpose of central analysis, reporting, and license auditing.")

