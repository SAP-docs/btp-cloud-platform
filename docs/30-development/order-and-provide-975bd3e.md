<!-- loio975bd3e54cbe4e52af346740658d1a4a -->

# Order and Provide

After the initial add-on version has been built, you have to deploy and provide it as a SaaS solution so that the add-on can be consumed by customers via a subscription in the SAP BTP cockpit.

 <a name="loio4e35eb027f284b7fa6219bc70561fb4e"/>

<!-- loio4e35eb027f284b7fa6219bc70561fb4e -->

## Deploy



For multitenant applications based on the ABAP environment, the ABAP Solution service is used to provision ABAP systems, tenants, and users on demand. Once you’ve configured this implementation, you can deploy it to the *Provide* space of your *05 Provide* subaccount in the global account for development. After testing the subscription process in this provider subaccount during the development phase, the multitenant application can be deployed to the *Provide* space in the *Provide* subaccount in the global account for production. See [System Landscape/Account Model](concepts-9482e7e.md#loio4ca756395fc24e56a42b77632a6bd862).

After the multitenant application has been deployed for production purposes, the SaaS solution is ready for commercialization.



<a name="loio4e35eb027f284b7fa6219bc70561fb4e__section_wrn_2x4_drb"/>

## Prerequisites

-   To configure the sizing of a SaaS solution, you have to determine the expected load per region by using the Technical Monitoring Cockpit. See [Technical Monitoring Cockpit \(Cloud Version\)](https://help.sap.com/viewer/tmc_cloud/eb867c69739a4cf3be6361d3990d26a2.html).
-   To implement and deploy a multitenant application for a SaaS solution, you have to assign the necessary entitlements in the provider subaccount, for example for the ABAP Solution service. See [Developing Multitenant Applications in the ABAP Environment](developing-multitenant-applications-in-the-abap-environment-195031f.md) and [Entitlements and Quotas](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/00aa2c23479d42568b18882b1ca90d79.html).
-   To subscribe to the Landscape Portal application, you need the corresponding entitlement. See [Using Landscape Portal to Perform Lifecycle Management Operations](using-landscape-portal-to-perform-lifecycle-management-operations-5eb70fb.md).

 <a name="loio1782f253e102484dac378887b3d6d769"/>

<!-- loio1782f253e102484dac378887b3d6d769 -->

### Sizing

The sizing of the SaaS application determines the scope and metric of your offering.

For multitenancy offerings, there’s no sizing/quota per customer. You must decide on an overall sizing depending on the expected load in a region. Sizing can be configured via parameters in the ABAP Solution service, that is managing systems and tenants for systems used to provide the SaaS application.

 <a name="loio6cb128101a6f40f3a8f234a1d9bb8b01"/>

<!-- loio6cb128101a6f40f3a8f234a1d9bb8b01 -->

#### Multitenancy

As a DevOps engineer using parameter `tenant_mode` in the ABAP Solution service, you can define whether a customer gets a tenant in a dedicated system \(single\) or a shared system \(multi\). See [Define Your ABAP Solution](define-your-abap-solution-1697387.md).

> ### Tip:  
> For in-depth information about multitenancy, check out [Multitenancy](concepts-9482e7e.md#loioc8730736a52645b49ca76c08214bf181).

 <a name="loiobb8bc1e3c99145c79106ecafc73f5a4f"/>

<!-- loiobb8bc1e3c99145c79106ecafc73f5a4f -->

#### Runtime and Persistence

Parameters `size_of_runtime` and `size_of_persistence` are used to determine the number of ABAP compute units and HANA compute units for the creation of an ABAP system.

For systems and tenants created automatically by the ABAP Solution service, the following parameters can be used to determine the sizing of runtime and persistence:


<table>
<tr>
<td valign="top">

`size_of_runtime`



</td>
<td valign="top">

Default sizing for solution



</td>
<td valign="top">

Parameter `size_of_runtime` is part of the quota plan `abap/abap_compute_unit`. See [Creating an ABAP System](../20-getting-started/creating-an-abap-system-50b32f1.md).



</td>
</tr>
<tr>
<td valign="top">

`size_of_persistence`



</td>
<td valign="top">

Default sizing for solution



</td>
<td valign="top">

Parameter `size_of_persistence` is part of the quota plan `abap/hana_compute_unit`. See [Creating an ABAP System](../20-getting-started/creating-an-abap-system-50b32f1.md).



</td>
</tr>
</table>

See [Define Your ABAP Solution](define-your-abap-solution-1697387.md).

> ### Note:  
> If the quota for a system is exceeded, you can request a resizing of the ABAP runtime or persistency depending on the needs of the SaaS application.

 <a name="loiof3305f65648248318028e02c84375323"/>

<!-- loiof3305f65648248318028e02c84375323 -->

### Multitenant Application

**Implement the Multitenant Application**

As a DevOps engineer, you can implement the multitenancy functionality using SAP Business Application Studio in the development subaccount.

For more information on how to create multitenant-enabled applications in the ABAP environment, see [Developing Multitenant Applications in the ABAP Environment](developing-multitenant-applications-in-the-abap-environment-195031f.md).

> ### Recommendation:  
> We recommend following the MTA-based implementation approach. See [MTA-Based Approach \(Recommended\)](mta-based-approach-recommended-ca0cc10.md).

1.  You start off by defining your ABAP solution, for example, the parameters explained in the previous chapter need to be configured. See [Define Your ABAP Solution](define-your-abap-solution-1697387.md).

    > ### gCTS Delivery:  
    > When defining your ABAP solution, you can ignore the add-on product name in the service configuration. The value for `addon_product_name` has to be empty so that ABAP systems without an add-on \(abap/standard\) are provisioned for the solution.
    > 
    > See [Delivery via Add-On or gCTS](delivery-via-add-on-or-gcts-438d7eb.md#loio438d7ebfdc4a41de82dcdb156f01857e).

2.  In the configuration for the XSUAA instance, you specify the functional authorization scopes for the application. See [Create an XSUAA Instance](create-an-xsuaa-instance-2ce1a96.md).

3.  A tenant-aware approuter application is developed that is used to authenticate business users of the application at runtime. See [Develop the Approuter Application](develop-the-approuter-application-44dbd0a.md).

    Depending on the purpose of the approuter application, whether used for development or production, it needs to be configured differently. See [Configure the Approuter Application](configure-the-approuter-application-3725815.md)

4.  To make a multitenant application available for subscription to SaaS consumer tenants, you have to register the application in the Cloud Foundry environment via the SaaS Provisioning service \(saas-registry\). See [Register the Multitenant Application to the SaaS Provisioning Service](register-the-multitenant-application-to-the-saas-provisioning-service-2cd8913.md).

5.  Bind your approuter application to the xsuaa service instance, which acts as an OAuth 2.0 client to your application, and to the ABAP Solution service instance, which represents your ABAP solution. See [Bind the approuter Application to the xsuaa and the ABAP Solution Service Instance](bind-the-approuter-application-to-the-xsuaa-and-the-abap-solution-service-instance-04b9258.md).


> ### Note:  
> If you need support or experience issues during implementation of the multitenant application, see [Troubleshoot and Debug](maintain-monitor-support-5d25603.md#loio3687b52c5d3349f7956e93bf2f807e6c).

**Deploy Multitenant Application**

After completing development, you, as a DevOps engineer, must build and deploy the resulting multitenant application for testing purposes to the *Provide* space in the *05 Provide* subaccount in your global account for development.

By using MTA extension descriptors, you can configure the required values for deployment in the development phase. See [Development Descriptor](development-descriptor-767fb00.md) and [Using MTA Extension Descriptors](using-mta-extension-descriptors-383f3a3.md).

> ### gCTS Delivery:  
> If you use gCTS instead of add-ons for delivering software components to production systems, the value for the add-on product name inside the MTA extension descriptor file has to be empty.
> 
> See [Delivery via Add-On or gCTS](delivery-via-add-on-or-gcts-438d7eb.md#loio438d7ebfdc4a41de82dcdb156f01857e).

**Create Cloud Controller Destination**

As an operator, you need to create a destination for the Cloud Foundry Cloud Controller access in the *05 Provide* subaccount in the global accounts for development and production. See [Create a Destination for the Cloud Foundry Cloud Controller Access](create-a-destination-for-the-cloud-foundry-cloud-controller-access-35b5acb.md). The Cloud Foundry Cloud Controller API maintains records of orgs, spaces, services, service instances, user roles, and more and is used to create new ABAP instances in the *Provide* space when necessary.

> ### Recommendation:  
> We recommend using a dedicated technical Cloud Foundry platform user registered in SAP ID Service for Cloud Controller access. This can either be a non-personalized S-user created via SAP One Support Launchpad or a P-user registered directly for an SAP ID service account. See [Create SAP User Accounts](../50-administration-and-ops/create-sap-user-accounts-ebe42f6.md).

**Test Multitenant Application Deployed for Development Purposes**

> ### Note:  
> Using a multitenant application deployed during the development phase, you need to add a new tenant-specific route pointing to the approuter application.
> 
> You have to create a route for the consumer subaccount that maps to the approuter in the multitenant application. New routes are created inside the space where the multitenant application is deployed. For the creation of a new route, you have to specify the domain and hostname. In the development phase, the hostname combines the subdomain of the consumer \(sub-\)account, using a "***-***" separator, and the app name of the SaaS solution. Once the route is created, you have to map it to the approuter application.
> 
> Since "***-***" is used as separator, only 63 characters minus the number of characters used for the app name of the solution can be used for subdomains.

As a DevOps engineer test the multitenant application deployed to the *05 Provide* subaccount in the global account for development by subscribing from a consumer subaccount created in the global account for development. See [Subscribe New Consumers](subscribe-new-consumers-b90cde1.md).

Finally, test the access from the consumer subaccount. See [Consumer Access](consumer-access-a197d6f.md).

**Deploy Multitenant Application for Production Purposes**

> ### Note:  
> During the production phase, you should use a route with wildcard hostname combined with a custom domain so that you don't have to create them manually in the space where the multitenant application is deployed. See [Configure the Approuter Application](configure-the-approuter-application-3725815.md) and [Create Routes](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/9fddeea396b34b528bc8d286f3d5d9cf.html?version=Cloud). This guarantess the following:
> 
> -   All possible subdomains can be replaced in tenant host pattern while resulting in a valid hostname/route since separator "***.***" is used instead of "***-***".
> 
> -   The desired route is not reserved. That means, in case of a shared domain, such as cfapps.eu10.hana.ondemand.com, the subdomains are not reserved and could be used by other SAP BTP platform customers.

After completing development, as a DevOps engineer you must build and deploy the multitenant application for production purposes to the *Provide* space in the *05 Provide* subaccount in the global account for production. See [Configure the Approuter Application](configure-the-approuter-application-3725815.md).

By using MTA extension descriptors, you can configure the required values for deployment in the production phase. See [Development Descriptor](development-descriptor-767fb00.md) and [Using MTA Extension Descriptors](using-mta-extension-descriptors-383f3a3.md).

 <a name="loio195a685a71f84953813e7b3bd255e849"/>

<!-- loio195a685a71f84953813e7b3bd255e849 -->

### Access to Landscape Portal

The *Landscape Portal* acts as a central tool that allows you to perform lifecycle management operations, such as provisioning new consumers tenants, users, and more. See [Using Landscape Portal to Perform Lifecycle Management Operations](using-landscape-portal-to-perform-lifecycle-management-operations-5eb70fb.md).

As an operator, subscribe to the *Landscape Portal* application in the *05 Provide* subaccount in both the global account for development and global account for production. The `LandscapePortalAdminRoleCollection` needs to be assigned to the users in the configured default identity provider of the subaccount that you want to provide access to the *Landscape Portal* app. See [Accessing the Landscape Portal](accessing-the-landscape-portal-2e1e393.md).

> ### gCTS Delivery:  
> In the Landscape Portal, you can access the provider system and choose the provider tenant \(client 100\). Via the provider tenant, you get access to Fiori Apps, for example the *Manage Software Components* app, which is used for importing software components via gCTS.
> 
> See [Delivery via Add-On or gCTS](delivery-via-add-on-or-gcts-438d7eb.md#loio438d7ebfdc4a41de82dcdb156f01857e).

 <a name="loio57c19c7c4dfa4c3cbb846c1ac57e2095"/>

<!-- loio57c19c7c4dfa4c3cbb846c1ac57e2095 -->

## Commercialize



To offer your SaaS solution to customers, register the SaaS solution in the SAP Store. See [SAP Store](https://store.sap.com/dcp/en/).

Additionally, you can request an SAP Extension Suite certification for your product so that it gets listed in the SAP Certified Solutions Directory. See [SAP Extension Suite Certification](https://www.sap.com/documents/2016/10/7cf3eaec-907c-0010-82c7-eda71af511fa.html) and [SAP Certified Solutions Directory](https://www.sap.com/dmc/exp/2013_09_adpd/enEN/#/solutions).

After finishing this process, your customers can order the SaaS solution, which is the preliminary step to actual subscription.



<a name="loio57c19c7c4dfa4c3cbb846c1ac57e2095__section_p4d_j1p_drb"/>

## Prerequisites

Before registering a SaaS solution in SAP Store or certifying the solution, you have to deploy the first add-on version and multitenant application. See [Developing Multitenant Applications in the ABAP Environment](developing-multitenant-applications-in-the-abap-environment-195031f.md).

 <a name="loio607aa8614ea34ee7b366b01ad03bfc4c"/>

<!-- loio607aa8614ea34ee7b366b01ad03bfc4c -->

### \(Optional\) Register SaaS Solution in SAP Store

SAP Store is the enterprise marketplace where we bring together customers and partners on a single, easy-to-use, global online platform. See [SAP Store](https://store.sap.com/dcp/en/).

To learn more about how you can offer your SaaS solution to SAP customers via SAP Store, see [Getting Started with SAP Store](https://store.sap.com/dcp/en/partner-with-us/documentation).

 <a name="loioace3b22147eb40d3989c5525491eb729"/>

<!-- loioace3b22147eb40d3989c5525491eb729 -->

### \(Optional\) Certification

With an SAP Extension Suite certification, your SaaS solution is featured in the SAP Certified Solution Directory, which allows for more growth and customer participation. See [SAP ICC Integration Scenario - SAP Extension Suite Certification](https://www.sap.com/documents/2016/10/7cf3eaec-907c-0010-82c7-eda71af511fa.html) and [SAP Certified Solution Directory](https://www.sap.com/dmc/exp/2013_09_adpd/enEN/#/solutions).

 <a name="loioa24217a0d6fa434bbce97869dfb70dda"/>

<!-- loioa24217a0d6fa434bbce97869dfb70dda -->

## Order and Provide



Once the SaaS solution has been fully deployed and commercialized, customers can order the offered product. After the buying process has been completed, you, as a SaaS solution operator, have to create a consumer subaccount in the global account for production and subscribe to the SaaS solution. This in turn triggers the provisioning of the required ABAP systems and tenants for the customer. You can follow this process using the *Landscape Portal* service, which gives you an overview of the available ABAP systems and tenants belonging to a SaaS solution.

When tenant or system provisioning has been completed, you receive a confirmation mail as a SaaS solution operator.



<a name="loioa24217a0d6fa434bbce97869dfb70dda__section_sxb_gms_vnb"/>

## Prerequisites

-   To create a consumer subaccount, all the details, such as the account name, provider, region and subdomain should be known. See [Account Model](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/8ed4a705efa0431b910056c0acdbf377.html#loio8d6e3a0fa4ab43e4a421d3ed08128afa) and [Regions and API Endpoints for the ABAP Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/350356d1dc314d3199dca15bd2ab9b0e.html#loio879f37370d9b45e99a16538e0f37ff2c).
-   To subscribe to the SaaS solution, you need a consumer subaccount. To monitor system and tenant provisioning, you have to subscribe to the Landscape Portal app and configure user access using the `LandscapePortalAdminRoleCollection`. See [Accessing the Landscape Portal](accessing-the-landscape-portal-2e1e393.md).
-   To configure the consumer subaccount, the details for destinations, cloud connectors and trust configuration need to be available to you. To delegate access to the consumer subaccount, a consumer subaccount admin user of the customer is required. See [Using the Destinations Editor in the Cockpit](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/565fdb3dd19d4cda80864341dc5a0451.html), [Cloud Connector](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e6c7616abb5710148cfcf3e75d96d596.html), [Trust and Federation with Identity Providers](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/cb1bc8f1bd5c482e891063960d7acd78.html), and [Add Members to Your Subaccount \[Feature Set B\]](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/1e1b7b60bb1b4764a2d4bb96bd73182d.html).
-   For the initial user onboarding, you need a consumer subaccount administrator in the consumer subaccount. See [Consumer Access](consumer-access-a197d6f.md).



### Customer Buys SaaS Solution

Depending on the marketplace platform, for example SAP Store, or other distribution channels, customers can buy the SaaS solution.

For the following process of creating a consumer subaccount for your customer, you should have the following information readily available:

-   Customer name and email address for the creation of a consumer subaccount admin user
-   Name and scope of the SaaS solution for the subscription to the SaaS solution
-   Quantity of users, t-shirt size of solution etc. to determine necessary configuration steps

 <a name="loio8b92024cc5d44268bf4737551e4fa981"/>

<!-- loio8b92024cc5d44268bf4737551e4fa981 -->

### Create Consumer Subaccount

For the following process of creating a consumer subaccount for your customer, you have to create consumer subaccounts in the global account for production so that customers can subscribe to the provided SaaS solution.

This means, on top of subaccount *05 Provide*, you have to create a subaccount in the global account for production for each consumer. See [Set Up a Global Account for Production](develop-test-build-3bf575a.md#loio2e7b4b631e814de1b8fe3959af4105bc).

After a customer has ordered the SaaS solution, you, as an operator of the global account for production, need to create a *06 Consume* subaccount. See [Subscribe New Consumers](subscribe-new-consumers-b90cde1.md).

While creating the subaccount, you must provide the following details:

-   **Name**: Give the subaccount a unique display name. This can be the name of the customer, a customer number or a specific naming pattern
-   **Provider**: Choose the IaaS provider according to the IaaS provider selected for the provider subaccount
-   **Region**: Choose the subaccount region according to the region where the provider subaccount was created. See [Regions and API Endpoints for the ABAP Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/350356d1dc314d3199dca15bd2ab9b0e.html#loio879f37370d9b45e99a16538e0f37ff2c).
-   **Subdomain**: The subdomain of the subaccount becomes part of the application URL, according to the `TENANT_HOST_PATTERN` that you defined in the approuter configuration for the multitenant application. See [Configure the Approuter Application](configure-the-approuter-application-3725815.md).

 <a name="loio477ea31394504182b2ea5ef9ce26802d"/>

<!-- loio477ea31394504182b2ea5ef9ce26802d -->

### Subscribe to SaaS Solution

After you have finalized the consumer subaccount configuration as an operator user on the provider side, the subscription to the SaaS solution is enabled for the consumer.

**Subscribe to SaaS solution in consumer subaccount**

> ### gCTS Delivery:  
> In case of delivery via gCTS, you, as a SaaS solution operator, can use a separate test subscription that is not related to a customer to trigger the creation of the system before the actual customer subscription. This initial system creation and import of the software components needs to be performed for each customer production system.

In the consumer subaccount, navigate to the *Service Marketplace*. To subscribe to the SaaS solution, choose *Create*. The subscribed application is now displayed in *Services* \> *Instances and Subscriptions*. Once the subscription to the SaaS Solution is complete, you receive a notification via email. The email address is defined in the service configuration of your ABAP solution by setting parameter `provider_admin_email`. See [Define Your ABAP Solution](define-your-abap-solution-1697387.md).

**Check tenant provisioning in Landscape Portal**

The subscription process triggers provisioning of

-   A new ABAP system, if necessary according to ABAP solution configuration \(parameter`tenant_mode`\)

-   A new consumer tenant that is represented by an additional client in the ABAP system


In both cases, you, as a SaaS solution operator, receive a confirmation mail.

As an operator user assigned to the role collection `LandscapePortalAdminRoleCollection`, you can access the systems overview of the *Landscape Portal* and check both provisioned systems and new tenants.

See [Using Landscape Portal to Perform Lifecycle Management Operations](using-landscape-portal-to-perform-lifecycle-management-operations-5eb70fb.md).

**Assign `SolutionAdmin` role**

Once the SaaS subscription process is completed, as an operator user in the trust settings of the *06 Consume* subaccount, assign the user onboarding role `SolutionAdmin` provided by the multitenant application to a customer user.

 <a name="loio6301a275af664613a51147e3451386e6"/>

<!-- loio6301a275af664613a51147e3451386e6 -->

### Configure Consumer Subaccount \(Feature Set B\)

Depending on the scope of the SaaS solution and customer requirements, you can make the following configurations in the consumer subaccount:

-   **Trust Configuration**

    You can configure a custom identity provider for the authentication of subscribed applications in the consumer subaccount. See [Trust and Federation with Identity Providers](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/cb1bc8f1bd5c482e891063960d7acd78.html).

    To restrict access based on certain criteria, such as the IP address, use the SAP Cloud Identity Services - Identity Authentication.

-   **Cloud Connector**

    Using Cloud Connector, you can create a link between SAP BTP applications and on-premise systems. See [Managing Subaccounts](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/f16df12fab9f4fe1b8a4122f0fd54b6e.html) on how to add and connect a consumer subaccount to Cloud Connector.

-   **Destination**

    Configure destinations, including technical information about the target resource, to connect your application to a remote service or system. See [Managing Destinations](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/84e45e071c7646c88027fffc6a7bb787.html).


As a SaaS solution operator, you can provide customers access to these configurations by assigning the subaccount administrator role collection to the consumer subaccount administrator.

The consumer subaccount administrator can then access the consumer subaccount in the SAP BTP cockpit including subscriptions, trust configuration, Cloud Connectors and destinations without having access to other consumer subaccounts in the global account for production.

The consumer subaccount administrator can assign the Cloud Connector administrator role collection to a preferred user to operate the data transmission tunnels used by the Cloud Connector. While adding the consumer subaccount in Cloud Connector, the same Cloud Connector administrator user is being configured.

See [Role Collections and Roles in Global Accounts, Directories, and Subaccounts \[Feature Set B\]](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/0039cf082d3d43eba9200fe15647922a.html) for more information on available role collections in the consumer subaccount.

 <a name="loio4a9c5011922847ac91db165c78656149"/>

<!-- loio4a9c5011922847ac91db165c78656149 -->

### Initial User Onboarding

After the configuration in the consumer subaccount, your customer needs an initial administrator user in the consumer tenant that was created for the subscription.

To create such an initial administrator user, as a consumer subaccount administrator, you have to assign the role collection including the `SolutionAdmin` role to your user in the *Role Collections* view in the consumer subaccount.

In a confirmation form, you have to confirm details such as email, subdomain, and subaccount ID. Afterwards, the consumer subaccount administrator can access the SAP Fiori launchpad of the subscribed SaaS solution via *Instances and Subscriptions*.

**Check tenant user provisioning in Landscape Portal**

On the provider side, as an operator user assigned to the `LandscapePortalAdminRoleCollection`, you can check ongoing tenant user provisioning in the *Landscape Portal*. After selecting the target system in the system overview app, ongoing tenant user provisioning is displayed in the *Requests* section. See [View the Request Log](view-the-request-log-0ea69c2.md).

