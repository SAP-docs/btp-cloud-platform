<!-- loiodac47aed9ca24e87953905e078f13c29 -->

# Configure a Pipeline Template

The *Build Product Version* app offers templates based on the [ABAP Environment Pipeline](https://www.project-piper.io/pipelines/abapEnvironment/introduction/) that you can configure for the following types of pipelines:


<table>
<tr>
<th valign="top">

Type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Release Delivery



</td>
<td valign="top">

Release versions of the product usually include new deliveries of software components that are planned and used for new functionalities and feature enhancements. In case of multiple software components, release deliveries may also include new support package- or patch deliveries of software components. Not yet included software components can only be added with a new release delivery version of the product. The template can be executed using a transient build system or to create a new permanent build system which can be reused to create patches or support packages. Additionally, the integration test stage should be performed.



</td>
</tr>
<tr>
<td valign="top">

Support Package Stack



</td>
<td valign="top">

Support package stack deliveries of the product usually include new support package deliveries of software components that are planned and used for smaller functional enhancements. Support package deliveries of software components are created based on a delta comparison in regard to the previous support package level in the same release. In case of multiple software components, support package stacks may also include new patch deliveries of software components. The template can be executed using a transient build system or to create a new permanent build system which can be reused to create patches. Additionally, an installation test should be performed.



</td>
</tr>
<tr>
<td valign="top">

Patch Delivery



</td>
<td valign="top">

Patch delivery versions of the product should only include new patch deliveries of software components that contain unplanned, urgent and small corrections. Patch deliveries of software components are created based on a delta comparison in regard to the previous patch level on the same support package, in the same release. The template should be executed using a permanent build system and an update test should be performed.



</td>
</tr>
<tr>
<td valign="top">

Test Release Delivery



</td>
<td valign="top">

Release versions of the product usually include new deliveries of software components that are planned and used for new functionalities and feature enhancements. *Test Release Delivery* is part of the continuous testing in the development process. The run performs static code checks and builds the next release delivery locally \(no upload to the product framework\) to detect findings early that might delay a productive build later on. It should be executed using a permanent build system. Execution of an integration test stage is not possible as no package is uploaded to the product framework.

The generated product versions in the test run are not released, thus the versioning of the build runs can be reused for multiple runs, and hence reducing the consumption of product version numbers.



</td>
</tr>
<tr>
<td valign="top">

Test Support Package Stack



</td>
<td valign="top">

Support package stack deliveries of the product usually include new support package deliveries of software components that are planned and used for smaller functional enhancements. *Test Support Package* is part of the continuous testing in the development branch. The run performs static code checks and builds the next support package locally \(no upload to the product framework\) to detect findings early that might delay a productive build. It should be executed using a permanent build or test system dedicated to the development branch. An add-on update test is not possible as no package is uploaded to the product framework.

The generated product versions in the test run mode are not released, thus the versioning of the build runs can be reused for multiple runs, and hence reducing the consumption of product version numbers.



</td>
</tr>
<tr>
<td valign="top">

Test Patch Delivery



</td>
<td valign="top">

Patch delivery versions of the product should only include new patch deliveries of software components that contain unplanned, urgent and small corrections. *Test Patch Delivery* is part of the continuous testing in the development branch. The run performs static code checks and builds the next patch delivery locally \(no upload to the product framework\) to detect findings early that might delay a productive build. It should be executed using a permanent build or test system dedicated to the development branch. An add-on update test is not possible as no package is uploaded to the product framework.

The generated product versions in the test run mode are not released, thus the versioning of the build runs can be reused for multiple runs, and hence reducing the consumption of product version numbers.



</td>
</tr>
</table>

These three different pipeline templates need to be configured for each of your products. For each template you add information on the credentials that should be used, the clone strategy, software components, tests, and more. Once you’ve configured the templates for a product, you can easily trigger the build of new versions \(be it release deliveries, support package stacks or patch deliveries\) of this product based on the information given in the templates. For more information on add-on product/software component versioning, see [The Add-On Product.](https://www.project-piper.io/scenarios/abapEnvironmentAddons/#the-add-on-product)

Let’s take a closer look at how to configure a pipeline template for a product:

1.  Log in to the *Landscape Portal* and click on the tile *Build Product Version*.

2.  Select one of your products from the list and navigate to the *Templates* tab. The templates table displays whether the templates have already been configured for this product. Select the template type that you would like to configure.

    You will now be guided through a series of steps. Please be aware that fields marked with a red asterisk are mandatory and need to be filled out.

3.  **Prepare System:**

    In this section you can configure a job that will build your product.


    <table>
    <tr>
    <th valign="top">

    Group


    
    </th>
    <th valign="top">

    Field


    
    </th>
    <th valign="top">

    Explanation


    
    </th>
    <th valign="top">

    Remarks


    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
        Cloud Foundry


    
    </td>
    <td valign="top">
    
        API Endpoint


    
    </td>
    <td valign="top">
    
        The Cloud Foundry API endpoint specific to the region of the Cloud Foundry Environment to be used. See [Regions and API Endpoints for the ABAP Environment.](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/879f37370d9b45e99a16538e0f37ff2c.html)


    
    </td>
    <td valign="top">
    
        Can be retrieved from Subaccount Overview in BTP Cockpit → Cloud Foundry Environment → API Endpoint


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
         


    
    </td>
    <td valign="top">
    
        Credential Name


    
    </td>
    <td valign="top">
    
        The credentials for the space developer user to authenticate to the Cloud Foundry API. See [Creating New Space Members and Assigning Space Developer Roles to Them.](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/967fc4e2b1314cf7afc7d7043b53e566.html)


    
    </td>
    <td valign="top">
    
        User needs to be org member and assigned to space withs space developer role


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
         


    
    </td>
    <td valign="top">
    
        Organization


    
    </td>
    <td valign="top">
    
        The Cloud Foundry org used to create the assembly system. See [Managing Orgs.](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/fe1ebf3cd6fe46798efcaf45c73a54ce.html)


    
    </td>
    <td valign="top">
    
        Can be retrieved from Subaccount Overview in BTP Cockpit → Cloud Foundry Environment → Org Name


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
         


    
    </td>
    <td valign="top">
    
        Space


    
    </td>
    <td valign="top">
    
        The Cloud Foundry space used to create the assembly system. See [Managing Spaces.](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/5209d55d8dd84228897112b0655d999b.html)


    
    </td>
    <td valign="top">
    
         


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        Assembly System


    
    </td>
    <td valign="top">
    
        Service Instance Name


    
    </td>
    <td valign="top">
    
        The name of the ABAP Service instance for the assembly of the product version. See [Creating an ABAP System.](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/50b32f144e184154987a06e4b55ce447.html)

    The installation test system is created with service plan `abap/standard.`


    
    </td>
    <td valign="top">
    
        The service instance name can be used to identify systems in Systems Overview application


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
         


    
    </td>
    <td valign="top">
    
        System ID


    
    </td>
    <td valign="top">
    
        The three-character name of the assembly system. This maps to `sap_system_name` service instance parameter.


    
    </td>
    <td valign="top">
    
        The system ID can be used to identify systems in Systems Overview application


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
         


    
    </td>
    <td valign="top">
    
        System Admin E-Mail


    
    </td>
    <td valign="top">
    
        The email-address for the initial administrator in the assembly system. This administrator can be used to access the system in case of errors if the "Keep System" flag has been selected and the system was created from scratch. See [Creating an ABAP System](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/50b32f144e184154987a06e4b55ce447.html).


    
    </td>
    <td valign="top">
    
         


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
         


    
    </td>
    <td valign="top">
    
        Keep System


    
    </td>
    <td valign="top">
    
        Check this box if the system should be kept after the build is complete to allow debugging. Please be aware that the system occurs in costs and you are responsible for deleting the system manually once you have finished.


    
    </td>
    <td valign="top">
    
         


    
    </td>
    </tr>
    </table>
    
    Proceed to the next step.

4.  **Clone Repositories:**

    Here you can select the clone strategy \(*CheckoutPull*, *Clone*, *Pull*\) for software components that are relevant for the build of the product version. This influences which steps will be executed to import the repositories. For more information, see [Clone Repositories](https://www.project-piper.io/pipelines/abapEnvironment/stages/cloneRepositories/).

    Select the desired clone strategy from the drop-down menu and proceed to the next step.

5.  **ATC:**

    The ABAP Test Cockpit \(ATC\) can check the software components which will be assembled as part of the product version build. Select whether the ATC stage should be executed and enter the ATC check variant that should be used to check the configured software. Then proceed to the next step.

    Without Run ATC Stage enabled, you risk a defective product version being built.

    > ### Note:  
    > Created delivery packages for an add-on product version are final, so to fix any errors in these packages, another add-on product version would have to be built. ATC findings should be resolved during development as early as possible, e.g. [during transport release](https://help.sap.com/docs/BTP/5371047f1273405bb46725a417f95433/c0d95a9263da476eb5b6ae03225ce7ba.html?version=Cloud) and by using an additional pipeline configured for the [Continuous Testing on SAP BTP, ABAP Environment scenario.](https://www.project-piper.io/scenarios/abapEnvironmentTest/)

6.  **Build:**

    In this step, a system is prepared for the product version build. Per default, the system will be deprovisioned after a successful build has been completed. You can, however, override this in order to perform checks in that system.

    Enter the information needed for the build of the product version.


    <table>
    <tr>
    <th valign="top">

    Group


    
    </th>
    <th valign="top">

    Field


    
    </th>
    <th valign="top">

    Explanation


    
    </th>
    <th valign="top">

    Remarks


    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
        AAKaaS


    
    </td>
    <td valign="top">
    
        Credential Name


    
    </td>
    <td valign="top">
    
        The credential name referring to a [2174416](https://launchpad.support.sap.com/#/notes/2174416)technical communication user used to access Add-on Assembly Kit as a Service


    
    </td>
    <td valign="top">
    
         


    
    </td>
    </tr>
    </table>
    
    Proceed to the next step

7.  **Integration Tests**

    Please notice that this step is mandatory to execute in order to achieve a secured deployment in production.

    The possibility to disable it might be turned off without any further notice from SAP in the future.

    In this stage a system is prepared for the product version test installation. The system will be deprovisioned after successful testing has been completed.

    Enter the information.

    > ### Note:  
    > The pipeline step '5. Integration Tests' is inactive when you are configuring a test template.


    <table>
    <tr>
    <th valign="top">

    Group


    
    </th>
    <th valign="top">

    Field


    
    </th>
    <th valign="top">

    Explanation


    
    </th>
    <th valign="top">

    Remarks


    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
         


    
    </td>
    <td valign="top">
    
        Run Integration Test Stage:


    
    </td>
    <td valign="top">
    
        Check this box if the integration test stage should be executed.


    
    </td>
    <td valign="top">
    
        The Run Integration Test Stage prevents from defective add-ons being installed onto the production system.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        Cloud Foundry


    
    </td>
    <td valign="top">
    
         


    
    </td>
    <td valign="top">
    
         


    
    </td>
    <td valign="top">
    
         


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
         


    
    </td>
    <td valign="top">
    
        API Endpoint


    
    </td>
    <td valign="top">
    
        The Cloud foundry API endpoint specific to the region of Cloud Foundry Environment to be used. See [Regions and API Endpoints for the ABAp Environment.](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/879f37370d9b45e99a16538e0f37ff2c.html)


    
    </td>
    <td valign="top">
    
        Can be retrieved from Subaccount Overview in BTP Cockpit → Cloud Foundry Environment → API Endpoint


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
         


    
    </td>
    <td valign="top">
    
        Credential Name


    
    </td>
    <td valign="top">
    
        The credentials for the space developer user to authenticate to the Cloud Foundry API. See [Creating New Space Members an Assigning Space Developer Roles to Them.](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/967fc4e2b1314cf7afc7d7043b53e566.html)


    
    </td>
    <td valign="top">
    
        User needs to be org member and assigned to space withs space developer role


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
         


    
    </td>
    <td valign="top">
    
        Organization


    
    </td>
    <td valign="top">
    
        The Cloud Foundry org used to create the integration test system. See [Managing Orgs.](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/fe1ebf3cd6fe46798efcaf45c73a54ce.html)


    
    </td>
    <td valign="top">
    
        Can be retrieved from Subaccount Overview in BTP Cockpit → Cloud Foundry Environment → Org Name


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
         


    
    </td>
    <td valign="top">
    
        Space


    
    </td>
    <td valign="top">
    
        The Cloud Foundry space used to create the integration test system. See [Managing Spaces.](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/5209d55d8dd84228897112b0655d999b.html)


    
    </td>
    <td valign="top">
    
         


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        Installation Test System


    
    </td>
    <td valign="top">
    
        Service Instance Name


    
    </td>
    <td valign="top">
    
        The name of the ABAP Service instance for the installation test of the product version. See [Creating an ABAP System.](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/50b32f144e184154987a06e4b55ce447.html)

    The installation test system is created with service plan `abap/saas_oem.`


    
    </td>
    <td valign="top">
    
        The service instance name can be used to identify systems in Systems Overview application


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
         


    
    </td>
    <td valign="top">
    
        System ID


    
    </td>
    <td valign="top">
    
        The three-character name of the integration system. This maps to `sap_system_name` service instance parameter.


    
    </td>
    <td valign="top">
    
        The system ID can be used to identify systems in Systems Overview application


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
         


    
    </td>
    <td valign="top">
    
        System Admin E-Mail


    
    </td>
    <td valign="top">
    
        The email-address for the initial administrator of the integration test system. This user can be used to access the system for error analysis purposes. See [Creating an ABAP System.](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/50b32f144e184154987a06e4b55ce447.html)

    The email-address for the initial administrator of the integration test system. This user can be used to access the system for error analysis purposes.


    
    </td>
    <td valign="top">
    
         


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
         


    
    </td>
    <td valign="top">
    
        Keep System


    
    </td>
    <td valign="top">
    
        Check this box if the system should be kept after the build is complete to allow debugging. Please be aware that the system occurs in costs and you are responsible for deleting the system manually once you have finished.


    
    </td>
    <td valign="top">
    
         


    
    </td>
    </tr>
    </table>
    
    Click on *Finish* to complete the template configuration.


