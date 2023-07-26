<!-- loioed08c7dcb35d4082936c045e7d7b3ecd -->

# Using SAP SaaS Provisioning Service APIs to Manage Multitenant Applications

Use the SaaS Provisioning Service \(technical name: `saas-registry`\) APIs to work with multitenant applications.



<a name="loioed08c7dcb35d4082936c045e7d7b3ecd__section_zns_szy_5vb"/>

## Background

Most of the SaaS Provisioning Service APIs are concentrated into two main groups:

1.  APIs for Application Providers
2.  APIs for Application Consumers

Application providers can use both groups to either manage their application subscriptions from the global account in which they deployed their multitenant application when using the first group, or mimic their consumers in working with the application from a different global account than the one in which their application is deployed, when using the second group.

Consumers can use the second group to work with the multitenant applications.



<a name="loioed08c7dcb35d4082936c045e7d7b3ecd__section_c12_z5j_5vb"/>

## APIs for Application Providers

> ### Tip:  
> Instead of APIs, can use a dedicated user interface with the same capabilities to manage your multitenant application's subscriptions.
> 
> For more information, see [Using the Subscription Management Dashboard](using-the-subscription-management-dashboard-434be69.md).



### Prerequisites

-   You have a global account and have deployed a multitenant application in it.

-   You've registered your multitenant application to the SaaS Provisioning Service. For more information, see [Register the Multitenant Application to the SAP SaaS Provisioning Service](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/3971151ba22e4faa9b245943feecea54.html?version=Cloud).




### Preparation

1.  For an existing instance of `saas-registry` service with the `application` plan, create a service key or service binding if you don't already have one. For more information, see [Service Bindings](https://help.sap.com/docs/SERVICEMANAGEMENT/09cc82baadc542a688176dce601398de/bb8009dbb7814a2a94e42983fbaa9bae.html?version=Cloud).
2.  From the created key or service binding, extract the values of the following fields:

    -   `url`
    -   `clientid`
    -   `clientsecret`
    -   `saas_registry_url`


You need the first three values to authenticate your SaaS Provisioning Service API requests and the last one as base URL in each API call.



### Authentication

To authenticate, obtain an OAuth token by calling a POST API with the acquired parameters in any REST API tool or directly in your code. For example:

```
curl -XPOST '<url>/oauth/token?grant_type=client_credentials&client_id=<clientid>' -H 'Content-Type: application/x-www-form-urlencoded' -H 'Authorization: Basic <encodedString>'
```

where:

*<encodedString\>* is the result of base64 encoding <code><i class="varname">&lt;clientid&gt;</i>:<i class="varname">&lt;clientsecret&gt;</i>.</code>



### Available APIs

Go to [SAP Business Accelerator Hub](https://api.sap.com/api/APISaasManagerService/resource) and select the **Application Operations for App Providers** section to get information about all the available APIs and their details.

You can also try out the APIs in theSAP Business Accelerator Hub.

For more information, see [Trying Out APIs](https://help.sap.com/viewer/e56a6c50d31541ea826021dc8e721a53/Cloud/en-US/de255b9e0c374ce68151f6b9ad517aba.html).

> ### Note:  
> To authenticate to try out the APIs in SAP Business Accelerator Hub, configure an environment.
> 
> During the environment configuration, select the *OAuth 2.0 Application Flow* option from the dropdown menu. You must do so for the Application Provider API group because these specific APIs only support the Client Credentials authentication type.
> 
> For more information about configuring an environment in general, see [Trying Out APIs in a Configured Environment](https://help.sap.com/viewer/e56a6c50d31541ea826021dc8e721a53/Cloud/en-US/f7796baaef6a48e9867298827f5028ff.html).



<a name="loioed08c7dcb35d4082936c045e7d7b3ecd__section_dqy_mfk_lqb"/>

## APIs for Application Consumers



### Prerequisites

-   You've created an instance of Cloud Management \(technical name: `cis`\) service with `local` plan.




### Authentication

To learn how to authenticate, see [Getting an Access Token for SAP Cloud Management Service APIs](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/3670474a58c24ac2b082e76cbbd9dc19.html).



### Available APIs

Go to [SAP Business Accelerator Hub](https://api.sap.com/api/APISaasManagerService/resource) and select the **Subscription Operations for App Consumers** section to get information about all the available APIs and their details.

You can also try out the APIs in the SAP Business Accelerator Hub. For more information, see [Trying Out APIs](https://help.sap.com/viewer/e56a6c50d31541ea826021dc8e721a53/Cloud/en-US/de255b9e0c374ce68151f6b9ad517aba.html).

To authenticate to try out the APIs inSAP Business Accelerator Hub, configure an environment.

For more information about configuring an environment in general, see [Trying Out APIs in a Configured Environment](https://help.sap.com/viewer/e56a6c50d31541ea826021dc8e721a53/Cloud/en-US/f7796baaef6a48e9867298827f5028ff.html).

