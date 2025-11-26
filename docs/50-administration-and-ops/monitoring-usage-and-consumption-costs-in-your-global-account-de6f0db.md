<!-- loiode6f0db8919f4e6f97e54bc4ddaf2ab8 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Monitoring Usage and Consumption Costs in Your Global Account

SAP BTP cockpit supports advanced usage and cost monitoring of services in your global account. You can compare the usage and costs of multiple services and subaccounts, see monthly trends, and drill down into subaccounts and service plans for detailed information.

> ### Note:  
> -   The use of the consumption-based commercial model is subject to its availability in your country or region.
> 
> -   If your global account uses only the subscription-based commercial model, then refer only to information described here about usage data and the *Usage* tab. You can ignore any information in this topic about costs, cloud credits, and the *Overview* and *Billing* tabs.

The *Costs and Usage* page in the cockpit provides a central and flexible experience for the following cost control flows:

-   Continuously monitor and analyze the monthly usage and costs of services consumed by subaccounts and directories in your global account.
-   Help you to verify your monthly billing statement against actual resource consumption.
-   Help you to verify periodic cross-charges between your various business units based on subaccount and directory allocation/distribution.

Check out also [this blog](https://url.sap/ff08fy) for more information.

The *Costs and Usage* page uses the same terms that are printed in your monthly balance statement, which facilitates better contract-to-billing traceability and verification for cost controllers. Get your latest balance statement from [SAP for Me](https://me.sap.com/).

> ### Remember:  
> -   The monthly balance statement, which is provided separately, contains legally binding information regarding your monthly costs. Details about costs on the *Costs and Usage* page in the cockpit are provided for informational purposes only. Any discrepancy between the information displayed in the cockpit and the information in your balance statement will be resolved in favor of the balance statement.
> -   Costs are displayed according to your contract currency.
> -   Global accounts are the only contractual billable entity for SAP BTP. Directories and subaccounts are used as structural entities in global accounts. The usage and cost data displayed for directories and subaccounts are estimations and may differ from the actual global account metrics. Hence, you should use their data only for internal cost estimations.
> 
>     The relative calculation per billable usage within each subaccount is an estimation only as it is based on certain measures, which in some cases can either be different from the metrics that are presented on the global account level, or that use different formulas than the ones used for billing.
> 
> -   Cloud credit information and monthly costs apply to all regions used by the subaccounts in your global account. Usage and cost data is updated after your monthly balance statement has been generated.
> -   Usage data is updated after your monthly balance statement has been generated. For new global accounts, data is updated with the first billing cycle.
> -   Prices are listed as estimates if a consumable item has not yet been billed.
> -   In the cost and usage charts, estimated values are used for the period between the last balance statement and the current date. These are displayed as striped bars.
> 
>     These estimates are based on resource usage values before computation for billing and might change after the next balance statement is issued. The estimated values are not projected or forecast values.
> 
> -   Some SAP BTP services report their billing and usage at the global account level, and not at the subaccount level. Such services are listed in the *Costs and Usage* page under a reserved technical entity named `REPORTED-AT-GLOBAL-ACCOUNT-LEVEL` with the ID `DEFAULT_SA`.



<a name="loiode6f0db8919f4e6f97e54bc4ddaf2ab8__section_opc_4d3_m1c"/>

## Accessing the Costs and Usage Page

To access the *Costs and Usage* page, open the global account in the cockpit and choose *Costs and Usage* in the navigation area.

> ### Note:  
> The *Costs and Usage* page is available only if your global account uses the consumption-based commercial model.
> 
> If your global account uses the subscription-based commercial model exclusively, then you must access the *Usage* page instead. The *Usage* page resembles the *Costs and Usage* page, except you cannot see any data relating to costs or cloud credits since your eligible services are already prepaid and you aren't charged per usage. See [Using the Usage Tab](monitoring-usage-and-consumption-costs-in-your-global-account-de6f0db.md#loiode6f0db8919f4e6f97e54bc4ddaf2ab8__section_vff_dr3_m1c).



<a name="loiode6f0db8919f4e6f97e54bc4ddaf2ab8__section_u3v_vd3_m1c"/>

## Understanding the Layout of the Costs and Usage Page



### Overview, Billing, Usage, and Budget Tabs

The tab row at the top of the *Costs and Usage* page allows you to quickly navigate to the different features designed to help you monitor your usage and consumption costs across your global account.

  
  
**Tab row of the Costs and Usage page**

![](images/Costs_and_Usage_Page_-_Tab_Row_3cb66a7.png "Tab row of the Costs and Usage page")


<table>
<tr>
<th valign="top">

Tab

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

**Overview** 

</td>
<td valign="top">

Shows several cards that provide you with key insights into your monthly costs, prepaid subscription quota, cost distribution and breakdown, and cost-related recommendations.

For more information, see [Using the Overview Tab](monitoring-usage-and-consumption-costs-in-your-global-account-de6f0db.md#loiode6f0db8919f4e6f97e54bc4ddaf2ab8__section_tnf_1ld_hhc).

</td>
</tr>
<tr>
<td valign="top">

**Billing** 

</td>
<td valign="top">

Shows the monthly billable service charges in your global account, based on the aggregation of your resource's actual usage.

The aggregation of usage from all your subaccounts is calculated according to the pricing structure and legally billable metric of each service, as mentioned in the [SAP BTP Service Description Guide](https://www.sap.com/about/trust-center/agreements/cloud/cloud-services.html?sort=latest_desc&search=SAP%20Business%20technology%20platform%20service%20description%20guide&tag=language:english).

> ### Note:  
> This tab relevant only if your global account uses a consumption-based commercial model. If your global account uses only the subscription-based commercial model, then all your eligible services and entitled quota are prepaid.

For more information, see [Using the Billing Tab](monitoring-usage-and-consumption-costs-in-your-global-account-de6f0db.md#loiode6f0db8919f4e6f97e54bc4ddaf2ab8__section_bfz_xd3_m1c).

</td>
</tr>
<tr>
<td valign="top">

**Usage** 

</td>
<td valign="top">

Shows the data representing your actual non-aggregated monthly usage for services consumed in your subaccounts within your global account.

This tab applies to both the consumption-based and subscription-based commercial models.

For more information, see [Using the Usage Tab](monitoring-usage-and-consumption-costs-in-your-global-account-de6f0db.md#loiode6f0db8919f4e6f97e54bc4ddaf2ab8__section_vff_dr3_m1c).

</td>
</tr>
<tr>
<td valign="top">

**Budgets** 

</td>
<td valign="top">

In this tab, you can set up budget limits for your global account so that you can better manage your global account spending and plan for future consumption. Here you can also opt to have automatic e-mail alerts sent to all global account administrators to notify them when spending exceeds defined budget thresholds.

For more information, see [Managing Budgets in Your Global Account](managing-budgets-in-your-global-account-e115d5f.md#loioe115d5fbe1454f58aabeb3b4b1e7a847).

</td>
</tr>
</table>

  
  
**Billing tab in the Costs and Usage page**

![](images/Costs_and_Usage_-_Billing_Tab_f57177d.png "Billing tab in the Costs and Usage page")



### Filter and Search Bar

At the top of the *Billing* and *Usage* tabs, you can find the filter and search bar. Apply the filters to choose which services, subaccounts, directories, or billing month you want to view in these two tabs.

You can also use the *Search* option. When you start typing, the search offers results that apply to service names, plan names, subaccount names, directory names, labels assigned to subaccounts and directories, product IDs \(SKU\), and metrics. The search offers suggestions only for items that are currently listed.

> ### Tip:  
> If you've set up labels in your subaccounts and directories that reflect the distribution of these entities to your company structure or projects, you can easily track and manage cross-charges by entering the labels of your subaccount and directory labels in the search.

When you enter filter and search criteria in either the *Billing* or *Usage* tab, the same filters and search terms are applied to both tabs, allowing you to view consistent data across both sections more efficiently.

> ### Tip:  
> To share or save a filtered tab, click the <span class="SAP-icons-V5"></span> \(Bookmarks\) option in the header area. The URL of the tab and its filters is saved to your clipboard.
> 
> You can then save this URL as a bookmark in your browser, or you can share it with a colleague so they can quickly open the same tab and filter settings.



### General Tips for the Billing and Usage Tabs

In the following table, you can find some useful tips that are common to both the *Billing* and *Usage* tabs:


<table>
<tr>
<th valign="top">

To Do This…

</th>
<th valign="top">

Do This…

</th>
</tr>
<tr>
<td valign="top">

Find out what each table column means

</td>
<td valign="top">

Click the <span class="SAP-icons-V5"></span> \(More Info\) buttons in the column headings, where available.

</td>
</tr>
<tr>
<td valign="top">

Sort the data in ascending or descending order

</td>
<td valign="top">

Click a column heading in the table and choose the sort order you want.

Sorting the tables can be useful for determining which service plans and subaccounts have the highest and lowest costs.

</td>
</tr>
<tr>
<td valign="top">

Show or hide table columns

</td>
<td valign="top">

Click :gear: to configure which table columns you'd like to show and hide.

The tables in each tab have columns that are hidden by default. Open this setting to check if any of these columns apply to your needs.

</td>
</tr>
<tr>
<td valign="top">

Maximize the tables across the entire page

</td>
<td valign="top">

Collapse the navigation panel to maximize the tables across the entire page.

</td>
</tr>
<tr>
<td valign="top">

Adjust the width of table columns

</td>
<td valign="top">

Drag the column separators to the left or right.

</td>
</tr>
<tr>
<td valign="top">

Manage the custom labels of your directories and subaccounts

</td>
<td valign="top">

Choose either the *Add Labels* or the *Edit Labels* option in the <span class="SAP-icons-V5"></span> \(Actions\) context menu of any listed directory or subaccount in either the *Billing* or *Usage* tab.

In the *View by Account* view of the *Billing* tab, these context menu options are available in the main table, while in the *View by Service* view, you need to open the details view of a service plan.

Existing labels of directories and subaccounts are listed under the *Labels* columns in the *Billing* or *Usage* tabs. You can hide this column if you have no use for it.

> ### Remember:  
> You can also add, remove, and edit the labels of your directories and subaccounts on the *Account Explorer* page. Adding custom labels to your directories and subaccounts is optional, but they can help you narrow down cost results by focusing on specific labels in the *Search* fields.

For more information about labels, see [Labels](../10-concepts/account-model-8ed4a70.md#loioe8663c08ead648faa673b0d63c5b478e).

</td>
</tr>
</table>



<a name="loiode6f0db8919f4e6f97e54bc4ddaf2ab8__section_tnf_1ld_hhc"/>

## Using the Overview Tab

The *Overview* tab is where you can get key insights into your monthly costs, prepaid subscription quota, cost distribution and breakdown, and cost-related recommendations in the following cards:


<table>
<tr>
<th valign="top">

Card

</th>
<th valign="top">

**What Information is Displayed**

</th>
</tr>
<tr>
<td valign="top">

**Monthly Cost Summary** 

</td>
<td valign="top">

Shows key indicators of your global account's monthly consumption costs over the past 12 months, including:

-   Estimated costs so far this month \(based on raw usage data before computation for billing; values may update after your next balance statement\)
-   Forecasted total cost for the current month
-   Total cost for the previous month
-   Months with the highest and lowest costs
-   Average monthly cost

> ### Note:  
> The available indicators in this card depend on which consumption-based model is used by your global account. For example, the *Total forecasted cost for current month* indicator is not available for the Pay-As-You-Go for SAP BTP model.
> 
> Some indicators also require a minimum amount of historical data.



</td>
</tr>
<tr>
<td valign="top">

**SAP BTP Enterprise Agreement** 

</td>
<td valign="top">

Shows information relating to your cloud-credit usage and costs per month relative to your total cloud credits for the current cloud credits period. It also shows your monthly trend of cloud-credit usage and costs.

This card is displayed only if your global account uses the SAP BTPEA flavor of the consumption-based commercial model.

In this card, you'll see warnings if you're approaching or exceeded your cloud credit limit for the current cloud credits period. Any overages are billed at list price, so make sure to contact SAP if you need more cloud credits.

> ### Tip:  
> To allow you to better manage your global account spending and plan for future consumption, turn on the *Show forecast* option. When turned on, you can view a projection of your anticipated cloud-credit costs and usage for the next 6 months or the end of current contract period, whichever is shorter.
> 
> For more information about this option, see [Estimated and Forecasted Data](monitoring-usage-and-consumption-costs-in-your-global-account-de6f0db.md#loiode6f0db8919f4e6f97e54bc4ddaf2ab8__section_gqh_qtp_tcc).

Note the following:

-   Cloud-credit usage and cost information is displayed only for the current cloud credits period. The total contract duration is split into cloud credit periods \(typically one year each\) and the total cloud credits are divided between these periods.

-   Cost information applies to all regions used by the subaccounts in your global account. Data is updated after your monthly balance statement has been generated.

-   Your cloud credit balance is calculated each month by deducting the corresponding costs of all SAP BTP services for the previous month.

-   If your global account has received a cloud-credit refund at any time during the current cloud credits period, you may see a difference between your total costs and the monthly costs in the chart.

-   If you've previously over-consumed your available cloud credits and then purchased additional credits, you may see a shift in your monthly cloud credits cost graph from overage to within limits. This change indicates that the extra credits have balanced out any previous overages, and it is an expected part of managing your cloud credits usage.

-   If your global account uses both consumption-based and subscription-based models, this card only displays usage charged under the consumption-based model. For services included in your subscription, only usage beyond your prepaid quota is shown here and is billed per your contract’s consumption-based terms.

    For instance, if your subscription covers 100 site visits and you have 151, this card reflects data for the extra 51 visits that exceed your subscription-based quota.


> ### Tip:  
> To see more details about your contract, cloud credit or cost details, click <span class="SAP-icons-V5"></span> \(Expand\).

> ### Tip:  
> To extract the data to a spreadsheet document, use the **Export** option. For more information, see [Exporting Usage and Cost Data Information](monitoring-usage-and-consumption-costs-in-your-global-account-de6f0db.md#loiode6f0db8919f4e6f97e54bc4ddaf2ab8__section_vt2_dg4_2jb)..



</td>
</tr>
<tr>
<td valign="top">

**Cloud Platform Enterprise Agreement** 

</td>
<td valign="top">

This card has the same functionality as the **SAP BTP Enterprise Agreement** card \(see previous row\) and is displayed only if your global account uses the CPEA flavor of the consumption-based commercial model.

</td>
</tr>
<tr>
<td valign="top">

**Pay-As-You-Go for SAP BTP** 

</td>
<td valign="top">

Shows the cumulative cost trend and monthly cost trend of your global account over the last 12 months according to the licensing of your Pay-As-You-Go for SAP BTP commercial model agreement.

This card is displayed only if your global account uses the Pay-As-You-Go for SAP BTP flavor of the consumption-based commercial model.

With this commercial model, you pay only for the SAP BTP services that you use, and you are billed monthly in arrears. If your global account uses both the Pay-As-You-Go for SAP BTP consumption-based commercial model and the subscription-based model, this card displays only the usage that is charged under the consumption-based model. For services included in your subscription, only usage beyond your prepaid quota is shown here and is billed per your contract’s consumption-based terms. For instance, if your subscription covers 100 site visits and you have 151, this card reflects data for the extra 51 visits that exceed your subscription-based quota.

If your global account has received a refund at any time during the current cloud credits period, you may see a difference between the displayed monthly costs and your billing document.

Cost information applies to all regions used by the subaccounts in your global account. Data is updated after your monthly balance statement has been generated.

> ### Tip:  
> To see more details about your contract, cloud credit or cost details, click <span class="SAP-icons-V5"></span> \(Expand\).

> ### Tip:  
> To extract the data to a spreadsheet document, use the **Export** option. For more information, see [Exporting Usage and Cost Data Information](monitoring-usage-and-consumption-costs-in-your-global-account-de6f0db.md#loiode6f0db8919f4e6f97e54bc4ddaf2ab8__section_vt2_dg4_2jb)..



</td>
</tr>
<tr>
<td valign="top">

**Cost and Usage Recommendations** 

</td>
<td valign="top">

Provides actionable insights and suggestions related to your global account's costs and usage patterns. These recommendations can help you to proactively manage your cloud costs and usage, prevent unexpected expenses, and optimize resource planning.

The types of recommendations you may see include:

-   **Budget Alerts:** Notifications if budgets amounts or budget thresholds have been exceeded, prompting review and assessment of potential overruns and additional costs.

-   **Budget Management:** Suggestions to set up new budgets or reactivate expired ones to maintain control over future spending.

-   **Cloud Credit Monitoring:** Alerts if cloud credits are forecasted to be exceeded soon or if current cloud credits have been surpassed, advising monitoring or purchasing additional cloud credits.

-   **Cost Spikes:** Notifications about unusual increases in costs for specific services, subaccounts, or the entire global account, encouraging your to review detailed cost data and investigate causes.




</td>
</tr>
<tr>
<td valign="top">

**Last Month's Prepaid Quota Consumption** 

</td>
<td valign="top">

Shows how many service plans were used during the previous month within the limits of your prepaid quota as defined by your subscription-based commercial model agreement.

You can use this card to understand the utilization of service usage relative to the subscription-based plans associated with your global account so you can manage your quota more effectively.

Note that services used within your prepaid quota are billed as part of your subscription, with no additional charges. However, any usage exceeding your prepaid quota is billed according to your consumption-based commercial model terms as outlined in your agreement.

This card is displayed only if your global account uses both consumption-based and subscription-based models.

> ### Note:  
> The total number of service plans shown in this card reflects only the services that had recorded usage in your global account during the previous month.
> 
> To see all services included in your subscription, regardless of whether they were used in the past month, follow these steps:
> 
> 1.  Open the *Entitlements* \> *Service Assignments* page.
> 2.  Toggle on the *Show commercial info* option.
> 3.  In the *Entitlement Source* filter, select all services listed under *All Subscription Based*.



</td>
</tr>
<tr>
<td valign="top">

**Cost Breakdown** 

</td>
<td valign="top">

Shows a breakdown of your costliest service plans or subaccounts over the last 12 months.

> ### Tip:  
> The card shows 5 items initially. To see additional service plans and subaccounts, click <span class="SAP-icons-V5"></span> \(Expand\).



</td>
</tr>
<tr>
<td valign="top">

**Cost Distribution** 

</td>
<td valign="top">

Shows the distribution of your costliest service plans or subaccounts in the current month and over the last 12 months.

> ### Tip:  
> The card shows 5 items initially. To see additional service plans and subaccounts, click <span class="SAP-icons-V5"></span> \(Expand\).



</td>
</tr>
</table>



<a name="loiode6f0db8919f4e6f97e54bc4ddaf2ab8__section_bfz_xd3_m1c"/>

## Using the Billing Tab

You can use the *Billing* tab to display, monitor, and analyze your monthly charges of billable services, which have been consumed by the subaccounts in your global account over the last 12 months.

The billing data represents the aggregation of usage and its rating, which is determined by the pricing structure of each service. You can view the bill items for previous months or the estimated charge for the current month, to monitor your consumption costs.

The parameters for charged usage can include the amount of data processed, the number of users, the duration of use, or the specific functionality or modules used by each service. The specifics of these metrics are outlined in your contract.

> ### Tip:  
> This tab is available only if your global account uses a consumption-based commercial model.

In the *Billing* tab, you can switch between the *View by Service* and *View by Account* views:


<table>
<tr>
<td valign="top">

**View by Service** 

</td>
<td valign="top">

This view provides an overview of your charged usage across different services and their associated plans, and is useful for verifying billing details.

Here are some useful tips for working in this view:

-   To drill down and display more details about a particular service, click on an entry in the table or its <span class="SAP-icons-V5"></span> \(View Details\) button. When you drill down, a new pane opens and you can see, for example, exactly which subaccounts consume the selected service and the subtotal of charges and usage per directory and subaccount.

    In this details view, subaccounts are displayed in the context of their account hierarchy. If you want to hide their directories and display the subaccounts as a flat list, choose the *Show subaccounts only* checkbox.

    > ### Tip:  
    > In this details view, you can use the <span class="SAP-icons-V5"></span> \(Switch\) button for any subaccount to quickly open the *View by Account* view with the specific subaccount selected and displaying the plans it consumes.
    > 
    > You can also click :gear: to display and hide columns.

-   To filter the main table for specific services, use the *Service* dropdown list.

-   If the display is cluttered by too many service plans or account entities that have no charged usage, you can choose the *Show only services with charged usage* checkbox to hide them.

-   To filter the main table for specific subaccounts or directories, use the *Subaccounts/Directories* dropdown list.

-   To view a visual chart of the monthly cost trend, cumulative costs, or breakdown of the costliest subaccounts for a specific service plan over the last 12 months, first select the service plan from the main table and then scroll down past the main table to the chart area. Then, select the chart type from the *View By* dropdown list that is located adjacent to the chart area.

    > ### Tip:  
    > These charts are useful for seeing in which months a service plan has usage and costs, which service plans have increased or decreased usage/costs over time, or the months that have the highest and lowest usage/costs per service plan.

-   To view a visual chart with a summary of the costs of all service plans in your global account over the last 12 months, make sure you do not have a specific service plan selected in the main table. Then, scroll past the table to the *Global Account - Cost Summary* chart area.

    In the *View By* dropdown list, select a chart type; for example, *List Price*, *Cost Breakdown by Service Plans*, or *Cumulative List Price*.

    > ### Tip:  
    > In the cost breakdown chart, the 8 costliest service plans in your global account over the last 12 months are displayed. Click *Show More* below the chart legend to expand the chart and to view the cost breakdown of additional plans.

-   To open the SAP Price List for a specific service, choose *Open in SAP Price List* from the service plan's <span class="SAP-icons-V5"></span> \(Actions\) context menu, or you can open the service plan's details view and then click *SAP Price List* located in the header area.


See other useful tips, such as table sorting, filtering, and searching, under *General Tips for the Billing and Usage Tabs* in the [Understanding the Layout of the Costs and Usage Page](monitoring-usage-and-consumption-costs-in-your-global-account-de6f0db.md#loiode6f0db8919f4e6f97e54bc4ddaf2ab8__section_u3v_vd3_m1c) section.

</td>
</tr>
<tr>
<td valign="top">

**View by Account** 

</td>
<td valign="top">

This view provides an overview of your charged usage across different subaccounts and directories within your account hierarchy. It is useful for verifying cross-charges within your company or organization.

Here are some useful tips for working in this view:

-   To drill down and display more details about a particular subaccount or directory, click on an entry in the table or its <span class="SAP-icons-V5"></span> \(View Details\) button. When you drill down, a new pane opens and you can see, for example, exactly which plans are consumed by the selected subaccount or directory and the subtotal of the charges and usage per plan.

    > ### Tip:  
    > In this details view, you can use the <span class="SAP-icons-V5"></span> \(Switch\) button to quickly open the *View by Services* view with the specific plan selected and displaying the subaccounts that consume it.
    > 
    > You can also click :gear: to display and hide columns.

-   To filter the main table for specific subaccounts or directories, use the *Subaccounts/Directories* dropdown list.

-   If your account hierarchy includes directories, you can hide them and display your subaccounts as a flat list by choosing the *Show only subaccounts* checkbox.

-   You can quickly expand or collapse the entire account hierarchy by clicking the <span class="SAP-icons-V5"></span> \(Expand All\) and <span class="SAP-icons-V5"></span> \(Collapse All\) buttons.
-   To filter the main table for specific services, use the *Services* dropdown list.

-   To view a visual chart of the monthly cost trend, cumulative costs, or breakdown of the costliest service plans for a specific subaccount or directory over the last 12 months, first select the subaccount or directory from the main table and then scroll down past the main table to the chart area. Then, select the chart type from the *View By* dropdown list that is located adjacent to the chart area.

    > ### Tip:  
    > These charts are useful for seeing in which months a subaccount or directory has usage and costs, which subaccounts or directories have increased or decreased usage/costs over time, or the months that have the highest and lowest usage/costs per subaccount or directory.
    > 
    > When you choose a directory, the cost information applies to all subaccounts under the directory.

-   To view a visual chart with a summary of the costs of all subaccounts in your global account over the last 12 months, make sure you do not have a specific subaccount or directory selected in the main table. Then, scroll past the table to the *Global Account - Cost Summary* chart area.

    In the *View By* dropdown list, select a chart type; for example, *List Price*, *Cost Breakdown by Subaccounts*, or *Cumulative List Price*.

    > ### Tip:  
    > In the cost breakdown chart, the 8 costliest subaccounts in your global account over the last 12 months are displayed. If your global account has more than 8 subaccounts, click *Show More* below the chart legend to expand the chart and to view the cost breakdown of additional subaccounts.

-   To open the SAP Price List for a specific service used in a directory or subaccount, first open the details view of the directory or subaccount, then locate the service, and choose *Open in SAP Price List* from the service's <span class="SAP-icons-V5"></span> \(Actions\) context menu.


See other useful tips, such as table sorting and searching, under *General Tips for the Billing and Usage Tabs* in the [Understanding the Layout of the Costs and Usage Page](monitoring-usage-and-consumption-costs-in-your-global-account-de6f0db.md#loiode6f0db8919f4e6f97e54bc4ddaf2ab8__section_u3v_vd3_m1c) section.

</td>
</tr>
</table>

If your global account has subaccounts that have been deleted but have charges in the last 12 months while they were still active, they’ll still be listed. Such subaccounts are marked with *\(deleted\)* after their name. If these subaccounts were originally located under a directory, you'll see them listed directly under the root global account.

If your global account uses both a subscription and a consumption-based commercial model, the *Usage* column shows the combined total usage of services, both subscription-based and consumption-based. Note that:

-   The subscription-based consumption includes usage of services that falls within the prepaid quota that is specified in your subscription-based commercial model agreement. This part of the combined usage is shown in the *Prepaid Quota* column. There is no additional billing for consumption of the services that falls within this prepaid quota.
-   The consumption-based usage includes the usage of services that exceeds the prepaid subscription-based quota. This part of the combined usage is shown in the *Charged Usage* column. For this usage, you are charged based on the terms outlined in your consumption-based commercial model agreement.



<a name="loiode6f0db8919f4e6f97e54bc4ddaf2ab8__section_vff_dr3_m1c"/>

## Using the Usage Tab

Use the *Usage* tab to display, monitor, and analyze the distribution of the actual \(also called raw\) monthly usage metrics for services consumed by subaccounts in your global account over the last 12 months.

> ### Note:  
> The *Usage* tab displays data prior to aggregation for billing and can contain metrics that will not be aggregated since they are always free or belong to free services. Hence, you may notice some discrepancies when comparing the data in the *Usage* tab to the overall usage data shown in the *Billing* tab. Billable usage data is aggregated at the global account level and then processed according to accounting formulas to generate your monthly billing statement.

Pay attention also to the following:

-   If your global account uses only a consumption-based commercial model, such as SAP BTP Enterprise Agreement \(SAP BTPEA\),Cloud Platform Enterprise Agreement \(CPEA\), and Pay-As-You-Go for SAP BTP, this tab includes all usage data, including non-rated services, such as free service plans.
-   If your global account uses both the consumption-based and subscription-based commercial models, this tab combines all usage data, which falls under your consumption-based plans, prepaid subscription quota, and non-rated data sets, such as free service plans. You can see the distribution of charged and prepaid usage and costs in the *Billing* tab.


<table>
<tr>
<th valign="top">

To Do This...

</th>
<th valign="top">

Do This...

</th>
</tr>
<tr>
<td valign="top">

Drill down and display more details about a particular service

</td>
<td valign="top">

Click on an entry in the table or its <span class="SAP-icons-V5"></span> \(View Details\) button. When you drill down, a new pane opens and you can see, for example, which subaccounts are consuming the selected service and the subtotal of usage per directory and subaccount.

In this details view, subaccounts are displayed in the context of their account hierarchy. If you want to hide their directories and display the subaccounts as a flat list, choose the *Show subaccounts only* checkbox.

> ### Tip:  
> In this details view, you can click :gear: to display and hide columns.



</td>
</tr>
<tr>
<td valign="top">

Filter by specific services

</td>
<td valign="top">

Choose one or more in the *Service* dropdown list.

> ### Tip:  
> If the display is cluttered by too many service plans that have no usage, choose the *Show only used services* checkbox to quickly hide them.



</td>
</tr>
<tr>
<td valign="top">

Filter by specific subaccounts and directories

</td>
<td valign="top">

Choose one or more subaccounts or directories in the *Subaccounts/Directories* dropdown list.

</td>
</tr>
<tr>
<td valign="top">

View the monthly usage trend of a specific service plan over the last 12 months

</td>
<td valign="top">

Select the service plan from the main table and scroll past the table to the chart area. Then, choose *Actual Usage* in the *View By* dropdown list that is located adjacent the chart area.

This chart is useful for seeing changes in usage trends over time, including the months with the highest and lowest usage per service.

</td>
</tr>
<tr>
<td valign="top">

View a monthly breakdown of subaccounts that have used a specific service plan the most over the last 12 months

</td>
<td valign="top">

Select the service plan from the main table and scroll past the table to the chart area. Then, choose *Usage Breakdown by Subaccounts* in the *View By* dropdown list.

The top 8 subaccounts that use the selected plan the most are displayed initially. If there are more than 8 subaccounts that use the plan, click *Show More* to expand the chart and to view the breakdown of additional subaccounts.

</td>
</tr>
</table>

> ### Tip:  
> See other useful tips, such as table sorting, filtering, and searching, in the [Understanding the Layout of the Costs and Usage Page](monitoring-usage-and-consumption-costs-in-your-global-account-de6f0db.md#loiode6f0db8919f4e6f97e54bc4ddaf2ab8__section_u3v_vd3_m1c) section.



<a name="loiode6f0db8919f4e6f97e54bc4ddaf2ab8__section_ftl_cdm_gfc"/>

## Using the Budgets Tab

For detailed information about using this tab to help you manage your global account spending and to plan for future consumption, see [Managing Budgets in Your Global Account](managing-budgets-in-your-global-account-e115d5f.md#loioe115d5fbe1454f58aabeb3b4b1e7a847).



<a name="loiode6f0db8919f4e6f97e54bc4ddaf2ab8__section_gqh_qtp_tcc"/>

## Estimated and Forecasted Data

In addition to actual usage that you've already been charged for, the **Costs and Usage** page also shows estimated and forecasted values in the cloud credits usage and cost charts:

-   **Estimated Data:** The estimated values reflect your accrued service usage during the period between the last balance statement and the current date.

    The values are estimated because they are based on resource usage values before computation for billing and might change after the next balance statement is issued. The estimated values are not forecast values.

-   **Forecasted Data:**The SAP BTP Enterprise Agreement and Cloud Platform Enterprise Agreement cards in the *Overview* tab offer a *Show forecast* option that allows you to display a forecast of your cloud-credit costs and usage for the next 6 months or until the end of current contract period, whichever is shorter.

    The forecast is based on certain assumptions and the historical data taken from your global account. To make a reliable forecast, you need to have consistent data from the recent past covering at least 9 months. If the available historical data in your global account doesn't allow for a reliable prediction, you cannot turn on the forecasting option.

    The forecast does not include the costs and usage of the current month \(since this estimated data only\), nor does it take into consideration any changes to future usage patterns or costs. Additionally, you cannot turn on the forecasting when you're in the last month of the current cloud credits period.

    > ### Note:  
    > The forecast data provided by our software is intended for informational purposes only; however, it can you help to anticipate and plan for future usage needs and to budget accordingly.
    > 
    > SAP is not responsible for and cannot guarantee the accuracy or reliability of the forecast data, and it should not be considered as financial, legal, professional, or any other advice. It is your responsibility to independently review and validate the forecast information before making any decisions or taking any actions based on it.




<a name="loiode6f0db8919f4e6f97e54bc4ddaf2ab8__section_vt2_dg4_2jb"/>

## Exporting Usage and Cost Data Information

To export your usage and cost data to a Microsoft Excel spreadsheet document, use the *Export* button menu in the header of the *Costs and Usage* page.

> ### Note:  
> Cost information is exported only if your global account uses the consumption-based commercial information.

The *Export* button menu has various options depending on the period and type of data that you want to export:

-   If you want to export all data for the last 12 months, click the main *Export* button.
-   If you want to export all data for the last 12, 24, or 36 months, click the button's dropdown menu and choose the relevant period.
-   If you want to export only the data that you've currently filtered in the main table for the current month or last 12, 24, or 36 months, choose *Export* \> *Custom*.

    > ### Tip:  
    > Use this option also if you want to export all your cost and usage data for the current month without considering any currently set filters. To do this, deselect the *Export only filtered data* checkbox in the *Custom Export*dialog box.
    > 
    > In the *Custom Export* dialog box, you can also choose any label names \(keys\) that you want to add as dedicated columns to the `Subaccount Costs by Service` and `Actual Usage` sheets \(tabs\) in the exported Microsoft Excel file. Start typing to list the available label names for your existing subaccounts and directories. In the exported spreadsheet, the values for each selected label name are displayed in the data rows under their respective label column.


The exported document contains several sheets \(tabs\). The sheets that are included depend on the commercial model that is used by your global account as shown in the following table:


<table>
<tr>
<th valign="top" rowspan="2">

Sheet Name

</th>
<th valign="top" rowspan="2">

Description

</th>
<th valign="top" align="center" colspan="2">

Commercial Model

</th>
</tr>
<tr>
<th valign="top" align="center">

Subscription-Based

</th>
<th valign="top" align="center">

Consumption-Based

</th>
</tr>
<tr>
<td valign="top">

**Global Account Info** 

</td>
<td valign="top">

Provides general information about your global account. If there is a cloud-credit balance for the global account, then its cloud-credit usage, per month as a percentage of your total cloud credits for the current cloud credits period, is also shown.

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

**Global Account Costs** 

</td>
<td valign="top">

Allows you to view total monthly usage data and costs for all billable services and plans consumed at the level of your global account.

The items listed are all the billed items that are created in the accounting system and deducted from the cloud-credit balance of your global account.

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

**Subaccount Costs by Service** 

</td>
<td valign="top">

Allows you to view monthly usage data and costs of all billable services consumed by plan and subaccount.

All subaccount calculations are estimated and proportionate to the total global account usage:

`[Subaccount usage / Global account usage x Rate plan per SKU]`

> ### Note:  
> Global accounts are the only contractual billable entity for SAP BTP. Directories and subaccounts are used as structural entities in the global account, and their usage and cost data should only be used for your internal cost estimations. The relative calculation per billable usage within each subaccount is an estimation only as it is based on certain measures which in some cases can either be different from the metrics that are presented in the **SAP BTP Enterprise Agreement**, **Cloud Platform Enterprise Agreement**, and**Pay-As-You-Go for SAP BTP** cards in the *Overview* tab, or which use different formulas than the ones used for billing.



</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

**Actual Usage** 

</td>
<td valign="top">

Allows to you to view the actual monthly usage data of all consumed services by plan, subaccount, and space.

Actual or raw usage data is different to the billed usage that is used in your billing document, and includes non-billable services.

The aggregated usage for each service is based on a formula that is specific to each service, for example, MIN, MAX, or AVG.

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

**CF Space Costs by Service** 

</td>
<td valign="top">

Allows you to view the monthly cost distribution of your service plans across the Cloud Foundry spaces in your global account.

> ### Note:  
> This is a beta feature. Beta features aren't part of the officially delivered scope that SAP guarantees for future releases. For more information, see [Important Disclaimers and Legal Information](https://help.sap.com/viewer/disclaimer).

To include this information in the spreadsheet, you must choose the *Export cost distribution by Cloud Foundry spaces* option in the *Custom Export* dialog box.

The cost distribution in the exported spreadsheet is estimated and proportionate to the usage of each service across the Cloud Foundry spaces within a subaccount. For example, if the distribution of the total usage of a service is 20% in one space and 80% in another space within the same subaccount, the cost per space is calculated proportionately as 20% and 80% of the total cost of the service in that subaccount for the two spaces, respectively.

When a specific service **instance** is used by multiple spaces in Cloud Foundry, the full cost of that service is only charged to the space where it is provisioned. So, the cost breakdown by spaces in the exported Excel file works best when the service is used in the same space it was set up in. However, you can use the exported subaccount data to split the costs differently to better fit your setup.

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

**Labels**

</td>
<td valign="top">

Lists the user-defined labels that are assigned directly to each subaccount that has usage data. Also lists the labels that are inherited by the subaccounts from their parent directories, and the IDs of those subaccounts.

This sheet does not display any usage data; however, you can use this information to determine usage by label by extrapolating the subaccount usage data in the other sheets to the labels assigned to the subaccounts in this sheet.

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
</table>

**Related Information**  


[Managing Budgets in Your Global Account](managing-budgets-in-your-global-account-e115d5f.md#loioe115d5fbe1454f58aabeb3b4b1e7a847 "Budgets allow you to better control your global account spending and plan for future consumption by setting up budget limits for your global account in SAP BTP.")

[Commercial Models](../10-concepts/commercial-models-263d400.md "SAP BTP offers two different commercial models for enterprise accounts.")

[Trial Accounts and Free Tier](../10-concepts/trial-accounts-and-free-tier-046f127.md "Explore the different options for trying out SAP BTP.")

[Using Free Service Plans](../10-concepts/using-free-service-plans-524e108.md "The free tier model for SAP BTP lets you try out services in global accounts without any additional cost using the consumption-based commercial model and an enterprise account.")

[Managing Entitlements and Quotas Using the Cockpit](managing-entitlements-and-quotas-using-the-cockpit-c824874.md "When you purchase an enterprise account, you are entitled to use a specific set of resources, such as the amount of memory that can be allocated to your applications.")

[View Subaccount Usage Analytics](view-subaccount-usage-analytics-8f4d9db.md "You can explore, compare, and analyze all your actual usage data for the services and applications that are available in your subaccount.")

[View Directory Usage Analytics](view-directory-usage-analytics-a287782.md "You can explore, compare, and analyze all your actual usage data for the services and applications that are available in your directory.")

[Labels](../10-concepts/account-model-8ed4a70.md#loioe8663c08ead648faa673b0d63c5b478e "Labels are user-defined words or phrases that you can assign to various entities in SAP BTP to categorize them in your global account, to identify them more easily.")

[Monitoring Usage Information Using APIs of the SAP Usage Data Management Service](monitoring-usage-information-using-apis-of-the-sap-usage-data-management-service-bf2b304.md "Provides information about using the Resource Consumption APIs of the SAP Usage Data Management service for SAP BTP for gathering, storing, and making usage information available for all services and applications in all regions in a cloud deployment. This information is for the purpose of central analysis, reporting, and license auditing.")

