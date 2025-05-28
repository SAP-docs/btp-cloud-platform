<!-- loiobf2b3043d0474ea0a2c11c0390460d85 -->

# Monitoring Usage Information Using APIs of the SAP Usage Data Management Service 

Provides information about using the *Resource Consumption* APIs of the SAP Usage Data Management service for SAP BTP for gathering, storing, and making usage information available for all services and applications in all regions in a cloud deployment. This information is for the purpose of central analysis, reporting, and license auditing. 

The service accumulates the information and provides reports in SAP BTP cockpit via APIs for resource planning and cross-billing purposes.

> ### Note:  
> The SAP Usage Data Management service is not sold to SAP BTP customers as a service; however, customers can see their usage data in the cockpit, for example, in the Usage Analytics pages.



<a name="loiobf2b3043d0474ea0a2c11c0390460d85__section_esj_34z_fmb"/>

## Accessing the API

For more information about the APIs, including their specifications and endpoints, go to [Resource Consumption](https://api.sap.com/api/APIUasReportingService/resource) for the list of all SAP Usage Data Management service APIs in the SAP Business Accelerator Hub.

> ### Remember:  
> To call the core platform API methods, you must obtain an access token. See [Configuration for Using the Resource Consumption APIs in the SAP Business Accelerator Hub](configuration-for-using-the-resource-consumption-apis-in-the-sap-business-accelerator-h-4bfe9c7.md).

**Base URI:** <code>https://uas-reporting.cfapps.<i class="varname">&lt;landscape domain&gt;</i>/reports/v1</code>

Your global account admin has entitled the service plan for the SAP Usage Data Management service in your subaccount. See [SAP Usage Data Management Service - Service Plans](sap-usage-data-management-service-service-plans-c94c85e.md).



<a name="loiobf2b3043d0474ea0a2c11c0390460d85__section_ymz_k4z_fmb"/>

## Methods


<table>
<tr>
<th valign="top">

HTTP Method

</th>
<th valign="top">

Action

</th>
<th valign="top">

URI

</th>
</tr>
<tr>
<td valign="top">

GET

</td>
<td valign="top">

Get the cloud credit data history for a global account.

</td>
<td valign="top">

`/cloudCreditDetails`

</td>
</tr>
<tr>
<td valign="top">

GET

</td>
<td valign="top">

Get monthly usage reporting data for a directory and a specified time period.

</td>
<td valign="top">

`/monthlyDirectoryUsage`

</td>
</tr>
<tr>
<td valign="top">

GET

</td>
<td valign="top">

Get monthly usage-reporting data for a global account and a specified time period.

</td>
<td valign="top">

`/monthlyUsage`

</td>
</tr>
<tr>
<td valign="top">

GET

</td>
<td valign="top">

Get usage-reporting data for a subaccount.

</td>
<td valign="top">

`/subaccountUsage`

</td>
</tr>
<tr>
<td valign="top">

GET

</td>
<td valign="top">

Get monthly cost reporting data for all subaccounts for the Cloud Platform Enterprise Agreement \(CPEA\) consumption-based commercial model.

</td>
<td valign="top">

`/monthlySubaccountsCost`

</td>
</tr>
</table>

**Related Information**  


[Configuration for Using the Resource Consumption APIs in the SAP Business Accelerator Hub](configuration-for-using-the-resource-consumption-apis-in-the-sap-business-accelerator-h-4bfe9c7.md "The Resource Consumption APIs of the SAP Usage Data Management service for SAP BTP are protected with OAuth 2.0 Client Credentials grant type and in some cases, also the Password grant type.")

[SAP Usage Data Management Service - Service Plans](sap-usage-data-management-service-service-plans-c94c85e.md "Describes the plans available for the SAP Usage Data Management service for SAP BTP.")

