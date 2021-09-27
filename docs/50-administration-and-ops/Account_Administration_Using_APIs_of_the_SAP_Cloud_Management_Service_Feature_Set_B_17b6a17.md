<!-- loio17b6a171552544a6804f12ea83112a3f -->

# Account Administration Using APIs of the SAP Cloud Management Service \[Feature Set B\]

> ### Note:  
> The content in this section is only relevant for cloud management tools feature set B. For more information, see [Cloud Management Tools - Feature Set Overview](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/caf4e4e23aef4666ad8f125af393dfb2.html).

Provides information about using the APIs of the SAP Cloud Management service for SAP BTP to manage some of the administrative operations in your accounts.

The APIs of the core services for SAP BTP allow you to manage, build, and extend the core capabilities of SAP BTP. Each core service focuses on a different aspect of the platform, such as the management of accounts and product entitlements, and the registration and provisioning of subscriptions for multitenant applications and services.

The APIs of the SAP Cloud Management service are included in the core services for SAP BTP.

The following table provides an overview of the SAP Cloud Management service APIs:


<table>
<tr>
<th>

API / Microservice



</th>
<th>

Description



</th>
<th>

Region Availability<sup>\(1\)</sup>



</th>
</tr>
<tr>
<td>

`Accounts`



</td>
<td>

Provides functions to manage the directories and subaccounts in your global accounts' structure in SAP BTP.



</td>
<td>

Central region<sup>\(2\)</sup>



</td>
</tr>
<tr>
<td>

`Entitlements`



</td>
<td>

Provides functions to manage product entitlements and assignments across your global account, directories, and subaccounts.



</td>
<td>

Central region<sup>\(2\)</sup>



</td>
</tr>
<tr>
<td>

`Provisioning`



</td>
<td>

Provides functions to manage the provisioning of your environment instances, multitenant application subscriptions, and services for subaccounts in their corresponding region.



</td>
<td>

All regions



</td>
</tr>
<tr>
<td>

`Events`



</td>
<td>

Provides functions to get information about events relating to administrative operations in your accounts.



</td>
<td>

All regions



</td>
</tr>
</table>

<sup>\(1\)</sup> For more information about available regions, see [Regions](../10-concepts/Regions_350356d.md#loio350356d1dc314d3199dca15bd2ab9b0e).

<sup>\(2\)</sup> Refers to the eu10 Europe \(Frankfurt\) region, unless your global account is located in the China \(Shanghai\) and Government Cloud \(US\) regions then use the landscape domain of your central region.

For detailed information about the APIs, including their specifications and endpoints, go to [SAP Core Services for SAP BTP](https://api.sap.com/package/SAPCloudPlatformCoreServices) on SAP API Business Hub.

Alternatively, go to `https://events-service.*<app domain\>*.*<landscape domain\>*/swagger-index.html` where you can try out the APIs.

> ### Example:  
> If your global account is running on the US East \(VA\) region, use this URL:
> 
> `https://events-service.cfapps.us10.hana.ondemand.com/swagger-index.html`

> ### Remember:  
> -   When using the `Accounts` and `Entitlements` APIs, make sure the endpoint you are using points to the landscape domain of the central region.
> 
> -   To call the core platform API methods, you must obtain an access token. See [Getting an Access Token for SAP Cloud Management Service APIs](Getting_an_Access_Token_for_SAP_Cloud_Management_Service_APIs_3670474.md).

For information about the APIs of the SAP Service Manager service, see [Working with Service Management APIs](https://help.sap.com/viewer/DRAFT/09cc82baadc542a688176dce601398de/Cloud/en-US/4e19b11211fe4ca2a266d3fdd4a72188.html).

For additional information about using the SAP Cloud Management service APIs with subaccounts in the Neo environment, see [Working with Cloud Management Tools Feature Set B in the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/8c963e83a42545e29d1b4277a287a01b.html "Enterprise accounts in SAP BTP that have access to cloud management tools feature set B, can also use the enhanced capabilities offered by feature set B with their subaccounts in the Neo environment.") :arrow_upper_right:.

-   **[Getting an Access Token for SAP Cloud Management Service APIs](Getting_an_Access_Token_for_SAP_Cloud_Management_Service_APIs_3670474.md "The APIs of the SAP Cloud Management service
                                    for SAP BTP are protected with the OAuth 2.0
    Password grant and, in some cases, also the Client
    Credentials grant type. This procedure guides you through the steps to create an OAuth client and obtain an access token from SAP Authorization and Trust
                                    Management service (xsuaa) to call the APIs of
    the SAP Cloud Management
                                    service.")**  
The APIs of the SAP Cloud Management service for SAP BTP are protected with the OAuth 2.0 Password grant and, in some cases, also the Client Credentials grant type. This procedure guides you through the steps to create an OAuth client and obtain an access token from SAP Authorization and Trust Management service \(`xsuaa`\) to call the APIs of the SAP Cloud Management service.
-   **[Using the Events Service APIs](Using_the_Events_Service_APIs_94e1895.md "The Events service provides REST APIs that collect information about events relating to account administrative operations in the
		microservices of the SAP Cloud Management service
                                    for SAP BTP, such as Accounts, Entitlements,
		Provisioning, and the SAP SaaS Provisioning
                                    service, within central and local
		regions.")**  
The Events service provides REST APIs that collect information about events relating to account administrative operations in the microservices of the SAP Cloud Management service for SAP BTP, such as Accounts, Entitlements, Provisioning, and the SAP SaaS Provisioning service, within central and local regions.
-   **[Error Response Format](Error_Response_Format_77fef2f.md "Describes the response format for the errors from the SAP Cloud Management service
                                    for SAP BTP.")**  
Describes the response format for the errors from the SAP Cloud Management service for SAP BTP.
-   **[Asynchronous Jobs](Asynchronous_Jobs_0a0a6ab.md "Describes the asynchronous calls that are supported by some functionality from the SAP Cloud Management service
                                    for SAP BTP.")**  
Describes the asynchronous calls that are supported by some functionality from the SAP Cloud Management service for SAP BTP.
-   **[Rate Limiting](Rate_Limiting_77b217b.md " Describes how all API requests to the SAP Cloud Management service
                                    for SAP BTP adhere to rate
		limiting rules.")**  
 Describes how all API requests to the SAP Cloud Management service for SAP BTP adhere to rate limiting rules.

**Related Information**  


[Error Response Format](Error_Response_Format_77fef2f.md "Describes the response format for the errors from the SAP Cloud Management service for SAP BTP.")

[Asynchronous Jobs](Asynchronous_Jobs_0a0a6ab.md "Describes the asynchronous calls that are supported by some functionality from the SAP Cloud Management service for SAP BTP.")

[Using the Events Service APIs](Using_the_Events_Service_APIs_94e1895.md "The Events service provides REST APIs that collect information about events relating to account administrative operations in the microservices of the SAP Cloud Management service for SAP BTP, such as Accounts, Entitlements, Provisioning, and the SAP SaaS Provisioning service, within central and local regions.")

[Rate Limiting](Rate_Limiting_77b217b.md "Describes how all API requests to the SAP Cloud Management service for SAP BTP adhere to rate limiting rules.")

[Monitoring Usage Information Using APIs of the SAP Usage Data Management Service \[Feature Set B\]](Monitoring_Usage_Information_Using_APIs_of_the_SAP_Usage_Data_Management_Service_Feature_Set_B_bf2b304.md "Provides information about using the Resource Consumption APIs of the SAP Usage Data Management service for SAP BTP for gathering, storing, and making usage information available for all services and applications in all regions in a cloud deployment. This information is for the purpose of central analysis, reporting, and license auditing.")

[Using SAP SaaS Provisioning Service APIs to Manage Multitenant Applications](../30-development/Using_SAP_SaaS_Provisioning_Service_APIs_to_Manage_Multitenant_Applications_ed08c7d.md "You can use the SAP Software-as-a-Service Provisioning service (technical name: saas-registry) APIs to manage your multitenant application.")

[Using Platform APIs](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/392af9d162694d6595499f1549978aa6.html "Platform APIs are protected with OAuth 2.0 client credentials. Create an OAuth client and obtain an access token to call the platform API methods.") :arrow_upper_right:

[Account Model](../10-concepts/Account_Model_8ed4a70.md#loio8ed4a705efa0431b910056c0acdbf377 "Learn more about the different types of accounts on SAP BTP and how they relate to each other.")

[Environments](../10-concepts/Environments_15547f7.md "Environments constitute the actual platform-as-a-service offering of SAP BTP that allows for the development and administration of business applications. Environments are anchored in SAP BTP on subaccount level.")

[Entitlements and Quotas](../10-concepts/Entitlements_and_Quotas_00aa2c2.md "When you purchase an enterprise account, you’re entitled to use a specific set of resources, such as the amount of memory that can be allocated to your applications.")

[Cloud Management Tools — Feature Set Overview](../10-concepts/Cloud_Management_Tools_—_Feature_Set_Overview_caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

[Data Protection and Privacy](../60-security/Data_Protection_and_Privacy_7e513d3.md "Data protection is associated with numerous legal requirements and privacy concerns. In addition to compliance with general data protection and privacy acts, it is necessary to consider compliance with industry-specific legislation in different countries.")

