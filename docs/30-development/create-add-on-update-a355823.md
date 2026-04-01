<!-- loioa35582346bff4914a5b4b0bcb776668c -->

# Create Add-On Update

As an add-on administrator, you can provide different kinds of updates. The decision regarding which one to use depends on the motivation behind a given update.

-   Small and urgent corrections are delivered as patches
-   Collections of less urgent corrections and other functional enhancements should be delivered as support packages
-   New release versions are released with updates containing significant enhancements and new features

> ### Tip:  
> Use the [Check Product Version](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/4de24e56f52d4ca4ae8971aae6861f8e.html) app in the Landscape Portal to find out which product version has already been built.

> ### Note:  
> If you use gCTS for delivery, the process of creating an update for SaaS solutions is grouped into urgent corrections \(patch version\) and new releases \(release version\). See [Use Case 2: One Development and Correction Codeline in a 5-System Landscape](https://help.sap.com/docs/btp/sap-business-technology-platform/use-case-2-one-development-and-correction-codeline-in-5-system-landscape?version=Cloud) and [Delivery via Add-On or gCTS](https://help.sap.com/docs/btp/sap-business-technology-platform/delivery-via-add-on-or-gcts?version=Cloud).
> 
> For delivering an emergency patch via gCTS, see section *Urgent Corrections* in [Use Case 2: One Development and Correction Codeline in a 5-System Landscape](https://help.sap.com/docs/btp/sap-business-technology-platform/use-case-2-one-development-and-correction-codeline-in-5-system-landscape?version=Cloud).
> 
> For delivering a new major version via gCTS instead of using add-ons, see section *For Go Live/Development after Go Live \(Including Deferrable Corrections\)* in [Use Case 2: One Development and Correction Codeline in a 5-System Landscape](https://help.sap.com/docs/btp/sap-business-technology-platform/use-case-2-one-development-and-correction-codeline-in-5-system-landscape?version=Cloud).
> 
> For general information regarding gCTS delivery, see [Delivery via Add-On or gCTS](https://help.sap.com/docs/btp/sap-business-technology-platform/delivery-via-add-on-or-gcts?version=Cloud).

**Create new patch version \(emergency patch\)**

Patch versions are used to deliver unplanned and most likely urgent corrections that are required to keep the application up and running. These changes could be required for a service consumption model of an OData Client Proxy in case of changes to the structure of the underlying OData service. See [Consuming an OData Service](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/consume-odata-service).

Bug fixes are delivered as a new patch version of a software component and are implemented on the correction code line. Therefore, the dedicated ABAP correction system COR is used. For more information on the different software component version numbers, see [Software Component Version](https://www.project-piper.io/scenarios/abapEnvironmentAddons/#software-component-version).

> ### Note:  
> While creating patch versions for the same support package level or release version, the same maintenance branch should be used.

To deliver a new patch version, see the following steps:

-   **Develop**
    -   As an add-on admin, check out the maintenance branch, which is the branch that is created for bug fixes and maintenance deliveries in correction system COR and quality assurance system QAS. See [Work with Branches](../50-administration-and-ops/work-with-branches-6b2f0bf.md).

    -   In case of released APIs: If not already done, upload the API snapshot that was created for the latest support package or release version into quality assurance system QAS and correction system COR. Set the API snapshot to check-relevant if not already enabled. See [Manage API Snapshots](https://help.sap.com/docs/btp/sap-business-technology-platform/manage-api-snapshots?version=Cloud).

        > ### Note:  
        > While creating new patch versions, the maintenance branch is usually checked out for the first time in correction system COR and quality assurance system QAS. Thus, the corresponding snapshot must uploaded and set to check-relevant. See [Released APIs and API Snapshots](https://help.sap.com/docs/btp/sap-business-technology-platform/concepts?version=Cloud#released-apis-and-api-snapshots).

    -   Implement the bug fix in the ABAP correction system

        As a developer, implement the required changes to the software component in the ABAP correction system COR. These changes shouldn’t introduce new features because patch versions should only contain small emergency corrections. Release the transport tasks and requests.


-   **Test**
    -   Import the maintenance branch in the ABAP quality assurance system

        You need to test the implemented corrections by importing the maintenance branch for the current support package level, where the transports for necessary bug fixes were released, in the dedicated test system, which is the ABAP quality assurance system QAS. See [Pull Software Components](../50-administration-and-ops/pull-software-components-90b9b9d.md).

    -   Test bugfix in ABAP quality assurance systemAs a tester, test the corrections in the QAS system to validate that the provided bug fixes are solving the problem and are working properly. Required testing can involve anything from maintaining business roles, creating communication arrangements to more complex testing scenarios where connectivity is involved.

-   **Double maintenance of corrections into development**

    As a developer, you have to maintain the corrections that have been developed in the ABAP correction system COR as separate transports in development system DEV \(so called double-maintenance\). See [Double Maintenance of Corrections into Development](double-maintenance-of-corrections-into-development-1241b14.md).

-   **Configure new product version**

    As an add-on admin, you can use the Build Product Version app in the Landscape Portal to create new patches:

-   Make sure that the pipeline template for Patch Delivery is configured. If you want to validate the add-on build beforehand, configure the template for Test Patch Delivery as well. See [Configure Pipeline Template](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/5919ca97b3d54c758cf56dfb0887c306.html).

-   Choose the parent version that shall be patched and create a new product version of type Patch Delivery. See [Create a New Product Version](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/d4c9f0877f1640bebe1f6fbe267bf9af.html).


If you are configuring the add-on build pipeline manually, adjust your add-on descriptor file to build the new patch version. See [Build and Publish Add-on Products on SAP BTP ABAP Environment](https://www.project-piper.io/scenarios/abapEnvironmentAddons/#addonyml).

**Create new support package version \(hotfix collection\)**

Support package versions are used to deliver planned functional enhancements outside of new major releases. They are often used to bundle multiple patch versions to a hotfix collection.

A support package version could be used for example to deliver a new simple business configuration UI. See [Business Configuration in SAP BTP ABAP Environment \(1\): Overview and BC Maintenance Apps](https://blogs.sap.com/2021/09/22/business-configuration-in-sap-btp-abap-environment-1-overview-and-bc-maintenance-apps/).

> ### Note:  
> Support package deliveries aren’t limited to changes to only one software component. But only software component support packages and patches should be included in a support package delivery. The software components that are part of an add-on product can only be changed as part of a release delivery.

> ### Note:  
> If you use a quarterly delivery approach, new features are not delivered using support package versions. Instead, a new maintenance branch is created from the previous maintenance branch, using systems COR and QAS instead. See [Delivery Models](https://help.sap.com/docs/btp/sap-business-technology-platform/concepts?version=Cloud#loio326508756a144c49b98e5fcf442cce40).

To deliver a new support package stack, see the following steps:

-   **Develop**
    -   As a developer, implement the new feature in the main branch in the ABAP development system DEV. Bug fixes should be delivered via patch deliveries if they need to be available before the next support package delivery cycle. See [The Add-On Product](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentAddons/#the-add-on-product).

-   **Test**

    As an add-on admin, use the *Manage Software Components* app to import the changes in the main branch into test system TST.

-   As a tester, test the new implemented features in the TST system to validate the functionality.

    Required testing can involve anything from maintaining business roles, creating communication arrangements to more complex testing scenarios where connectivity is involved.

-   **Create maintenance branches**

    As an add-on admin, create a new maintenance branch for each new support package level of a software component. These maintenance branches are used for developing bug fixes and maintaining deliveries. This assures that these bug fixes can be implemented in the correction code line to not block ongoing development on the main branch.

-   **Create new product version**

    As an add-on admin, you can use the Build Product Version app in the Landscape Portal to create new support package stacks:

    1.  Make sure that the pipeline template for Suport Package Stack is configured. If you want to validate the add-on build beforehand, configure the template for Test Support Package Stack as well. See [Configure a Pipeline Template](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/5919ca97b3d54c758cf56dfb0887c306.html).
    2.  Choose the parent version that shall be patched and create a new product version of type Patch Delivery. See [Create a New Product Version](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/d4c9f0877f1640bebe1f6fbe267bf9af.html).

    If you are configuring the add-on build pipeline manually, adjust your add-on descriptor file to build the new patch version. See [Build and Publish Add-on Products on SAP BTP ABAP Environment](https://www.project-piper.io/scenarios/abapEnvironmentAddons/#addonyml).


-   **Download API Snapshot for use in other systems**

    In case of released APIs, download the API snapshot created for the new support package version from the add-on build system BLD. The snapshot is created automatically during the add-on build. Afterwards, upload the snapshot into the test system TST and the development System DEV. Set the new API snapshot as check-relevant so that it will be used as a reference for API compatibility checks.


**Create new release version \(product version\)**

Release versions are used to deliver new major, planned functional enhancements. Typically, they include multiple new implemented features. For example, multiple new apps could be introduced with such a major release.

> ### Note:  
> Only with new release deliveries, you can change the software component version bundle in a new release.

To deliver a new release version, see the following steps:

-   **Develop**

    As a developer, implement the new feature in the main branch in the ABAP development system DEV. Bug fixes should be delivered via patches or support packages instead. Release the transport tasks and requests.

-   **Test**

    As an add-on admin, use the *Manage Software Components* app to import the main branch into the test system TST so that new developments can be tested.

    As a tester, test the new implemented features in system TST to validate the functionality.

    Required testing can involve anything from maintaining business roles, creating communication arrangements to more complex testing scenarios where connectivity is involved.

-   **Create maintenance branches**

    As an add-on admin, create a new maintenance branch for each new release version of a software component. These maintenance branches are used for developing bug fixes and maintaining deliveries. This assures that these bug fixes can be implemented in the correction code line to not block ongoing development on the main branch.

-   **Configure new product version**

    As an add-on admin, you can use the Build Product Version app in the Landscape Portal to create new release versions:

    1.  Make sure that the pipeline template for Release Delivery is configured. If you want to validate the add-on build beforehand, configure the template for *Test Release Delivery* as well. See [Configure Pipeline Template](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/5919ca97b3d54c758cf56dfb0887c306.html).

    2.  Choose the relevant add-on product and create a new product version of type *Release Delivery*. See [Create a New Product Version](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/d4c9f0877f1640bebe1f6fbe267bf9af.html).

-   **Download API Snapshot for use in other systems**

    In case of released APIs, download the API snapshot created for the new release version from the add-on build system BLD. The snapshot is created automatically during the add-on build. Afterwards, upload the snapshot into the test system TST and the development System DEV. Set the new API snapshot as check-relevant so that it will be used as a reference for API compatibility checks.


If you are configuring the add-on build pipeline manually, adjust your add-on descriptor file to build the new patch version. See [Build and Publish Add-on Products on SAP BTP ABAP Environment](https://www.project-piper.io/scenarios/abapEnvironmentAddons/#addonyml).

