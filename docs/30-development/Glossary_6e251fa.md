<!-- loio6e251fa1b63f4ac48ac12c9d7201fae1 -->

# Glossary




<table>
<tr>
<td>

Add-on Assembly Kit as a Service \(AAKaaS\)



</td>
<td>

The Add-on Assembly Kit as a Service registers and publishes the software product. It is accessible via APIs with a technical communication user.



</td>
</tr>
<tr>
<td>

ABAP environment pipeline



</td>
<td>

The ABAP environment pipeline enables continuous integration for the ABAP environment. The pipeline contains several stages and supports different scenarios. See [ABAP Environment Pipeline](https://sap.github.io/jenkins-library/pipelines/abapEnvironment/introduction/).



</td>
</tr>
<tr>
<td>

ABAP System



</td>
<td>

The ABAP environment service \(abap/standard\) is used to create development and test systems. See [Creating an ABAP System](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/50b32f144e184154987a06e4b55ce447.html).



</td>
</tr>
<tr>
<td>

ABAP System \(SaaS, OEM\)



</td>
<td>

The ABAP environment \(abap/saas-oem\) service is used to create the add-on installation test system and production systems, where a specific add-on product needs to be installed in the system.



</td>
</tr>
<tr>
<td>

Add-on build pipeline



</td>
<td>

A pipeline configured for the add-on build scenario of the ABAP environment pipeline. See [Build and Publish Add-on Products on SAP BTP ABAP Environment](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentAddons/).



</td>
</tr>
<tr>
<td>

Add-on descriptor



</td>
<td>

The build process is controlled by an add-on descriptor file called `addon.yml`. This file must be created manually and stored in the Git repository of the pipeline. It must contain information about the software product version to be delivered and the containing software component versions. See [Add-On Descriptor File](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentAddons/#add-on-descriptor-file).



</td>
</tr>
<tr>
<td>

Add-on installation test system



</td>
<td>

To verify that the delivery packages included in the add-on product version being built are installable, a target vector is published in "test" scope. In the integration tests stage, an ABAP system of service plan `saas_oem` is created. This ABAP OEM service allows you to install a specific add-on product version into an ABAP system that is provisioned.



</td>
</tr>
<tr>
<td>

Add-on product version \(software product version\)



</td>
<td>

To install and maintain ABAP software, software product versions are used. A software product version is a bundle of software component versions made available at the same time for implementing a well-defined scope of functionality. See [Software Product Version](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentAddons/#software-product-version).



</td>
</tr>
<tr>
<td>

ABAP Solution \(Provider\)



</td>
<td>

The ABAP Solution service maintains ABAP systems and tenants to provide an add-on product as a SaaS solution.



</td>
</tr>
<tr>
<td>

Assembly System



</td>
<td>

The ABAP system responsible for the add-on assembly.

It is created during the pipeline and eventually deleted. All actions related to the ABAP source code are executed on this system, e.g. running checks with the ABAP Test Cockpit \(ATC\) or the physical build of the software components.



</td>
</tr>
<tr>
<td>

ABAP Test Cockpit \(ATC\)



</td>
<td>

ATC checks can be executed using `abapEnvironmentRunATCCheck`. The step can receive software components or packages configured in a YML file. The results are returned in checkstlye format. With the use of a pipeline extension, you can configure quality gates. See [https://sap.github.io/jenkins-library/pipelines/abapEnvironment/configuration/](https://sap.github.io/jenkins-library/pipelines/abapEnvironment/configuration/) and [ABAP Test Cockpit Configurator](../50-administration-and-ops/ABAP_Test_Cockpit_Configurator_22c26ff.md).



</td>
</tr>
<tr>
<td>

Branch



</td>
<td>

Git repository branches can be used to control the flow of changes through the test and production landscape. They separate changes from each other, which shall or might not be delivered together \(i.e. development vs. correction, feature A vs. feature B\). A branch is created on the current state of another branch, the parent branch, and reflected by a new copy of all included objects. Depending on which branch is supposed to be changed, the corresponding copy is worked on.



</td>
</tr>
<tr>
<td>

Business role



</td>
<td>

A business role provides users with authorizations to access apps.



</td>
</tr>
<tr>
<td>

CI/CD server



</td>
<td>

The pipeline for building ABAP add-ons has been created specifically for Jenkins. Therefore, a Jenkins server is required. The project "Piper" provides a Jenkins image, which already includes the necessary configurations. Note that you can also configure an existing server.



</td>
</tr>
<tr>
<td>

 Cloud Foundry environment



</td>
<td>

The Cloud Foundry environment enables you to develop new business applications and business services, supporting multiple runtimes, programming languages, libraries, and services. See [Cloud Foundry Environment](../10-concepts/Cloud_Foundry_Environment_9c7092c.md#loio9c7092c7b7ae4d49bc8ae35fdd0e0b18).



</td>
</tr>
<tr>
<td>

Communication arrangement



</td>
<td>

A communication arrangement describes a communication scenario with a remote system during configuration time. It provides the necessary metadata for service configuration. See [Communication Arrangement](Communication_Arrangement_201de48.md).



</td>
</tr>
<tr>
<td>

Communication scenario



</td>
<td>

A communication scenario in the ABAP environment is a design time description of how two communication partners communicate with each other.

It provides technical information, such as the used inbound and outbound services and their service type, for example OData or SOAP, and the number of allowed communication arrangement instances. See [Communication Scenario](Communication_Scenario_7ea7276.md).



</td>
</tr>
<tr>
<td>

Consumer



</td>
<td>

The service consumer is an end-customer of the service provider and has access to the SaaS application in a specific tenant



</td>
</tr>
<tr>
<td>

Correction codeline



</td>
<td>

Corrections need to run in parallel to development and on a released state. This is performed in the correction codeline and on a maintenance branch.



</td>
</tr>
<tr>
<td>

Cx server



</td>
<td>

Cx server is a life-cycle management tool to bootstrap a preconfigured Jenkins instance within minutes on your own \(virtual\) server, that uses Docker images. To avoid manual startup of the Docker image with all the required parameters and sidecar images, this command line tool automates the bootstrapping. See [Cx Server](https://sap.github.io/jenkins-library/infrastructure/overview/#cx-server-recommended).



</td>
</tr>
<tr>
<td>

Destination service



</td>
<td>

The Destination service lets you find the destination information that is required to access a remote service or system from your Cloud Foundry application. See [Consuming the Destination Service](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/7e306250e08340f89d6c103e28840f30.html).



</td>
</tr>
<tr>
<td>

Development codeline



</td>
<td>

Infinity development \(infinity codeline\) is done based on the latest software component state in the main branch.



</td>
</tr>
<tr>
<td>

Development namespace



</td>
<td>

Naming conflicts can be avoided through agreements on naming conventions or by carrying out development in separate namespaces. See SAP note [84282](https://launchpad.support.sap.com/#/notes/).



</td>
</tr>
<tr>
<td>

Global account



</td>
<td>

A global account is the realization of a contract you made with SAP. A global account is used to manage subaccounts, members, entitlements, and quotas. You receive entitlements and quotas to use platform resources per global account and then distribute the entitlements and quotas to the subaccount for actual consumption. See [Getting a Global Account](../20-getting-started/Getting_a_Global_Account_d61c281.md#loiod61c2819034b48e68145c45c36acba6e).



</td>
</tr>
<tr>
<td>

 Identity Authentication Service \(IAS\)



</td>
<td>

The Identity Authentication service provides you with controlled cloud-based access to business processes, applications, and data. It simplifies your user experience through authentication mechanisms, single sign-on, on-premise integration, and convenient self-service options. See [What Is Identity Authentication?](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/27882717f44b445fa287936c6f43dc1f.html).



</td>
</tr>
<tr>
<td>

 Identity Provisioning Service \(IPS\)



</td>
<td>

The Identity Provisioning service automates identity lifecycle processes. It helps you provision identities and their authorizations to various cloud and on-premise business applications. See [Identity Provisioning Service](https://help.sap.com/doc/c30747989e33466e8e4f789dd9c3c81c/Cloud/en-US/Provisioning_Service.pdf).



</td>
</tr>
<tr>
<td>

Identity Provider \(IdP\)



</td>
<td>

SAP Business Technology Platform supports identity federation, a concept of linking and reusing digital identities of a user base across loosely coupled systems. Identity federation frees applications on SAP Business Technology Platform from the need to obtain and store the credentials of users to authenticate them. Instead, the application user base is reused from identity providers, which support the administration of digital user identities, authentication, and authorizations in a centralized and decoupled manner. See [Trust and Federation with Identity Providers](../50-administration-and-ops/Trust_and_Federation_with_Identity_Providers_cb1bc8f.md).



</td>
</tr>
<tr>
<td>

Landscape Portal



</td>
<td>

The Landscape Portal app acts as a central tool to allow service providers to perform lifecycle management operations such as add-on updates, provisioning new consumers as new tenants, and more. See [Landscape Portal](Landscape_Portal_5eb70fb.md).



</td>
</tr>
<tr>
<td>

Multitenancy



</td>
<td>

A multitenant service/application serves requests from different customers - the tenants - and processes their data strictly isolated from one another.



</td>
</tr>
<tr>
<td>

Patch level



</td>
<td>

Patch deliveries shall only contain small corrections. They are shipped with delivery packages of type *Correction Package*.

For both the add-on product version and the software component version, the patch level is denoted in the third digit.



</td>
</tr>
<tr>
<td>

Project "Piper"



</td>
<td>

SAP implements tooling for continuous delivery in project "Piper". The goal of project "Piper" is to substantially ease setting up continuous delivery in your project using SAP technologies. See [Project Piper](https://sap.github.io/jenkins-library/infrastructure/overview/).



</td>
</tr>
<tr>
<td>

Provider



</td>
<td>

The provider is responsible for the development and maintenance of the SaaS application. This is typically an independent software vendor or development partner.



</td>
</tr>
<tr>
<td>

Release



</td>
<td>

Release deliveries contain the whole software component and deliver new and enhancements of existing functionalities.

For both the add-on product version and the software component version, the release is denoted in the first digit.



</td>
</tr>
<tr>
<td>

SAP App Center



</td>
<td>

SAP App Center is the enterprise marketplace where we bring together customers and partners on a single, easy-to-use, global online platform. Here, customers can discover, try, and buy SAP-validated partner applications that are built on or extend their existing SAP technology and solutions. For partners, it's the only place they can market and deliver their apps, add-ons, and integration kits to SAP's global customers — solutions that help customers grow their business. [SAP App Center](https://www.sapappcenter.com/en/about).



</td>
</tr>
<tr>
<td>

SAP Business Application Studio



</td>
<td>

Available as a cloud service, SAP Business Application Studio provides a desktop-like experience similar to leading IDEs, with command line and optimized editors. At the heart of SAP Business Application Studio are the dev spaces, which are similar to isolated virtual machines in the cloud containing tailored tools and pre-installed runtimes per business scenario, such as SAP Fiori, SAP S/4HANA extensions, Workflow, Mobile and more. This simplifies and saves time in setting up your development environment and allows you to efficiently develop, test, build, and run your solution locally or in the cloud. See [What is SAP Business Application Studio](https://help.sap.com/viewer/9d1db9835307451daa8c930fbd9ab264/Cloud/en-US/8f46c6e6f86641cc900871c903761fd4.html).



</td>
</tr>
<tr>
<td>

SAP ID Service



</td>
<td>

The default platform identity provider and application identity provider of SAP Business Technology Platform is SAP ID service. See [SAP ID Service](../50-administration-and-ops/SAP_ID_Service_d6a8db7.md).



</td>
</tr>
<tr>
<td>

SAP ONE Support Launchpad



</td>
<td>

SAP ONE Support Launchpad provides you access to task-driven support resources in an intuitive interface. By using customizable role profiles, it displays only the relevant applications and insights to you. See [https://launchpad.support.sap.com/](https://launchpad.support.sap.com/)



</td>
</tr>
<tr>
<td>

SAP PartnerEdge



</td>
<td>

Get information, training, tools, and resources regarding partner licensing at [https://partneredge.sap.com](https://partneredge.sap.com) 



</td>
</tr>
<tr>
<td>

Software component



</td>
<td>

In ABAP environment systems, you develop within software components \(also called repositories\). The add-ons being built in this scenario are made up by one or multiple software components combined to an add-on product. See [Software Components](Software_Components_58480f4.md).



</td>
</tr>
<tr>
<td>

Software component version



</td>
<td>

A software component version is a technically distinguishable unit of software and is installed and patched as a whole. See [Software Component Version](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentAddons/#software-component-version).



</td>
</tr>
<tr>
<td>

Subaccount



</td>
<td>

Subaccounts allow you to structure a global account according to your organization’s and project’s requirements with regard to members, authorizations, and entitlements. See [Subaccounts](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/8ed4a705efa0431b910056c0acdbf377.html#loio8d6e3a0fa4ab43e4a421d3ed08128afa).



</td>
</tr>
<tr>
<td>

Support package level



</td>
<td>

Support package deliveries contain a larger collection of corrections and may contain smaller functional enhancements. For both the add-on product version and the software component version, the support package level is denoted in the second digit.



</td>
</tr>
<tr>
<td>

Web Access for ABAP



</td>
<td>

Subscribe to the Web access for ABAP to get direct browser access to your instances in the ABAP environment, including access to the administration launchpad for ABAP. See [Subscribing to the Web Access for ABAP](../20-getting-started/Subscribing_to_the_Web_Access_for_ABAP_98928b0.md).



</td>
</tr>
</table>

