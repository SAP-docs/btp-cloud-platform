<!-- loio4b4deeea31f74bfaa2598dc6b1c99eb9 -->

# Users and Roles


<table>
<tr>
<th>

User



</th>
<th>

Role



</th>
<th>

Description



</th>
<th>

Tasks/Usage



</th>
</tr>
<tr>
<td rowspan="8">

Provider



</td>
<td>

Add-On Administrator



</td>
<td>

The add-on administrator is responsible for everything related to the add-on production, for example, releasing an add-on product version.



</td>
<td>

-   Creating software component

-   Importing changes in software component to test systems

-   Adjusting add-on descriptor file `addon.yml` for new versions

-   Registering add-on product and global account with SAP

-   Executing add-on build pipeline in Jenkins instance

-   Confirming Integration Tests stage in add-on build pipeline

-   Confirming build in Confirm stage during add-on build pipeline

-   Creating maintenance branches \(for example v1.0.0\) per support package level in *Manage Software Components* app. See [Manage Software Components](Manage_Software_Components_3dcf76a.md).

-   Checking out maintenance branch in correction system COR and quality assurance system QAS using the *Manage Software Components* app.




</td>
</tr>
<tr>
<td>

DevOps Engineer



</td>
<td>

The DevOps engineer is responsible for the configuration of the pipeline and implementation of the multitenant application that needs to be provided to enable the add-on as a SaaS solution.



</td>
<td>

-   Initial configuration of add-on pipeline, especially `config.yml`file in git repository

-   Implementing pipeline extensions if required

-   Implementing and deploying multitenant application \(SaaS Registry and ABAP Solution Provider\). See [Developing Multitenant Applications in the ABAP Environment](Developing_Multitenant_Applications_in_the_ABAP_Environment_195031f.md).




</td>
</tr>
<tr>
<td>

Developer



</td>
<td>

Developer users use ABAP Development Tools \(ADT\) to create backend service artifacts and UI developers create and deploy SAP Fiori apps in SAP Business Application Studio. See [What is SAP Business Application Studio](https://help.sap.com/viewer/9d1db9835307451daa8c930fbd9ab264/Cloud/en-US/8f46c6e6f86641cc900871c903761fd4.html).

Additionally, they are responsible for their pipeline \(e.g. automation of the build process\) and implementing an approuter application to provide a multi-tenant business application. See [Configure the Approuter Application](Configure_the_Approuter_Application_3725815.md).



</td>
<td>

-   Developing backend services in ABAP Development Tools \(ADT\) using ABAP RESTful Application Programming Model. See [Eclipse Tool for the ABAP Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/54dd7126d5b74efeb7a21f6b0bfe5f1a.html) and [ABAP RESTful Application Programming Model](ABAP_RESTful_Application_Programming_Model_33a301e.md).

-   Developing SAP Fiori based UI in SAP Business Application Studio and deploying back to ABAP system. See [Develop an SAP Fiori Application UI and Deploy it to ABAP Using SAP Business Application Studio](Develop_an_SAP_Fiori_Application_UI_and_Deploy_it_to_ABAP_Using_SAP_Business_Application_Studio_eaaeba4.md).

-   Supporting and troubleshooting customer issues via provider support access in the Landscape Portal. See [Landscape Portal](Landscape_Portal_5eb70fb.md).




</td>
</tr>
<tr>
<td>

Test User



</td>
<td>

Test users are business users in test systems TST and QAS that validate the correct implementation of the add-on. This involves, among others, maintaining business roles and communication arrangements delivered as part of the add-on. See [Communication Arrangement](Communication_Arrangement_201de48.md).



</td>
<td>

-   Maintaining business roles. See [Maintain Business Roles](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/8980ad05330b4585ab96a8e09cef4688.html).

-   Maintaining communication arrangements. See [Communication Arrangements](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/1decd8b8747443ee8839ce4474a3643e.html).

-   Tesingt ABAP backend services

-   Testing SAP Fiori UIs




</td>
</tr>
<tr>
<td>

Provider IAS Administrator



</td>
<td>

An Identity Authentication service tenant can be configured for authentication in development/test/assembly systems. The IAS administrator configures the trust setup between the subaccount and IAS application. See [SAP Cloud Identity Services - Identity Authentication](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/d17a116432d24470930ebea41977a888.html).



</td>
<td>

-   Configuring IAS application for trust setup in development/test/assembly subaccounts. See [Create New Application](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/0d4b255051c74955a959146beee4bd8c.html).

-   Configuring corporate identity provider in IAS tenant. See [Corporate Identity Providers](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/19f3eca47db643b6aad448b5dc1075ad.html).




</td>
</tr>
<tr>
<td>

Operator



</td>
<td>

The SaaS solution operator is responsible for creating the account model on the provider side \(creating consumer subaccounts\), adding subaccount members etc.



</td>
<td>

-   Setting up global development and global production accounts including entitlements, subaccounts, Cloud Foundry org, spaces, services, and apps, as well as trust configuration and connectivity per subaccount. See [System Landscape/Account Model](Concepts_9482e7e.md#loio4ca756395fc24e56a42b77632a6bd862).

-   Consumer tenant onboarding: creating consumer subaccount and subscription. See [Subscribe New Consumers](Subscribe_New_Consumers_b90cde1.md).

-   Creating users in ABAP systems. See [Creation of Additional Administrator Users](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/ced83807a6dc4e33a2cfcdce06e9f9f3.html).

    -   Developer users in DEV/COR systems. See [Creation of Developer Users](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/f87151e385ba428cb7d12d0085060ebc.html).

    -   Tester users in TST/QAS systems

-   Add-on update of existing systems in the Landscape Portal. See [Landscape Portal](Landscape_Portal_5eb70fb.md).

-   Monitoring of system/tenant provisioning and user onboarding in Landscape Portal




</td>
</tr>
<tr>
<td>

Jenkins Administrator



</td>
<td>

A Jenkins CI/CD server is used as the infrastructure for automation purposes. Pipeline configuration, user management, credentials management etc. is handled by the Jenkins administrator. See [Continuous Integration and Delivery \(CI/CD\)](Continuous_Integration_and_Delivery_(CICD)_fe74df5.md).



</td>
<td>

-   Creating Jenkins instance via Cx server

-   Maintaining Jenkins credentials for:

    -   Cloud Foundry technical platform user

    -   Technical communication user

    -   Credentials of service user for git repository of pipeline configuration

-   Maintaining Jenkins pipeline with reference to git repository of pipeline configuration

-   Adding additional Jenkins users, for example for add-on administrator user




</td>
</tr>
<tr>
<td>

S-User



</td>
<td>

S-users are used by partners and customers to log on to SAP ONE Support Launchpad to reserve development namespaces or to create technical communication users. User management is taken care of by user administrators in the *User Management* app. If customer numbers are assigned to a Partner ID, S-users are registered via PartnerEdge. See [User Management](https://support.sap.com/content/dam/support/en_us/library/ssp/my-support/help-for-sap-support-applications/online_help-user_management.html) and SAP note [2261006](https://launchpad.support.sap.com/#/notes/2261006).



</td>
<td>

-   Requesting development namespace. See SAP note [2006427](https://launchpad.support.sap.com/#/notes/2006427).

-   Creating technical communication user. See SAP note [2532813](https://launchpad.support.sap.com/#/notes/2532813).




</td>
</tr>
<tr>
<td rowspan="3">

Technical Users of Provider



</td>
<td>

Technical Cloud Foundry Platform User



</td>
<td>

A P-user \(SAP ID Service\) or S-user \(created via SAP ONE Support Launchpad\) is added as a member to subaccounts in the Cloud Foundry environment to create or delete ABAP service instances, create service keys etc. This user does not need authoriziations in SAP ONE Support Launchpad since only authentication via SAP ID Service is used. See [SAP ID Service](SAP_ID_Service_d6a8db7.md) and SAP note [1271482](https://launchpad.support.sap.com/#/notes/1271482).



</td>
<td>

-   Creating ABAP system AMT via ABAP solution service for consumer tenants. See [Define Your ABAP Solution](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/1697387c02e74e66a55cf21a05678167.html).

-   Creating ABAP system BLD via add-on build pipeline for add-on assembly

-   Creating ABAP system ATI via add-on build pipeline for add-on installation test

-   Deleting ABAP systems




</td>
</tr>
<tr>
<td>

Service User Git



</td>
<td>

Jenkins pipeline definitions are source-code-based and stored in a source code repository, usually a Git repository. To retrieve the pipeline definition from the repository, a \(technical\) service user is configured.



</td>
<td>

-   Pulling changes in git repository of pipeline configuration

-   Pulling changes in SAP/Jenkins library to Piper library steps




</td>
</tr>
<tr>
<td>

Technical Communication User



</td>
<td>

A technical communication user \(created via SAP ONE Support Launchpad\) is used for system-to-system connections with the SAP Support backbone. For information on how technical communication users are different from S-users, see SAP note [2668288](https://launchpad.support.sap.com/#/notes/2668288).



</td>
<td>

Used for communication with the AAKaaS:

-   [abapAddonAssemblyKitCheckPV](http://help.sap.com/disclaimer?site=https://sap.github.io/jenkins-library/steps/abapAddonAssemblyKitCheckPV/)


-   [abapAddonAssemblyKitCheckCVs](http://help.sap.com/disclaimer?site=https://sap.github.io/jenkins-library/steps/abapAddonAssemblyKitCheckCVs/)


-   [abapAddonAssemblyKitReleasePackages](http://help.sap.com/disclaimer?site=https://sap.github.io/jenkins-library/steps/abapAddonAssemblyKitReleasePackages/)


-   [abapAddonAssemblyKitReserveNextPackages](http://help.sap.com/disclaimer?site=https://sap.github.io/jenkins-library/steps/abapAddonAssemblyKitReserveNextPackages/)


-   [abapAddonAssemblyKitRegisterPackages](http://help.sap.com/disclaimer?site=https://sap.github.io/jenkins-library/steps/abapAddonAssemblyKitRegisterPackages/)


-   [abapAddonAssemblyKitCreateTargetVector](http://help.sap.com/disclaimer?site=https://sap.github.io/jenkins-library/steps/abapAddonAssemblyKitCreateTargetVector/)


-   [abapAddonAssemblyKitPublishTargetVector](http://help.sap.com/disclaimer?site=https://sap.github.io/jenkins-library/steps/abapAddonAssemblyKitPublishTargetVector/)




</td>
</tr>
<tr>
<td rowspan="4">

Consumer



</td>
<td>

Consumer IAS Administrator



</td>
<td>

An Identity Authentication Service tenant can be configured for authentication at consumer tenants in the productive ABAP systems. The IAS admin configures the trust setup between consumer subaccount and IAS application. See [Identity Authentication Service](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/d17a116432d24470930ebea41977a888.html).



</td>
<td>

-   Configuring IAS application for trust setup in consumer subaccount

-   Optional: Configuring corporate identity provider in IAS tenant




</td>
</tr>
<tr>
<td>

Consumer Subaccount Administrator



</td>
<td>

The consumer subaccount administrator is responsible for the configuration of:

-   Trust settings \(custom identity provider\), see [Log On Manually With a Custom Identity Provider](Log_On_Manually_With_a_Custom_Identity_Provider_e1009b4.md).
-   Connectivity via Cloud Connector , see [Connectivity in the Cloud Foundry Environment](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/34010ace6ac84574a4ad02f5055d3597.html)
-   Destinations, see [Managing Destinations](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/84e45e071c7646c88027fffc6a7bb787.html) in the consumer subaccount created for the customer.



</td>
<td>

-   Setting up connectivity via Cloud Connector

-   Adding destinations in consumer subaccount

-   Setting up trust configuration




</td>
</tr>
<tr>
<td>

Business User



</td>
<td>

Business users make use of the SaaS solution in the consumer tenant for their daily work.



</td>
<td>

-   Initial administrator onboarding

-   Creating additional business users

-   Creating business roles

-   Creating communication arrangements

-   Using SAP Fiori UIs




</td>
</tr>
<tr>
<td>

Cloud Connector Administrator



</td>
<td>

To connect on-premise systems on the customer side to the consumer tenant with the SaaS solution, Cloud Connector can be configured in the consumer subaccount. The Cloud Connector administrator maintains the consumer subaccount, cloud-to-on-premise system mappings etc. See [Cloud Connector](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e6c7616abb5710148cfcf3e75d96d596.html#loioe6c7616abb5710148cfcf3e75d96d596__context).



</td>
<td>

-   Adding a consumer subaccount to Cloud Connector. See [Managing Subaccounts](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/f16df12fab9f4fe1b8a4122f0fd54b6e.html).

-   Configuring cloud to on-premise system mappings. See [Configure Access Control](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/f42fe4471d6a4a5fb09b7f3bb83c66a4.html).

-   Synchronizing trust configuration for principal propagation. See [Set Up Trust for Principal Propagation](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/a4ee70f0274248f8bbc7594179ef948d.html).




</td>
</tr>
</table>

