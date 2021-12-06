<!-- loio975bd3e54cbe4e52af346740658d1a4a -->

# Order and Provide

After the initial add-on version has been built, you have to deploy and provide it as a SaaS solution so that the add-on can be consumed by customers via a subscription in the SAP BTP cockpit.

 <a name="loio4e35eb027f284b7fa6219bc70561fb4e"/>

<!-- loio4e35eb027f284b7fa6219bc70561fb4e -->

## Deploy



For the deployment and offering of the add-on as SaaS solution, you have to create a dedicated global account and implement a multitenant application. For multitenant applications based on the ABAP environment, the ABAP Solution service is used to provision ABAP systems, tenants, and users on demand. Once you’ve configured this implementation, you can deploy it to the *05 Provide* space of your provider subaccount *05 Provide*. See [Set Up a Production Account](Develop,_Test,_Build_3bf575a.md#loio2e7b4b631e814de1b8fe3959af4105bc).

After the multitenant application has been deployed, the SaaS solution is ready for commercialization.



<a name="loio4e35eb027f284b7fa6219bc70561fb4e__section_wrn_2x4_drb"/>

## Prerequisites

-   To configure the sizing of a SaaS solution, you have to determine the expected load per region by using the Technical Monitoring Cockpit. See [Technical Monitoring Cockpit \(Cloud Version\)](https://help.sap.com/viewer/tmc_cloud/eb867c69739a4cf3be6361d3990d26a2.html).
-   To implement and deploy a multitenant application for a SaaS solution, you have to assign the necessary entitlements in the provider subaccount, for example for the ABAP Solution service. See [Developing Multitenant Applications in the ABAP Environment](Developing_Multitenant_Applications_in_the_ABAP_Environment_195031f.md) and [Entitlements and Quotas](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/00aa2c23479d42568b18882b1ca90d79.html).
-   To subscribe to the Landscape Portal application, you need the corresponding entitlement. See [Landscape Portal](Landscape_Portal_5eb70fb.md).

 <a name="loiof3305f65648248318028e02c84375323"/>

<!-- loiof3305f65648248318028e02c84375323 -->

### Multitenant Application

**Implement the Multitenant Application**

As a DevOps engineer, you can implement the multitenancy functionality using SAP Business Application Studio in the development subaccount.

For more information on how to create multitenant-enabled applications in the ABAP environment, see [Developing Multitenant Applications in the ABAP Environment](Developing_Multitenant_Applications_in_the_ABAP_Environment_195031f.md).

> ### Recommendation:  
> We recommend following the MTA-based implementation approach. See [MTA-Based Approach \(Recommended\)](MTA-Based_Approach_(Recommended)_ca0cc10.md).

1.  You start off by defining your ABAP solution, for example, the parameters explained in the previous chapter need to be configured. See [Define Your ABAP Solution](Define_Your_ABAP_Solution_1697387.md).

    > ### gCTS Delivery:  
    > When defining your ABAP solution, you can ignore the add-on product name in the service configuration. The value for `addon_product_name` has to be empty so that ABAP systems without an add-on \(abap/standard\) are provisioned for the solution.
    > 
    > See [Delivery via Add-On or gCTS](Concepts_9482e7e.md#loio438d7ebfdc4a41de82dcdb156f01857e).

2.  In the configuration for the XSUAA instance, you specify the functional authorization scopes for the application. See [Create an XSUAA Instance](Create_an_XSUAA_Instance_2ce1a96.md).

3.  A tenant-aware approuter application is developed that is used to authenticate business users of the application at runtime. See [Develop the Approuter Application](Develop_the_Approuter_Application_44dbd0a.md).

    Depending on the purpose of the approuter application, whether used for development or production, it needs to be configured differently. See [Configure the Approuter Application](Configure_the_Approuter_Application_3725815.md)

4.  To make a multitenant application available for subscription to SaaS consumer tenants, you have to register the application in the Cloud Foundry environment via the SaaS Provisioning service \(saas-registry\). See [Register the Multitenant Application to the SaaS Provisioning Service](Register_the_Multitenant_Application_to_the_SaaS_Provisioning_Service_2cd8913.md).

5.  Bind your approuter application to the xsuaa service instance, which acts as an OAuth 2.0 client to your application, and to the ABAP Solution service instance, which represents your ABAP solution. See [Bind the approuter Application to the xsuaa and the ABAP Solution Service Instance](Bind_the_approuter_Application_to_the_xsuaa_and_the_ABAP_Solution_Service_Instance_04b9258.md).


> ### Note:  
> If you need support or experience issues, please report an incident by using component `BC-CP-ABA`.

**Deploy Multitenant Application**

After completing development, you, as a DevOps engineer, must build and deploy the resulting multitenancy implementation.

By using MTA extension descriptors, you can configure the required values during deployment. See [Using MTA Extension Descriptors](Using_MTA_Extension_Descriptors_383f3a3.md).

> ### gCTS Delivery:  
> If you use gCTS instead of add-ons for delivering software components to production systems, the value for the add-on product name inside the MTA extension descriptor file has to be empty.
> 
> See [Delivery via Add-On or gCTS](Concepts_9482e7e.md#loio438d7ebfdc4a41de82dcdb156f01857e).

**Create Cloud Controller Destination**

As an operator of the provider subaccount, you need to create a destination for the Cloud Foundry Cloud Controller access. See [Create a Destination for the Cloud Foundry Cloud Controller Access](Create_a_Destination_for_the_Cloud_Foundry_Cloud_Controller_Access_35b5acb.md). The Cloud Foundry Cloud Controller API maintains records of orgs, spaces, services, service instances, user roles, and more and is used to create new ABAP instances in the *05 Provide* space when necessary.

> ### Recommendation:  
> We recommend using a dedicated technical Cloud Foundry platform user registered in SAP ID Service for Cloud Controller access. This can either be a non-personalized S-user created via SAP One Support Launchpad or a P-user registered directly for an SAP ID account. See [Create SAP User Accounts](../50-administration-and-ops/Create_SAP_User_Accounts_ebe42f6.md).

 <a name="loio195a685a71f84953813e7b3bd255e849"/>

<!-- loio195a685a71f84953813e7b3bd255e849 -->

### Access to Landscape Portal

The *Landscape Portal* acts as a central tool that allows you to perform lifecycle management operations, such as provisioning new consumers tenants, users, and more. See [Landscape Portal](Landscape_Portal_5eb70fb.md).

As an operator of the provider subaccount, subscribe to the Landscape Portal application. The `LandscapePortalAdminRoleCollection` needs to be assigned to the users in the configured default identity provider of the subaccount that you want to provide access to the *Landscape Portal* app. See [Accessing the Landscape Portal](Accessing_the_Landscape_Portal_2e1e393.md).

> ### gCTS Delivery:  
> In the Landscape Portal, you can access the provider system and choose the provider tenant. Via the provider tenant, you get access to Fiori Apps, for example the *Manage Software Components* app, which is used for importing software components via gCTS.
> 
> See [Delivery via Add-On or gCTS](Concepts_9482e7e.md#loio438d7ebfdc4a41de82dcdb156f01857e).

 <a name="loio57c19c7c4dfa4c3cbb846c1ac57e2095"/>

<!-- loio57c19c7c4dfa4c3cbb846c1ac57e2095 -->

## Commercialize



To offer your SaaS solution to customers, register the SaaS solution in the SAP App Center. See [SAP App Center](https://www.sapappcenter.com/en/partner-with-us/documentation).

Additionally, you can request an SAP Extension Suite certification for your product so that it gets listed in the SAP Certified Solutions Directory. See [SAP Extension Suite Certification](https://www.sap.com/documents/2016/10/7cf3eaec-907c-0010-82c7-eda71af511fa.html) and [SAP Certified Solutions Directory](https://www.sap.com/dmc/exp/2013_09_adpd/enEN/#/solutions).

After finishing this process, your customers can order the SaaS solution, which is the preliminary step to actual subscription.



<a name="loio57c19c7c4dfa4c3cbb846c1ac57e2095__section_p4d_j1p_drb"/>

## Prerequisites

Before registering a SaaS solution in SAP App Center or certifying the solution, you have to deploy the first add-on version and multitenant application. See [Developing Multitenant Applications in the ABAP Environment](Developing_Multitenant_Applications_in_the_ABAP_Environment_195031f.md).

 <a name="loio607aa8614ea34ee7b366b01ad03bfc4c"/>

<!-- loio607aa8614ea34ee7b366b01ad03bfc4c -->

### \(Optional\) Register SaaS Solution in SAP App Center

SAP App Center is the enterprise marketplace where we bring together customers and partners on a single, easy-to-use, global online platform. See [SAP App Center](https://www.sapappcenter.com/).

To learn more about how you can offer your SaaS solution to SAP customers via the App Center, see [Getting Started with the New SAP App Center](https://www.sapappcenter.com/en/partner-with-us/documentation).

 <a name="loioace3b22147eb40d3989c5525491eb729"/>

<!-- loioace3b22147eb40d3989c5525491eb729 -->

### \(Optional\) Certification

With an SAP Extension Suite certification, your SaaS solution is featured in the SAP Certified Solution Directory, which allows for more growth and customer participation. See [SAP ICC Integration Scenario - SAP Extension Suite Certification](https://www.sap.com/documents/2016/10/7cf3eaec-907c-0010-82c7-eda71af511fa.html) and [SAP Certified Solution Directory](https://www.sap.com/dmc/exp/2013_09_adpd/enEN/#/solutions).

 <a name="loioa24217a0d6fa434bbce97869dfb70dda"/>

<!-- loioa24217a0d6fa434bbce97869dfb70dda -->

## Order and Provide



Once the SaaS solution has been fully deployed and commercialized, customers can order the offered product. After the buying process has been completed, you, as a SaaS solution operator, have to create a consumer subaccount in the global production account and subscribe to the SaaS solution. This in turn triggers the provisioning of the required ABAP systems and tenants for the customer. You can follow this process using the *Landscape Portal* service, which gives you an overview of the available ABAP systems and tenants belonging to a SaaS solution.

When tenant or system provisioning has been completed, you receive a confirmation mail as a SaaS solution operator.



<a name="loioa24217a0d6fa434bbce97869dfb70dda__section_sxb_gms_vnb"/>

## Prerequisites

-   To create a consumer subaccount, all the details, such as the account name, provider, region and subdomain should be known. See [Account Model](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/8ed4a705efa0431b910056c0acdbf377.html#loio8d6e3a0fa4ab43e4a421d3ed08128afa) and [Regions and API Endpoints for the ABAP Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/350356d1dc314d3199dca15bd2ab9b0e.html#loio879f37370d9b45e99a16538e0f37ff2c).
-   To subscribe to the SaaS solution, you need a consumer subaccount. To monitor system and tenant provisioning, you have to subscribe to the Landscape Portal app and configure user access using the `LandscapePortalAdminRoleCollection`. See [Accessing the Landscape Portal](Accessing_the_Landscape_Portal_2e1e393.md).
-   To configure the consumer subaccount, the details for destinations, cloud connectors and trust configuration need to be available to you. To delegate access to the consumer subaccount, a consumer subaccount admin user of the customer is required. See [Using the Destinations Editor in the Cockpit](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/565fdb3dd19d4cda80864341dc5a0451.html), [Cloud Connector](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e6c7616abb5710148cfcf3e75d96d596.html), [Trust and Federation with Identity Providers](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/cb1bc8f1bd5c482e891063960d7acd78.html), and [Add Members to Your Subaccount \[Feature Set B\]](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/1e1b7b60bb1b4764a2d4bb96bd73182d.html).
-   For the initial user onboarding, you need a consumer subaccount administrator in the consumer subaccount. See [Consumer Access](Consumer_Access_a197d6f.md).



### Customer Buys SaaS Solution

Depending on the marketplace platform \(for example SAP App Center\) or other distribution channels, customers can buy the SaaS solution.

-   Customer name and email address for the creation of a consumer subaccount admin user
-   For the following process of creating a consumer subaccount for your customer, you should have the following information readily available:
    -   Name and scope of the SaaS solution for the subscription to the SaaS solution
    -   Quantity of users, t-shirt size of solution etc. to determine necessary configuration steps


 <a name="loio8b92024cc5d44268bf4737551e4fa981"/>

<!-- loio8b92024cc5d44268bf4737551e4fa981 -->

### Create Consumer Subaccount

**Consumer account structure**

For the following process of creating a consumer subaccount for your customer, you have to create consumer subaccounts in the global production account so that customers can subscribe to the provided SaaS solution.

This means, on top of subaccount*04 Build/Test* and *05 Provide*, you have to create a subaccount in the production global account for each consumer. See [Set Up a Production Account](Develop,_Test,_Build_3bf575a.md#loio2e7b4b631e814de1b8fe3959af4105bc).

After a customer has ordered the SaaS solution, you, as an operator of the global production account, need to create a *06 Consume* subaccount. See [Subscribe New Consumers](Subscribe_New_Consumers_b90cde1.md).

While creating the subaccount, you must provide the following details:

-   **Name**: Give the subaccount a unique display name. This can be the name of the customer, a customer number or a specific naming pattern
-   **Provider**: Choose the IaaS provider according to the IaaS provider selected for the provider subaccount
-   **Region**: Choose the subaccount region according to the region where the provider subaccount was created. See [Regions and API Endpoints for the ABAP Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/350356d1dc314d3199dca15bd2ab9b0e.html#loio879f37370d9b45e99a16538e0f37ff2c).
-   **Subdomain**: The subdomain of the subaccount becomes part of the application URL, according to the `TENANT_HOST_PATTERN` that you defined in the approuter configuration for the multitenant application. See [Configure the Approuter Application](Configure_the_Approuter_Application_3725815.md).

 <a name="loio477ea31394504182b2ea5ef9ce26802d"/>

<!-- loio477ea31394504182b2ea5ef9ce26802d -->

### Subscribe to SaaS Solution

After you have finalized the consumer subaccount configuration as an operator user on the provider side, the subscription to the SaaS solution is enabled for the consumer.

**Subscribe to SaaS solution in consumer subaccount**

In the consumer subaccount, navigate to the *Service Marketplace*. To subscribe to the SaaS solution, choose *Create*. The subscribed application is now displayed in *Services* \> *Instances and Subscriptions*. Once the subscription to the SaaS Solution is complete, you receive a notification via email. The email address is defined in the JSON file of your ABAP solution by setting parameter `provider_admin_email`\). See [Define Your ABAP Solution](Define_Your_ABAP_Solution_1697387.md).

**Check tenant provisioning in Landscape Portal**

The subscription process triggers provisioning of

-   A new ABAP system, if necessary according to ABAP solution configuration \(single/multi-tenancy\)

-   A new consumer tenant that is represented by an additional client in the ABAP system


In both cases, you, as a SaaS solution operator, receive a confirmation mail.

As an operator user assigned to the role collection `LandscapePortalAdminRoleCollection`, you can access the systems overview of the *Landscape Portal* and check both provisioned systems and new tenants.

See [Landscape Portal](Landscape_Portal_5eb70fb.md).

**Assign `SolutionAdmin` role**

Once the SaaS subscription process is completed, as an operator user in the trust settings of the *06 Consume* subaccount, assign the user onboarding role `SolutionAdmin` provided by the multitenant application to a customer user.

 <a name="loio3c44b19161d742a5a96576d64e70d505"/>

<!-- loio3c44b19161d742a5a96576d64e70d505 -->

### Configure Consumer Subaccount \(Feature Set A\)

Depending on the scope of the SaaS solution and consumer requirements, you, as an operator, have to configure the following:

-   Trust configuration for integration of corporate identity provider

    If you want to integrate an existing corporate identity provider for authentication/authorization in the consumer subaccount, please refer to [Trust and Federation with Identity Providers](../50-administration-and-ops/Trust_and_Federation_with_Identity_Providers_cb1bc8f.md). To restrict access based on certain criteria, such as the IP address,. you need to use the Identity Authentication service. See [Identity Authentication Service](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/d17a116432d24470930ebea41977a888.html).

-   Destinations and connectivity whenever the SaaS solution requires to connect to a destination \(cloud or on-premise\) that is configured by the consumer. See [Connectivity in the Cloud Foundry Environment](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/34010ace6ac84574a4ad02f5055d3597.html).


**Option A: Provider configures consumer subaccount**

As an operator user of the provider, you configure the consumer subaccount *06 Consume* for the customer. The customer only needs to provide the following:

-   Configuration details regarding the identity provider that is supposed to be used by providing the relevant SAML metadata file. See [Exporting SAML Identity Provider Metadata](../20-getting-started/Exporting_SAML_Identity_Provider_Metadata_5c1479e.md).

-   Configuration details regarding Cloud Connector connectivity: to configure the Cloud Connector, you, as the provider, need to enable a technical user of the customer as a security administrator of the consumer subaccount. See [Security Administration: Managing Authentication and Authorization](../50-administration-and-ops/Security_Administration_Managing_Authentication_and_Authorization_1ff47b2.md). This can either be a nonpersonalized S-user created by the customer in SAP One Support Launchpad or a P-user directly registered in SAP ID service.

    Subsequently, the customer configures the subaccount in the Cloud Connector by authenticating with the provided technical user.

-   Configuration details regarding destinations: The destination credentials might be exchanged in file format.

    > ### Note:  
    > Destination credentials need to be provided in clear text to the provider, which might be a security risk. In that case, option B might be more suitable.


On the provider side, you, as a SaaS solution operator, must take care of the following:

-   Set up the trust configuration according to customer configuration details. See [Establishing Trust to the SAML Identity Provider for the Cloud Foundry Account](../20-getting-started/Establishing_Trust_to_the_SAML_Identity_Provider_for_the_Cloud_Foundry_Account_55e7d92.md).

-   Add a technical user of the customer as a security administrator of the consumer subaccount

-   Configure destinations according to the credentials provided by the customer


**Option B: Consumer configures consumer subaccount**

The consumer configures the consumer subaccount after you, as an operator user on the provider side, grant access by doing the following:

-   In the consumer subaccount, enable the Cloud Foundry organization so that organization members can be added to that subaccount

-   As an operator, add the customer user as a member of the enabled Cloud Foundry organization such that the consumer subaccount *06 Consume* is visible to the customer user even without global account member privileges. No role needs to be assigned to the organization member.

-   To configure trust configuration and connectivity/destination settings in the subaccounts, add the customer user as a security administrator. See [Security Administration: Managing Authentication and Authorization](../50-administration-and-ops/Security_Administration_Managing_Authentication_and_Authorization_1ff47b2.md).


Once you, as an operator, have provided the relevant subaccount information, the customer user can then log on to the SAP BTP cockpit as the consumer subaccount admin and configure trust settings and connectivity/destination settings in the subaccount.

 <a name="loio6301a275af664613a51147e3451386e6"/>

<!-- loio6301a275af664613a51147e3451386e6 -->

### Configure Consumer Subaccount \(Feature Set B\)

Depending on the scope of the SaaS solution and customer requirements, you can make the following configurations in the consumer subaccount:

-   **Trust Configuration**

    You can configure a custom identity provider for the authentication of subscribed applications in the consumer subaccount. See [Trust and Federation with Identity Providers](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/cb1bc8f1bd5c482e891063960d7acd78.html).

    To restrict access based on certain criteria, such as the IP address, use the SAP Cloud Identity Services - Identity Authentication.

-   **Cloud Connector**

    Using Cloud Connector , you can create a link between SAP BTP applications and on-premise systems. See [Managing Subaccounts](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/f16df12fab9f4fe1b8a4122f0fd54b6e.html) on how to add and connect a consumer subaccount to Cloud Connector.

-   **Destination**

    Configure destinations, including technical information about the target resource, to connect your application to a remote service or system. See [Managing Destinations](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/84e45e071c7646c88027fffc6a7bb787.html).


As a SaaS solution operator, you can provide customers access to these configurations by assigning the subaccount administrator role collection to the consumer subaccount administrator.

The consumer subaccount administrator can then access the consumer subaccount in the SAP BTP cockpit including subscriptions, trust configuration, Cloud Connectors and destinations without having access to other consumer subaccounts in the global production account.

The consumer subaccount administrator can assign the Cloud Connector administrator role collection to the Cloud Connector administrator user to operate the data transmission tunnels used by the Cloud Connector. While adding the consumer subaccount in Cloud Connector, the same Cloud Connector administrator user is being configured.

See [Role Collections and Roles in Global Accounts, Directories, and Subaccounts \[Feature Set B\]](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/0039cf082d3d43eba9200fe15647922a.html) for more information on available role collections in the consumer subaccount.

 <a name="loio4a9c5011922847ac91db165c78656149"/>

<!-- loio4a9c5011922847ac91db165c78656149 -->

### Initial User Onboarding

After trust/connectivity configuration in the consumer subaccount, your customer needs an initial administrator user in the consumer tenant that was created for the subscription.

To create such an initial administrator user, as a consumer subaccount administrator, you have to assign the role collection including the `SolutionAdmin` role to your user in the *Role Collections* view in the consumer subaccount.

In a confirmation form, you have to confirm details such as email, subdomain, and subaccount ID. Afterwards, the consumer subaccount administrator can access the SAP Fiori launchpad of the subscribed SaaS solution via *Instances and Subscriptions*.

> ### Note:  
> Depending on the approuter configuration, as the operator, you might need to add a new tenant-specific route pointing to the approuter application.
> 
> You have to create a route for the consumer subaccount that maps to the approuter in the multitenant application. New routes are created inside the space where the multitenant application is deployed. For the creation of a new route, you have to specify the domain and hostname. In the development phase, the hostname combines the subdomain of the consumer \(sub-\)account, a dash, and the app name of the SaaS solution. Once the route is created, you have to map it to the approuter application.
> 
> During the production phase, you should use a route with wildcard hostname combined with a custom domain so that you don't have to create them manually in the space where the multitenant application is deployed.
> 
> See [Configure the Approuter Application](Configure_the_Approuter_Application_3725815.md) and [Create Routes](../50-administration-and-ops/Create_Routes_9fddeea.md).

**Check tenant user provisioning in Landscape Portal**

On the provider side, as an operator user assigned to the `LandscapePortalAdminRoleCollection`, you can check ongoing tenant user provisioning in the *Landscape Portal*. After selecting the target system in the system overview app, ongoing tenant user provisioning is displayed in the *Requests* section. See [View the Request Log](View_the_Request_Log_0ea69c2.md).

