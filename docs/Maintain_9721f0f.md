<!-- loio9721f0fb92a84e2a95309acf445cb0a9 -->

# Maintain

After the initial add-on release has been shipped as a SaaS solution offering, the development of maintenance patches, support packages, and consequent add-on releases comes into play.

 <a name="loio9721f0fb92a84e2a95309acf445cb0a9 loio44035458f01e4142a18d44f9c0301e62__loio44035458f01e4142a18d44f9c0301e62"/>

<!-- loio44035458f01e4142a18d44f9c0301e62 -->

# Set Up Maintenance System Landscape

![](images/Prepare_a_Development_Account_e29111f.png)

Bug fixes aren’t implemented as part of the development code line \(systems DEV and TST\) but in a separate correction code line with separate systems to develop and test these corrections.

The ABAP systems that you use for development, testing, and add-on assembly are of type`abap/standard` and made available via entitlements. As a SaaS solution operator, you have to assign service entitlements to different subaccounts according to the following structure:


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

Entitlements



</th>
<th>

ABAP System



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

1x abap/standard

abap/hana\_compute\_unit \(standard: 4\)

abap/abap\_compute\_unit \(standard: 1\)



</td>
<td>

COR



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

1x abap/standard

abap/hana\_compute\_unit \(standard: 4\)

abap/abap\_compute\_unit \(standard: 1\)



</td>
<td>

QAS



</td>
</tr>
</table>

Use service parameter `is_development_allowed` to differentiate between development and test systems.

-   For development in the ABAP correction system COR, you, as a SaaS solution operator, create a system in the development subaccount in the development space. For correction system COR, set parameter `is_development_allowed = true`.

-   For testing in the ABAP quality assurance system QAS, you, as a SaaS solution operator, create a system in the test subaccount in the test space. For quality assurance system QAS, set parameter `is_development_allowed = false`.


Users in the ABAP correction system COR might be locked and need to be unlocked for development of corrections. See [Use Case 2: One Development and Correction Codeline in a 5-ABAP-System Landscape](Use_Case_2_One_Development_and_Correction_Codeline_in_a_5-ABAP-System_Landscape_4e53874.md)

> ### Tip:  
> For in-depth information about the system landscape/account model, check out [System Landscape/Account Model](Concepts_9482e7e.md#loio4ca756395fc24e56a42b77632a6bd862).

 <a name="loio9721f0fb92a84e2a95309acf445cb0a9 loioa35582346bff4914a5b4b0bcb776668c__loioa35582346bff4914a5b4b0bcb776668c"/>

<!-- loioa35582346bff4914a5b4b0bcb776668c -->

# Create Update for SaaS Solution

As an add-on administrator, you can provide different kinds of updates. The decision regarding which one to use depends on the motivation behind a given update.

> ### gCTS:  
> If you use gCTS, the process of creating an update for SaaS solutions is grouped into urgent corrections \(patch version\) and new releases \(release version\). See [Use Case 2: One Development and Correction Codeline in a 5-ABAP-System Landscape](Use_Case_2_One_Development_and_Correction_Codeline_in_a_5-ABAP-System_Landscape_4e53874.md)..

-   Small and urgent corrections are delivered as patches
-   Collections of less urgent corrections and other functional enhancements should be delivered as support packages
-   New release versions are released with updates containing significant enhancements and new features

> ### Note:  
> New features are developed on different code lines \(branches\). If you create a so-called maintenance branch to implement patches while new features are implemented in the main branch of a software component, you can implement new features and provide bug fixes at the same time. For more information, see [Versioning and Branches](Concepts_9482e7e.md#loio8c087bca40584f9b899282b4ec515753).
> 
> To learn more about terminology related to software lifecycle management in the ABAP environment, such as cloning and checkout, see [Basic Concepts and Terms](Basic_Concepts_and_Terms_fb3a076.md).

**Create new patch version \(emergency patch\)**

> ### gCTS:  
> For delivering an emergency patch via gCTS instead of using add-ons, see section *Urgent Corrections* in [Use Case 2: One Development and Correction Codeline in a 5-ABAP-System Landscape](Use_Case_2_One_Development_and_Correction_Codeline_in_a_5-ABAP-System_Landscape_4e53874.md) and follow the steps.
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

> ### Note:  
> For the new patch version, you can use a permanent add-on assembly system to save build time. See [ABAP System Types: Transient and Permanent Systems](Concepts_9482e7e.md#loio52fb6a9e22714843b6e83b7f333b184b).

Small corrections are delivered as patches, also known as emergency patches.

-   **Develop**
    -   Import the maintenance branch in the ABAP correction system

        Bug fixes are delivered as a new patch version of a software component and are implemented on the correction code line. Therefore, the dedicated ABAP correction system COR is used.

        As an add-on admin, check out the maintenance branch, which is the branch that is created for bug fixes and maintenance deliveries. See [How to Work with Branches](How_to_Work_with_Branches_6b2f0bf.md).

    -   Implement the bug fix in the ABAP correction system

        As a developer, implement the required changes to the software component in the ABAP correction system COR. These changes shouldn’t introduce new features because patch versions should only contain small emergency corrections.

        For more information on the different software component versions, see [The Add-on Product](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentAddons/#the-add-on-product) .

        After releasing the transport tasks and requests in the correction system, the changes are imported into and tested in the quality assurance system.

-   **Test**
    -   Import the maintenance branch in the ABAP quality assurance system

        You need to test the implemented corrections by importing the maintenance branch for the current support package level, where the transports for necessary bug fixes were released, in the dedicated test system, which is the ABAP quality assurance system QAS.

        [How to Pull Software Component](How_to_Pull_Software_Component_90b9b9d.md).

    -   Test bugfix in ABAP quality assurance system

        As a tester, test the corrections in the QAS system to validate that the provided bug fixes are solving the problem and are working properly.As an add-on admin, use the software components app to import the latest changes into the quality assurance system QAS. See

        Required testing can involve anything from maintaining business roles, creating communication arrangements to more complex testing scenarios where connectivity is involved. See [Maintain Business Roles](Maintain_Business_Roles_8980ad0.md), [How to Create a Communication Arrangement](How_to_Create_a_Communication_Arrangement_a0771f6.md), and [Connectivity](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e54cc8fbbb571014beb5caaf6aa31280.html). What needs to be tested is related to the implemented corrections.

-   **Double maintenance of corrections into development**

    As an add-on admin, useAs a developer, you have to maintain the corrections that have been developed and tested in the ABAP correction system COR and quality assurance system QAS in the development system DEV \(so called double-maintenance\). See [Double Maintenance of Corrections into Development](Double_Maintenance_of_Corrections_into_Development_1241b14.md).

-   **Configure addon.yml file**

    As an add-on admin, change the add-on descriptor file according to the add-on product version that you want to build.

    Optionally, you can specify a commit ID. All released changes up to the specified commit are included. You can retrieve this ID from the branch history in the *Manage Software Components* app.

    ```
    ---
    addonProduct: /NAMESPC/PRODUCTX
    addonVersion: 1.0.1
    repositories:
       - name: /NAMESPC/PRODUCTX
         branch: v1.0.0
         version: 1.0.1
         commitID: 12345xy
    
    ```

    See [Build and Publish Add-on Products on SAP BTP ABAP Environment](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentAddons/#addonyml).

    `addonProduct` must include the development namespace prefix.

    `addonVersion` is version 1.0.1, marking a patch delivery.

    The repositories include all involved software components as well as the branch and software component version to be used for the add-on build.

    In the example configuration, the branch of software component `/NAMESPC/PRODUCTX` is pointing to the maintenance branch v1.0.0 as the bug fix is based on the delivered support package level 0 of software component release 1. The commit ID is referencing the short commit ID for the latest changes in the maintenance branch. You can retrieve these software component details from the *Manage Software Components* app.


**Create new support package version \(hotfix collection\)**

Larger collections of corrections and smaller function enhancements are delivered as support packages.

-   **Develop**
    -   Implement new feature in ABAP development system

        As a developer, implement the new feature in the main branch in the ABAP development system DEV. Bug fixes should be delivered via patch deliveries if they need to be available before the next support package delivery cycle. See [The Add-On Product](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentAddons/#the-add-on-product).

        After releasing the transport task and request in the development system, you can import the changes for testing in the ABAP test system TST.

-   **Test**
    -   Import main branch into ABAP test system

        As development in system DEV is done on the main branch, the same branch is imported into the test system.

        As an add-on admin, use the *Manage Software Components* app to import the changes in the main branch into test system TST. Alternatively, changes can be imported automatically by using a Jenkins pipeline, see section *Transport from dev to test system via gCTS* described in [ABAP Environment Pipeline](Concepts_9482e7e.md#loio2398b874f7c5445db188b780ff0cef89). The pipeline creation is described in section *Set Up Transport from Development to Test System via gCTS* in [Prepare](Develop,_Test,_Build_3bf575a.md#loio4338854e3133407abb47d3a281dbd1e1).

        > ### Note:  
        > Support package deliveries aren’t limited to changes to only one software component. But only software component support packages and patches should be included in a support package delivery. The software components that are part of an add-on product can only be changed as part of a release delivery.

    -   Test new feature in ABAP test system

        As a tester, test the new implemented features in the TST system to validate the functionality.

        Required testing can involve anything from maintaining business roles, creating communication arrangements to more complex testing scenarios where connectivity is involved. What needs to be tested is of course related to the implemented features.

-   **Create maintenance branch**

    For each new support package level of a software component, you, as an add-on admin user, create a maintenance branch that is used for developing bug fixes and maintaining deliveries. To do so, create branch v1.1.0 based on the main branch in the *Manage Software Components* app.

-   **Configure addon.yml file**

    As an add-on admin, change the add-on descriptor file according to the add-on product version that you want to build.

    ```
    ---
    addonProduct: /NAMESPC/PRODUCTX
    addonVersion: 1.1.0
    repositories:
       - name: /NAMESPC/PRODUCTX
         branch: v1.1.0
         version: 1.1.0
         commit ID: 12345xy
    ```

    `addonProduct` must include the development namespace prefix.

    `addonVersion` is version 1.1.0, marking a support package delivery.

    The repositories include all involved software components as well as branch and software component version to be used for the add-on build.

    The branch of software component `/NAMESPC/PRODUCTX` is pointing to the maintenance branch that was created for support package level 1. The commit ID is referencing the short commit ID for the latest changes in the maintenance branch. You can retrieve these software component details from the *Manage Software Components* app.

    > ### Note:  
    > Maintenance branch v1.1.0, created based on the main branch, is used later on for any necessary bug fixes delivered via patches on support package level 1. This assures that these bug fixes can be implemented in the correction code line to not block ongoing development on the main branch.


**Create new release version \(product version\)**

> ### gCTS:  
> For delivering a new product version via gCTS instead of using add-ons, see section *For Go Live/Development after Go Live \(Including Deferrable Corrections\)* in [Use Case 2: One Development and Correction Codeline in a 5-ABAP-System Landscape](Use_Case_2_One_Development_and_Correction_Codeline_in_a_5-ABAP-System_Landscape_4e53874.md) and follow the steps.
> 
> -   **Develop**
> 
>     For a new product version, implement your new release deliveries in the main branch of your development system DEV and release it, see step 1-2.
> 
> -   **Test**
> 
>     Using the *Manage Software Components* app in your test system TST, pull the main branch to import the changes to your test system, see step 3-4. Test the changes to validate the functionality.
> 
> -   **Create Maintenance Branch**
> 
>     In the *Manage Software Components* app in your quality and assurance system QAS, create a new maintenance branch for your new product version. Check out the maintenance branch and test your changes, see step 5-7.
> 
> -   In your correction system COR, check out and pull the maintenance branch. In case of a deferrable correction, implement your correction in the maintenance branch of your correction system and release it \(step 8-10\). Pull the changes to your quality and assurance system \(QAS\) and test the changes, see step 12-14.
> -   **Release**
> 
>     In the *Manage Software Components* app of the provider tenant in your production system AMT, pull the maintenance branch, see step 15. The corrections and new functionalities are now imported into the production system AMT.
> 
> -   **Double Maintenance of Corrections**
> 
>     If you want to implement deferrable corrections, perform the same changes in your development system DEV. Release it to maintain it on the main branch of your software component and pull it into your test system TST, see step 16-18.

> ### Note:  
> The software components that are part of an add-on product can only be changed as part of a release delivery.

Release deliveries that contain the whole software component and deliver new functionalities as well as enhancements of existing functionalities.

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

    For each new release version of a software component, you, as an add-on admin user, create a maintenance branch v1.1.0 based on the main branch in development system DEV using the *Manage Software Components* app.

    1.  In the test system, open the *Manage Software Components* app.
    2.  Open the software component.
    3.  Create branch v2.0.0 based on the main branch.
-   **Configure addon.yml file**

    As an add-on admin, change the add-on descriptor file according to the add-on product version that you want to build.

    Optionally, you can specify a commit ID. All released changes up to the specified commit are included. You can retrieve this ID from the branch history in the *Manage Software Components* app.

    ```
    ---
    addonProduct: /NAMESPC/PRODUCTX
    addonVersion: 2.0.0
    repositories:
       - name: /NAMESPC/PRODUCTX
         branch: v2.0.0
         version: 2.0.0
         commitID: 12345xy
    ```

    `addonProduct` must include a development namespace prefix.

    `addonVersion` is version 2.0.0, marking an add-on installation package delivery.

    The repositories include all involved software components as well as the branch and software component version to be used for the add-on build.

    The branch of software component `/NAMESPC/PRODUCTX` is pointing to the maintenance branch that was created for the support package level 0 of the new release version 2. The commit ID is referencing the short commit ID for the latest changes in the maintenance branch. You can retrieve these software component details from the *Manage Software Components* app.

    > ### Note:  
    > Only with new release deliveries, you can change the software component version bundle in a new release.


 <a name="loio9721f0fb92a84e2a95309acf445cb0a9 loio7f6988a9a9f94845825d8c7ff66990fb__loio7f6988a9a9f94845825d8c7ff66990fb"/>

<!-- loio7f6988a9a9f94845825d8c7ff66990fb -->

# Trigger Add-On Product Build

> ### gCTS:  
> If you are using gCTS instead of add-on for delivering software components into production systems, an add-on build is not required.

Similar to the build of the initial add-on version, you, as an add-on administrator, need to trigger the execution of the configured ABAP environment pipeline for an add-on build.

![](images/Pipeline_add-on_build_d36cfe1.png)

 <a name="loio9721f0fb92a84e2a95309acf445cb0a9 loio0a80d4c5c079435e9aca4eb9e6841de9__loio0a80d4c5c079435e9aca4eb9e6841de9"/>

<!-- loio0a80d4c5c079435e9aca4eb9e6841de9 -->

# Apply Update for SaaS Solution

> ### gCTS:  
> If you are using gCTS instead of add-on for delivering software components into production systems, an add-on build is not required.

As a SaaS solution operator, you can apply add-on updates to existing systems via the Landscape Portal. See [Landscape Portal](Landscape_Portal_5eb70fb.md).

> ### Note:  
> Keep in mind that you can't select the target version of the update. The latest released version \(target vector for add-on product published with productive scope\) is automatically determined. The target vector is created as part of the add-on build process and is published in the productive scope after the release decision. See [The Add-On Product](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentAddons/#the-add-on-product).

> ### Note:  
> If you need support or experience issues, please report an incident under component `BC-CP-ABA-LP`.

