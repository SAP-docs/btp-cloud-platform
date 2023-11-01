<!-- loio975bd3e54cbe4e52af346740658d1a4a -->

# Order and Provide

After the initial add-on version has been built, you have to deploy and provide it as a SaaS solution so that the add-on can be consumed by customers via a subscription in the SAP BTP cockpit.

<a name="loio4e35eb027f284b7fa6219bc70561fb4e"/>

<!-- loio4e35eb027f284b7fa6219bc70561fb4e -->

## Deploy



To offer a multitenant application based on an ABAP add-on product, a multi-target application \(MTA\) is developed and deployed to the Cloud Foundry environment on SAP BTP. The MTA integrates the different services required for this scenario, such as the ABAP Solution service, responsible for provisioning ABAP systems, tenants, and users on demand. For more in-depth information, see [Multitenant Application](https://help.sap.com/docs/btp/sap-business-technology-platform/multitenant-application?version=Cloud).

Once you’ve configured your multitenant application, you can deploy it once for testing purposes in the global account for development.

After testing the subscription process in this provider subaccount during the development phase, the multitenant application can be deployed to the *Provide* space in the *05 Provide* subaccount in the global account for production. See [System Landscape/Account Model](https://help.sap.com/docs/btp/sap-business-technology-platform/concepts?version=Cloud#system-landscape%2Faccount-model).

After the multitenant application has been deployed for production purposes, the SaaS solution is ready for commercialization.

You have two options for implementing and deploying the application. The recommended approach is to use the Maintain Solution app in the Landscape Portal. See [Maintain Solution](https://help.sap.com/docs/btp/sap-business-technology-platform/maintain-solution?version=Cloud). Alternatively, you can create your own multitenant application. This allows you to modify parameters that are not exposed in the Maintain Solution app. However, the app should cover all common use cases. See [Developing Multitenant Applications in the ABAP Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/developing-multitenant-applications-in-abap-environment?version=Cloud).

> ### gCTS Delivery:  
> If you use gCTS instead of add-ons for delivering software components to production systems, the value for the add-on product name inside the MTA extension descriptor file has to be empty.
> 
> See [Delivery via Add-On or gCTS](delivery-via-add-on-or-gcts-438d7eb.md#loio438d7ebfdc4a41de82dcdb156f01857e).



<a name="loio4e35eb027f284b7fa6219bc70561fb4e__section_wrn_2x4_drb"/>

## Prerequisites

-   To configure the sizing of a SaaS solution, you need to determine the expected load per region by using the Technical Monitoring Cockpit. See [Technical Monitoring Cockpit \(Cloud Version\)](https://help.sap.com/viewer/tmc_cloud/eb867c69739a4cf3be6361d3990d26a2.html).
-   To implement and deploy a multitenant application for a SaaS solution, you need to assign the necessary entitlements in the provider subaccount, for example for the ABAP Solution service. See [Multitenant Application](https://help.sap.com/docs/btp/sap-business-technology-platform/multitenant-application?version=Cloud) and [Entitlements and Quotas](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/00aa2c23479d42568b18882b1ca90d79.html).

<a name="loio1782f253e102484dac378887b3d6d769"/>

<!-- loio1782f253e102484dac378887b3d6d769 -->

### Sizing

The sizing of the SaaS application determines the scope and metric of your offering.

Before deploying your application, you must decide on a tenant limit. Once that number of consumer tenants is reached in a system, a new system will be provisioned for the next consumer. If you choose a limit of 1, you will be defining a single tenant offering, with one consumer per system.

> ### Tip:  
> For in-depth information about multitenancy, check out [this section](https://help.sap.com/docs/btp/sap-business-technology-platform/concepts?version=Cloud#multitenancy).

Additionally, you need to define the sizing of each provisioned ABAP system. The sizing is defined by the number of ABAP compute units \(runtime\) and HANA compute units \(persistence\) each system is assigned.

For multitenancy offerings, there’s no sizing/quota per customer. You must decide on an overall sizing depending on the expected load in a region.

> ### Note:  
> If the quota for a system is exceeded, you can request a resizing of the ABAP runtime or persistency depending on the needs of the SaaS application.

<a name="loio6cb128101a6f40f3a8f234a1d9bb8b01"/>

<!-- loio6cb128101a6f40f3a8f234a1d9bb8b01 -->

#### Multitenancy

As a DevOps engineer using parameter `tenant_mode` in the ABAP Solution service, you can define whether a customer gets a tenant in a dedicated system \(single\) or a shared system \(multi\). See [ABAP Solution Service](abap-solution-service-1697387.md).

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

Parameter `size_of_runtime` is referring to quota plan `abap/abap_compute_unit`. See [Creating an ABAP System](../20-getting-started/creating-an-abap-system-50b32f1.md).

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

Parameter `size_of_persistence` is referring to quota plan `abap/hana_compute_unit`. See [Creating an ABAP System](../20-getting-started/creating-an-abap-system-50b32f1.md).

</td>
</tr>
</table>

See [ABAP Solution Service](abap-solution-service-1697387.md).

> ### Note:  
> If the quota for a system is exceeded, you can request a resizing of the ABAP runtime or persistency depending on the needs of the SaaS application.

<a name="loiof3305f65648248318028e02c84375323"/>

<!-- loiof3305f65648248318028e02c84375323 -->

### Multitenant Application

**Implement the Multitenant Application**

As a DevOps engineer, you can implement the multitenant application using the Maintain Solution app in the Landscape Portal. Create a new solution using your add-on and initial add-on verison. Create two deployment configurations, one pointing to the *05 Provide* subaccount of the global account for *development* and one pointing to the*05 Provide* subaccount of the global account for *production*. See [Create Process](https://help.sap.com/docs/btp/sap-business-technology-platform/solutions?version=Cloud).

You can also configure the multitenant application manually. In this case, you can use MTA extension descriptors to configure the required values for deployment to different targets. See [Multitenant Applications](multitenant-applications-195031f.md).

> ### Note:  
> If you need support or experience issues during implementation of the multitenant application, see [Troubleshooting](troubleshooting-257ba65.md).

**Deploy the Multitenant Application for Test Purposes**

After completing development, you, as a DevOps engineer, must build and deploy the resulting multitenant application for testing purposes to the *Provide* space in the *05 Provide* subaccount in your global account for development.

You can deploy your configuration from the Maintain Solution app using the Deploy action. See [Deployment Process](https://help.sap.com/docs/btp/sap-business-technology-platform/credentials?version=Cloud).

**Test Multitenant Application Deployed for Development Purposes**

If you want to configure your application manually, build and deploy your project using the corresponding command line tools. See [Multitenant Application](https://help.sap.com/docs/btp/sap-business-technology-platform/multitenant-application?version=Cloud).

As a DevOps engineer test the multitenant application deployed to the *05 Provide* subaccount in the global account for development by subscribing from a consumer subaccount created in the global account for development. See [**Subscribe to Multitenant Applications Using the Cockpit**](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/7a3e39622be14413b2a4df7c02ca1170.html).

Once the subscription is successful, you may also want to test the initial user onboarding process that can be accessed via the application URL: first, assign the onboarding role collection, that includes the `SolutionAdmin role`, to your user. Afterwards, trigger the user onboarding.

**Deploy Multitenant Application for Production Purposes**

After completing development, as a DevOps engineer you must build and deploy the multitenant application for production purposes to the *Provide* space in the *05 Provide* subaccount in the global account for production. Once it is successfully deployed, subscription to your solution will be possible.

You can deploy your configuration from the Maintain Solution app using the *Deploy* action. See [Deployment Process](https://help.sap.com/docs/btp/sap-business-technology-platform/credentials?version=Cloud).

If you want to configure your application manually, build and deploy your project using the corresponding command line tools. See [Multitenant Application](https://help.sap.com/docs/btp/sap-business-technology-platform/multitenant-application?version=Cloud).

<a name="loioc52ca397062a4f9e9cff449babe82122"/>

<!-- loioc52ca397062a4f9e9cff449babe82122 -->

#### Using a Custom Domain for the Multitenant Application

The SAP Custom Domain Service \(see [SAP Custom Domain service](https://discovery-center.cloud.sap/serviceCatalog/custom-domain?region=all&service_plan=custom-domain&commercialModel=cpea)\) lets you configure your own custom domain \(see [What Is Custom Domain?](https://help.sap.com/docs/custom-domain/custom-domain-manager/what-is-custom-domain?version=Cloud)\) to publicly expose your application instead of using an SAP-provided default/shared/standard domain like cfapps.eu10.hana.ondemand.com for your application URLs.

By using this service, subaccount owners can make their SAP BTP applications accessible via a custom domain that is different from the default one; for example, myshop.com.

In case of multitenant applications \(see [Multitenant Applications](multitenant-applications-195031f.md)\), using a custom domain comes with another advantage: For each subscription there needs to be a CF route \(see [Routes](https://docs.cloudfoundry.org/devguide/deploy-apps/routes-domains.html#routes)\) that is mapped to the approuter module of the multitenant application, so that the application is accessible via a URL.

While using a default domain, a new route like `<SUBSCRIBER_TENANT_SUBDOMAIN>-<APPROUTER_APPLICATION_HOST>.<SAP-PROVIDED_STANDARD_DOMAIN>` must be created manually for each new tenant.

By configuring the multitenant application with a custom domain, a route with a wildcard hostname like `*.<YOUR_CUSTOM_DOMAIN>` can be mapped, so that there is no need to create a new route for each new tenant manually. For more information, refer to [Approuter Application](approuter-application-44dbd0a.md).

It is recommended to use a custom domain for your multitenant application only during the production phase; during the development phase using a default domain is sufficient.

Please follow the steps outlined in [Configuring Custom Domains](https://help.sap.com/docs/custom-domain/custom-domain-manager/configuring-custom-domains?version=Cloud) or[Get Started with the Custom Domain Manager](https://developers.sap.com/tutorials/btp-custom-domain-manager-getting-started.html) \(refer to PaaS-User\) to register your custom domain in the provider subaccount’s CF org \(see [Multitenancy in the ABAP Environment](multitenancy-in-the-abap-environment-633cc61.md)\). After registering the custom domain successfully, the domain becomes available as private domain \(see [Private domains](https://docs.cloudfoundry.org/devguide/deploy-apps/routes-domains.html#private-domains)\) for route creation in any space of the provider subaccount’s CF org.

To create a multitenant application for use with a custom domain, following configurations are adjusted accordingly:

-   `TENANT_HOST_PATTERN` configuration of the approuter application: String containing a regular expression with a capturing group. The request host is matched against this regular expression. The value of the first capturing group is used as tenant id. Please refer to [TENANT\_HOST\_PATTERN](https://help.sap.com/docs/btp/sap-business-technology-platform/environment-variables?state=DRAFT#loioba527058dc4d423a9e0a69ecc67f4593__section_zhq_xch_wx).

-   SaaS Registry Callback URLs getDependencies and onSubscription. Please refer to [Saas Provisioning Service](saas-provisioning-service-cbc379e.md).

-   XSUAA OAuth 2.0 Client configuration redirect-uris. Please refer to [Listing Allowed Redirect URIs](https://help.sap.com/docs/btp/sap-business-technology-platform/security-considerations-for-sap-authorization-and-trust-management-service?version=Cloud#loio88b7d9d4c6ff4498b48dbc0b7be8a294) 

-   [CF routes](https://docs.cloudfoundry.org/devguide/deploy-apps/routes-domains.html#routes) assigned to approuter application


For the subscriptions to the multitenant application to work correctly, configured SaaS Registry callback URLs need to be reachable \(cis… route\). For Application Routing routing to work, the approuter needs to be able to resolve the application URL based on current `TENANT_HOST_PATTERN` configuration.

You can use the [Maintain Solution](maintain-solution-4985d3c.md) app in the Landscape Portal to easily create such a multitenant application with custom domain, please refer to [Create Deployment Configuration](create-deployment-configuration-58b90ec.md) → **Step 3: Routing Information**.

Or, if you are following the MTA-based approach to create your multitenant application, in the [MTA Extension descriptor for production phase](https://github.com/sap-software/abap-saas-reference-solution/blob/main/extensions/examples/prod.mtaext) these configurations are changed using following MTA parameters:

-   app-domain: the registered custom domain, e.g. mydomain.com

-   route-prefix: needs to be empty because application URLs are mapped using following structure:`*.<YOUR_CUSTOM_DOMAIN>` \(dot separator\) and therefore do not include a route prefix


A route with wildcard hostname for tenant access is added to the approuter module, on top of the route used for SaaS Registry callback URLs:

> ### Sample Code:  
> ```
> 
> modules: 
> 
>   - name: approuter 
>     parameters: 
>       routes: 
>         - route: "cis${route-prefix}.${app-domain}" 
>         - route: "*${route-prefix}.${app-domain}" 
> ```

To reduce risks use[Blue-Green Deployment of Multitarget Applications](https://help.sap.com/docs/btp/sap-business-technology-platform/blue-green-deployment-strategy) while deploying multitenant application MTA during production phase.

After MTA build and deployment, the approuter application is created with a route cis.mydomain.com that is used for the SaaS Registry callback URLs `getDependencies` and `onSubscription`. On top of that a route with wild card hostname `*.mydomain.com` is mapped to the approuter. In this format, since the wildcard is replaced by an actual tenant during runtime, there is no need to create a new route for each new tenant manually.

If you change the domain type of your multitenant application from shared to custom domain, you need to update the application URL of existing subscriptions. Please use the option to update the application URL of an active subscription in the [Subscription Management Dashboard](https://help.sap.com/docs/btp/sap-business-technology-platform/using-subscription-management-dashboard?version=Cloud). In such case, make sure to inform application consumers beforehand about temporary downtimes that might occur during this change.

<a name="loio57c19c7c4dfa4c3cbb846c1ac57e2095"/>

<!-- loio57c19c7c4dfa4c3cbb846c1ac57e2095 -->

## Commercialize



To offer your SaaS solution to customers, register the SaaS solution in the SAP Store. See [SAP Store](https://store.sap.com/dcp/en/).

Additionally, you can request an SAP Extension Suite certification for your product so that it gets listed in the SAP Certified Solutions Directory. See [SAP Extension Suite Certification](https://www.sap.com/documents/2016/10/7cf3eaec-907c-0010-82c7-eda71af511fa.html) and [SAP Certified Solutions Directory](https://www.sap.com/dmc/exp/2013_09_adpd/enEN/#/solutions).

After finishing this process, your customers can order the SaaS solution, which is the preliminary step to actual subscription.



<a name="loio57c19c7c4dfa4c3cbb846c1ac57e2095__section_p4d_j1p_drb"/>

## Prerequisites

Before registering a SaaS solution in SAP Store or certifying the solution, you have to deploy the first add-on version and multitenant application. See [Multitenant Applications](multitenant-applications-195031f.md).

<a name="loio607aa8614ea34ee7b366b01ad03bfc4c"/>

<!-- loio607aa8614ea34ee7b366b01ad03bfc4c -->

### \(Optional\) Register SaaS Solution in SAP Store

SAP Store is the enterprise marketplace where we bring together customers and partners on a single, easy-to-use, global online platform. See [SAP Store](https://store.sap.com/dcp/en/).

To learn more about how you can offer your SaaS solution to SAP customers via SAP Store, see [Getting Started with SAP Store](https://store.sap.com/dcp/en/partner-with-us/documentation/getting-started-with-sap-app-center).

<a name="loioace3b22147eb40d3989c5525491eb729"/>

<!-- loioace3b22147eb40d3989c5525491eb729 -->

### \(Optional\) Certification

With an SAP Extension Suite certification, your SaaS solution is featured in the SAP Certified Solution Directory, which allows for more growth and customer participation. See [SAP ICC Integration Scenario - SAP Extension Suite Certification](https://www.sap.com/documents/2016/10/7cf3eaec-907c-0010-82c7-eda71af511fa.html) and [SAP Certified Solution Directory](https://www.sap.com/dmc/exp/2013_09_adpd/enEN/#/solutions).

> ### Note:  
> Certification of SaaS solutions is only available if you have used add-on build delivery.

<a name="loioa24217a0d6fa434bbce97869dfb70dda"/>

<!-- loioa24217a0d6fa434bbce97869dfb70dda -->

## Order and Provide



Once the SaaS solution has been fully deployed and commercialized, customers can order the offered product. After the buying process has been completed, you, as a SaaS solution operator, have to create a consumer subaccount in the global account for production and subscribe to the SaaS solution. This in turn triggers the provisioning of the required ABAP systems and tenants for the customer. You can follow this process using the *Landscape Portal* service, which gives you an overview of the available ABAP systems and tenants belonging to a SaaS solution.

When tenant or system provisioning has been completed, you receive a confirmation mail as a SaaS solution operator.



<a name="loioa24217a0d6fa434bbce97869dfb70dda__section_sxb_gms_vnb"/>

## Prerequisites

-   To create a consumer subaccount, all the details, such as the account name, provider, region and subdomain should be known. See [Account Model](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/8ed4a705efa0431b910056c0acdbf377.html#loio8d6e3a0fa4ab43e4a421d3ed08128afa) and [Regions and API Endpoints for the ABAP Environment](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/879f37370d9b45e99a16538e0f37ff2c.html).
-   To subscribe to the SaaS solution, you need a consumer subaccount. To monitor system and tenant provisioning, you have to subscribe to the Landscape Portal app and configure user access using the `LandscapePortalAdminRoleCollection`. See [Accessing the Landscape Portal](accessing-the-landscape-portal-2e1e393.md).
-   To configure the consumer subaccount, the details for destinations, cloud connectors and trust configuration need to be available to you. To delegate access to the consumer subaccount, a consumer subaccount admin user of the customer is required. See [Using the Destinations Editor in the Cockpit](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/565fdb3dd19d4cda80864341dc5a0451.html), [Cloud Connector](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e6c7616abb5710148cfcf3e75d96d596.html), [Trust and Federation with Identity Providers](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/cb1bc8f1bd5c482e891063960d7acd78.html), and [Add Members to Your Subaccount \[Feature Set B\]](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/1e1b7b60bb1b4764a2d4bb96bd73182d.html).
-   For the initial user onboarding, you need a consumer subaccount administrator in the consumer subaccount.



### Customer Buys SaaS Solution

Depending on the marketplace platform, for example SAP Store, or other distribution channels, customers can buy the SaaS solution.

For the following process of creating a consumer subaccount for your customer, you should have the following information readily available:

-   Customer name and email address for the creation of a consumer subaccount admin user
-   Name and scope for the subscription to the SaaS solution
-   Quantity of users, t-shirt size of solution etc. to determine necessary configuration steps

<a name="loio8b92024cc5d44268bf4737551e4fa981"/>

<!-- loio8b92024cc5d44268bf4737551e4fa981 -->

### Create Consumer Subaccount

For the following process of creating a consumer subaccount for your customer, you have to create consumer subaccounts in the global account for production so that customers can subscribe to the provided SaaS solution.

This means, on top of subaccount *05 Provide*, you have to create a subaccount in the global account for production for each consumer. See [Set Up a Global Account for Production](prepare-4338854.md#loio2e7b4b631e814de1b8fe3959af4105bc).

After a customer has ordered the SaaS solution, you, as an operator of the global account for production, need to create a *06 Consume* subaccount.

While creating the subaccount, you must provide the following details:

-   **Name**: Give the subaccount a unique display name. This can be the name of the customer, a customer number or a specific naming pattern
-   **Provider**: Choose the IaaS provider according to the IaaS provider selected for the provider subaccount
-   **Region**: Choose the subaccount region according to the region where the provider subaccount was created. See [Regions and API Endpoints for the ABAP Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/350356d1dc314d3199dca15bd2ab9b0e.html#loio879f37370d9b45e99a16538e0f37ff2c).
-   **Subdomain**: The subdomain is important because it becomes the consumer-specific part of the tenant-specific application URL according to the `TENANT_HOST_PATTERN` that you defined in the approuter configuration for the multitenant application. See [Approuter Application](approuter-application-44dbd0a.md).

<a name="loio477ea31394504182b2ea5ef9ce26802d"/>

<!-- loio477ea31394504182b2ea5ef9ce26802d -->

### Subscribe to SaaS Solution

After you have finalized the consumer subaccount configuration as an operator user on the provider side, the subscription to the SaaS solution is enabled for the consumer.

**Subscribe to SaaS solution in consumer subaccount**

> ### gCTS Delivery:  
> In case of delivery via gCTS, you, as a SaaS solution operator, can use a separate test subscription that is not related to a customer to trigger the creation of the system before the actual customer subscription. This initial system creation and import of the software components needs to be performed for each customer production system.

Follow the instructions in [Subscribe to Multitenant Applications Using the Cockpit](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/7a3e39622be14413b2a4df7c02ca1170.html) to subscribe consumers:

In the consumer subaccount, navigate to the *Service Marketplace*. To subscribe to the SaaS solution, choose *Create*. The subscribed application is now displayed in *Services* \> *Instances and Subscriptions*. Once the subscription to the SaaS Solution is complete, an email notification about system/tenant provisioning is sent. The email address is defined in the service configuration of your ABAP solution by setting parameter `provider_admin_email`. See [ABAP Solution Service](abap-solution-service-1697387.md).

> ### Note:  
> In the production phase, the link to the application only works if you have defined a route with wildcard hostname \(and custom domain\) for the approuter application so that routes do not need to be created manually for each new subscription.

**Check tenant provisioning in Landscape Portal**

The subscription process triggers provisioning of

-   A new ABAP system, if necessary according to ABAP solution configuration \(parameter`tenant_mode`\)

-   A new consumer tenant that is represented by an additional client in the ABAP system


In both cases, you, as a SaaS solution operator, receive a confirmation mail.

The business type of the consumer tenant depends on the usage parameter configured for the ABAP Solution service. If you have set `usage = prod`, a tenant of business type `Partner Customer Production Tenant` is created. If you have set `usage = test`, a tenant of business type `Partner Customer Test Tenant` is created. For more information on the solution usage, see [ABAP Solution Service](abap-solution-service-1697387.md).

As an operator user assigned to the role collection `LandscapePortalAdminRoleCollection`, you can access the systems overview of the *Landscape Portal* and check both provisioned systems and new tenants. See [Landscape Portal](landscape-portal-5eb70fb.md).

> ### Tip:  
> For an overview of all processes, such as tenant provisioning across multiple systems, see [Operations Dashboard](operations-dashboard-0a3a735.md).

**Assign `SolutionAdmin` role**

Once the SaaS subscription process is completed, as an operator user in the trust settings of the *06 Consume* subaccount, assign the user onboarding role `SolutionAdmin` provided by the multitenant application to a customer user.

<a name="loio6301a275af664613a51147e3451386e6"/>

<!-- loio6301a275af664613a51147e3451386e6 -->

### Configure Consumer Subaccount \(Feature Set B\)

Depending on the scope of the SaaS solution and customer requirements, you can make the following configurations in the consumer subaccount:

-   **Trust Configuration**

    You can configure a custom identity provider for the authentication of subscribed applications in the consumer subaccount. See [Trust and Federation with Identity Providers](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/cb1bc8f1bd5c482e891063960d7acd78.html).

    To restrict access based on certain criteria, such as the IP address, use the SAP Cloud Identity Services - Identity Authentication.

    > ### Note:  
    > With new subaccounts created after September 24th 2020, [automatic creation of shadow users is switched off](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/d8525671e8b14147b96ef497e1e1af80.html) by default for the default identity provider, SAP ID service. If the creation of shadow users is disabled, any additional business users need to be added manually to the users of the consumer subaccount so that authentication on subaccount level is possible. Business users can only log on to the ABAP tenant if there is an existing employee/business user in the ABAP system.

-   **Cloud Connector**

    Using Cloud Connector, you can create a link between SAP BTP applications and on-premise systems. See [Managing Subaccounts](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/f16df12fab9f4fe1b8a4122f0fd54b6e.html) on how to add and connect a consumer subaccount to Cloud Connector.

-   **Destination**

    Configure destinations, including technical information about the target resource, to connect your application to a remote service or system. See [Managing Destinations](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/84e45e071c7646c88027fffc6a7bb787.html).


As a SaaS solution operator, you can provide customers access to these configurations by assigning role collection `Subaccount Administrator` to the consumer subaccount administrator.

The consumer subaccount administrator can then access the consumer subaccount in the SAP BTP cockpit including subscriptions, trust configuration, Cloud Connectors and destinations without having access to other consumer subaccounts in the global account for production.

The consumer subaccount administrator can assign role collection `Cloud Connector Administrator` to a user to operate the data transmission tunnels used by the Cloud Connector. While adding the consumer subaccount in Cloud Connector, the same Cloud Connector administrator user is being configured.

See [Role Collections and Roles in Global Accounts, Directories, and Subaccounts \[Feature Set B\]](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/0039cf082d3d43eba9200fe15647922a.html) for more information on available role collections in the consumer subaccount.

<a name="loio4a9c5011922847ac91db165c78656149"/>

<!-- loio4a9c5011922847ac91db165c78656149 -->

### Initial User Onboarding

After the configuration in the consumer subaccount, your customer needs an initial administrator user in the consumer tenant that was created for the subscription.

To create such an initial administrator user, as a consumer subaccount administrator, you have to assign the role collection including the `SolutionAdmin` role to your user in the *Role Collections* view in the consumer subaccount.

1.  Log on to the consumer subaccount and navigate to *Security* \> *Role Collections*.
2.  Select the role collection you defined in [SAP Authorization and Trust Management Service](sap-authorization-and-trust-management-service-2ce1a96.md), choose *Edit*, scroll down to *Users*, and select *\+*. Enter the email address of the initial consumer, select SAP ID Service as your identity provider or use your preferred custom identity provider, and save your changes.

In the confirmation dialog, you must confirm details such as email, subdomain, and subaccount ID to onboard the initial user:

1.  Open the URL your provider has sent you to get access to their SaaS application.
2.  On the initial administrator onboarding screen, your email address, subdomain, and subaccount ID are displayed. Select *Onboard User* to start the onboarding process. This might take a few minutes. Once the process is finished, you are redirected to the system. This onboarding process only needs to be performed once.

**Check tenant user provisioning in Landscape Portal**

On the provider side, as an operator user assigned to the `LandscapePortalAdminRoleCollection`, you can check ongoing tenant user provisioning in the *Landscape Portal*. After selecting the target system in the system overview app, ongoing tenant user provisioning is displayed in the *Requests* section. See [View the Request Log](view-the-request-log-0ea69c2.md).

> ### Tip:  
> For an overview of all processes, such as tenant provisioning across multiple systems, see [Operations Dashboard](operations-dashboard-0a3a735.md).

