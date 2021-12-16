<!-- loio3bf575a3dc5043f895f8bd411d2a86a1 -->

# Develop, Test, Build

To develop and provide add-ons, you have to set up a suitable system landscape and Cloud Foundry environment account structure.



You need a partner contract to create the account structure. The accounts for the upstream \(add-on development, test, build\) and downstream \(providing add-on as SaaS solution\) parts of the process need to be separated from each other and therefore are handled in dedicated global accounts. We refer to these as global development account and global production account. For more information regarding the development license, see [SAP PartnerEdge Test, Demo & Development Price List](https://partneredge.sap.com/en/library/assets/partnership/sales/order_license/pl_pl_part_price_list.html). To find out more about production licenses, see [SAP PartnerEdge: Resources for OEM Partners](https://partneredge.sap.com/en/partnership/manage/op_resource/oem.html).

> ### Tip:  
> For in-depth information about the system landscape/account model, check out [System Landscape/Account Model](concepts-9482e7e.md#loio4ca756395fc24e56a42b77632a6bd862).

For the initial add-on delivery, you should create a development and test landscape following the guidelines mentioned in [Concepts](concepts-9482e7e.md#loio9482e7eef4634cb993a4ae296b2029fa). Once backend and frontend development is completed, you can test the add-on implementation in a persistent test system. Upon successful completion of this step, set up a CI/CD server along with a Jenkins pipeline to execute the add-on build allowing for an automated and efficient assembly. This automated pipeline can then be reused transforming all upgrade and update activities into a straightforward process.

Once the add-on build/assembly is finished, you can release the add-on to the productive global account. First, the add-on build is installed in a test system in the production account to verify that it works correctly. If successful, you can provide the add-on to customers. See [SAP Business Technology Platform](../sap-business-technology-platform-6a2c1ab.md), [ABAP Environment Learning Journey](https://help.sap.com/doc/221f8f84afef43d29ad37ef2af0c4adf/HP_2.0/en-US/49047e7668844d419ccee567923a475e.html), and [ABAP Environment Community](https://community.sap.com/topics/cloud-platform-abap-environment). Also consider starting out with a trial account to get hands-on development experience with the ABAP environment as described in [Blog: Trial for ABAP in SAP Business Technology Platform](https://blogs.sap.com/2019/09/28/its-trialtime-for-abap-in-sap-cloud-platform/) and [Getting Started with a Trial Account in the ABAP Environment](../20_getting_started/getting-started-with-a-trial-account-in-the-abap-environment-720c423.md).

> ### gCTS Delivery:  
> Besides using add-ons for delivering software components to production systems, gCTS can be used as an alternative approach. It is used for transporting software components between different ABAP systems.
> 
> See [Delivery via Add-On or gCTS](delivery-via-add-on-or-gcts-438d7eb.md#loio438d7ebfdc4a41de82dcdb156f01857e).

 <a name="loio4338854e3133407abb47d3a281dbd1e1"/>

<!-- loio4338854e3133407abb47d3a281dbd1e1 -->

## Prepare



Before you can proceed with the development of the add-on, you have to perform several preliminary steps.

-   Register the development namespaces before any system is set up. To start the actual add-on development process, you have to set up the system landscape and global account structure for development. For pipeline automation, set up a CI/CD server, in this case a Jenkins server.
-   Create one or more software components that make up the add-on in the namespaces registered for you. In this scenario, namespaces are required for both the add-on product name and software components. You can register these namespaces with the development namespace/license keys tool.
-   Purchase the SAP BTP, Cloud Foundry environment entitlements necessary for the account setup, which includes the service ABAP environment for development. The ABAP environment \(service plan `saas_oem`\), Application runtime, SaaS provisioning, ABAP Solution service as well as the Landscape Portal are used for providing the SaaS app.

    > ### Recommendation:  
    > We recommend using the browser-based IDE SAP Business Application Studio for UI development. In this case, additional configuration is required to enable developers to use this service.


Once you’ve completed these steps, you can start developing an add-on.



<a name="loio4338854e3133407abb47d3a281dbd1e1__section_zxr_sp4_drb"/>

## Prerequisites

-   To register a namespace, you need an S user in SAP One Support Launchpad with authorization to reserve a development namespace. See SAP note [1271482](https://launchpad.support.sap.com/#/notes/1271482).
-   To set up a global development and global poduction account, you need two global accounts in SAP BTP with the corresponding entitlements for services and applications. See [Entitlements and Quotas](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/00aa2c23479d42568b18882b1ca90d79.html).
-   To create ABAP instances, you have to set up the account structure in the global development account, and assign entitlements for each subaccount. See [Configure Entitlements and Quotas for Subaccounts](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/5ba357b4fa1e4de4b9fcc4ae771609da.html).
-   To develop UIs, you need an entitlement for SAP Business Application Studio and an assignment to a subaccount for development. See [SAP Business Application Studio](https://help.sap.com/viewer/product/SAP%20Business%20Application%20Studio/Cloud/en-US).
-   To set up transports from the development to the test system, you need a test system and optionally a pipeline in a Jenkins CI/CD server that is provisioned using a Cx Server to automatically import new changes. See [https://www.jenkins.io/](https://www.jenkins.io/) and [Cx Server](https://www.project-piper.io/infrastructure/overview/#cx-server-recommended).
-   To set up add-on development, you need a development system.

 <a name="loiocc5a3c6f78cf4889960c314dd09a5060"/>

<!-- loiocc5a3c6f78cf4889960c314dd09a5060 -->

### Register a Namespace

Using a reserved namespace for add-on development and build is necessary for a unique add-on product and software component name.

> ### Note:  
> You need to register a namespace before the first ABAP system is provisioned. For namespaces that are registered after the system provisioning, create an incident using component `BC-CP-ABA`.

If you need a new S-user, get in touch with a user administrator

As an S-user with authorization *Reserve Namespaces*, you have to reserve a namespace for your partner customer ID to register a namespace with the *Namespace* app. See [https://launchpad.support.sap.com/\#/namespaces](https://launchpad.support.sap.com/#/namespaces).

Due to length restrictions of some objects, namespaces should have 5–8 characters. See SAP note [105132](https://launchpad.support.sap.com/#/notes/105132) and [395083](https://launchpad.support.sap.com/#/notes/395083).

 <a name="loio9f2150f2b15e414aacd46c1723ce48fb"/>

<!-- loio9f2150f2b15e414aacd46c1723ce48fb -->

### Set Up a Development Account

As a SaaS solution operator, you have to configure the global development account.

![](images/Prepare_a_Development_Account_e29111f.png)

The add-on development is separated from providing the add-on for consumption as a SaaS solution.

> ### Recommendation:  
> We recommend the following subaccount structure:
> 
> -   In the *01 Develop* subaccount, add-on development is performed in a permanent development system. See [Development in the ABAP Environment](development-in-the-abap-environment-31367ef.md).
> -   In the *02 Test* subaccount, the developed software components are tested after a successful import into a permanent test system.
> -   In the *03 Build/Assemble* subaccount, the add-on package assembly is performed in a transient assembly system that is created and deleted automatically by the build pipeline.

> ### gCTS Delivery:  
> If you use gCTS instead of add-ons for delivering software components to production systems, the setup and usage of a *03 Build/Assemble* \(used for the add-on assembly\) subaccount is redundant.
> 
> See [Delivery via Add-On or gCTS](delivery-via-add-on-or-gcts-438d7eb.md#loio438d7ebfdc4a41de82dcdb156f01857e).

You should configure a Cloud Foundry space in each subaccount. Dividing the development, testing, and assembling activities into different subaccounts allows for maximum flexibility. For instance, you may want to use different identity providers or consume different connectivity services during testing and development.

The ABAP systems that you use for development, testing, and add-on assembly are of type `abap/standard` and made available via entitlements. These service entitlements must be assigned by an administrator to different subaccounts, according to the following structure:


<table>
<tr>
<th valign="top">

Global Account



</th>
<th valign="top">

Subaccount



</th>
<th valign="top">

Space



</th>
<th valign="top">

Services



</th>
</tr>
<tr>
<td valign="top">

Partner Saas on ABAP \(Dev\)



</td>
<td valign="top">

01 Develop



</td>
<td valign="top">

Develop



</td>
<td valign="top">

1x abap/standard

abap/hana\_compute\_unit \(standard: 4\)

abap/abap\_compute\_unit \(standard: 1\)



</td>
</tr>
<tr>
<td valign="top">

Partner Saas on ABAP \(Dev\)



</td>
<td valign="top">

02 Test



</td>
<td valign="top">

Test



</td>
<td valign="top">

1x abap/standard

abap/hana\_compute\_unit \(standard: 4\)

abap/abap\_compute\_unit \(standard: 1\)



</td>
</tr>
<tr>
<td valign="top">

Partner Saas on ABAP \(Dev\)



</td>
<td valign="top">

03 Build/Assemble



</td>
<td valign="top">

Build/Assemble



</td>
<td valign="top">

1x abap/standard

abap/hana\_compute\_unit \(standard: 4\)

abap/abap\_compute\_unit \(standard: 1\)



</td>
</tr>
</table>

Additionally, the following entitlements for SaaS application subscriptions are required:

-   SAP Business Application Studio for UI development. See [SAP Business Application Studio](sap-business-application-studio-c736960.md).
-   Web access for ABAP for access to systems during development phase. See [Subscribing to the Web Access for ABAP](../20_getting_started/subscribing-to-the-web-access-for-abap-98928b0.md).
-   Landscape Portal for provider support access. See [Landscape Portal](landscape-portal-5eb70fb.md).

If you want to integrate an existing corporate identity provider in the subaccounts of the global development account for authentication/authorization, see [Trust and Federation with Identity Providers](../50_administration_and_ops/trust-and-federation-with-identity-providers-cb1bc8f.md). To restrict access based on certain criteria such as the IP address, you need to use the [Identity Authentication Service](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/d17a116432d24470930ebea41977a888.html).

> ### Tip:  
> For in-depth information about the system landscape/account model, check out [System Landscape/Account Model](concepts-9482e7e.md#loio4ca756395fc24e56a42b77632a6bd862).

 <a name="loio2e7b4b631e814de1b8fe3959af4105bc"/>

<!-- loio2e7b4b631e814de1b8fe3959af4105bc -->

### Set Up a Production Account

As a SaaS solution operator, you have to configure the global production account.

![](images/Prepare_a_Production_Account_ad3698a.png)

The finished add-on product is provisioned to customers in a dedicated global production account.

> ### Recommendation:  
> We recommend the following subaccount structure:
> 
> -   In the *04 Build/Test* subaccount, the add-on build is installed and tested again
> -   In the *05 Provide* subaccount, the add-on product is provided to customers

In the provider context, the `ABAP environment (saas_oem)` service plan is used.

> ### gCTS Delivery:  
> If you use gCTS instead of add-ons for delivering software components to production systems, the setup and usage of a *04 Build/Test* \(used for add-on installation test\) subaccount is redundant.
> 
> Additionally, considering the availability of software components only in the same global accounts, you have to create the production systems as well as development and test systems in the same global account \(global development account = global production account\).
> 
> In the provider subaccount, an ABAP instance of service plan type `abap/standard` instead of `abap/saas_oem` is used.
> 
> See [Delivery via Add-On or gCTS](delivery-via-add-on-or-gcts-438d7eb.md#loio438d7ebfdc4a41de82dcdb156f01857e).

These provider ABAP instances allow flexible sizing, multitenancy, and the possibility to install an add-on product during provisioning.

For the provisioning of these ABAP systems of service plan `saas_oem`, another set of services comes into play: With the ABAP Solution Provider and the saas-registry service, you can provide your add-ons as SaaS solution offerings. See [Define Your ABAP Solution](define-your-abap-solution-1697387.md).

Note that these service entitlements must be assigned to different subaccounts, according to the following structure:


<table>
<tr>
<th valign="top">

Global Account



</th>
<th valign="top">

Subaccount



</th>
<th valign="top">

Space



</th>
<th valign="top">

Services



</th>
</tr>
<tr>
<td valign="top">

Partner Saas on ABAP \(Provider\)



</td>
<td valign="top">

04 Build/Test



</td>
<td valign="top">

Build/Test



</td>
<td valign="top">

abap/saas\_oem

abap/hana\_compute\_unit \(standard: 4\)

abap/abap\_compute\_unit \(standard: 1\)



</td>
</tr>
<tr>
<td valign="top">

Partner Saas on ABAP \(Provider\)



</td>
<td valign="top">

05 Provide



</td>
<td valign="top">

Provide



</td>
<td valign="top">

abap/saas\_oem

abap/hana\_compute\_unit \(standard: 4\)

abap/abap\_compute\_unit \(standard: 1\)

Application Runtime

abap-solution

saas-registry

xsuaa



</td>
</tr>
</table>

Additionally, the following SaaS application subscription is required:

*Landscape Portal* to manage systems and tenants in the provider subaccount. The *Landscape Portal* app acts as a central tool to allow service providers to perform lifecycle management operations, such as provisioning new consumers as new tenants, moving tenants, and more.

If you want to integrate an existing corporate identity provider in the subaccounts of the global production account for authentication/authorization, see [Trust and Federation with Identity Providers](../50_administration_and_ops/trust-and-federation-with-identity-providers-cb1bc8f.md). To restrict access based on certain criteria such as the IP address, you need to use the [Identity Authentication Service](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/d17a116432d24470930ebea41977a888.html).

> ### Tip:  
> For in-depth information about the system landscape/account model, check out [System Landscape/Account Model](concepts-9482e7e.md#loio4ca756395fc24e56a42b77632a6bd862).

 <a name="loio17aa433273c24bd2b949c297513851fe"/>

<!-- loio17aa433273c24bd2b949c297513851fe -->

### Create ABAP Instances

As a SaaS solution operator, you have to create ABAP instances.

For development and testing in the development codeline, one system is provisioned in each of the development and test subaccounts.


<table>
<tr>
<th valign="top">

Global Account



</th>
<th valign="top">

Subaccount



</th>
<th valign="top">

Space



</th>
<th valign="top">

ABAP Instances



</th>
</tr>
<tr>
<td valign="top">

Global Development Account



</td>
<td valign="top">

01 Develop



</td>
<td valign="top">

Develop



</td>
<td valign="top">

Create an ABAP instance \(abap/standard\) DEV

Set parameter `is_development_allowed = true`



</td>
</tr>
<tr>
<td valign="top">

Global Development Account



</td>
<td valign="top">

02 Test



</td>
<td valign="top">

Test



</td>
<td valign="top">

Create an ABAP instance \(abap/standard\) TST

Set parameter `is_development_allowed = false`



</td>
</tr>
</table>

> ### Note:  
> You don't have to create an ABAP instance \(abap/standard,`is_development_allowed = false`\) in the *03 Build/Assemble* account because this instance is created automatically during the add-on build process .

In the *03 Build/Assemble* account, assembly systems are provisioned by the add-on build pipeline. These systems are used to import the desired software components that are then packaged for add-on delivery \(see [Software Assembly Integration \(SAP\_COM\_0582\)](software-assembly-integration-sap-com-0582-26b8df5.md)\). As an operator, you don’t have to provision these systems manually as we recommend using transient systems for the build process. But sufficient entitlement/quota for abap/standard services need to be available.

Use service parameter `is_development_allowed` to differentiate between development and test systems. The test and assembly systems must be productive to avoid changes being made to the add-on outside of the development system.

For more information on how to get started with your customer account, see [Getting Started with a Customer Account in the ABAP Environment](../20_getting_started/getting-started-with-a-customer-account-in-the-abap-environment-e34a329.md) and [Creating an ABAP System](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/50b32f144e184154987a06e4b55ce447.html).

In the *04 Build/Test* subaccount of the global production account, an add-on installation test system is automatically created. This ABAP environment service instance of plan `saas_oem` is provisioned with parameter `is_development_allowed = false`.

Subscribe to the Web Access for ABAP to gain access to the SAP Fiori launchpad in all subaccounts of the global production account.

 <a name="loio3f03dfe2f21b471ab98abc6f208c3762"/>

<!-- loio3f03dfe2f21b471ab98abc6f208c3762 -->

### Set Up UI Development

As a SaaS solution operator, you have to set up SAP Business Application Studio for development.

As a developer user, you can then create an SAP Fiori dev space and generate UI projects.

> ### Recommendation:  
> For frontend development, we recommend using SAP Business Application Studio. See [Develop an SAP Fiori Application UI and Deploy it to ABAP Using SAP Business Application Studio](develop-an-sap-fiori-application-ui-and-deploy-it-to-abap-using-sap-business-application-eaaeba4.md).

 <a name="loiobf557544f90f4bc88911c4865ec78207"/>

<!-- loiobf557544f90f4bc88911c4865ec78207 -->

### Set Up Transport from Development to Test System via gCTS

You can set up the transport of your development from a development to a test system either manually with the *Manage Software Components* app or in an automated fashion.

**Manually import into test system via gCTS**

As an add-on admin user, you can pull the latest released changes of a software component to the test system by using the main branch. You can test these changes in the test system independent from ongoing development. See [How to Pull Software Components](../50_administration_and_ops/how-to-pull-software-components-90b9b9d.md) and [ABAP Lifecycle Management](abap-lifecycle-management-5c7b17d.md).

**\[Optional\] Set up a CI server and pipeline for automatic testing**

To schedule a regular import of new changes into the test system, you can use a CI server and pipeline to automate this process.

![](images/Pipeline_dev_to_test_8d52073.png)

As a DevOps engineer, you can configure the ABAP environment pipeline for an automated DEV to TST transport. To do so, a static and preconfigured system is used.With the pipeline, the pulling of specified software components/Git repositories is automated, triggered by the pipeline execution of the add-on administrator. See [Continuous Testing on SAP BTP ABAP Environment](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentTest/) and [Running ATC Checks on a Static ABAP Environment System](https://github.com/SAP-samples/abap-platform-ci-cd-samples/tree/atc-static) for further details and an example.

 <a name="loio89a353151e534380a03b2a572a227731"/>

<!-- loio89a353151e534380a03b2a572a227731 -->

### Set Up Add-On Development

To transport new developments from system to system, the add-on development is structured by software components. Software components are independent development containers.

To create a new software component for add-on development, as an add-on admin user, use the *Manage Software Components* app and create a new component of type `Development`. The name of the software component begins with a namespace that was activated in the development system. By default, all namespaces of the global account owner are enabled in the systems. See [How to Create Software Components](../50_administration_and_ops/how-to-create-software-components-67e2f2e.md).

Clone the main branch of the software component to the development and test system.

Software components in the development and test system should always stay on the main branch. If you want to work on maintenance branches to develop bug fixes and other maintenance deliveries, create a dedicated hotfix development and test system \(maintenance codeline\).

> ### Tip:  
> For in-depth information about versioning and branches, check out [Versioning and Branches](versioning-and-branches-8c087bc.md#loio8c087bca40584f9b899282b4ec515753).

 <a name="loio9464e3af139d4e0581cb4e819886b0c8"/>

<!-- loio9464e3af139d4e0581cb4e819886b0c8 -->

## Develop



Both the initial implementation and any further development of the add-on are performed in the development system of the development subaccount.

You can use various SAP technologies at this point, such as the ABAP RESTful application programming model \(RAP\) for modeling and implementing business objects and the browser-based IDE SAP Business Application Studio for developing SAP Fiori UIs. Depending on the business use case, some additional development effort may be necessary to implement suitable launchpad content, Identity & Access Management artifacts, or communication management artifacts.

Once you’ve completed these development activities, the solution is ready to be tested in a suitable test system.



<a name="loio9464e3af139d4e0581cb4e819886b0c8__section_s1q_ds4_drb"/>

## Prerequisites

-   For ABAP development, you need a developer user using ABAP Development Tools. See [Getting Started as a Developer in the ABAP Environment](../20_getting_started/getting-started-as-a-developer-in-the-abap-environment-4b896c9.md).
-   For UI development, you need a developer user using SAP Business Application Studio. See[Develop an SAP Fiori Application UI and Deploy it to ABAP Using SAP Business Application Studio](develop-an-sap-fiori-application-ui-and-deploy-it-to-abap-using-sap-business-application-eaaeba4.md).
-   For custom code migration, you need a business user that is assigned the business role based on business role template `SAP_BR_IT_PROJECT_MANAGER`, and a communication arrangement instance for `SAP_COM_0464`. See [Custom Code Migration](../50_administration_and_ops/custom-code-migration-651ef65.md).

 <a name="loiofa5af4ecdf90496b8eec54fe0e22150c"/>

<!-- loiofa5af4ecdf90496b8eec54fe0e22150c -->

### ABAP Development

As a developer user, implement your custom business services with the ABAP RESTful application programming model. See [ABAP RESTful Application Programming Model](https://help.sap.com/viewer/923180ddb98240829d935862025004d6/Cloud/en-US/289477a81eec4d4e84c0302fb6835035.html). Maintain business catalogs \(see [Identity and Access Management \(IAM\)](identity-and-access-management-iam-5b62901.md)\) and communication scenarios \(see [Overview of Communication Management](overview-of-communication-management-5b8ff39.md)\) to expose services to business users and communication users.

**Identity and Access Management**

SAP Fiori applications and business services are represented by IAM apps and can be used to define the necessary authorizations. In an IAM business catalog, you bundle multiple IAM apps and their predefined authorizations, for example, for a specific business area.

Additionally, you can define business role templates to make it easier for administrators to find the relevant business catalogs. See [Identity and Access Management \(IAM\)](identity-and-access-management-iam-5b62901.md).

**Communication Management**

> ### Note:  
> Use customer-managed communication scenarios as a design time description to store technical information, such as inbound and outbound services and their service type, for example OData or SOAP by using the `create_by_comm_arrangement` method. See [Communication Scenarios Managed by Customers](communication-scenarios-managed-by-customers-31f5566.md).
> 
> Instead of coding against destination names, as described in [Usage of the Destination Service](usage-of-the-destination-service-40ecb5c.md), using communication scenarios allows consumers of the SaaS solution to create communication arrangements based on provided communication scenarios. Therefore, you don't have to create specific destinations in the consumer subaccount.

> ### Restriction:  
> The ABAP environment only supports one communication configuration layer intended to be used by the consumer. It’s currently not possible to enforce a communication configuration exclusively managed by the service provider within the consumer tenant.

Services with the following protocols supported for **inbound communication** can be included as part of customer-managed communication scenarios:

-   HTTP
-   SOAP
-   RFC Internet/Cloud Connector

> ### Restriction:  
> RFC is currently not supported for inbound communication in consumer tenants.

For **outbound communication**, the following protocols are supported:

-   HTTP \(Internet\)
-   HTTP \(Cloud Connector\)
-   SOAP \(Internet\)
-   SOAP \(Cloud Connector\)
-   RFC \(Internet\)
-   RFC \(Cloud Connector\)

See [Supported Protocols and Authentication Methods](supported-protocols-and-authentication-methods-437e9d4.md).

**Business Configuration**

Business configuration plays a major role in SaaS solutions. It refers to a predefined set of configuration options that affect its functionality and behavior. See [Business Configuration in SAP BTP ABAP Environment \(1\): Overview and BC Maintenance Apps](https://blogs.sap.com/2021/09/22/business-configuration-in-sap-btp-abap-environment-1-overview-and-bc-maintenance-apps/).

To maintain these configuration options, you have to create dedicated apps using the ABAP RESTful Application Programming Model. See [Create a Business Configuration App for Factory Calendar Using the ABAP RESTful Application Programming Model](https://developers.sap.com/mission.abap-dev-factory-calendar.html).

Using the business configurations API, you can register business configurations. These business configurations are then displayed in the list of all maintainable business configurations in the SAP Fiori App Maintain Business Configurations, unless the user has the necessary authorizations for the service of the business configuration. See [Maintain Business Configurations API](../50_administration_and_ops/maintain-business-configurations-api-508d406.md).



**Key User Extensibility Enablement**

Using SaaS solutions, you can provide key user extensibility for system-internal use \(contract C1\) and use in key user apps. This allows customers who use the solution to extend it to their specific requirements.

As a developer user, you have to implement key user extensibility in the development system in the Partner Development tenant \(client 100\) using ABAP Development Tools.

See [Providing Business Add-Ins](providing-business-add-ins-6747acb.md) for guidance on how to prepare business add-ins \(BAdIs\) so that customers can add their own business logic in the solution by using the *Custom Logic* app.

See[Configuring Predefined Custom Fields](../50_administration_and_ops/configuring-predefined-custom-fields-0033cbc.md) for guidance on how to equip your SaaS solution with support for customer-specific extension fields.

> ### Note:  
> Released APIs, such as BAdIs or predefined custom fields, must only be changed compatibly. Otherwise, for example, runtime errors might occur or an upgrade might fail.
> 
> Using API snapshots to store the state of a released object locally can provide incompatibility warnings in ABAP Development Tools where the current state of the released object is compared to the last API snapshot.
> 
> The provider is responsible for preparing the solution to be lifecycle-stable for consumption by customers. Thus, as a developer user, you need to take these warnings into consideration before activating new changes in released objects.



**Multitenancy**

With the ABAP environment, you can build multitenancy-enabled SaaS solutions. To do so, the add-on implementation has to follow certain guidelines. See [Development Guideline to Enable Multitenancy of Products Built on the ABAP Environment](development-guideline-to-enable-multitenancy-of-products-built-on-the-abap-environment-9d994c8.md).

> ### Recommendation:  
> If the add-on implementation is aligned with the development guideline for multitenancy, we recommend configuring your solution by setting `tenant_mode = multi` so that the same ABAP service instance is used for multiple consumers.

> ### Tip:  
> For in-depth information about multitenancy, check out [Multitenancy](concepts-9482e7e.md#loioc8730736a52645b49ca76c08214bf181).

 <a name="loiof3be8246edc74be59c10779443f67793"/>

<!-- loiof3be8246edc74be59c10779443f67793 -->

### UI Development

SAP Fiori applications are developed in SAP Business Application Studio on top of business services in the ABAP development system and then deployed to the ABAP development system to be part of the same software component as backend artifacts.

As a developer user, once business services are implemented as UI services, you can create SAP Fiori elements apps using SAP Business Application Studio. See [Develop an SAP Fiori Application UI and Deploy it to ABAP Using SAP Business Application Studio](develop-an-sap-fiori-application-ui-and-deploy-it-to-abap-using-sap-business-application-eaaeba4.md).

> ### Note:  
> Launchpad spaces and pages offer more flexibility to influence the launchpad layout for specific user groups. As of now, there is no possibility to create templates for a specific spaces/pages setup and to deliver this as part of an add-on. Therefore, for every consumer, this needs to be configured manually.
> 
> To simplify this process, we recommend structuring the IAM business catalogs that include IAM apps for the UI according to business roles by using business role templates. See [Providing Access to the SAP Fiori Application](providing-access-to-the-sap-fiori-application-b569abb.md).

 <a name="loiof438645cb5664399a6b21f8d9bd3d004"/>

<!-- loiof438645cb5664399a6b21f8d9bd3d004 -->

### \(Optional\) Code Migration from On-Premise

Optionally, you can migrate existing custom ABAP code for add-on development purposes. This custom code migration process analyzes your existing code for cloud-readiness. See [How to Check your Custom ABAP Code for SAP BTP ABAP Environment](https://blogs.sap.com/2018/10/02/how-to-check-your-custom-abap-code-for-sap-cloud-platform-abap-environment/) and [Custom Code Migration](../50_administration_and_ops/custom-code-migration-651ef65.md).

After adapting the code and making necessary changes, you can migrate the code via abapGit. See [How to Bring your ABAP Custom Code to SAP BTP ABAP Environment](https://blogs.sap.com/2019/11/11/how-to-bring-your-abap-custom-code-to-sap-cloud-platform-abap-environment/).

 <a name="loio023cf9d301b1479484e70b17cd5cf587"/>

<!-- loio023cf9d301b1479484e70b17cd5cf587 -->

## Test



Once development has been completed, you can test the solution in the test subaccount that you have previously set up. The software components that make up the solution are imported into a provisioned test system, while any additionally required configuration has to be carried out by you. This may entail creating suitable business roles, maintaining communication arrangements, or other administrative tasks performed via the SAP Fiori launchpad of your ABAP system.

You can also use a CI server and a Jenkins pipeline to automate the test process. This allows you to schedule regular tests and to be notified as soon as issues arise within the solution.

If the solution is successfully tested and works correctly, you can proceed with the add-on build.



<a name="loio023cf9d301b1479484e70b17cd5cf587__section_t5k_vt4_drb"/>

## Prerequisites

-   For testing in SAP Fiori launchpad in your ABAP environment, you need a business user in the test system that has the required authorizations to use the *Manage Software Components* app as well as authorizations that are required as a test user.
-   For testing in the ABAP Test Cockpit, you need a developer user using ABAP Development Tools. See [Getting Started as a Developer in the ABAP Environment](../20_getting_started/getting-started-as-a-developer-in-the-abap-environment-4b896c9.md).
-   \(Optional\) For running ATC checks as part of the ABAP environment pipeline, you have to create a pipeline in a Jenkins CI/CD server that is provisioned using the Cx Server tool. See [https://www.jenkins.io/](https://www.jenkins.io/) and [Cx Server](https://www.project-piper.io/infrastructure/overview/#cx-server-recommended).

 <a name="loio8c5b4d76a05b4bed8df01937f4d8d487"/>

<!-- loio8c5b4d76a05b4bed8df01937f4d8d487 -->

### Test in the ABAP Environment SAP Fiori Launchpad

**Import Software Components**

Before testing new developments in a software component in the test system, as an add-on admin, you have to import the latest changes from the remote repository. After you have cloned a software component into the test system TST, you can import the latest changes by pulling the software component in the *Manage Software Components* app. See [How to Pull Software Components](../50_administration_and_ops/how-to-pull-software-components-90b9b9d.md).

**Create and Assign Business Roles**

To test the developed business services, as a test user, create business roles from the role templates in the test system and assign them to the test user. See [Maintain Business Roles](../50_administration_and_ops/maintain-business-roles-8980ad0.md).

**Create Spaces and Pages for Business Roles**

To enable navigation to custom UIs via tiles, enable launchpad spaces and pages. Add spaces to the relevant business roles and add the needed SAP Fiori launchpad tiles to those spaces. Finally, enable spaces for business users in the system launchpad settings. See [How to Create Spaces and Pages for a Business Role](../50_administration_and_ops/how-to-create-spaces-and-pages-for-a-business-role-18cdb97.md).

**Create Communication Arrangements**

To test inbound and outbound communication, create communication arrangements in the test system TST based on the implemented communication scenarios. See [How to Create a Communication Arrangement](../50_administration_and_ops/how-to-create-a-communication-arrangement-a0771f6.md).

> ### Note:  
> Depending on whether you want to use an authentication method for outbound communication that requires a business user context \(Oauth2 SAML Bearer Assertion, Oauth2 User Token Exchange, JWT Principal Propagation\), you need to configure a destination in a communication arrangement instead of maintaining credentials by using an outbound communication user. See [Supported Protocols and Authentication Methods](supported-protocols-and-authentication-methods-437e9d4.md) and [Create a Destination](create-a-destination-3fa7934.md).

You can integrate the test system TST with on-premise systems. See [Integrating On-Premise Systems](integrating-on-premise-systems-c95327f.md).

In the subaccount of test system TST, the subaccount for testing, you can assign the Cloud Connector administrator role collection to the Cloud Connector administrator user to operate the data transmission tunnels used by the Cloud Connector. See [Role Collections and Roles in Global Accounts, Directories, and Subaccounts \[Feature Set B\]](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/0039cf082d3d43eba9200fe15647922a.html).

**Create Business Configuration**

As a test user, you can adjust business configuration objects in the *Maintain Business Configurations* app to change and influence the system behavior. See [Maintain Business Configurations App](../50_administration_and_ops/maintain-business-configurations-app-76384d8.md).



**Configure Key User Extensibility**

Key user extensibility that is enabled in the SaaS solution can be configured and consumed in test systems.

> ### Note:  
> Key user extensibility provided in a SaaS solution can only be configured in tenants of particular types, for testing purposes in tenants of type Partner Test.
> 
> These tenant types are provisioned in non-development systems, such as test system TST or quality assurance system QAS, where development is not allowed \(`is_development_allowed = false`\). The tenants are created independently from a subscription to the SaaS solution by using the *Landscape Portal* application. See [Use Test Tenants](use-test-tenants-dd7d8e8.md).

As a test user in a Partner Test tenant \(client \>= 200\), you configure key user extensibility in a test system.

-   See [Custom Logic](../50_administration_and_ops/custom-logic-05880c7.md) for guidance on how to use the *Custom Logic* app to create and maintain custom logic for business add-ins \(BAdIs\).
-   See [Configuring Predefined Custom Fields](../50_administration_and_ops/configuring-predefined-custom-fields-0033cbc.md) for guidance on how to configure predefined custom fields to customize applications and their UIs.

 <a name="loiof0b71a1c959842258772c27d292c43b0"/>

<!-- loiof0b71a1c959842258772c27d292c43b0 -->

### Test in the ABAP Test Cockpit

With the ABAP Test Cockpit, you can run a set of checks \(check variants\) on software component or package level. See [ABAP Test Cockpit Configurator](../50_administration_and_ops/abap-test-cockpit-configurator-22c26ff.md) and [ABAP Test Cockpit in the Cloud – What is already possible](https://blogs.sap.com/2020/08/14/abap-test-cockpit-in-the-cloud-what-is-already-possible/).

To schedule a regular execution of ATC checks for a software component in the test system, you can use a CI server and pipeline to automate this process.

For automated ATC check runs, you can reuse the previously described setup of a transport from dev to test using the ABAP environment pipeline.

As a DevOps engineer, configure the ABAP environment pipeline by using a static and preconfigured system. With the pipeline, the following steps are then automated, triggered by the pipeline execution of a Jenkins administrator:

-   Pulling the specified software components/Git repositories
-   Running the configured ABAP Test Cockpit \(ATC\) checks

See [Continuous Testing on SAP BTP ABAP Environment](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentTest/) for further details and [Running ATC Checks on a Static ABAP Environment System](https://github.com/SAP-samples/abap-platform-ci-cd-samples/tree/atc-static) for an example.

To fix and revalidate ATC findings, as a developer user, you can run ATC checks on developed software components locally via ABAP Development Tools in the DEV system.

 <a name="loio25049720bde447e395b3df0bc05e5a50"/>

<!-- loio25049720bde447e395b3df0bc05e5a50 -->

## Build



> ### gCTS Delivery:  
> If you use gCTS instead of add-ons for delivering software components into production systems, the add-on build is not required.
> 
> Instead, you have to import the software component using the *Manage Software Components* app. For the initial import of the software component, clone the software component and pull its main branch into the development and test system. In the production system, clone the software component for an initial import.
> 
> Once it is pulled on the main branch, create a maintenance branch and check it out.
> 
> In the *Branching* tab, you have to create and check out a new branch with the version, for example v1.0.0.
> 
> See [Delivery via Add-On or gCTS](delivery-via-add-on-or-gcts-438d7eb.md#loio438d7ebfdc4a41de82dcdb156f01857e).

As a Jenkins administrator, you have to trigger the add-on build process and execute it in the *03 Build/Assemble* subaccount. An assembly system is created in the *03 Build/Assemble* subaccount. The process is automated using the add-on build pipeline and the existing CI/CD server.

As an add-on admin, you define the add-on product information in the add-on descriptor file. Afterwards, you register the add-on product and global production account with SAP.

During the build process, each of the software components is composed and packaged to be delivered by the AAKaaS. To ensure that the add-on provisioning works correctly, you have to set up an installation test system, in which the assembled add-on is installed.

Once the build and test installation have been completed successfully, an add-on administrator has to confirm the release decision. Now, the add-on is technically available for deployment to the ABAP environment .



<a name="loio25049720bde447e395b3df0bc05e5a50__section_bl3_dv4_drb"/>

## Prerequisites

-   For the add-on build, you have to set up a Jenkins CI/CD server that is provisioned using the Cx server, an S user in SAP One Support Launchpad with user management authorization as well as authorization to create a customer incident for add-on registration. See [https://www.jenkins.io/](https://www.jenkins.io/), [Cx Server](https://www.project-piper.io/infrastructure/overview/#cx-server-recommended), and SAP note [1271482](https://launchpad.support.sap.com/#/notes/1271482).
-   To build the first add-on version, you have to configure the add-on build pipeline. See [Build and Publish Add-on Products on SAP BTP, ABAP Environment](https://www.project-piper.io/scenarios/abapEnvironmentAddons/).

 <a name="loioccf0c1ef30ce4d6aa6e39bb583fb8ba1"/>

<!-- loioccf0c1ef30ce4d6aa6e39bb583fb8ba1 -->

### Set Up Add-On Build



The following section explains how to build the initial version of the add-on product. The result is a delivery of type AOI \(Add-on Installation\) for the initial release 1.0.0 of both the software component and the add-on product.

**Set up a CI server and pipeline for the add-on build**

For the add-on build process, you must use a CI server and pipeline to automate this process.

-   **Add technical platform user to *03 Build/Assemble* space**

    For the add-on assembly, an assembly system in the *03 Build/Assemble* space is created in the global development account.

    To trigger the gCTS import in the assembly system, communication scenario `SAP_COM_0510` is used. See [Test Integration \(SAP\_COM\_0510\)](test-integration-sap-com-0510-b04a9ae.md).

    To trigger the build process in the assembly system, communication scenario `SAP_COM_0582` is used. See [Software Assembly Integration \(SAP\_COM\_0582\)](software-assembly-integration-sap-com-0582-26b8df5.md).

    The credentials for an instance of these scenarios are retrieved by creating a service key in the system. See [Create a Communication Arrangement for Inbound Communication with Service Key Type Basic](create-a-communication-arrangement-for-inbound-communication-with-service-key-type-basic-1cc5a1d.md).

    To do so, as an operator, assign a technical platform user to the global development account as an administrator and as a space developer in the build/assemble space. Later, this user’s credentials are stored in the Jenkins credentials. See [User and Member Management](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/cc1c676b43904066abb2a4838cbd0c37.html).

-   **Add technical platform user to *04 Build/Test* space**

    For the add-on installation test, a test system in the *04 Build/Test* space is created in the global production account.

    To do so, as an operator, assign a technical platform user to the global production account as an administrator and as a space developer in the build/test space. Later, this user’s credentials are stored in the Jenkins credentials. See [Creating New Space Members and Assigning Space Developer Roles to Them](../20_getting_started/creating-new-space-members-and-assigning-space-developer-roles-to-them-967fc4e.md).

-   **Configure pipeline**

    As a DevOps engineer, create the pipeline definition Jenkins file and the configuration file `.pipeline/config.yml` in the Git repository. See [Create Pipeline Configuration](https://www.project-piper.io/stages/introduction/#1-create-pipeline-configuration).


After that, as a Jenkins administrator, create a pipeline pointing to the Jenkins file in the Jenkins server. See [Build and Publish Add-on Products on SAP BTP, ABAP Environment](https://www.project-piper.io/scenarios/abapEnvironmentAddons/) and [ABAP Platform CI/CD Samples](https://github.com/SAP-samples/abap-platform-ci-cd-samples/tree/addon-build) for more information and an example.

**Create a technical communication user for access to AAKaaS**

As part of the add-on build process, the Add-on Assembly Kit is used. With AAKaaS, the on-premise tooling is now available as a cloud service that is used by the build pipeline.

To access the service that is offered via SAP Support Launchpad, a technical communication user is used. See [2532813](https://launchpad.support.sap.com/#/notes/2532813).

In the *Support User Management* app in SAP ONE Support Launchpad, as an S-user, request a new technical communication user. After the technical communication user has been generated, activate the user.

> ### Note:  
> To create technical communication users in SAP Support Launchpad, you have to assign the user administratorauthorization/function to the logged-on user.
> 
> Make sure that this technical communication user is assigned to the customer number under which the ABAP environment tenants are licensed and for which the development namespace was reserved.

Finally, as a Jenkins administrator, add the credentials of the technical communication user to the Jenkins Credentials store.

See SAP note [2174416](https://launchpad.support.sap.com/#/notes/2174416) for more information on how to create and activate technical communication users.

**Register add-on product/global production account**

The registration of a new add-on product is a manual step. Your add-on product should only be installed in ABAP systems within your global production account. Therefore, the add-on product name and global production account need to be registered with SAP.

As an add-on admin, create an incident using component `BC-CP-ABA`, and provide the following information:

-   Add-on product name = *addonProduct* in `addon.yml` file, e.g. /NAMESPACE/NAME

-   Global production account ID = *Account ID* in section *Global Account Info* on the overview page of your global account, e.g. 151b5fdc-58c1-4a55-95e1-467df2134c5f \(Feature Set A\) or *Global Account Info* on the *Usage Analytics* page of your global account \(Feature Set B\).


This step can be triggered by you or by SAP partner management \(governance process to be negotiated\). As a response to the service request, SAP creates a configuration for the requested add-on product so that the add-on product can be installed in the global account.

 <a name="loio96f9db9e6c784e5a89ede4d038daaa43"/>

<!-- loio96f9db9e6c784e5a89ede4d038daaa43 -->

### Build the First Add-On Version

**Create maintenance branch**

> ### Recommendation:  
> For each release and support package level, as an add-on admin, create a maintenance branch that is used for development of bug fixes and maintenance deliveries. See [Versioning and Branches](versioning-and-branches-8c087bc.md#loio8c087bca40584f9b899282b4ec515753).

In test system TST, create branch ***v1.0.0*** that is based on the main branch.

**Configure addon.yml file**

As add-on admin user, create the `addon.yml` file in the Git repository used for the add-on build pipeline configuration. This file includes metadata of the add-on product that is being built, such as versioning information and the included software component versions.

Maintain a metadata file that defines the add-on version and store it in a Git repository \(`addon.yml`\).

```
---
addonProduct: /NAMESPC/PRODUCTX
addonVersion: 1.2.0
repositories:
  - name: /NAMESPC/COMPONENTA
    branch: v1.2.0
    version: 1.2.0
    commitID: 7d4516e9
  - name: /NAMESPC/COMPONENTB
    branch: v2.0.0
    version: 2.0.0
    commitID: 9f102ffb

```

`addonProduct` must include the reserved development namespace.

`addonVersion` starts with version 1.0.0 for the initial delivery.

The software components, defined in repositories, include the name, branch, and software component version to be used for the add-on build.

For the software components in the repositories section of the `addon.yml` file, you have to maintain the following details:

-   name = name of software component including namespace
-   branch = name of active maintenance branch, e.g. v1.2.0, can be retrieved from the *Manage Software Components* app
-   version = software component version
-   commitID = short commit ID of changes to be included, can be retrieved from commit history in the *Manage Software Components* app

> ### Tip:  
> For in-depth information about versioning and branches, check out [Versioning and Branches](versioning-and-branches-8c087bc.md#loio8c087bca40584f9b899282b4ec515753).
> 
> To learn how software lifecycle management in the ABAP environment works with software components, see [Basic Concepts and Terms](basic-concepts-and-terms-fb3a076.md). Please follow the best practices on how to define the addon.yml file. See [Add-On Descriptor File](https://www.project-piper.io/scenarios/abapEnvironmentAddons/#add-on-descriptor-file).

**Trigger add-on product build**

As an add-on administrator, trigger the execution of the configured ABAP environment pipeline for the add-on build. During the add-on build, delivery packages corresponding to included software component versions are created. For the add-on product version, a target vector is created and published in test scope. See [Target Vector](https://www.project-piper.io/scenarios/abapEnvironmentAddons/#target-vector).

![](images/Pipeline_add-on_build_d36cfe1.png)

> ### Tip:  
> For in-depth information about the ABAP environment pipeline, check out [ABAP Environment Pipeline](concepts-9482e7e.md#loio2398b874f7c5445db188b780ff0cef89).

**Trigger add-on product test**

Based on the target vector published in the build stage, the integration tests stage of the ABAP environment pipeline creates the add-on installation test system ATI. After the system and the add-on have been provisioned successfully, a provisioning mail is sent to the system administrator and the pipeline stage can be confirmed by the add-on administrator.

Use add-on installation test system ATI to confirm the successful add-on installation before the new add-on version is published.

You can also use add-on installation test system ATI for additional tests, similar to the steps described in [Test in the ABAP Environment SAP Fiori Launchpad](develop-test-build-3bf575a.md#loio8c5b4d76a05b4bed8df01937f4d8d487). For testing in a consumer-like environment, you can create tenants of type Partner Test using the Landscape Portal application. See [Use Test Tenants](use-test-tenants-dd7d8e8.md).

**Trigger add-on product release**

Finally, the previously created target vector for the new add-on product version is published in production scope after the release decision is confirmed in the *Confirm* stage by the add-on administrator.

After a successful build, all ABAP systems used are deprovisioned.

The add-on is now technically available for deployment to the ABAP environment.

> ### Note:  
> If you need support or experience issues during the add-on build, please refer to [Troubleshooting](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentAddons/#troubleshooting).

