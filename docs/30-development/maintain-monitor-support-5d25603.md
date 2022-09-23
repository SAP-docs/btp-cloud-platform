<!-- loio5d25603f9f9e442795f5e45612e2ffb8 -->

# Maintain, Monitor, Support

After the go-live of the SaaS solution and the deployment of its updates, consumers using the solution might run into issues that you have to troubleshoot and debug.

 <a name="loio9721f0fb92a84e2a95309acf445cb0a9"/>

<!-- loio9721f0fb92a84e2a95309acf445cb0a9 -->

## Maintain

After the initial add-on release has been shipped as a SaaS solution offering, the development of maintenance patches, support packages, and consequent add-on releases comes into play.

Once everything is implemented, built, and the maintenance delivery is deployed, the corresponding changes become available in the customer production system AMT.



<a name="loio9721f0fb92a84e2a95309acf445cb0a9__section_qhv_tdp_drb"/>

## Prerequisites

-   To set up the maintenance system landscape, you need the relevant entitlements in the global account for development. See [Entitlements and Quotas](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/00aa2c23479d42568b18882b1ca90d79.html).
-   To create updates for the SaaS solution, you need a maintenance system landscape. Business users with authorization to use the *Manage Software Components* app and developer users using ABAP Development Tools have to be available in the systems. See [Manage Software Components](../50-administration-and-ops/manage-software-components-3dcf76a.md) and [Getting Started as a Developer in the ABAP Environment](../20-getting-started/getting-started-as-a-developer-in-the-abap-environment-4b896c9.md).
-   To configure new add-on versions, you need the existing pipeline configuration for an add-on build pipeline. See [Build and Publish Add-on Products on SAP BTP, ABAP Environment](https://www.project-piper.io/scenarios/abapEnvironmentAddons/).
-   To trigger the add-on product build, you need a Jenkins pipeline and a pipeline configuration including the new add-on version.
-   To apply updates for the SaaS solution, you need a subscription to the Landscape Portal application and a user assigned to role collection `LandscapePortalAdminRoleCollection`.

 <a name="loio44035458f01e4142a18d44f9c0301e62"/>

<!-- loio44035458f01e4142a18d44f9c0301e62 -->

### Set Up Maintenance System Landscape

![](images/Prepare_a_Development_Account_e29111f.png)

Bug fixes aren’t implemented as part of the development code line \(systems DEV and TST\) but in a separate correction code line with separate systems to develop and test these corrections.

The ABAP systems that you use for development, testing, and add-on assembly are of type`abap/standard` and made available via entitlements. As a SaaS solution operator, you have to assign service entitlements to different subaccounts according to the following structure:


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

Entitlements



</th>
<th valign="top">

ABAP System



</th>
</tr>
<tr>
<td valign="top" rowspan="2">

Global Account for Development



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
<td valign="top">

COR



</td>
</tr>
<tr>
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
<td valign="top">

QAS



</td>
</tr>
</table>

Use service parameter `is_development_allowed` to differentiate between development and test systems.

-   For development in the ABAP correction system COR, you, as a SaaS solution operator, create a system in subaccount *01 Develop* in the development space. For correction system COR, set parameter `is_development_allowed = true`.

-   For testing in the ABAP quality assurance system QAS, you, as a SaaS solution operator, create a system in subaccount *02 Test* in the test space. For quality assurance system QAS, set parameter `is_development_allowed = false`.


Users in the ABAP correction system COR might be locked and need to be unlocked for development of corrections. See [Use Case 2: One Development and Correction Codeline in a 5-System Landscape](use-case-2-one-development-and-correction-codeline-in-a-5-system-landscape-4e53874.md)

> ### Tip:  
> For in-depth information about the system landscape/account model, check out [System Landscape/Account Model](concepts-9482e7e.md#loio4ca756395fc24e56a42b77632a6bd862).

 <a name="loioa35582346bff4914a5b4b0bcb776668c"/>

<!-- loioa35582346bff4914a5b4b0bcb776668c -->

### Create Add-On Update

> ### gCTS Delivery:  
> If you use gCTS for delivery, the process of creating an update for SaaS solutions is grouped into urgent corrections \(patch version\) and new releases \(release version\). See [Use Case 2: One Development and Correction Codeline in a 5-System Landscape](use-case-2-one-development-and-correction-codeline-in-a-5-system-landscape-4e53874.md).
> 
> See [Delivery via Add-On or gCTS](delivery-via-add-on-or-gcts-438d7eb.md#loio438d7ebfdc4a41de82dcdb156f01857e).

> ### Note:  
> New features are developed on different code lines \(branches\). If you create a so-called maintenance branch to implement patches while new features are implemented in the main branch of a software component, you can implement new features and provide bug fixes at the same time. For more information, see [Versioning and Branches](concepts-9482e7e.md#loio8c087bca40584f9b899282b4ec515753).
> 
> Only by changing the version string of a software component in the add-on descriptor file `addon.yml`, the build of a new delivery package with the latest changes is created. When defining an addon.yml file, please follow the best practices. See [Add-On Descriptor File](https://www.project-piper.io/scenarios/abapEnvironmentAddons/#add-on-descriptor-file).
> 
> To learn more about terminology related to software lifecycle management in the ABAP environment, such as cloning and checkout, see [Basic Concepts and Terms](basic-concepts-and-terms-fb3a076.md).

As an add-on administrator, you can provide different kinds of updates. The decision regarding which one to use depends on the motivation behind a given update.

-   Small and urgent corrections are delivered as patches
-   Collections of less urgent corrections and other functional enhancements should be delivered as support packages
-   New release versions are released with updates containing significant enhancements and new features

> ### Tip:  
> Use the [Check Product Version](check-product-version-0da158a.md) app in Landscape Portal to find out which product version has already been built.

**Create new patch version \(emergency patch\)**

> ### gCTS Delivery:  
> For delivering an emergency patch via gCTS instead of using add-ons, see section *Urgent Corrections* in [Use Case 2: One Development and Correction Codeline in a 5-System Landscape](use-case-2-one-development-and-correction-codeline-in-a-5-system-landscape-4e53874.md) and follow the steps.
> 
> -   **Develop**
> 
>     If you haven't created a maintenance branch yet, create a maintenance branch in your correction system COR. Check out the maintenance branch, implement your corrections on the software component in the correction system, and release it, see step 1-3.
> 
> -   **Test**
> 
>     Using the *Manage Software Components* app in your quality and assurance system QAS, clone and pull the maintenance branch that contains the emergency patch, and test the changes, see step 4-5.
> 
> -   **Release**
> 
>     In the *Manage Software Components* app of the provider tenant in your production system AMT, pull the maintenance branch with the emergency patch, see step 7. The corrections are now imported into your production system AMT .
> 
> -   **Double Maintenance of Corrections**
> 
>     Perform the same corrections in your development system DEV. Release the corrections to maintain them on the main branch of your software component and pull it into your test system TST, see step 9-10.
> 
> 
> See [Delivery via Add-On or gCTS](delivery-via-add-on-or-gcts-438d7eb.md#loio438d7ebfdc4a41de82dcdb156f01857e).

> ### Note:  
> For a new patch version, you can use a permanent add-on assembly system to save build time. See [ABAP Environment Pipeline](concepts-9482e7e.md#loio2398b874f7c5445db188b780ff0cef89).

Patch versions are used to deliver unplanned and most likely urgent corrections that are required to keep the application up and running. These changes could be required for a service consumption model of an OData Client Proxy in case of changes to the structure of the underlying OData service. See [OData Client Proxy Configurations](odata-client-proxy-configurations-0d92f49.md).

-   **Develop**
    -   Import the maintenance branch in the ABAP correction system

        Bug fixes are delivered as a new patch version of a software component and are implemented on the correction code line. Therefore, the dedicated ABAP correction system COR is used.

        As an add-on admin, check out the maintenance branch, which is the branch that is created for bug fixes and maintenance deliveries. See [How to Work with Branches](../50-administration-and-ops/how-to-work-with-branches-6b2f0bf.md).

    -   Implement the bug fix in the ABAP correction system

        As a developer, implement the required changes to the software component in the ABAP correction system COR. These changes shouldn’t introduce new features because patch versions should only contain small emergency corrections.

        For more information on the different software component version numbers, see [Software Component Version](https://www.project-piper.io/scenarios/abapEnvironmentAddons/#software-component-version).

        After releasing the transport tasks and requests in the correction system, the changes are imported into and tested in the quality assurance system QAS.


-   **Test**
    -   Import the maintenance branch in the ABAP quality assurance system

        You need to test the implemented corrections by importing the maintenance branch for the current support package level, where the transports for necessary bug fixes were released, in the dedicated test system, which is the ABAP quality assurance system QAS. See [How to Pull Software Components](../50-administration-and-ops/how-to-pull-software-components-90b9b9d.md).

    -   Test bugfix in ABAP quality assurance system

        As a tester, test the corrections in the QAS system to validate that the provided bug fixes are solving the problem and are working properly. As an add-on admin, use the software components app to import the latest changes into the quality assurance system QAS.

        Required testing can involve anything from maintaining business roles, creating communication arrangements to more complex testing scenarios where connectivity is involved. See [Maintain Business Roles](../50-administration-and-ops/maintain-business-roles-8980ad0.md), [How to Create a Communication Arrangement](../50-administration-and-ops/how-to-create-a-communication-arrangement-a0771f6.md), and [Connectivity](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e54cc8fbbb571014beb5caaf6aa31280.html). What needs to be tested is related to the implemented corrections.


-   **Double maintenance of corrections into development**

    As a developer, you have to maintain the corrections that have been developed in the ABAP correction system COR as separate transports in development system DEV \(so called double-maintenance\). See [Double Maintenance of Corrections into Development](double-maintenance-of-corrections-into-development-1241b14.md).

-   **Configure addon.yml file**

    > ### Note:  
    > While creating patch versions for the same support package level or release version, the same maintenance branch should be used.

    As an add-on admin, change the add-on descriptor file according to the add-on product version that you want to build.

    Optionally, you can specify a commit ID. All released changes up to the specified commit are included. You can retrieve this commit ID from the commit history in the *Manage Software Components* app.

    ```
    ---
    addonProduct: "/NAMESPC/PRODUCTX"
    addonVersion: "1.0.1"
    repositories:
       - name: "/NAMESPC/PRODUCTX"
         branch: "v1.0.0"
         version: "1.0.1"
         commitID: "12345xy"
    
    ```

    See [Build and Publish Add-on Products on SAP BTP ABAP Environment](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentAddons/#addonyml).

    `addonProduct` must include the development namespace prefix and the add-on product name.

    `addonVersion` is version 1.0.1, marking a patch delivery.

    The repositories include all involved software components as well as the branch and software component version to be used for the add-on build.

    In the example configuration, the branch of software component `/NAMESPC/PRODUCTX` is pointing to the maintenance branch v1.0.0 as the bug fix is based on the delivered support package level 0 of software component release 1. The commit ID is referencing the short commit ID for the latest changes in the maintenance branch. You can retrieve these software component details from the *Manage Software Components* app.


**Create new support package version \(hotfix collection\)**

> ### Note:  
> If you use a quarterly delivery approach, new features are not delivered using support package versions.
> 
> Instead, a new maintenance branch is created from the previous maintenance branch, using systems COR and QAS instead. See [Delivery Models](concepts-9482e7e.md#loio326508756a144c49b98e5fcf442cce40).

Support package versions are used to deliver planned functional enhancements outside of new major releases. They are often used to bundle multiple patch versions to a hotfix collection.

A support package version could be used for example to deliver a new simple business configuration UI. See [Business Configuration in SAP BTP ABAP Environment \(1\): Overview and BC Maintenance Apps](https://blogs.sap.com/2021/09/22/business-configuration-in-sap-btp-abap-environment-1-overview-and-bc-maintenance-apps/).

-   **Develop**
    -   Implement new feature in ABAP development system

        As a developer, implement the new feature in the main branch in the ABAP development system DEV. Bug fixes should be delivered via patch deliveries if they need to be available before the next support package delivery cycle. See [The Add-On Product](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentAddons/#the-add-on-product).

        After releasing the transport task and request in the development system, you can import the changes for testing in the ABAP test system TST.


-   **Test**
    -   Import main branch into ABAP test system

        As development in system DEV is done on the main branch, the same branch is imported into the test system.

        As an add-on admin, use the *Manage Software Components* app to import the changes in the main branch into test system TST. Alternatively, changes can be imported automatically by using a Jenkins pipeline, see section *Transport from dev to test system via gCTS* described in [ABAP Environment Pipeline](concepts-9482e7e.md#loio2398b874f7c5445db188b780ff0cef89). The pipeline creation is described in section *Set Up Transport from Development to Test System via gCTS* in [Prepare](develop-test-build-3bf575a.md#loio4338854e3133407abb47d3a281dbd1e1).

        > ### Note:  
        > Support package deliveries aren’t limited to changes to only one software component. But only software component support packages and patches should be included in a support package delivery. The software components that are part of an add-on product can only be changed as part of a release delivery.

    -   Test new feature in ABAP test system

        As a tester, test the new implemented features in the TST system to validate the functionality.

        Required testing can involve anything from maintaining business roles, creating communication arrangements to more complex testing scenarios where connectivity is involved. What needs to be tested is related to the implemented features.


-   **Create maintenance branch**

    For each new support package level of a software component, you, as an add-on admin user, create a maintenance branch that is used for developing bug fixes and maintaining deliveries. To do so, create branch v1.1.0 based on the main branch in the *Manage Software Components* app.

-   **Configure addon.yml file**

    As an add-on admin, change the add-on descriptor file according to the add-on product version that you want to build.

    ```
    ---
    addonProduct: "/NAMESPC/PRODUCTX"
    addonVersion: "1.1.0"
    repositories:
       - name: "/NAMESPC/PRODUCTX"
         branch: "v1.1.0"
         version: "1.1.0"
         commit ID: "12345xy"
    ```

    `addonProduct` must include the development namespace prefix and the add-on product name.

    `addonVersion` is version 1.1.0, marking a support package delivery.

    The repositories include all involved software components as well as branch and software component version to be used for the add-on build.

    The branch of software component `/NAMESPC/PRODUCTX` is pointing to the maintenance branch that was created for support package level 1. The commit ID is referencing the short commit ID for the latest changes in the maintenance branch. You can retrieve these software component details from the *Manage Software Components* app.


Maintenance branch v1.1.0, created based on the main branch, is used later on for any necessary bug fixes delivered via patches on support package level 1. This assures that these bug fixes can be implemented in the correction code line to not block ongoing development on the main branch.

**Create new release version \(product version\)**

> ### gCTS Delivery:  
> For delivering a new major version via gCTS instead of using add-ons, see section *For Go Live/Development after Go Live \(Including Deferrable Corrections\)* in [Use Case 2: One Development and Correction Codeline in a 5-System Landscape](use-case-2-one-development-and-correction-codeline-in-a-5-system-landscape-4e53874.md) and follow the steps.
> 
> -   **Develop**
> 
>     For a new major version, implement your new release deliveries in the main branch of your development system DEV and release it, see step 1-2.
> 
> -   **Test**
> 
>     Using the *Manage Software Components* app in your test system TST, pull the main branch to import the changes to your test system, see step 3-4. Test the changes to validate the functionality.
> 
> -   **Create Maintenance Branch**
> 
>     In the *Manage Software Components* app in your quality and assurance system QAS, create a new maintenance branch for your new major version. Check out the maintenance branch and test your changes, see step 5-7.
> 
> -   In your correction system COR, check out and pull the maintenance branch. In case of a deferrable correction, implement your correction in the maintenance branch of your correction system and release it \(step 8-10\). Pull the changes to your quality and assurance system \(QAS\) and test the changes, see step 12-14.
> -   **Release**
> 
>     In the *Manage Software Components* app of the provider tenant in your production system AMT, pull the maintenance branch, see step 15. The corrections and new functionalities are now imported into the production system AMT.
> 
> -   **Double Maintenance of Corrections**
> 
>     If you want to implement deferrable corrections, perform the same changes in your development system DEV. Release it to maintain it on the main branch of your software component and pull it into your test system TST, see step 16-18.
> 
> 
> See [Delivery via Add-On or gCTS](delivery-via-add-on-or-gcts-438d7eb.md#loio438d7ebfdc4a41de82dcdb156f01857e).

Release versions are used to deliver new major, planned functional enhancements. Typically, they include multiple new implemented features. For example, multiple new apps could be introduced with such a major release.

-   **Develop**
    -   Implement a new feature in the ABAP development system

        As a developer, implement the new feature in the main branch in the ABAP development system DEV. Bug fixes should be delivered via patches or support packages instead.

        After releasing the transport task and request in the development system, the changes are available for testing in the ABAP test system TST.


-   **Test**
    -   Import the main branch into the ABAP test system

        As development in system DEV is done on the main branch, the same branch is imported into the test system TST.

        As an add-on admin, use the *Manage Software Components* app to import the main branch into the test system TST so that new developments can be tested.

    -   Test the new feature in the ABAP test system

        As a tester, test the new implemented features in system TST to validate the functionality.

        Required testing can involve anything from maintaining business roles, creating communication arrangements to more complex testing scenarios where connectivity is involved.


-   **Create maintenance branch**

    For each new release version of a software component, you, as an add-on admin user, create a maintenance branch based on the main branch in development system DEV using the *Manage Software Components* app.

    1.  In the test system, open the *Manage Software Components* app.
    2.  Open the software component.
    3.  Create branch v2.0.0 based on the main branch.

-   **Configure addon.yml file**

    As an add-on admin, change the add-on descriptor file according to the add-on product version that you want to build.

    Optionally, you can specify a commit ID. All released changes up to the specified commit are included. You can retrieve this commit ID from the commit history in the *Manage Software Components* app.

    ```
    ---
    addonProduct: "/NAMESPC/PRODUCTX"
    addonVersion: "2.0.0"
    repositories:
       - name: "/NAMESPC/PRODUCTX"
         branch: "v2.0.0"
         version: "2.0.0"
         commitID: "12345xy"
    ```

    `addonProduct` must include a development namespace prefix and the add-on product name.

    `addonVersion` is version 2.0.0, marking an add-on installation delivery.

    The repositories include all involved software components as well as the branch and software component version to be used for the add-on build.

    The branch of software component `/NAMESPC/PRODUCTX` is pointing to the maintenance branch that was created for the support package level 0 of the new release version 2. The commit ID is referencing the short commit ID for the latest changes in the maintenance branch. You can retrieve these software component details from the *Manage Software Components* app.

    > ### Note:  
    > Only with new release deliveries, you can change the software component version bundle in a new release.


 <a name="loio7f6988a9a9f94845825d8c7ff66990fb"/>

<!-- loio7f6988a9a9f94845825d8c7ff66990fb -->

### Trigger Add-On Build Pipeline

> ### gCTS Delivery:  
> If you are using gCTS instead of add-ons for delivering software components into production systems, an add-on build is not required.

> ### Tip:  
> For in-depth information about the ABAP environment pipeline, check out [ABAP Environment Pipeline](concepts-9482e7e.md#loio2398b874f7c5445db188b780ff0cef89).

![](images/Pipeline_add-on_build_d36cfe1.png)

Similar to the build of the initial add-on version, as an add-on administrator, you need to trigger the execution of the configured ABAP environment pipeline for an add-on build.

Based on the target vector published in the Build stage, the Integration Tests stage of the ABAP environment pipeline creates add-on installation test system ATI. After the system and the add-on have been provisioned successfully, a provisioning mail is sent to the system administrator and the pipeline stage can be confirmed by the add-on administrator.

Use add-on installation test system ATI to confirm the successful add-on installation before the new add-on version is published.

You can also use add-on installation test system ATI for additional tests, similar to the steps described in [Test in the ABAP Environment SAP Fiori Launchpad](develop-test-build-3bf575a.md#loio8c5b4d76a05b4bed8df01937f4d8d487). For testing in a multitenancy environment, you can create tenants of type Partner Test using the Landscape Portal application. See [Use Test Tenants](use-test-tenants-dd7d8e8.md).

> ### Note:  
> Please make sure that the add-on product version to be published is properly tested before confirming the release decision. This includes testing in SAP Fiori launchpad and the ABAP Test Cockpit. See [Test in the ABAP Environment SAP Fiori Launchpad](develop-test-build-3bf575a.md#loio8c5b4d76a05b4bed8df01937f4d8d487) and [Test in the ABAP Test Cockpit](develop-test-build-3bf575a.md#loiof0b71a1c959842258772c27d292c43b0).

Finally, the previously created target vector for the new add-on product version is published in production scope after the add-on administrator has confirmed the release decision in the Confirm stage.

After a successful build, all ABAP systems used are deprovisioned and the add-on is technically available for deployment to the ABAP environment.

 <a name="loio90ada4e99f684deba48664fed04acc12"/>

<!-- loio90ada4e99f684deba48664fed04acc12 -->

### Check Add-on Build Result

Use the *Check Product Version* app in Landscape Portal to check whether the product version, its components, and respective packages are ready for delivery. See [Check Product Version](check-product-version-0da158a.md).

 <a name="loio0a80d4c5c079435e9aca4eb9e6841de9"/>

<!-- loio0a80d4c5c079435e9aca4eb9e6841de9 -->

### Deploy Add-On Update

> ### gCTS Delivery:  
> To create a new software component or update an existing one, we recommend using the development and correction codeline in a 5-ABAP-System landscape. See [Use Case 2: One Development and Correction Codeline in a 5-System Landscape](use-case-2-one-development-and-correction-codeline-in-a-5-system-landscape-4e53874.md).
> 
> Following this codeline, the software component is implemented in the development system and runs through a test, correction, and quality and assurance system before it can be imported into the production system.
> 
> See [Delivery via Add-On or gCTS](delivery-via-add-on-or-gcts-438d7eb.md#loio438d7ebfdc4a41de82dcdb156f01857e).

As a SaaS solution operator, you can apply add-on updates to existing systems via the [Update Product Version](update-product-version-32c4f7d.md) app in the Landscape Portal.

You can select the target add-on product and version for the update.

The listed add-on product versions are based on these versions where the corresponding target vector was published during the add-on build. The target vector is created as part of the add-on build process and is published in the productive scope after the release decision. See [The Add-On Product](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentAddons/#the-add-on-product).

Afterwards, you can select the systems where the update should be applied, and schedule the update.

 <a name="loio00de26798389472f989601306d2207e1"/>

<!-- loio00de26798389472f989601306d2207e1 -->

## Manage Incidents

**Incident Management System**

As a provider of a SaaS solution, you should establish an incident management system, such as SAP Resolve, so that consumers can report issues.

If consumers of your SaaS solution run into problems, they need to be able to contact the provider of the software in a standardized way.

**Information to Identify ABAP System and Consumer Tenant for Incident Processing**

To process an incident, you have to identify the ABAP system and tenant, where the consumer issue has occurred. Therefore, the following information is required:

-   SAP Fiori launchpad URL

    In the SAP Fiori launchpad user actions menu, the SAP Fiori launchpad URL of a consumer tenant is displayed as *Server* in the *Settings* dialog. See [Settings](https://experience.sap.com/fiori-design-web/services/#settings).

-   System Details

    In the user actions menu, information about the ABAP system and tenant is displayed in section *System* in the *About* dialog. See [About](https://experience.sap.com/fiori-design-web/services/#about).

    The system name and description are of particular interest.


**Information to Reproduce the Customer Issue**

To reproduce the consumer issue, the following information should be provided:

-   Application details

    In the user actions menu, information about the SAP Fiori application is displayed in the *About* dialog in the *Application* section. See [About](https://experience.sap.com/fiori-design-web/services/#about).

    The application title and technical component ID are of particular interest.

-   Error details

    The error message is displayed in the SAP Fiori application or as a status code of the HTTP request that is failing.

-   Business user details

    In the user actions menu, the name and email address identifying the business user of the consumer are displayed in the *Settings* dialog in the *User Account* section. See [Settings](https://experience.sap.com/fiori-design-web/services/#settings).

-   Step-by-Step Description of the User Actions and Input

    To reproduce the customer issue, you need detailed information about the user actions that lead to the error, and, if possible, user input that was performed during these steps.


 <a name="loio3687b52c5d3349f7956e93bf2f807e6c"/>

<!-- loio3687b52c5d3349f7956e93bf2f807e6c -->

## Troubleshoot and Debug

If a customer faces an issue, you have to provide troubleshooting based on a reported consumer incident. You can access the SAP Fiori launchpad of the consumer tenant or the backend using ABAP Development Tools to further analyze the issue.

**Identify ABAP System and Consumer Tenant**

The ABAP system can be identified in the *Systems Overview* in the Landscape Portal application. See [View Tenants and Systems](view-tenants-and-systems-99c975e.md).

The system ID is defined in the ABAP Solution service via configuration parameter `sap_system_name`. If there are multiple solutions, the system description identifies the corresponding ABAP system as it always follows the same pattern: *ABAP Solution System for <parameter "name" in ABAP Solution service\>*. See [Define Your ABAP Solution](define-your-abap-solution-1697387.md).

Based on the SAP Fiori launchpad URL of a consumer tenant, the consumer subaccount subdomain, that uniquely identifies the tenant, can be derived. The pattern to extract the subdomain is defined in `TENANT_HOST_PATTERN`. This is defined as environment variable of the deployed approuter, which is part of the multitenant application. See [Configure the Approuter Application](configure-the-approuter-application-3725815.md).

> ### Example:  
> Identifying the subdomain with a multitenant application created based on the [MTA-Based Approach \(Recommended\)](mta-based-approach-recommended-ca0cc10.md).
> 
> -   `TENANT_HOST_PATTERN = (.*)${route-prefix}.${app-domain}`
> 
> -   `${route-prefix} = <empty>`
> -   `${app-domain} = mydomain.com`
> -   SAP Fiori Launchpad URL = `myconsumer.mydomain.com`
> 
> 
> In this example, `myconsumer` is the subdomain identifying the consumer tenant.

The subdomain is displayed in the *Tenants View* as *Subaccount Domain* when selecting the system in the Landscape Portal app and thus can be used to find the consumer tenant \(business type *Partner Customer Test* and *Partner Customer Production*\).

**Access the Consumer Tenant of the ABAP System**

A consumer tenant in client \>= 200 \(business type *Partner Customer Test* or *Partner Customer Production*\) can be accessed with a provider support user created in the Landscape Portal. See [Create Support Users](create-support-users-b31712c.md).

-   **Frontend Access to SAP Fiori launchpad**

    The SAP Fiori launchpad of a consumer tenant in client \>= 200 can be accessed via the link listed in the tenant overview in the Landscape Portal. A provider support user must be requested for the tenant beforehand. Such a user can only access a limited set of SAP-provided apps, for example for Identity and Access Management and Communication Management.

-   **Backend Access using ABAP Development Tools**

    Access to a consumer tenant in client \>= 200 using ABAP Development Tools requires an adapted service key in the service instance in the SAP BTP cockpit: The service key `SAP_ASP` displayed in the cockpit needs to be adjusted with the GUID of the consumer tenant. See [Create Support Users](create-support-users-b31712c.md).


ABAP Development Tools access with a provider support user created in the Landscape Portal grants access to troubleshooting capabilities, such as those granted with business role `Application Support Engineer - Development Support (BR_APPL_SUP_ENG_DEV_SUP)`.

**Troubleshoot**

The most common use case for troubleshooting is to debug a business user or communication user executing the implemented business logic that is causing an issue in the consumer tenant. See [Troubleshoot Custom Apps](../50-administration-and-ops/troubleshoot-custom-apps-f9e1860.md).

With a provider support user, you need to connect with ABAP Development Tools to the system and consumer tenant, set a breakpoint in the logic, and afterwards the business user of the consumer must reproduce the error.

Apart from debugging, you can also use other troubleshooting tools in ABAP Development Tools to analyze issues in a consumer tenant. See [Troubleshooting Tools](../50-administration-and-ops/troubleshooting-tools-911438b.md).

