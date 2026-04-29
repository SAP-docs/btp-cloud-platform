<!-- loioa67aa51c5a094a8888cfe3c2019d4e08 -->

# Service Availability and URLs

Find information about the URLs and Cloud Foundry regions on which the SAP Cloud Deployment service is available.



The SAP Cloud Deployment service is currently available on the following URLs:

-   `https://deploy-service.cf.<domain>`
-   `https://deploy-service.cfapps.<domain>` - legacy route

    > ### Note:  
    > The legacy route `https://deploy-service.cfapps.<domain>` is deprecated and will be removed by the end of 2026. For more information, see SAP Note [3695458](https://me.sap.com/notes/3695458).


The `<domain>` is derived from the Cloud Foundry API endpoint, which you can find in the *Overview* section of your subaccount in the SAP BTP cockpit.

The SAP Cloud Deployment service is available in all Cloud Foundry regions \(see [Regions and API Endpoints Available for the Cloud Foundry Environment](../10-concepts/regions-and-api-endpoints-available-for-the-cloud-foundry-environment-f344a57.md)\). For some Cloud Foundry regions, there are multiple CF API endpoints, and the SAP Cloud Deployment service is available on each of them:

> ### Example:  
> **Example for region cf-eu10**
> 
> 
> <table>
> <tr>
> <th valign="top">
> 
> CF API Endpoint
> 
> </th>
> <th valign="top">
> 
> Domain
> 
> </th>
> <th valign="top">
> 
> SAP Cloud Deployment service URL
> 
> </th>
> <th valign="top">
> 
> SAP Cloud Deployment service Legacy URL
> 
> </th>
> </tr>
> <tr>
> <td valign="top">
> 
> `api.cf.eu10.hana.ondemand.com`
> 
> </td>
> <td valign="top">
> 
> `eu10.hana.ondemand.com`
> 
> </td>
> <td valign="top">
> 
> `https://deploy-service.cf.eu10.hana.ondemand.com`
> 
> </td>
> <td valign="top">
> 
> `https://deploy-service.cfapps.eu10.hana.ondemand.com`
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> `api.cf.eu10-002.hana.ondemand.com`
> 
> </td>
> <td valign="top">
> 
> `eu10-002.hana.ondemand.com`
> 
> </td>
> <td valign="top">
> 
> `https://deploy-service.cf.eu10-002.hana.ondemand.com`
> 
> </td>
> <td valign="top">
> 
> `https://deploy-service.cfapps.eu10-002.hana.ondemand.com`
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> `api.cf.eu10-003.hana.ondemand.com`
> 
> </td>
> <td valign="top">
> 
> `eu10-003.hana.ondemand.com`
> 
> </td>
> <td valign="top">
> 
> `https://deploy-service.cf.eu10-003.hana.ondemand.com`
> 
> </td>
> <td valign="top">
> 
> `https://deploy-service.cfapps.eu10-003.hana.ondemand.com`
> 
> </td>
> </tr>
> </table>
> 
> The same pattern applies for the other API endpoints for region cf-eu10 and for the other regions with multiple API endpoints.

**Related Information**  


[Regions and API Endpoints Available for the Cloud Foundry Environment](../10-concepts/regions-and-api-endpoints-available-for-the-cloud-foundry-environment-f344a57.md "")

