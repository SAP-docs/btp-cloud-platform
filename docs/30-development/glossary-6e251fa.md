<!-- loio6e251fa1b63f4ac48ac12c9d7201fae1 -->

# Glossary




<table>
<tr>
<td valign="top">

Add-on Assembly Kit as a Service \(AAKaaS\)



</td>
<td valign="top">

The Add-on Assembly Kit as a Service registers and publishes the software product. It is accessible via APIs with a technical communication user.



</td>
</tr>
<tr>
<td valign="top">

ABAP environment pipeline



</td>
<td valign="top">

The ABAP environment pipeline enables continuous integration for the ABAP environment. The pipeline contains several stages and supports different scenarios. See [ABAP Environment Pipeline](https://sap.github.io/jenkins-library/pipelines/abapEnvironment/introduction/).



</td>
</tr>
<tr>
<td valign="top">

ABAP System



</td>
<td valign="top">

The ABAP environment service \(abap/standard\) is used to create development and test systems. See [Creating an ABAP System](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/50b32f144e184154987a06e4b55ce447.html).



</td>
</tr>
<tr>
<td valign="top">

ABAP System \(SaaS, OEM\)



</td>
<td valign="top">

The ABAP environment \(abap/saas-oem\) service is used to create the add-on installation test system and production systems, where a specific add-on product needs to be installed in the system.



</td>
</tr>
<tr>
<td valign="top">

Add-on build pipeline



</td>
<td valign="top">

A pipeline configured for the add-on build scenario of the ABAP environment pipeline. See [Build and Publish Add-on Products on SAP BTP ABAP Environment](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentAddons/).



</td>
</tr>
<tr>
<td valign="top">

Add-on descriptor



</td>
<td valign="top">

The build process is controlled by an add-on descriptor file called `addon.yml`. This file must be created manually and stored in the Git repository of the pipeline. It must contain information about the software product version to be delivered and the containing software component versions. See [Add-On Descriptor File](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentAddons/#add-on-descriptor-file).



</td>
</tr>
<tr>
<td valign="top">

Add-on installation test system



</td>
<td valign="top">

To verify that the delivery packages included in the add-on product version being built are installable, a target vector is published in "test" scope. In the integration tests stage, an ABAP system of service plan `saas_oem` is created. This ABAP OEM service allows you to install a specific add-on product version into an ABAP system that is provisioned.



</td>
</tr>
<tr>
<td valign="top">

Add-on product version \(software product version\)



</td>
<td valign="top">

To install and maintain ABAP software, software product versions are used. A software product version is a bundle of software component versions made available at the same time for implementing a well-defined scope of functionality. See [Software Product Version](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentAddons/#software-product-version).



</td>
</tr>
<tr>
<td valign="top">

ABAP Solution \(Provider\)



</td>
<td valign="top">

The ABAP Solution service maintains ABAP systems and tenants to provide an add-on product as a SaaS solution.



</td>
</tr>
<tr>
<td valign="top">

Assembly System



</td>
<td valign="top">

The ABAP system responsible for the add-on build.

It is created during the pipeline and eventually deleted. All actions related to the ABAP source code are executed on this system, e.g. running checks with the ABAP Test Cockpit or the physical build of the software components.



</td>
</tr>
<tr>
<td valign="top">

ABAP Test Cockpit



</td>
<td valign="top">

ABAP Test Cockpit checks can be executed using `abapEnvironmentRunATCCheck`. The step can receive software components or packages configured in a YML file. The results are returned in checkstyle format. With the use of a pipeline extension, you can configure quality gates. See [ATC](https://www.project-piper.io/pipelines/abapEnvironment/stages/Test/#atc) and [ABAP Test Cockpit Configurator](../50-administration-and-ops/abap-test-cockpit-configurator-22c26ff.md).



</td>
</tr>
<tr>
<td valign="top">

Branch



</td>
<td valign="top">

Git repository branches can be used to control the flow of changes through the test and production landscape. They separate changes from each other, which shall or might not be delivered together \(i.e. development vs. correction, feature A vs. feature B\). A branch is created on the current state of another branch, the parent branch, and reflected by a new copy of all included objects. Depending on which branch is supposed to be changed, the corresponding copy is worked on.



</td>
</tr>
<tr>
<td valign="top">

Business role



</td>
<td valign="top">

A business role provides users with authorizations to access apps.



</td>
</tr>
<tr>
<td valign="top">

CI/CD server



</td>
<td valign="top">

The pipeline for building ABAP add-ons has been created specifically for Jenkins. Therefore, a Jenkins server is required. The project "Piper" provides a Jenkins image, which already includes the necessary configurations. Note that you can also configure an existing server.



</td>
</tr>
<tr>
<td valign="top">

 Cloud Foundry environment



</td>
<td valign="top">

The Cloud Foundry environment enables you to develop new business applications and business services, supporting multiple runtimes, programming languages, libraries, and services. See [Cloud Foundry Environment](../10-concepts/cloud-foundry-environment-9c7092c.md#loio9c7092c7b7ae4d49bc8ae35fdd0e0b18).



</td>
</tr>
<tr>
<td valign="top">

Communication arrangement



</td>
<td valign="top">

A communication arrangement describes a communication scenario with a remote system during configuration time. It provides the necessary metadata for service configuration. See [Communication Arrangement](communication-arrangement-201de48.md).



</td>
</tr>
<tr>
<td valign="top">

Communication scenario



</td>
<td valign="top">

A communication scenario in the ABAP environment is a design time description of how two communication partners communicate with each other.

It provides technical information, such as the used inbound and outbound services and their service type, for example OData or SOAP, and the number of allowed communication arrangement instances. See [Communication Scenario](communication-scenario-7ea7276.md).



</td>
</tr>
<tr>
<td valign="top">

Consumer



</td>
<td valign="top">

The service consumer is an end-customer of the service provider and has access to the SaaS application in a specific tenant



</td>
</tr>
<tr>
<td valign="top">

Correction codeline



</td>
<td valign="top">

Corrections need to run in parallel to development and on a released state. This is performed in the correction codeline and on a maintenance branch.



</td>
</tr>
<tr>
<td valign="top">

Cx server



</td>
<td valign="top">

Cx server is a life-cycle management tool to bootstrap a preconfigured Jenkins instance within minutes on your own \(virtual\) server, that uses Docker images. To avoid manual startup of the Docker image with all the required parameters and sidecar images, this command line tool automates the bootstrapping. See [Cx Server](https://sap.github.io/jenkins-library/infrastructure/overview/#cx-server-recommended).



</td>
</tr>
<tr>
<td valign="top">

Destination service



</td>
<td valign="top">

The Destination service lets you find the destination information that is required to access a remote service or system from your Cloud Foundry application. See [Consuming the Destination Service](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/7e306250e08340f89d6c103e28840f30.html).



</td>
</tr>
<tr>
<td valign="top">

Development codeline



</td>
<td valign="top">

Infinity development \(infinity codeline\) is done based on the latest software component state in the main branch.



</td>
</tr>
<tr>
<td valign="top">

Development namespace



</td>
<td valign="top">

Naming conflicts can be avoided through agreements on naming conventions or by carrying out development in separate namespaces. See SAP note [84282](https://launchpad.support.sap.com/#/notes/84282) and [Maintain Namespaces](maintain-namespaces-5456007.md).



</td>
</tr>
<tr>
<td valign="top">

Global account



</td>
<td valign="top">

A global account is the realization of a contract you made with SAP. A global account is used to manage subaccounts, members, entitlements, and quotas. You receive entitlements and quotas to use platform resources per global account and then distribute the entitlements and quotas to the subaccount for actual consumption. See [Getting a Global Account](../20-getting-started/getting-a-global-account-d61c281.md#loiod61c2819034b48e68145c45c36acba6e).



</td>
</tr>
<tr>
<td valign="top">

 Identity Authentication service



</td>
<td valign="top">

The Identity Authentication service provides you with controlled cloud-based access to business processes, applications, and data. It simplifies your user experience through authentication mechanisms, single sign-on, on-premise integration, and convenient self-service options. See [What Is Identity Authentication?](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/27882717f44b445fa287936c6f43dc1f.html).



</td>
</tr>
<tr>
<td valign="top">

 Identity Provisioning service



</td>
<td valign="top">

The Identity Provisioning service automates identity lifecycle processes. It helps you provision identities and their authorizations to various cloud and on-premise business applications. See [What is Identity Provisioning](https://help.sap.com/viewer/f48e822d6d484fa5ade7dda78b64d9f5/Cloud/en-US/f2b2df8a273642a1bf801e99ecc4a043.html).



</td>
</tr>
<tr>
<td valign="top">

Identity Provider



</td>
<td valign="top">

SAP Business Technology Platform supports identity federation, a concept of linking and reusing digital identities of a user base across loosely coupled systems. Identity federation frees applications on SAP Business Technology Platform from the need to obtain and store the credentials of users to authenticate them. Instead, the application user base is reused from identity providers, which support the administration of digital user identities, authentication, and authorizations in a centralized and decoupled manner. See [Trust and Federation with Identity Providers](../50-administration-and-ops/trust-and-federation-with-identity-providers-cb1bc8f.md).



</td>
</tr>
<tr>
<td valign="top">

Landscape Portal



</td>
<td valign="top">

The Landscape Portal app acts as a central tool to allow service providers to perform lifecycle management operations such as add-on updates, provisioning new consumers as new tenants, and more. See [Landscape Portal](landscape-portal-5eb70fb.md).



</td>
</tr>
<tr>
<td valign="top">

Multitenancy



</td>
<td valign="top">

A multitenant service/application serves requests from different customers - the tenants - and processes their data strictly isolated from one another.



</td>
</tr>
<tr>
<td valign="top">

Patch level



</td>
<td valign="top">

Patch deliveries shall only contain small corrections. They are shipped with delivery packages of type *Correction Package*.

For both the add-on product version and the software component version, the patch level is denoted in the third digit.



</td>
</tr>
<tr>
<td valign="top">

Project "Piper"



</td>
<td valign="top">

SAP implements tooling for continuous delivery in project "Piper". The goal of project "Piper" is to substantially ease setting up continuous delivery in your project using SAP technologies. See [Project Piper](https://sap.github.io/jenkins-library/infrastructure/overview/).



</td>
</tr>
<tr>
<td valign="top">

Provider



</td>
<td valign="top">

The provider is responsible for the development and maintenance of the SaaS application. This is typically an independent software vendor or development partner.



</td>
</tr>
<tr>
<td valign="top">

Release



</td>
<td valign="top">

Release deliveries contain the whole software component and deliver new features and enhancements of existing functionalities.

For both the add-on product version and the software component version, the release is denoted in the first digit.



</td>
</tr>
<tr>
<td valign="top">

SAP Store



</td>
<td valign="top">

SAP Store is the enterprise marketplace where we bring together customers and partners on a single, easy-to-use, global online platform. Here, customers can discover, try, and buy SAP-validated partner applications that are built on or extend their existing SAP technology and solutions. For partners, it's the only place they can market and deliver their apps, add-ons, and integration kits to SAP's global customers — solutions that help customers grow their business. See [https://store.sap.com/dcp/en/](https://store.sap.com/dcp/en/).



</td>
</tr>
<tr>
<td valign="top">

SAP Business Application Studio



</td>
<td valign="top">

Available as a cloud service, SAP Business Application Studio provides a desktop-like experience similar to leading IDEs, with command line and optimized editors. At the heart of SAP Business Application Studio are the dev spaces, which are similar to isolated virtual machines in the cloud containing tailored tools and pre-installed runtimes per business scenario, such as SAP Fiori, SAP S/4HANA extensions, Workflow, Mobile and more. This simplifies and saves time in setting up your development environment and allows you to efficiently develop, test, build, and run your solution locally or in the cloud. See [What is SAP Business Application Studio](https://help.sap.com/viewer/9d1db9835307451daa8c930fbd9ab264/Cloud/en-US/8f46c6e6f86641cc900871c903761fd4.html).



</td>
</tr>
<tr>
<td valign="top">

SAP ID service



</td>
<td valign="top">

The default platform identity provider and application identity provider of SAP Business Technology Platform is SAP ID service. See [Default Identity Provider](../50-administration-and-ops/default-identity-provider-d6a8db7.md).



</td>
</tr>
<tr>
<td valign="top">

SAP ONE Support launchpad



</td>
<td valign="top">

SAP ONE Support Launchpad provides you access to task-driven support resources in an intuitive interface. By using customizable role profiles, it displays only the relevant applications and insights to you. See [https://launchpad.support.sap.com/](https://launchpad.support.sap.com/)



</td>
</tr>
<tr>
<td valign="top">

SAP PartnerEdge



</td>
<td valign="top">

Get information, training, tools, and resources regarding partner licensing at [https://partneredge.sap.com](https://partneredge.sap.com) 



</td>
</tr>
<tr>
<td valign="top">

Software component



</td>
<td valign="top">

In ABAP environment systems, you develop within software components \(also called repositories\). The add-ons being built in this scenario are made up by one or multiple software components combined to an add-on product. See [Software Components](software-components-58480f4.md).



</td>
</tr>
<tr>
<td valign="top">

Software component version



</td>
<td valign="top">

A software component version is a technically distinguishable unit of software and is installed and patched as a whole. See [Software Component Version](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentAddons/#software-component-version).



</td>
</tr>
<tr>
<td valign="top">

Subaccount



</td>
<td valign="top">

Subaccounts allow you to structure a global account according to your organization’s and project’s requirements with regard to members, authorizations, and entitlements. See [Subaccounts](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/8ed4a705efa0431b910056c0acdbf377.html#loio8d6e3a0fa4ab43e4a421d3ed08128afa).



</td>
</tr>
<tr>
<td valign="top">

Support package level



</td>
<td valign="top">

Support package deliveries contain a larger collection of corrections and may contain smaller functional enhancements. For both the add-on product version and the software component version, the support package level is denoted in the second digit.



</td>
</tr>
<tr>
<td valign="top">

Web Access for ABAP



</td>
<td valign="top">

Subscribe to the Web access for ABAP to get direct browser access to your instances in the ABAP environment, including access to the administration launchpad for ABAP. See [Subscribing to the Web Access for ABAP](../20-getting-started/subscribing-to-the-web-access-for-abap-98928b0.md).



</td>
</tr>
</table>

