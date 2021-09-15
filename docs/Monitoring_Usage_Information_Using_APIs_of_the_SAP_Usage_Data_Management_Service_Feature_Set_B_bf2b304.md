<!-- loiobf2b3043d0474ea0a2c11c0390460d85 -->

# Monitoring Usage Information Using APIs of the SAP Usage Data Management Service \[Feature Set B\]

> ### Note:  
> The content in this section is only relevant for cloud management tools feature set B. For more information, see [Cloud Management Tools - Feature Set Overview](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/caf4e4e23aef4666ad8f125af393dfb2.html).

Provides information about using the *Resource Consumption* APIs of the SAP Usage Data Management service for SAP BTP for gathering, storing, and making usage information available for all services and applications in all regions in a cloud deployment. This information is for the purpose of central analysis, reporting, and license auditing.

The service accumulates the information and provides reports in SAP BTP cockpit via APIs for resource planning and cross-billing purposes.

> ### Note:  
> The SAP Usage Data Management service is not sold to SAP BTP customers as a service; however, customers can see their usage data in the cockpit, for example, in the Usage Analytics pages.



<a name="loiobf2b3043d0474ea0a2c11c0390460d85__section_esj_34z_fmb"/>

## Accessing the API

For more information about the APIs, including their specifications and endpoints, go to [Resource Consumption](https://api.sap.com/api/APIUasReportingService/resource) for the list of all SAP Usage Data Management service APIs in SAP API Business Hub.

Alternatively, go to `https://uas-reporting.*<app domain\>*.*<landscape domain\>*/swagger-ui.html` where you can try out the APIs.

> ### Example:  
> If your account is running on the Europe \(Frankfurt\) region, use this URL:
> 
> `https://uas-reporting.cfapps.eu10.hana.ondemand.com/swagger-ui.html`

> ### Remember:  
> To call the core platform API methods, you must obtain an access token. See [Getting an Access Token for Resource Consumption APIs](Getting_an_Access_Token_for_Resource_Consumption_APIs_4bfe9c7.md).

**Base URI:** `https://uas-reporting.cfapps.*<landscape domain\>*/reports/v1`

Your global account admin has entitled the service plan for the SAP Usage Data Management service in your subaccount. See [SAP Usage Data Management Service - Service Plans](SAP_Usage_Data_Management_Service_-_Service_Plans_c94c85e.md).



<a name="loiobf2b3043d0474ea0a2c11c0390460d85__section_ymz_k4z_fmb"/>

## Methods


<table>
<tr>
<th>

HTTP Method



</th>
<th>

Action



</th>
<th>

URI



</th>
</tr>
<tr>
<td>

GET



</td>
<td>

Get monthly usage-reporting data for a global account and a specified time period.



</td>
<td>

`/monthlyUsage`



</td>
</tr>
<tr>
<td>

GET



</td>
<td>

Get usage-reporting data for a subaccount.



</td>
<td>

`/subaccountUsage`



</td>
</tr>
<tr>
<td>

GET



</td>
<td>

Get monthly cost reporting data for all subaccounts for the Cloud Platform Enterprise Agreement \(CPEA\) consumption-based commercial model.



</td>
<td>

`/monthlySubaccountsCost`



</td>
</tr>
</table>

-   **[Getting an Access Token for Resource Consumption APIs](Getting_an_Access_Token_for_Resource_Consumption_APIs_4bfe9c7.md "The Resource Consumption APIs of the SAP Usage Data Management
                                    service for SAP BTP are protected
		with OAuth 2.0 Client Credentials grant type and in some cases, also the Password grant
		type.")**  
The **Resource Consumption** APIs of the SAP Usage Data Management service for SAP BTP are protected with OAuth 2.0 Client Credentials grant type and in some cases, also the Password grant type.
-   **[SAP Usage Data Management Service - Service Plans](SAP_Usage_Data_Management_Service_-_Service_Plans_c94c85e.md "Describes the plans available for the  SAP Usage Data Management
                                    service for SAP BTP.")**  
Describes the plans available for the SAP Usage Data Management service for SAP BTP.

**Related Information**  


[Getting an Access Token for Resource Consumption APIs](Getting_an_Access_Token_for_Resource_Consumption_APIs_4bfe9c7.md "The Resource Consumption APIs of the SAP Usage Data Management service for SAP BTP are protected with OAuth 2.0 Client Credentials grant type and in some cases, also the Password grant type.")

[SAP Usage Data Management Service - Service Plans](SAP_Usage_Data_Management_Service_-_Service_Plans_c94c85e.md "Describes the plans available for the SAP Usage Data Management service for SAP BTP.")

[Cloud Management Tools — Feature Set Overview](Cloud_Management_Tools_—_Feature_Set_Overview_caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

