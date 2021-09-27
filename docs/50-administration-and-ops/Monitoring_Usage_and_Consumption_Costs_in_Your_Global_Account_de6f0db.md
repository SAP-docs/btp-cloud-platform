<!-- loiode6f0db8919f4e6f97e54bc4ddaf2ab8 -->

# Monitoring Usage and Consumption Costs in Your Global Account

In a global account that uses the consumption-based commercial model, you can monitor the usage of billed services and your consumption costs in the SAP BTP cockpit.

> ### Note:  
> -   The use of the consumption-based commercial model is subject to its availability in your country or region.
> -   If your global account uses the subscription-based commercial model, then information in this topic that refers to usage data also applies to you. Ignore information about costs and cloud credits.
> -   Directories only apply to global accounts that are running in feature set B.



<a name="loiode6f0db8919f4e6f97e54bc4ddaf2ab8__section_nv3_bqx_lnb"/>

## Accessing Usage Analytics for Your Global Account

Accessing the global account's usage analytics is different when using cloud management tools feature set A or B. For more information on the two feature sets, see [Cloud Management Tools — Feature Set Overview](../10-concepts/Cloud_Management_Tools_—_Feature_Set_Overview_caf4e4e.md).

**Feature Set A**

To monitor and track usage in your global account, open the global account in the cockpit and choose *Overview* in the navigation area.

The global account's *Overview* page provides information about the usage of cloud credits \(if your account has a cloud-credit balance\) and costs for a global account, and the usage of services in the global account and its subaccounts.

**Feature Set B**

To monitor and track usage in your global account, open the global account in the cockpit and choose *Usage Analytics* in the navigation area.

The global account's *Usage Analytics* page provides information about the usage of cloud credits \(if your account has a cloud credits balance\) and costs for a global account, and the usage of services in the global account and its directories and subaccounts.



<a name="loiode6f0db8919f4e6f97e54bc4ddaf2ab8__section_lfq_cy5_c2b"/>

## Using the Global Account's Usage Analytics / Overview Page

> ### Note:  
> -   Global accounts that use the consumption-based commercial model can include actual usage information on the Cloud Foundry space level, which is different from billed usage used in your billing document. Usage data is processed according to accounting formulas that generate a billing document that aggregates all usage, from all spaces, so that it is favorable to customers. There is no unified method to calculate costs based on actual usage.
> 
> -   Costs are displayed according to your contract currency.
> 
> -   If your global account uses the subscription-based commercial model exclusively, then only usage data is displayed. Cloud credits and cost information is not relevant for such accounts.
> 
> -   If your global account is licensed for both the consumption-based and subscription-based commercial models, the *Global Account Costs*, *Cloud Credits Usage*, and *Global Account Overview* views in this page show billing and usage data that is charged solely according to the consumption-based commercial model. For services in your subscription-based commercial agreement, you'll see billing and usage data for usage that exceeds your subscribed quota. For any excess service usage, you are charged according to your contract for the consumption-based commercial model.
> 
>     For example, if your subscription contract is entitled to consume a given service at a fixed cost for up to 100 unique site visits, and 151 unique site visits are registered, these views will show data relating only to the 51 visits that have exceeded the 100 limit.
> 
>     When viewing usage data on the service or subaccount level for such accounts in the remaining views in this page, the displayed data is the total combined usage for both consumption-based and subscription-based commercial models.

-   When there is a cloud-credit balance for the global account, the cloud-credit usage information is displayed for the current contract period. The total contract duration is split into contract periods \(usually of one year each\) and the total cloud credits are divided between these periods.

    > ### Note:  
    > If your global account has received a cloud-credit refund at any time during the current contract phase, you may see a difference between your total usage and monthly usage in the chart.

-   When there is no cloud-credit balance for the global account, the monthly total costs for the global account are displayed from the contract start date.

    > ### Note:  
    > If your global account has received a refund at any time during the current contract phase, you may see a difference between the displayed monthly costs and your billing document.

-   In the resource usage views, use the filters to specify which information to display. The *Period* filter applies only to the chart display.
-   Some rounding or shortening is applied to large values. Mouse over values in the table to view the exact values in the tooltips.
-   Choose a row in the table to view its historic information in the *Monthly Usage* chart.
-   To display a larger view of a chart, choose the   \(Zoom\)  button.



<a name="loiode6f0db8919f4e6f97e54bc4ddaf2ab8__section_dfy_x5h_kcb"/>

## Understanding the Views


<table>
<tr>
<th>

View



</th>
<th>

Description



</th>
<th>

Action



</th>
</tr>
<tr>
<td>

 **Global Account Info** 



</td>
<td>

Displays general information about the global account, including the number of directories and subaccounts it contains, and the number of regions which have these subaccounts.



</td>
<td>

\[Feature Set B\]: Click the *Directories* or *Subaccounts* links to navigate directly to the *Account Explorer* page.

\[Feature Set A\]: Click the *Subaccounts* link to navigate directly to the *Subaccounts* page.



</td>
</tr>
<tr>
<td>

**Cloud Credits Usage**

\(Only displayed when there is a cloud-credit balance for a global account that uses the consumption-based commercial mode.\)



</td>
<td>

Displays the current balance and monthly usage of cloud credits as a percentage of the cloud credits allocated per contract period.

-   Cloud-credit information is based on the monthly balance statements for the global account.

-   For the time period between the last balance statement and the current date, the chart uses estimated values, which are displayed as striped bars.

    These estimates are based on resource usage values before computation for billing, and might change after the next balance statement is issued. The estimated values are not projected or forecast values.


Alerts are displayed when you have used more than 90% and when you reach 100% of your cloud credits.



</td>
<td>

 



</td>
</tr>
<tr>
<td>

**Global Account Costs**

\(Only displayed when there is no cloud-credit balance for a global account that uses the consumption-based commercial mode.\)



</td>
<td>

Displays the total cost per month for usage of services in the global account from the contract start date.

All cost information is for all regions in the global account.

Actual costs are updated after the monthly statement is generated.



</td>
<td>

 



</td>
</tr>
<tr>
<td>

 **Global Account Overview** 



</td>
<td>

Displays usage and costs of all services in the global account. The information is broken down according to service plans. All the regions in which a service plan is available are displayed; however, actual usage is only in the regions of your subaccounts.

> ### Note:  
> Usage and cost information is updated every 24 hours. Data for the first of the month might not appear until the following day.

The charts display information for each month for all service plans in the table or only for the selected row. Provisional data for the current month is displayed as striped bars.

> ### Note:  
> Some service plans have differential pricing depending on the region. Usage and costs of a service plan in multiple regions with differential pricing are displayed as separate items.



</td>
<td>

Use the *View By* options to switch the view between service plan usage and costs for the global account.

Use the filter to select the environment and service for which you want to view information.

For the chart display, select a row, and filter by period. If no row is selected, the chart displays information for all the service plans in the table.



</td>
</tr>
<tr>
<td>

 **Service Usage** 



</td>
<td>

Displays resource usage according to service. Some service plans may display usage according to multiple metrics.



</td>
<td>

Use the filter to select the service and directory or subaccount for which to display usage.

For the chart display, select a row, and filter by period. If no row is selected, the chart displays information for all the service plans in the table.



</td>
</tr>
<tr>
<td>

 **Directory/Subaccount Usage** 



</td>
<td>

Displays resource usage according to subaccount or directory. Some service plans may display usage according to multiple metrics.



</td>
<td>

Use the filter to select the directory or subaccount for which to display usage.

For the chart display, select a row and filter by period. If no row is selected, the chart displays information for all the service plans in the table.



</td>
</tr>
</table>



<a name="loiode6f0db8919f4e6f97e54bc4ddaf2ab8__section_vt2_dg4_2jb"/>

## Exporting Usage and Cost Data Information

You can export the displayed usage and cost data to a spreadsheet document:

-   To export usage and cost data from all the views, choose *Export* \> *All Data*.
-   To export only cloud-credit usage data, choose *Export* \> *Cloud Credits Usage*.

The document with the relevant data is downloaded. The document contains several sheets \(tabs\). The sheets that are included in the export depend on the commercial model that is used by your global account \(and the export option that you selected\).


<table>
<tr>
<th rowspan="2">

Sheet Name



</th>
<th rowspan="2">

Description



</th>
<th colspan="2">

Commercial Model



</th>
</tr>
<tr>
<th>

Subscription-Based



</th>
<th>

Consumption-Based



</th>
</tr>
<tr>
<td>

Global Account Info



</td>
<td>

Provides general information about your global account. If there is a cloud-credit balance for the global account, then its cloud-credit usage, per month as a percentage of your total cloud credits for the current contract period, is also shown.



</td>
<td>

Yes



</td>
<td>

Yes



</td>
</tr>
<tr>
<td>

Global Account Costs



</td>
<td>

Allows you to view total monthly usage data and costs for all billable services and plans consumed at the level of your global account.

The items listed are all the billed items that are created in the accounting system and deducted from the cloud-credit balance of your global account.



</td>
<td>

No



</td>
<td>

Yes



</td>
</tr>
<tr>
<td>

Subaccount Costs by Service



</td>
<td>

Allows you to view monthly usage data and costs of all billable services consumed by plan and subaccount.

All subaccount calculations are estimated and proportionate to the total global account usage:

`[Subaccount usage / Global account usage x Rate plan per SKU]`

> ### Note:  
> Global accounts are the only contractual billable entity for SAP BTP. Directories and subaccounts are used as structural entities in global account, and their usage and cost data should only be used for your internal cost estimations. The relative calculation per billable usage within each subaccount is an estimation only as it is based on certain measures which in some cases can either be different from the metrics that are presented in the *Global Account Costs* tab or which use different formulas than the ones used for billing.

This sheet is not included in the spreadsheet if your global account is licensed for both the consumption-based and subscription-based commercial models.



</td>
<td>

No



</td>
<td>

Yes



</td>
</tr>
<tr>
<td>

Actual Usage



</td>
<td>

Allows to you to view the actual monthly usage data of all consumed services by plan, subaccount, and space.

Actual or raw usage data is different to the billed usage that is used in your billing document, and includes non-billable services.

The aggregated usage for each service is based on a formula that is specific to each service, for example, MIN, MAX, or AVG.



</td>
<td>

Yes



</td>
<td>

Yes



</td>
</tr>
</table>

> ### Example:  
> A global account, which uses the consumption-based commercial model, has the following usage data in a given month, where SAP HANA and Application Runtime are billable services, and Destination is a non-billable service:
> 
> 
> <table>
> <tr>
> <td rowspan="2">
> 
> Subaccount 1
> 
> 
> 
> </td>
> <td>
> 
> 1x SAP HANA 256 GB, 200 MB of Application Runtime, and 300 API calls of Destination 
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td>
> 
> 200 MB of Application Runtime and 300 API calls of Destination 
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td>
> 
> Subaccount 2
> 
> 
> 
> </td>
> <td>
> 
> 1x SAP HANA 512 GB, 600 MB of Application Runtime, and 300 API calls of Destination 
> 
> 
> 
> </td>
> </tr>
> </table>
> 
> Based on these usage measurements, you would see the following data in the spreadsheet. Each listed item represents one row in the spreadsheet. Cost prices shown are for illustration purposes only and do not reflect the actual rates for the mentioned services.
> 
> 
> <table>
> <tr>
> <th>
> 
> Sheet
> 
> 
> 
> </th>
> <th>
> 
> Sample Usage and Cost Data Displayed in Spreadsheet
> 
> 
> 
> </th>
> </tr>
> <tr>
> <td>
> 
> Global Account Costs
> 
> 
> 
> </td>
> <td>
> 
> -   1 instance of SAP HANA 256 = EUR 1024
> 
> -   1 instance of SAP HANA 512 = EUR 2048
> 
> -   1 GB of Application Runtime = EUR 100 + estimated cost distribution to subaccounts
> 
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td>
> 
> Subaccount Costs by Service
> 
> 
> 
> </td>
> <td>
> 
> -   Subaccount 1: 1 instance of SAP HANA 256 = EUR 1024
> 
> -   Subaccount 2: 1 instance of SAP HANA 512 = EUR 2048
> 
> -   Subaccount 1: 400 MB of Application Runtime = EUR 40 \(400 MB / 1 GB x EUR 100\)
> 
> -   Subaccount 2: 600 MB of Application Runtime = EUR 60 \(600 MB / 1 GB x EUR 100\)
> 
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td>
> 
> Actual Usage
> 
> 
> 
> </td>
> <td>
> 
> -   Subaccount 1 | Space A: 1 instance of SAP HANA 256
> 
> -   Subaccount 2 | Space C: 1 instance of SAP HANA 512
> 
> -   Subaccount 1 | Space A: 200 MB of Application Runtime
> 
> -   Subaccount 1 | Space B: 200 MB of Application Runtime
> 
> -   Subaccount 2 | Space C: 600 MB of Application Runtime
> 
> -   Subaccount 1 | Space A: 300 API calls of Destination
> 
> -   Subaccount 1 | Space B: 300 API calls of Destination
> 
> -   Subaccount 2 | Space C: 300 API calls of Destination
> 
> 
> 
> 
> </td>
> </tr>
> </table>

**Related Information**  


[Cloud Management Tools — Feature Set Overview](../10-concepts/Cloud_Management_Tools_—_Feature_Set_Overview_caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

[What Is the Consumption-Based Commercial Model?](../10-concepts/What_Is_the_Consumption-Based_Commercial_Model_7047eb4.md "With the consumption-based model, your organization purchases an entitlement to all current and future SAP BTP services that are eligible for this model. Throughout the duration of your contract, you have complete flexibility to turn services on and off and to switch between services as your business requires.")

[View Subaccount Usage Analytics](View_Subaccount_Usage_Analytics_8f4d9db.md "You can explore, compare, and analyze all your actual usage data for the services and applications that are available in your subaccount.")

[View Directory Usage Analytics \[Feature Set B\]](View_Directory_Usage_Analytics_Feature_Set_B_a287782.md "You can explore, compare, and analyze all your actual usage data for the services and applications that are available in your directory.")

[Monitoring Usage Information Using APIs of the SAP Usage Data Management Service \[Feature Set B\]](Monitoring_Usage_Information_Using_APIs_of_the_SAP_Usage_Data_Management_Service_Feature_Set_B_bf2b304.md "Provides information about using the Resource Consumption APIs of the SAP Usage Data Management service for SAP BTP for gathering, storing, and making usage information available for all services and applications in all regions in a cloud deployment. This information is for the purpose of central analysis, reporting, and license auditing.")

