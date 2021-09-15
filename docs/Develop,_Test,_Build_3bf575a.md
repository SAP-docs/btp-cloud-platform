<!-- loio3bf575a3dc5043f895f8bd411d2a86a1 -->

# Develop, Test, Build

To develop and provide add-ons, you have to set up a suitable system landscape and Cloud Foundry environment account structure.



You need a partner contract to create the account structure. The accounts for the upstream \(add-on development, test, build\) and downstream \(providing add-on as SaaS solution\) parts of the process need to be separated from each other and therefore are handled in dedicated global accounts. We refer to these as global development account and global production account. For more information regarding the development license, see [SAP PartnerEdge Test, Demo & Development Price List](https://partneredge.sap.com/en/library/assets/partnership/sales/order_license/pl_pl_part_price_list.html). To find out more about production licenses, see [SAP PartnerEdge: Resources for OEM Partners](https://partneredge.sap.com/en/partnership/manage/op_resource/oem.html).

> ### Tip:  
> For in-depth information about the system landscape/account model, check out [System Landscape/Account Model](Concepts_9482e7e.md#loio4ca756395fc24e56a42b77632a6bd862).

For the initial add-on delivery, you should create a development and test landscape following the guidelines mentioned in [Concepts](Concepts_9482e7e.md#loio9482e7eef4634cb993a4ae296b2029fa). Once backend and frontend development is completed, you can test the add-on implementation in a persistent test system. Upon successful completion of this step, set up a CI/CD server along with a Jenkins pipeline to execute the add-on build allowing for an automated and efficient assembly. This automated pipeline can then be reused transforming all upgrade and update activities into a straightforward process.

Once the add-on build/assembly is finished, you can release the add-on to the productive global account. First, the add-on build is installed in a test system in the production account to verify that it works correctly. If successful, you can provide the add-on to customers. See [SAP Business Technology Platform](SAP_Business_Technology_Platform_6a2c1ab.md), [ABAP Environment Learning Journey](https://help.sap.com/doc/221f8f84afef43d29ad37ef2af0c4adf/HP_2.0/en-US/49047e7668844d419ccee567923a475e.html), and [ABAP Environment Community](https://community.sap.com/topics/cloud-platform-abap-environment). Also consider starting out with a trial account to get hands-on development experience with the ABAP environment as described in [Blog: Trial for ABAP in SAP Business Technology Platform](https://blogs.sap.com/2019/09/28/its-trialtime-for-abap-in-sap-cloud-platform/) and [Getting Started with a Trial Account in the ABAP Environment](Getting_Started_with_a_Trial_Account_in_the_ABAP_Environment_720c423.md).

> ### gCTS:  
> Besides using add-ons for delivering software components to production systems, gCTS can be used as an alternative approach. It is used for transporting software components between different ABAP systems.

 <a name="loio3bf575a3dc5043f895f8bd411d2a86a1 loio4338854e3133407abb47d3a281dbd1e1__loio4338854e3133407abb47d3a281dbd1e1"/>

<!-- loio4338854e3133407abb47d3a281dbd1e1 -->

# Prepare



Before you can proceed with the development of the add-on, you have to perform several preliminary steps.

-   Register the development namespaces before any system is set up. To start the actual add-on development process, you have to set up the system landscape and global account structure for development. For pipeline automation, set up a CI/CD server, in this case a Jenkins server.
-   Create one or more software components that make up the add-on in the namespaces registered for you. In this scenario, namespaces are required for both the add-on product name and software components. You can register these namespaces with the development namespace/license keys tool.
-   Purchase the SAP BTP, Cloud Foundry environment entitlements necessary for the account setup, which includes the service ABAP environment for development. The ABAP environment \(service plan `saas_oem`\), Application runtime, SaaS provisioning, ABAP Solution service as well as the Landscape Portal are used for providing the SaaS app.

    > ### Recommendation:  
    > We recommend using the browser-based IDE SAP Business Application Studio for UI development. In this case, additional configuration is required to enable developers to use this service.


Once you’ve completed these steps, you can start developing an add-on.

 <a name="loio3bf575a3dc5043f895f8bd411d2a86a1 loio4338854e3133407abb47d3a281dbd1e1 loiocc5a3c6f78cf4889960c314dd09a5060__loiocc5a3c6f78cf4889960c314dd09a5060"/>

<!-- loiocc5a3c6f78cf4889960c314dd09a5060 -->

# Register a Namespace

Using a reserved namespace for add-on development and build is necessary for a unique add-on product and software component name.

> ### Note:  
> You need to register a namespace before the first ABAP system is provisioned. For namespaces that are registered after the system provisioning, create an incident using component `BC-CP-ABA`.

As an S-user with authorization *Reserve Namespaces*, you have to reserve a namespace for your partner customer ID to register a namespace with the *Namespace* app. See [https://launchpad.support.sap.com/\#/namespaces](https://launchpad.support.sap.com/#/namespaces).

Due to length restrictions of some objects, namespaces should have 5–8 characters. See SAP note [105132](https://launchpad.support.sap.com/#/notes/) and [395083](https://launchpad.support.sap.com/#/notes/).

> ### Note:  
> If you need a new S-user, get in touch with a user administrator.

 <a name="loio3bf575a3dc5043f895f8bd411d2a86a1 loio4338854e3133407abb47d3a281dbd1e1 loio9f2150f2b15e414aacd46c1723ce48fb__loio9f2150f2b15e414aacd46c1723ce48fb"/>

<!-- loio9f2150f2b15e414aacd46c1723ce48fb -->

# Set Up a Development Account

As a SaaS solution operator, you have to configure the development account.

![](images/Prepare_a_Development_Account_e29111f.png)

The add-on development is separated from providing the add-on for consumption as a SaaS solution.

> ### Recommendation:  
> We recommend the following subaccount structure:
> 
> -   In the *01 Develop* subaccount, add-on development is performed in a permanent development system. See [Development in the ABAP Environment](Development_in_the_ABAP_Environment_31367ef.md).
> -   In the *02 Test* subaccount, the developed software components are tested after a successful import into a permanent test system.
> -   In the *03 Build/Assemble* subaccount, the add-on package assembly is performed in a transient assembly system that is created and deleted automatically by the build pipeline.

> ### gCTS:  
> If you use gCTS instead of add-ons for delivering software components to production systems, the setup and usage of a *03 Build/Assemble* \(used for the add-on assembly\) subaccount is redundant.

You should configure a Cloud Foundry space in each subaccount. Dividing the development, testing, and assembling activities into different subaccounts allows for maximum flexibility. For instance, you may want to use different identity providers or consume different connectivity services during testing and development.

The ABAP systems that you use for development, testing, and add-on assembly are of type `abap/standard` and made available via entitlements. These service entitlements must be assigned by an administrator to different subaccounts, according to the following structure:


<table>
<tr>
<th>

Global Account



</th>
<th>

Subaccount



</th>
<th>

Space



</th>
<th>

Services



</th>
</tr>
<tr>
<td>

Partner Saas on ABAP \(Dev\)



</td>
<td>

01 Develop



</td>
<td>

Develop



</td>
<td>

1x abap/standard

abap/hana\_compute\_unit \(standard: 4\)

abap/abap\_compute\_unit \(standard: 1\)



</td>
</tr>
<tr>
<td>

Partner Saas on ABAP \(Dev\)



</td>
<td>

02 Test



</td>
<td>

Test



</td>
<td>

1x abap/standard

abap/hana\_compute\_unit \(standard: 4\)

abap/abap\_compute\_unit \(standard: 1\)



</td>
</tr>
<tr>
<td>

Partner Saas on ABAP \(Dev\)



</td>
<td>

03 Build/Assemble



</td>
<td>

Build/Assemble



</td>
<td>

1x abap/standard

abap/hana\_compute\_unit \(standard: 4\)

abap/abap\_compute\_unit \(standard: 1\)



</td>
</tr>
</table>

Additionally, the following entitlements for SaaS application subscriptions are required:

-   SAP Business Application Studio for UI development. See [SAP Business Application Studio](SAP_Business_Application_Studio_c736960.md).
-   Web access for ABAP for access to systems during development phase. See [Subscribing to the Web Access for ABAP](Subscribing_to_the_Web_Access_for_ABAP_98928b0.md).
-   Landscape Portal for provider support access. See [Landscape Portal](Landscape_Portal_5eb70fb.md).

If you want to integrate an existing corporate identity provider in the subaccounts of the global development account for authentication/authorization, see [Trust and Federation with Identity Providers](Trust_and_Federation_with_Identity_Providers_cb1bc8f.md). To restrict access based on certain criteria such as the IP address, you need to use the [Identity Authentication Service](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/d17a116432d24470930ebea41977a888.html).

> ### Tip:  
> For in-depth information about the system landscape/account model, check out [System Landscape/Account Model](Concepts_9482e7e.md#loio4ca756395fc24e56a42b77632a6bd862).

 <a name="loio3bf575a3dc5043f895f8bd411d2a86a1 loio4338854e3133407abb47d3a281dbd1e1 loio2e7b4b631e814de1b8fe3959af4105bc__loio2e7b4b631e814de1b8fe3959af4105bc"/>

<!-- loio2e7b4b631e814de1b8fe3959af4105bc -->

# Set Up a Production Account

As a SaaS solution operator, you have to configure the production account.

![](images/Prepare_a_Production_Account_ad3698a.png)

The finished add-on product is provisioned to customers in a dedicated global production account.

> ### Recommendation:  
> We recommend the following subaccount structure:
> 
> -   In the *04 Build/Test* subaccount, the add-on build is installed and tested again
> -   In the *05 Provide* subaccount, the add-on product is provided to customers

> ### gCTS:  
> If you use gCTS instead of add-ons for delivering software components to production systems, the setup and usage of a *04 Build/Test* \(used for add-on installation test\) subaccount is redundant.
> 
> Additionally, considering the availability of software components only in the same global accounts, you have to create the production systems as well as development and test systems in the same global account \(global development account = global production account\).

In the provider context, the `ABAP environment (saas_oem)` service plan is used.

> ### gCTS:  
> In the provider subaccount, an ABAP instance of service plan type `abap/standard` instead of `abap/saas_oem` is used.

These provider ABAP instances allow flexible sizing, multitenancy, and the possibility to install an add-on product during provisioning.

For the provisioning of these ABAP systems of service plan `saas_oem`, another set of services comes into play: With the ABAP Solution Provider and the saas-registry service, you can provide your add-ons as SaaS solution offerings. See [Define Your ABAP Solution](Define_Your_ABAP_Solution_1697387.md).

Note that these service entitlements must be assigned to different subaccounts, according to the following structure:


<table>
<tr>
<th>

Global Account



</th>
<th>

Subaccount



</th>
<th>

Space



</th>
<th>

Services



</th>
</tr>
<tr>
<td>

Partner Saas on ABAP \(Provider\)



</td>
<td>

04 Build/Test



</td>
<td>

Build/Test



</td>
<td>

abap/saas\_oem

abap/hana\_compute\_unit \(standard: 4\)

abap/abap\_compute\_unit \(standard: 1\)



</td>
</tr>
<tr>
<td>

Partner Saas on ABAP \(Provider\)



</td>
<td>

05 Provide



</td>
<td>

Provide



</td>
<td>

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

If you want to integrate an existing corporate identity provider in the subaccounts of the global production account for authentication/authorization, see [Trust and Federation with Identity Providers](Trust_and_Federation_with_Identity_Providers_cb1bc8f.md). To restrict access based on certain criteria such as the IP address, you need to use the [Identity Authentication Service](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/d17a116432d24470930ebea41977a888.html).

> ### Tip:  
> For in-depth information about the system landscape/account model, check out [System Landscape/Account Model](Concepts_9482e7e.md#loio4ca756395fc24e56a42b77632a6bd862).

 <a name="loio3bf575a3dc5043f895f8bd411d2a86a1 loio4338854e3133407abb47d3a281dbd1e1 loio17aa433273c24bd2b949c297513851fe__loio17aa433273c24bd2b949c297513851fe"/>

<!-- loio17aa433273c24bd2b949c297513851fe -->

# Create ABAP Instances

As a SaaS solution operator, you have to create ABAP instances.

For development and testing purposes, one system is provisioned in each of the development and test subaccounts.


<table>
<tr>
<th>

Global Account



</th>
<th>

Subaccount



</th>
<th>

Space



</th>
<th>

ABAP Instances



</th>
</tr>
<tr>
<td>

Global Development Account



</td>
<td>

01 Develop



</td>
<td>

Develop



</td>
<td>

Create an ABAP instance \(abap/standard\)

Set parameter `is_development_allowed = true`



</td>
</tr>
<tr>
<td>

Global Development Account



</td>
<td>

02 Test



</td>
<td>

Test



</td>
<td>

Create an ABAP instance \(abap/standard\)

Set parameter `is_development_allowed = false`



</td>
</tr>
</table>

> ### Note:  
> You don't have to create an ABAP instance \(abap/standard,`is_development_allowed = false`\) in the *03 Build/Assemble* account because this instance is created automatically during the add-on build process .

In the *03 Build/Assemble* account, assembly systems are provisioned by the add-on build pipeline. These systems are used to import the desired software components that are then packaged for add-on delivery \(see [Software Assembly Integration \(SAP\_COM\_0582\)](Software_Assembly_Integration_(SAP_COM_0582)_26b8df5.md)\). As an operator, you don’t have to provision these systems manually as we recommend using transient systems for the build process. But sufficient entitlement/quota for abap/standard services need to be available.

Use service parameter `is_development_allowed` to differentiate between development and test systems. The test and assembly systems must be productive to avoid changes being made to the add-on outside of the development system.

For more information on how to get started with your customer account, see [Getting Started with a Customer Account in the ABAP Environment](Getting_Started_with_a_Customer_Account_in_the_ABAP_Environment_e34a329.md) and [Creating an ABAP System](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/50b32f144e184154987a06e4b55ce447.html).

In the *04 Build/Test* subaccount of the global production account, an add-on installation test system is automatically created. This ABAP environment service instance of plan `saas_oem` is provisioned with parameter `is_development_allowed = false`.

Subscribe to the Web Access for ABAP to gain access to the SAP Fiori launchpad in all subaccounts of the global production account.

 <a name="loio3bf575a3dc5043f895f8bd411d2a86a1 loio4338854e3133407abb47d3a281dbd1e1 loio3f03dfe2f21b471ab98abc6f208c3762__loio3f03dfe2f21b471ab98abc6f208c3762"/>

<!-- loio3f03dfe2f21b471ab98abc6f208c3762 -->

# Set Up UI Development

As a SaaS solution operator, you have to set up SAP Business Application Studio for development.

As a developer user, you can then create an SAP Fiori dev space and generate UI projects.

> ### Recommendation:  
> For frontend development, we recommend using SAP Business Application Studio. See [Develop an SAP Fiori Application UI and Deploy it to ABAP Using SAP Business Application Studio](Develop_an_SAP_Fiori_Application_UI_and_Deploy_it_to_ABAP_Using_SAP_Business_Application_Studio_eaaeba4.md).

 <a name="loio3bf575a3dc5043f895f8bd411d2a86a1 loio4338854e3133407abb47d3a281dbd1e1 loiobf557544f90f4bc88911c4865ec78207__loiobf557544f90f4bc88911c4865ec78207"/>

<!-- loiobf557544f90f4bc88911c4865ec78207 -->

# Set Up Transport from Development to Test System via gCTS

You can set up the transport of your development from a development to a test system either manually with the *Manage Software Components* app or in an automated fashion.

**Manually import into test system via gCTS**

As an add-on admin user, you can pull the latest released changes of a software component to the test system by using the main branch. You can test these changes in the test system independent from ongoing development. See [How to Pull Software Component](How_to_Pull_Software_Component_90b9b9d.md) and [ABAP Lifecycle Management](ABAP_Lifecycle_Management_5c7b17d.md).

**\[Optional\] Set up a CI server and pipeline for automatic testing**

To schedule a regular import of new changes into the test system, you can use a CI server and pipeline to automate this process.

![](images/Pipeline_dev_to_test_8d52073.png)

As a developer user, you can configure the ABAP environment pipeline for an automated DEV to TST transport. To do so, a static and preconfigured system is used. See [ABAP Environment Pipeline](https://sap.github.io/jenkins-library/pipelines/abapEnvironment/introduction/).With the pipeline, the pulling of specified software components/Git repositories is automated, triggered by the pipeline execution of a Jenkins administrator. See [Continuous Testing on SAP BTP ABAP Environment](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentTest/) and [Running ATC Checks on a Static ABAP Environment System](https://github.com/SAP-samples/abap-platform-ci-cd-samples/tree/atc-static) for further details and an example.

 <a name="loio3bf575a3dc5043f895f8bd411d2a86a1 loio4338854e3133407abb47d3a281dbd1e1 loio89a353151e534380a03b2a572a227731__loio89a353151e534380a03b2a572a227731"/>

<!-- loio89a353151e534380a03b2a572a227731 -->

# Set Up Add-On Development

To transport new developments from system to system, the add-on development is structured by software components. Software components are independent development containers.

To create a new software component for add-on development, as an add-on admin user, use the *Manage Software Components* app and create a new component of type `Development`. The name of the software component begins with a namespace that was activated in the development system. By default, all namespaces of the global account owner are enabled in the systems. See [How to Create Software Components](How_to_Create_Software_Components_67e2f2e.md).

Clone the main branch of the software component to the development and test system.

Software components in the development and test system should always stay on the main branch. If you want to work on maintenance branches to develop bug fixes and other maintenance deliveries, create a dedicated hotfix development and test system \(correction codeline\).

> ### Tip:  
> For in-depth information about versioning and branches, check out [Versioning and Branches](Concepts_9482e7e.md#loio8c087bca40584f9b899282b4ec515753).

 <a name="loio3bf575a3dc5043f895f8bd411d2a86a1 loio9464e3af139d4e0581cb4e819886b0c8__loio9464e3af139d4e0581cb4e819886b0c8"/>

<!-- loio9464e3af139d4e0581cb4e819886b0c8 -->

# Develop



Both the initial implementation and any further development of the add-on are performed in the development system of the development subaccount.

You can use various SAP technologies at this point, such as the ABAP RESTful application programming model \(RAP\) for modeling and implementing business objects and the browser-based IDE SAP Business Application Studio for developing SAP Fiori UIs. Depending on the business use case, some additional development effort may be necessary to implement suitable launchpad content, Identity & Access Management artifacts, or communication management artifacts.

Once you’ve completed these development activities, the solution is ready to be tested in a suitable test system.

 <a name="loio3bf575a3dc5043f895f8bd411d2a86a1 loio9464e3af139d4e0581cb4e819886b0c8 loiofa5af4ecdf90496b8eec54fe0e22150c__loiofa5af4ecdf90496b8eec54fe0e22150c"/>

<!-- loiofa5af4ecdf90496b8eec54fe0e22150c -->

# ABAP Development

As a developer user, implement your custom business services with the ABAP RESTful application programming model. See [ABAP RESTful Application Programming Model](https://help.sap.com/viewer/923180ddb98240829d935862025004d6/Cloud/en-US/289477a81eec4d4e84c0302fb6835035.html). Maintain business catalogs \(see [Identity and Access Management \(IAM\) Guide](Identity_and_Access_Management_(IAM)_Guide_5b62901.md)\) and communication scenarios \(see [Overview of Communication Management](Overview_of_Communication_Management_5b8ff39.md)\) to expose services to business users and communication users.

**Connectivity**

As part of the ABAP development, you can consume external services in the implementation of an add-on. These services can be based on the following protocols:

-   [SOAP Communication via Destination Service](SOAP_Communication_via_Destination_Service_72bb6b5.md)
-   [HTTP Communication via Destination Service](HTTP_Communication_via_Destination_Service_dee3a93.md)
-   [RFC Communication via Destination Service](RFC_Communication_via_Destination_Service_b4eaa0a.md)

See [Developing External Service Consumption \(Outbound Communication\)](Developing_External_Service_Consumption_(Outbound_Communication)_f871712.md).

The destination service is used to provide credentials and store endpoint information for these protocols. See [Create a Destination](Create_a_Destination_3fa7934.md).

As a SaaS solution operator, you can maintain destinations on subaccount level in the consumer subaccount. For each consumer, use a different destination endpoint. A typical scenario would be a side-by-side extension scenario where the SaaS solution makes use of services in an S/4HANA system of the consumer. See [SAP Extensibility Explorer for SAP S/4HANA Cloud](https://extensibilityexplorer.cfapps.eu10.hana.ondemand.com/ExtensibilityExplorer/).

Aside from consuming web services from the internet, you can also integrate the SaaS solution with on-premise systems. See [Integrating On-Premise Systems](Integrating_On-Premise_Systems_c95327f.md).

As a Cloud Connector administrator, you have to maintain Cloud Connector connectivity by connecting the Cloud Connector to the consumer subaccount.

> ### Restriction:  
> The ABAP environment supports only one communication configuration layer intended to be used by the consumer. It’s currently not possible to enforce a communication configuration exclusively managed by the service provider within the consumer tenant.

> ### Note:  
> Inbound RFC isn’t supported for inbound communication.

**Multitenancy**

With the ABAP environment, you can build multitenancy-enabled SaaS solutions. To do so, the add-on implementation has to follow certain guidelines and best practices. See [Development Guideline to Enable Multitenancy of Products Built on the ABAP Environment](Development_Guideline_to_Enable_Multitenancy_of_Products_Built_on_the_ABAP_Environment_9d994c8.md).

> ### Recommendation:  
> If the add-on implementation is aligned with the development guideline for multitenancy, we recommend configuring your solution by setting `tenant_mode = multi` so that the same ABAP service instance is used for multiple consumers.

> ### Tip:  
> For in-depth information about multitenancy, check out [Multitenancy](Concepts_9482e7e.md#loioc8730736a52645b49ca76c08214bf181).

 <a name="loio3bf575a3dc5043f895f8bd411d2a86a1 loio9464e3af139d4e0581cb4e819886b0c8 loiof3be8246edc74be59c10779443f67793__loiof3be8246edc74be59c10779443f67793"/>

<!-- loiof3be8246edc74be59c10779443f67793 -->

# UI Development

SAP Fiori applications are developed in SAP Business Application Studio on top of business services in the ABAP development system and then deployed to the ABAP development system to be part of the same software component as backend artifacts.

As a developer user, once business services are implemented as UI services, you can create SAP Fiori elements apps using SAP Business Application Studio. See [Develop an SAP Fiori Application UI and Deploy it to ABAP Using SAP Business Application Studio](Develop_an_SAP_Fiori_Application_UI_and_Deploy_it_to_ABAP_Using_SAP_Business_Application_Studio_eaaeba4.md).

> ### Note:  
> Launchpad spaces and pages offer more flexibility to influence the launchpad layout for specific user groups. As of now, there is no possibility to create templates for a specific spaces/pages setup and to deliver this as part of an add-on. Therefore, for every consumer, this needs to be configured manually.

> ### Recommendation:  
> To simplify this process, we recommend structuring the IAM business catalogs that include IAM apps for the UI according to business roles by using business role templates. See [Providing Access to the SAP Fiori Application](Providing_Access_to_the_SAP_Fiori_Application_b569abb.md).

 <a name="loio3bf575a3dc5043f895f8bd411d2a86a1 loio9464e3af139d4e0581cb4e819886b0c8 loiof438645cb5664399a6b21f8d9bd3d004__loiof438645cb5664399a6b21f8d9bd3d004"/>

<!-- loiof438645cb5664399a6b21f8d9bd3d004 -->

# \(Optional\) Code Migration from On-Premise

Optionally, you can migrate existing custom ABAP code for add-on development purposes. This custom code migration process analyzes your existing code for cloud-readiness. See [How to Check your Custom ABAP Code for SAP BTP ABAP Environment](https://blogs.sap.com/2018/10/02/how-to-check-your-custom-abap-code-for-sap-cloud-platform-abap-environment/).

After adapting the code and making necessary changes, you can migrate the code via abapGit. See [How to Bring your ABAP Custom Code to SAP BTP ABAP Environment](https://blogs.sap.com/2019/11/11/how-to-bring-your-abap-custom-code-to-sap-cloud-platform-abap-environment/).

 <a name="loio3bf575a3dc5043f895f8bd411d2a86a1 loio023cf9d301b1479484e70b17cd5cf587__loio023cf9d301b1479484e70b17cd5cf587"/>

<!-- loio023cf9d301b1479484e70b17cd5cf587 -->

# Test



Once development has been completed, you can test the solution in the test subaccount that you have previously set up. The software components that make up the solution are imported into a provisioned test system, while any additionally required configuration has to be carried out by you. This may entail creating suitable business roles, maintaining communication arrangements, or other administrative tasks performed via the SAP Fiori launchpad of your ABAP system.

You can also use a CI server and a Jenkins pipeline to automate the test process. This allows you to schedule regular tests and to be notified as soon as issues arise within the solution.

If the solution is successfully tested and works correctly, you can proceed with the add-on build.

 <a name="loio3bf575a3dc5043f895f8bd411d2a86a1 loio023cf9d301b1479484e70b17cd5cf587 loio8c5b4d76a05b4bed8df01937f4d8d487__loio8c5b4d76a05b4bed8df01937f4d8d487"/>

<!-- loio8c5b4d76a05b4bed8df01937f4d8d487 -->

# Test in Cloud System Using SAP BTP Cockpit

**Import the ABAP service and UI into the test system**

Before testing new developments in a software component in the test system, as an add-on admin, you have to import the latest changes from the remote repository with a checked out main branch.

**Create a role and assign it to the test user, execute the service and the UI**

To test the developed business services, as a test user, create business roles from the role templates in the test system and assign them to the test user. See [Maintain Business Roles](Maintain_Business_Roles_8980ad0.md).

To enable navigation to custom UIs via tiles, enable launchpad spaces and pages. Add spaces to the relevant business roles and add the needed SAP Fiori launchpad tiles to those spaces. Finally, enable spaces for business users in the system launchpad settings. See [How to Create Spaces and Pages for a Business Role](How_to_Create_Spaces_and_Pages_for_a_Business_Role_18cdb97.md).

To test developed technical services, create communication arrangements in the test system with dedicated technical communication users. See [How to Create a Communication Arrangement](How_to_Create_a_Communication_Arrangement_a0771f6.md).

 <a name="loio3bf575a3dc5043f895f8bd411d2a86a1 loio023cf9d301b1479484e70b17cd5cf587 loiof0b71a1c959842258772c27d292c43b0__loiof0b71a1c959842258772c27d292c43b0"/>

<!-- loiof0b71a1c959842258772c27d292c43b0 -->

# Use ABAP Test Cockpit

With the ABAP Test Cockpit, you can run a set of checks \(check variants\) on software component or package level. See [ABAP Test Cockpit Configurator](ABAP_Test_Cockpit_Configurator_22c26ff.md) and [ABAP Test Cockpit in the Cloud – What is already possible](https://blogs.sap.com/2020/08/14/abap-test-cockpit-in-the-cloud-what-is-already-possible/).

**\[Optional:\] Run ATC checks via CI/CD pipeline**

To schedule a regular execution of ATC checks for a software component in the test system, you can use a CI server and pipeline to automate this process.

For automated ATC check runs, you can reuse the previously described setup of a transport from dev to test using the ABAP environment pipeline.

As a DevOps engineer, configure the ABAP environment pipeline by using a static and preconfigured system. With the pipeline, the following steps are then automated, triggered by the pipeline execution of a Jenkins administrator:

-   Pulling the specified software components/Git repositories
-   Running the configured ABAP Test Cockpit \(ATC\) checks

See [Continuous Testing on SAP BTP ABAP Environment](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentTest/) for further details and [Running ATC Checks on a Static ABAP Environment System](https://github.com/SAP-samples/abap-platform-ci-cd-samples/tree/atc-static) for an example.

To fix and revalidate ATC findings, you, as a developer user, can run ATC checks on developed software components locally via ABAP Development Tools in the DEV system.

The solution can now be tested.

