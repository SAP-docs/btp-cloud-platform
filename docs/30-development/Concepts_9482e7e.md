<!-- loio9482e7eef4634cb993a4ae296b2029fa -->

# Concepts

Learn more about the system landscape/account model, ABAP environment pipeline, as well as versioning and branches.

 <a name="loio4ca756395fc24e56a42b77632a6bd862"/>

<!-- loio4ca756395fc24e56a42b77632a6bd862 -->

## System Landscape/Account Model

To separate development and productive systems, the recommended account model involves two global accounts in the Cloud Foundry environment. For both, a partner contract is required.

-   **Global development account**

    The development global account is used for add-on/UI development, testing, and add-on assembly as part of the add-on build pipeline.

    All ABAP systems in this global account are based on the `abap/standard` service.

    > ### Note:  
    > You have to acquire a development license for partners. See [SAP PartnerEdge Test, Demo & Development Price List](https://partneredge.sap.com/en/library/assets/partnership/sales/order_license/pl_pl_part_price_list.html).

-   **Global production account**

    All productive ABAP systems are created in the global production account. This includes systems for:

    -   The add-on installation test as part of the add-on build pipeline
    -   ABAP systems to provide the SaaS solution to consumer accounts. These consumer subaccounts are also created in the global production account.

    All ABAP systems in this global account use the `abap/saas_oem` service.

    > ### Note:  
    > You have to acquire a production license for partners. See [Resources for OEM Partners](https://partneredge.sap.com/en/partnership/manage/op_resource/oem.html).


> ### Recommendation:  
> We recommend creating subaccounts for the different stages of the SaaS solution enablement.



<a name="loio4ca756395fc24e56a42b77632a6bd862__section_wtx_qvj_xnb"/>

## Global Development Account

![](images/Global_Development_Account_d2da7d3.png)

1.  **Development subaccount including development space**

    ABAP development systems DEV and correction systems COR are created in this subaccount. An SAP Business Application Studio subscription is enabled in the subaccount for the development of SAP Fiori UIs and multitenant application implementation.

2.  **Test subaccount including test space**

    ABAP test systems TST and quality assurance systems QAS are created in this subaccount. See [Use Case 2: One Development and Correction Codeline in a 5-ABAP-System Landscape](Use_Case_2_One_Development_and_Correction_Codeline_in_a_5-ABAP-System_Landscape_4e53874.md). Since development is structured with software components that are stored in a repository for each global account, these software components can automatically be imported to the test system on a regular basis automated by the CI/CD server. See [Test Integration \(SAP\_COM\_0510\)](Test_Integration_(SAP_COM_0510)_b04a9ae.md). The CI/CD server uses a Git repository to read the pipeline definition and configuration.

3.  **Build/assemble subaccount including build/assemble space**

    For the add-on build process, an assembly system \(BLD\) is provisioned in this subaccount by the CI/CD server. See [Software Assembly Integration \(SAP\_COM\_0582\)](Software_Assembly_Integration_(SAP_COM_0582)_26b8df5.md). After the add-on has been successfully built, the system is deleted. In this case, the CI/CD server reads the add-on definition from a Git repository \(add-on descriptor\).




<a name="loio4ca756395fc24e56a42b77632a6bd862__section_mbj_tvj_xnb"/>

## Global Production Account

![](images/Global_Production_Account_e65057f.png)

1.  **Build/test subaccount including build/test space**

    After the add-on has been assembled during the build of an add-on version, an installation test is required to verify that the add-on can be installed into a system without errors. As part of the add-on build pipeline, an `abap/saas_oem` system \(ATI\) is provisioned in this subaccount and the add-on is installed. In this case, the CI/CD server reads the add-on definition \(add-on descriptor\) and the provisioning parameters for the add-on installation test system from a Git repository.

2.  **Provider subaccount including provider space**

    The multitenant application is deployed to this space. The ABAP solution service can then provision `abap/saas_oem` systems \(AMT\), tenants, and users in this account once a consumer subscribes to the provided SaaS solution.

3.  **Consumer subaccount**

    For each customer, a consumer subaccount is created in the global production account.

    ![](images/Account_Model_and_System_Landscape_2a1da2c.png)

    This allows consumers to have their own configuration of:

    -   Trust settings \(custom identity provider\).

        > ### Note:  
        > If you want to integrate an existing corporate identity provider for authentication/authorization in subaccounts of the development global account, see [Trust and Federation with Identity Providers](../50-administration-and-ops/Trust_and_Federation_with_Identity_Providers_cb1bc8f.md). To restrict access based on certain criteria such as the IP address you need to use the Identity Authentication service . See [Identity Authentication Service](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/d17a116432d24470930ebea41977a888.html).

    -   Connectivity via SAP Cloud Connector. See [Connectivity in the Cloud Foundry Environment](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/34010ace6ac84574a4ad02f5055d3597.html).

    -   Destinations. See [Managing Destinations](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/84e45e071c7646c88027fffc6a7bb787.html).

    -   Subscriptions

        > ### Restriction:  
        > As of now, you can only expose SaaS applications for subscription from the provider global account and therefore the subscription in the subaccount needs to be done by the provider.



Using different subaccounts for the different phases has multiple advantages: Trust settings and destination/connectivity settings can be adjusted for each subaccount. That means, you can connect the development subaccount to the developer user identity provider and the test subaccount to the tester user identity provider. In terms of connectivity, the development subaccount can be connected to the development on-premise system and the test subaccount can be connected to the test on-premise system.

The ABAP environment pipeline is executed in a Jenkins CI/CD server that is connected to the test, build/assemble, and build/test subaccounts by authenticating via a technical Cloud Foundry platform user.

![](images/Global_Development_Account_and_Branching_62a2652.png)

For development and maintenance processes, a use case similar to [Use Case 2: One Development and Correction Codeline in a 5-ABAP-System Landscape](Use_Case_2_One_Development_and_Correction_Codeline_in_a_5-ABAP-System_Landscape_4e53874.md) is followed:

-   ABAP systems COR and QAS have the same software state, unless a new change is tested and released. This means, transport requests are released in ABAP system DEV only if development is completed and it’s planned to import the changes to the production ABAP system.

-   Upon cutoff date, development is finished. All development that is released at this time must be tested and be of good quality. From then on, you must fix defects in the COR system and maintain them in parallel in the DEV system.

-   Upon release date, all defects must be fixed. If you make the decision during testing in the QAS system that a complete functionality isn’t delivered, developers must delete, revert, or disable the functionality in the COR system and release the corresponding transport requests. You cannot remove objects from the release branch, e.g. by deselecting transport requests. To revert objects to an older transported state, use the compare editor of the Eclipse *History* view. If you want to withdraw the functionality in the DEV system as well, it’s considered a correction and you have to perform double maintenance of corrections into the DEV system. See [Double Maintenance of Corrections into Development](Double_Maintenance_of_Corrections_into_Development_1241b14.md).
-   Users in ABAP system COR are locked during ongoing development and only unlocked when a correction has to be implemented



![](images/Pipeline_Overview_0e1c881.png)

-   [https://www.project-piper.io/pipelines/abapEnvironment/stages/initialChecks/](https://www.project-piper.io/pipelines/abapEnvironment/stages/initialChecks/)
-   [https://www.project-piper.io/pipelines/abapEnvironment/stages/prepareSystem/](https://www.project-piper.io/pipelines/abapEnvironment/stages/prepareSystem/)
-   [https://www.project-piper.io/pipelines/abapEnvironment/stages/cloneRepositories/](https://www.project-piper.io/pipelines/abapEnvironment/stages/cloneRepositories/)
-   [https://www.project-piper.io/pipelines/abapEnvironment/stages/ATC/](https://www.project-piper.io/pipelines/abapEnvironment/stages/ATC/)
-   [https://www.project-piper.io/pipelines/abapEnvironment/stages/build/](https://www.project-piper.io/pipelines/abapEnvironment/stages/build/)
-   [https://www.project-piper.io/pipelines/abapEnvironment/stages/integrationTest/](https://www.project-piper.io/pipelines/abapEnvironment/stages/integrationTest/)
-   [https://www.project-piper.io/pipelines/abapEnvironment/stages/confirm/](https://www.project-piper.io/pipelines/abapEnvironment/stages/confirm/)
-   [https://www.project-piper.io/pipelines/abapEnvironment/stages/publish/](https://www.project-piper.io/pipelines/abapEnvironment/stages/publish/)

On top of these static systems, as part of the add-on build, transient systems are used for add-on assembly \(BLD\) and installation tests \(ATI\).

For the consumption of the add-on as a SaaS solution, instead of importing a release branch into a productive system, software components are installed via add-on packages into multitenancy-enabled production systems \(AMT\) provisioned via the ABAP Solution service. See [Define Your ABAP Solution](Define_Your_ABAP_Solution_1697387.md).

 <a name="loio2398b874f7c5445db188b780ff0cef89"/>

<!-- loio2398b874f7c5445db188b780ff0cef89 -->

## ABAP Environment Pipeline



![](images/Pipeline_Stage_1_ed049b4.png)

-   [https://www.project-piper.io/pipelines/abapEnvironment/stages/initialChecks/](https://www.project-piper.io/pipelines/abapEnvironment/stages/initialChecks/)
-   [https://www.project-piper.io/pipelines/abapEnvironment/stages/prepareSystem/](https://www.project-piper.io/pipelines/abapEnvironment/stages/prepareSystem/)
-   [https://www.project-piper.io/pipelines/abapEnvironment/stages/cloneRepositories/](https://www.project-piper.io/pipelines/abapEnvironment/stages/cloneRepositories/)
-   [https://www.project-piper.io/pipelines/abapEnvironment/stages/ATC/](https://www.project-piper.io/pipelines/abapEnvironment/stages/ATC/)
-   [https://www.project-piper.io/pipelines/abapEnvironment/stages/build/](https://www.project-piper.io/pipelines/abapEnvironment/stages/build/)
-   [https://www.project-piper.io/pipelines/abapEnvironment/stages/integrationTest/](https://www.project-piper.io/pipelines/abapEnvironment/stages/integrationTest/)
-   [https://www.project-piper.io/pipelines/abapEnvironment/stages/confirm/](https://www.project-piper.io/pipelines/abapEnvironment/stages/confirm/)
-   [https://www.project-piper.io/pipelines/abapEnvironment/stages/publish/](https://www.project-piper.io/pipelines/abapEnvironment/stages/publish/)



For continuous import of software components into a test system and add-on build, the ABAP environment pipeline is provided. See [ABAP Environment Pipeline](https://sap.github.io/jenkins-library/pipelines/abapEnvironment/introduction/). You can configure it for different scenarios, where different pipeline stages are enabled:

-   **Transport from dev to test system via gCTS**

    The development and test system stay on the same development branch. To provide the latest implementations for testing in the test system, the developed software components are imported on a regular basis to the test system and checked with ABAP Test Cockpit checks. See [ABAP Test Cockpit Configurator](../50-administration-and-ops/ABAP_Test_Cockpit_Configurator_22c26ff.md) and [Continuous Testing on SAP BTP ABAP Environment](https://www.project-piper.io/scenarios/abapEnvironmentTest/).

    As part of this pipeline scenario, a test system including an instance of communication scenario `SAP_COM_0510` is used. See [Test Integration \(SAP\_COM\_0510\)](Test_Integration_(SAP_COM_0510)_b04a9ae.md).

-   **Build add-on version**

    The add-on build and assembly process are automated in a different pipeline scenario. From creating a combined data file in the assembly system to publishing the add-on release, all steps are part of this pipeline that has to be triggered by you as an add-on admin. See [Build and Publish Add-on Products on SAP BTP ABAP Environment](https://www.project-piper.io/scenarios/abapEnvironmentAddons/).

    The add-on product that you want to build is defined in an `addon.yml` configuration file that is checked into the pipeline repository.

    > ### Note:  
    > To define the add-on descriptor file, follow the best practices mentioned in [Add-On Descriptor File](https://www.project-piper.io/scenarios/abapEnvironmentAddons/#add-on-descriptor-file).

    ```
    ---
    addonProduct: /NAMESPC/PRODUCTX
    addonVersion: 1.2.0
    repositories:
      - name: /NAMESPC/COMPONENTA
        branch: v1.2.0
        version: 1.2.0
        commitID: 7d4516e9
    
    ```

    As part of this pipeline scenario, the following systems and services are being used:

    -   Provisioned by you, as the provider, via the add-on build pipeline

        -   ABAP environment system for assembly including an instance of communication scenario `SAP_COM_0510` and an instance of communication scenario `SAP_COM_0582`. See [Test Integration \(SAP\_COM\_0510\)](Test_Integration_(SAP_COM_0510)_b04a9ae.md) and [Software Assembly Integration \(SAP\_COM\_0582\)](Software_Assembly_Integration_(SAP_COM_0582)_26b8df5.md).

        -   Add-on Installation test system


    -   Provided as part of SAP support backbone

        -   Add-on Assembly Kit as a Service \(AAKaaS\) for registering and publishing the software product.

            AAKaaS is a service offered in the SAP Service and Support systems, which means that access is granted via a technical communication user\), that packs the delivery into an importable package format. It is similar to the Software Delivery Assembler \(SDA, transaction SSDA\) as a part of the [SAP Add-On Assembly Kit](https://help.sap.com/viewer/product/SAP_ADD-ON_ASSEMBLY_KIT/).

            See [Add-On Assembly Kit as a Service](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentAddons/#add-on-assembly-kit-as-a-service-aakaas).




The configuration of the ABAP environment pipeline follows the same approach regardless of the scenario that you want to configure:

1.  **Prepare Git Repository**

    As a DevOps engineer, you need to prepare a Git repository by including the Jenkins file, initializing the pipeline, and the pipeline configuration file `.pipeline/config.yml`. See [Jenkins File](https://sap.github.io/jenkins-library/pipelines/abapEnvironment/configuration/#2-jenkinsfile) and [Technical Pipeline Configuration](https://sap.github.io/jenkins-library/pipelines/abapEnvironment/configuration/#6-technical-pipeline-configuration).

2.  **Create Service User for Git Repository**

    To enable read access to the Git repository, you have to create a service user and assign it to the repository. Later, this user’s access credentials are stored in the Jenkins credentials by the Jenkins administrator. See [Using Credentials](https://www.jenkins.io/doc/book/using/using-credentials/).

3.  **Create Jenkins Instance via Cx Server**

    As a Jenkins administrator, you need to set up a new Jenkins instance using Cx Server Lifecycle Management. After initializing the Cx server that is based on a set of docker images, you can start the Jenkins server with `./cx-server start`. See [Cx Server](https://sap.github.io/jenkins-library/infrastructure/overview/#cx-server-recommended) and [Docker Hub](https://hub.docker.com/u/ppiper).

4.  **Configure Jenkins Instance**

    As a Jenkins administrator, you need to add technical Git user credentials and platform user credentials to the integrated secure store. Make sure that a shared library piper-lib-os is configured pointing to the project "Piper" library. See [Piper Library](https://github.com/SAP/jenkins-library.git).


For more information on how to configure the ABAP environment steps and stages, see [Configuration](https://sap.github.io/jenkins-library/pipelines/abapEnvironment/configuration/).

 <a name="loio52fb6a9e22714843b6e83b7f333b184b"/>

<!-- loio52fb6a9e22714843b6e83b7f333b184b -->

## Permanent Add-On Assembly System

The add-on process requires an add-on assembly system \(BLD\). We recommend creating the system from scratch for each new add-on version.

However, for certain scenarios, it is advisable to reuse a permanent system instead:

-   **Build Cost**: The costs of an ABAP system relate to the creation of a service instance. See [Create an ABAP System](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/50b32f144e184154987a06e4b55ce447.html).

-   **Build Time**: Provisioning an ABAP system takes some time. The time it takes to complete the add-on build process mostly depends on the creation of the BLD and ATI system. Additionally, importing a software component that has not been cloned yet to the system takes longer than importing a software component that has already been checked out.

    See [Cloning Git Repositories to an ABAP Environment System](Cloning_Git_Repositories_to_an_ABAP_Environment_System_0552763.md) and [Pulling Git Repositories to an ABAP Environment System](Pulling_Git_Repositories_to_an_ABAP_Environment_System_80a8d52.md).



<table>
<tr>
<td valign="top">

 



</td>
<td valign="top">

**Transient System**



</td>
<td valign="top">

**Permanent System**



</td>
</tr>
<tr>
<td valign="top">

**Build Costs**



</td>
<td valign="top">

A transient system is more cost-efficient as the system only exists during the ongoing pipeline execution.



</td>
<td valign="top">

A permanent system results in higher costs as the system is not used during periods where no add-on build is executed \(idle time\)



</td>
</tr>
<tr>
<td valign="top">

**Build Time**



</td>
<td valign="top">

A transient system has a negative impact on build performance as a new system is provisioned from scratch and a software component must be cloned \(duration depending on size of software component\). See [Software Components](Software_Components_58480f4.md).



</td>
<td valign="top">

Reusing a system results in a shorter build time as no system provisioning is required and only the latest changes are imported into software components via software component pull or add-on update.



</td>
</tr>
</table>

The configuration of the add-on build pipeline depends on the use of a transient or permanent system: For a pipeline configuration using a transient system, see [Example Build Add-Ons on a Transient System](https://github.com/SAP-samples/abap-platform-ci-cd-samples/tree/addon-build). When using a permanent system, see [Example Build Add-Ons on a Permanent System](https://github.com/SAP-samples/abap-platform-ci-cd-samples/tree/addon-build-static).



<a name="loio52fb6a9e22714843b6e83b7f333b184b__section_mnd_32z_cpb"/>

## Add-On Assembly System

In the *Prepare System* pipeline stage, a new system is provisioned for the add-on assembly. See [Prepare System](https://www.project-piper.io/pipelines/abapEnvironment/stages/prepareSystem/). ATC checks, software component imports, and the local build of deliveries are performed in this stage. In the *Post* pipeline stage, the system is deleted afterwards. See [Post](https://www.project-piper.io/pipelines/abapEnvironment/stages/post/).

However, you have the option to use a permanent add-on assembly system instead to save build time at the expense of build cost:

System provisioning is one of the most time consuming tasks performed by the pipeline, therefore, reusing an existing system leads to improved build time.

> ### Recommendation:  
> Whenever you create a new maintenance branch \(e.g. v1.0.0\), you should also create a new add-on assembly system. To do so, use the pipeline configuration for using a permanent ABAP system. See [Build Add-Ons on a Permanent ABAP Environment System](https://github.com/SAP-samples/abap-platform-ci-cd-samples/tree/addon-build-static). This system is used for the duration of a maintenance branch and gets deleted afterwards:
> 
> 1.  Maintenance branch v1.0.0 is created before the build of the initial add-on version 1.0.0
> 2.  For the add-on build of product version 1.0.0, a new add-on assembly system is created. Software components are imported via the *Manage Software Components* app. See [Manage Software Components](../50-administration-and-ops/Manage_Software_Components_3dcf76a.md).
> 3.  A new patch version 1.0.1 of the add-on is being built in the same add-on assembly system.
> 4.  A new maintenance branch v1.1.0 is created before build of a new add-on version 1.1.0.
> 5.  The previous add-on assembly system is deleted and a new add-on assembly system is created.

 <a name="loioc8730736a52645b49ca76c08214bf181"/>

<!-- loioc8730736a52645b49ca76c08214bf181 -->

## Multitenancy

Multitenancy defines the capability to host different customers \(tenants\) on a single, shared computing infrastructure to optimize administration and significantly reduce TCO. A tenant is an organizationally independent unit whose IT business or parts of it are operated together with the businesses of other tenants by a hosting provider. Multitenancy is especially relevant in a software as a service \(SaaS\) business model, where customers subscribe to hosted software solutions rather than buying and installing them. From the perspective of a hosting provider, the operation costs per user per tenant are a decisive factor. This applies even more to the SME market, where typically each tenant only has a small number of users \(10 – 50\) accessing the hosted solution. The hosting provider can only operate profitably if administration and maintenance costs for the hosted solution can be kept to a minimum. This cost pressure also limits the degree of individualization and customization a hosting provider is willing to accept for a hosted solution for many tenants.

The way ABAP service instances and tenants are used for consumer subscriptions application can be configured via parameter `tenant_mode` of the ABAP Solution service, see [Define Your ABAP Solution](Define_Your_ABAP_Solution_1697387.md):

-   **Single**: With each new consumer, a new ABAP service instance is created

-   **Multi**: For multiple consumers, the same ABAP service instance is used


> ### Note:  
> As of now, there is no consumer tenant threshold available to specify the number of tenants to be onboarded per system.

> ### Tip:  
> You should align your decision whether to enable multitenancy mode for your solution based on the [Development Guideline to Enable Multitenancy of Products Built on the ABAP Environment](Development_Guideline_to_Enable_Multitenancy_of_Products_Built_on_the_ABAP_Environment_9d994c8.md).

 <a name="loio8c087bca40584f9b899282b4ec515753"/>

<!-- loio8c087bca40584f9b899282b4ec515753 -->

## Versioning and Branches



<a name="loio8c087bca40584f9b899282b4ec515753__section_uvc_jbr_xnb"/>

## Add-On Versioning

For the add-on delivery process, certain versioning principles apply. Learn how software components are combined to an add-on product and what versioning rules are used for both parts. Software components and add-on products follow a similar versioning pattern.



### Add-on Product Version

Instead of importing software components into productive systems, when providing a SaaS solution in the ABAP environment, software components are packaged and installed into ABAP systems based on so-called add-on products/software products.

You can only install one add-on product for each system using the ABAP environment `saas_oem` service plan instead of the `standard` service. During provisioning of this service, parameters `addon_product_name` and `addon_product_version` are used to install a certain add-on product version into the system, after the system has been provisioned. See [Define Your ABAP Solution](Define_Your_ABAP_Solution_1697387.md).

The add-on product name includes a reserved development namespace to separate the name from other customers/partners. See SAP note [84282](https://launchpad.support.sap.com/#/notes/84282).

The versioning pattern `<Release>.<Support Package Level>.<Patch Level>` applies to the add-on product version.

> ### Note:  
> Only in a new release, you can change the bundled software components of the add-on product.

Technically, the allowed number range is 1.0.0 to 9999.9999.9999.

For the release, there are no technical restrictions regarding the number of new versions. You only have to consider that the version has to be ascending across builds and there must be no gaps between versions. The initial release is always 1.0.0.

The support package level count starts again from 0 with each release.

The patch level count starts again from 0 with each support package.

While providing a specific add-on version, leading zeroes should be omitted \(1.2.3 instead of 0001.0002.0003\).

For more information on software product versioning, see [Add-On Product Version](https://www.project-piper.io/scenarios/abapEnvironmentAddons/#add-on-product-version).



### Software Component Version

Software components are self-contained and include development packages as well as development objects. They are used in combination with a reserved development namespace to separate the name from other customers/partners. See [Software Components](Software_Components_58480f4.md).

The versioning pattern `<Release>.<Support Package Level>.<Patch Level>` also applies to the software component version.

> ### Note:  
> Software component versions are delivered with delivery packages. However, software component versions are not individual shipment entities. They can only be delivered to customers as part of a software product version.
> 
> Software component versions are only built once, independent from add-on product versions where the software component version was referenced. If an add-on product version is referring to a software component version that has already been created as part of a different add-on build, the created delivery package is reused.

Technically, the allowed number range is 1.0.0 to 9999.9999.9999.

For the release, there are no technical restrictions regarding the number of new versions. You only have to consider that the release has to be ascending across builds and there must be no gaps between versions. The initial release is always 1.0.0.

The support package level can only go up until 369 because of technical limitations. The support package level count starts again from 0 with each new release.

For the patch level, there is a technical limit of 36³, limited to 9999. The patch level count starts again from 0 with each support package.

For more information on software component versioning, see [Software Component Version](https://www.project-piper.io/scenarios/abapEnvironmentAddons/#software-component-version).



<a name="loio8c087bca40584f9b899282b4ec515753__section_snh_3dr_xnb"/>

## Add-On Package Types

For the delivery of add-ons, there are three package types that serve different purposes: AOI, CSP, and CPK.

Depending on the purpose, the development objects to be included in the object list of the package are calculated differently based on the state of the software component.

> ### Note:  
> The required type of delivery is automatically determined by the delivery production tools based on how the version number of software components is changed.



### AOI \(Addon Installation\)

Changes to the release of a software component are delivered as add-on installation packages.

The add-on installation package is used for the initial release of software components. It is used to deliver new and enhancements of existing functionalities. Each AOI package contains all the objects of the software component. That means, every object is included in the object list of the package. In contrast to CSP and CPK packages, the calculation of the object list is not based on a delta calculation.



### CSP \(Component Support Package\)

Changes to the support package level of a software component are delivered as component support package.

The CSP is an ABAP support package used for major fixes of a software component version. These major fixes can be a larger collection of corrections but can also contain smaller functional enhancements. Whenever a CSP containing new objects such as bug fixes and/or new features is built, these objects are delivered in any subsequent AOI package.

CSP packages are built with a delta process dependent on the previous state of the software component used for the build. That means, only the changes made since the last change of the support package level are included to the object list of the CSP.



### CPK \(Correction Package\)

Changes to the patch level of a software component are delivered as a correction package.

The ABAP correction package is used for minor fixes and should only contain small corrections. Whenever a CPK is built, these objects are delivered in the first component support package \(CSP\) to follow and any subsequent AOI package. That way, new installations are up to date without the need to install patches.

CPK packages are built with a delta process dependent on the previous state of the software component used for the build. That means, only the changes made since the last change of the patch level are included in the object list of the CPK.

For more information on the add-on package types and how these are determined based on changes to the software component version, see [Software Component Version](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentAddons/#software-component-version).



<a name="loio8c087bca40584f9b899282b4ec515753__section_ks3_f2r_xnb"/>

## Branching

For the first release, only the main branch of software components is supposed to be used for the add-on build process. In a later release, the functionality of using maintenance branches to separate the development and correction code line is supported. While development and add-on builds are done based on the same main branch, you should only release transport requests when there is no ongoing add-on build.

Git repository branches can be used to control the flow of changes through the test and production landscape. They are used to separate changes from each other, which shall or might not be delivered together \(i.e. development vs. correction, feature A vs. feature B\). A branch is created on the current state of another branch, the parent branch, and reflected by a new copy of the commit history and all included objects. Depending on which branch is supposed to be changed, the corresponding copy is worked on.

> ### Note:  
> Keep in mind the [ABAP Environment Specifics](ABAP_Environment_Specifics_1367346.md) for using branches in your development processes: e.g. merging of branches is not supported and has to be done manually with double maintenance. See [Double Maintenance of Corrections into Development](Double_Maintenance_of_Corrections_into_Development_1241b14.md).

To separate development and correction code lines, for each new support package level of a software component version, create a new branch. You can name these maintenance branches v1.2.0 for software component version 1.2.0. See [Use Case 2: One Development and Correction Codeline in a 5-ABAP-System Landscape](Use_Case_2_One_Development_and_Correction_Codeline_in_a_5-ABAP-System_Landscape_4e53874.md).

> ### Recommendation:  
> Create a new maintenance branch with each new support package level, and with each new AOI and CSP package.

All corrections to a software component based on a certain support package level are then released in the corresponding maintenance branch and maintained as new commits in the main branch \(double maintenance\).



<a name="loio8c087bca40584f9b899282b4ec515753__section_dcn_34r_xnb"/>

## Delivery Models

Based on the mentioned software component versioning principles, the add-on package types, and branching approach, you can use different delivery models.

> ### Recommendation:  
> You should choose the delivery model based on the existing processes in your development/shipment environment. As faster delivery cycles have certain advantages, especially for a software that is provided as a SaaS solution \(all consumers should be able to use the latest product version\), we recommend following the continous delivery approach whenever possible.



### Continuous Delivery

With the continuous delivery approach, new features should be delivered as soon as possible: In this case, new features can be shipped with support packages more often than new releases of a software component. These short development cycles ensure that changes can be deployed on short notice and in smaller increments. See [Continuous Integration and Delivery \(CI/CD\)](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/fe74df55b0f54e99bf6e13a3b53e1db0.html).

![](images/ABAP_Environment_Bi-Weekly_Support_Packages_0209ff2.png)

In this example, commit Z represents all the commits prior to the first build.

The maintenance branch v1.0.0 is used for bug fixes that must be manually maintained in the main branch, which requires double maintenance to make sure that the development code line is up to date.

Commit Z and commit C are new features implemented in the development code line on the main branch. Development of these features is done in the DEV system, testing in the TST system.

Commit A and commit D are small corrections that are implemented in the correction code line on the maintenance branch for support package level zero of software component release one.

Development of these bug fixes is done in the COR system, testing in the QAS system.

After releasing these corrections in the maintenance branch, you have to maintain them as well in the main branch in the DEV system to secure consistency of changes in the correction and development code lines. As a result, commit B and E are created in the main branch to reflect the corrections made in the maintenance branch \(commit A and commit D\).

The new support package build for version 1.1.0 is derived from the main branch and includes new features and bug fixes since the last support package level 1.0.0 has been released. With the new support package build for version 1.1.0 of the software component, a new maintenance branch v1.1.0 is created. All corrections for this support package level are developed on this branch.

For a new release, add-on version 2.0.0 is released. The resulting AOI package includes all features and bug fixes since the last AOI build for version 1.0.0 has been released.

With this delivery model, support packages not only include the corrections for the current support package level but also new features allowing shorter development cycles.

> ### Recommendation:  
> We recommend shipping new software component releases on a quarterly basis. These AOI packages contain every object that has been built and delivered with the support packages, including all the patches.
> 
> In a continuous delivery model, we recommend building and deploying a new CSP on a weekly or biweekly basis.



### Quarterly Shipment

The quarterly delivery approach is recommended whenever longer test cycles are necessary and faster incremental development is not feasible. This might be required due to industry requirements, legal requirement etc.

![](images/ABAP_Environment_Quarterly_Shipments_662ebc5.png)

Compared to the continuous delivery model, the maintenance branches for each support package level are not based on the main branch but on the previous maintenance branch: e.g. branch v1.1.0 is based on v1.0.0.

That way, support packages are only used for the purpose of patch collections: only the corrections in commit A and D that were already delivered as patches in version 1.0.1 and 1.0.2 are included in support package 1.1.0.

New features are only delivered with new release versions \(AOI packages\). The build for version 1.1.0 does not include commit C. As late as with the build for version 2.0.0, this feature is shipped. Consequently, new features take longer until they are available in production systems.

> ### Note:  
> Since only major software component releases are based on the main branch for this delivery model, the double maintenance of corrections in the maintenance branches is even more important.

This delivery model is similar to processes commonly used to ship on-premise solutions where upgrades are much more complex and usually performed on a quarterly basis. Instead of shipping more often but in smaller packages, this approach promotes building larger shipment packages with a lot of new features.

> ### Recommendation:  
> We recommend following the continuous delivery approach whenever possible to mitigate risks during installation and updates by shipping smaller packages.



<a name="loio8c087bca40584f9b899282b4ec515753__section_pfl_r4r_xnb"/>

## Multiple Software Components

Add-On products can consist of multiple software components. However, objects of one software component can't be used in another software component by default. Software components provide their functionality to other software components via explicitly released APIs. This means, you must set the API state of an object to *Released* if you want to use it from another software component. See [Released APIs](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/c479660d07374c15a1a5fe83fdbb1337.html) and [Finding Released APIs and Deprecated Objects](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/3f232ac7cecc4d9891ff512462240223.html).

Having this in mind, you can structure development into reuse components that are used across several components.

![](images/Software_Components_and_Add-On_Products_b0bbd71.png)

In this example, one add-on product consists of software component A and software component C, whereas another add-on product consists of software component B and C. Software component A and B use released objects of software component C, and thereby depend on this software component.

Once you have released an object, we recommend not changing it incompatibly because this can lead to errors for its consumers.

Software components must not have cyclic dependencies. In the example above, software component C must not use objects from software component A. For more information on software component restrictions, see [Software Components](Software_Components_58480f4.md).

In the add-on descriptor, dependencies are reflected by the order of the components in the repositories list:

```
---
addonProduct: /NAMESPC/PRODUCT_X
addonVersion: 1.2.0
repositories:
  - name: /NAMESPC/COMPONENT_C
    branch: v1.2.0
    version: 1.2.0 
    commitID: 7d4516e9
  - name: /NAMESPC/COMPONENT_A
    branch: v2.0.0
    version: 2.0.0 
    commitID: 9f102ffb 
    
```

In this case, component `/NAMESPC/COMPONENT_C` is the reuse component. It has no dependencies to any other top components and is therefore listed first. This is important for the right order during software component import. `/NAMESPC/COMPONENT_C` needs to be imported before `/NAMESPC/COMPONENT_A` to avoid import errors. In addition to that, software components in the bundle can use different namespaces in the software component name.

> ### Recommendation:  
> In a software component bundle with a reuse component, this component is assembled whenever the software component version is defined for the first time in the add-on descriptor file. Therefore, make sure to define the correct software component version to prevent building the wrong software component version for `/NAMESPC/COMPONENT_C`.
> 
> We recommend following the same delivery model \(identical shipment cycles\) for all involved software components in a delivery scenario with a reuse component.

![](images/Software_Components_and_Add-On_Products_Scenario_1_6c15e35.png)

In this scenario, add-on product X and Y are based on the continuous delivery model and still undergo development. That means, for both add-on products, a new version can be shipped on a bi-weekly basis.

Consequently, software components A and B refer to objects in the same branch of the reuse software component C, for example branch v1.2.0

Let’s assume that development and correction of both software components is performed in one DEV and COR system. If there has to be a bug fix in software component C, corrections to the corresponding software components A and B are still possible. This is due to the fact that branch v1.2.0 can remain checked out in software component C, while these changes are made.

The same applies to the develpoment process: A new feature can be developed in software component A using the main branch of software component C. Since only the main branch of software component C is used in the DEV system, the development in the corresponding software components A and B can continue in parrallel.

This scenario is resource-efficient: only one system is required for development in system DEV and one for corrections in COR. With respect to the developer experience, it is more convenient to have all implementation components in one development system because everything is in one place and the whole system landscape is easily understandable.

![](images/Software_Components_and_Systems_ac99365.png)

The system setup regarding the testing and quality assurance for corrections depends on how you want to test the add-on products:

-   Do you want to provide a test environment that is identical to a production system with the add-on product installed? Then you should establish one TST and one QAS system for each add-on product in the sense that only those software components used for each add-on product are imported into these systems.

-   Do you want to reduce the number of systems without restricting the test environment? Then you only need one TST and one QAS system, where all software components are imported.


The number of required systems for DEV, COR, TST, and QAS depends on the number of branches that are actively used in dev, test, and build processes. Whenever more than one branch is actively used, one ABAP system is required per branch because an ABAP system always checks out only one branch of a software component.

 <a name="loio438d7ebfdc4a41de82dcdb156f01857e"/>

<!-- loio438d7ebfdc4a41de82dcdb156f01857e -->

## Delivery via Add-On or gCTS

For SaaS solutions in the ABAP environment, software components including ABAP development objects have to be delivered to the customer production system. This is referred to as upstream process.

Afterwards, the SaaS solution is provided by offering a multitenant application that facilitates a subscription mechanism. This is referred to as downstream process.

There are multiple options to deliver software components to the systems. The delivery process described in this documentation mainly focuses on using add-on products as a means to deliver software components by installing or updating delivery packages in a system. See [The Add-On Product](https://www.project-piper.io/scenarios/abapEnvironmentAddons/#the-add-on-product).

As an alternative, you can choose a delivery process using the gCTS-based import of software components. See [Transport Mechanisms](Transport_Mechanisms_aa7f169.md).


<table>
<tr>
<td valign="top">

 



</td>
<td valign="top">

**Add-On-Based Delivery**



</td>
<td valign="top">

**gCTS-Based Delivery**



</td>
</tr>
<tr>
<td valign="top">

**Versioning**



</td>
<td valign="top">

-   Add-ons induce explicit versioning on product and software component level
-   The add-on product version is visible in the system details in the Landscape Portal application. See [View Tenants and Systems](View_Tenants_and_Systems_99c975e.md).
-   Different version numbers correspond to different types of delivery packages on software component level
-   The way various package types are imported into the systems is different



</td>
<td valign="top">

-   Explicit versioning is not integrated into the gCTS transport technology
-   No different import package types
-   When following this gCTS-based delivery approach, versioning needs to be managed and tracked manually. See [Use Case 2: One Development and Correction Codeline in a 5-ABAP-System Landscape](Use_Case_2_One_Development_and_Correction_Codeline_in_a_5-ABAP-System_Landscape_4e53874.md).



</td>
</tr>
<tr>
<td valign="top">

**Tool Support**



</td>
<td valign="top">

-   ABAP environment pipeline needs to be executed in a Jenkins CI/CD Server
-   Initial configuration effort and requires to setup Jenkins Server [Infrastructure](https://www.project-piper.io/infrastructure/overview/).
-   Resulting delivery packages are either installed as part of an add-on during system provisioning or updated centrally in the systems using the *Landscape Portal*application. See [Perform Add-on Updates](Perform_Add-on_Updates_8c5cb9e.md).



</td>
<td valign="top">

-   Changes to software components are released and exported to a central remote repository using transport requests
-   The *Manage Software Components* app that is part of every ABAP system is used to trigger the import of new changes locally per system
-   As an alternative, software component import can be triggered by using the ABAP environment pipeline. See [ABAP Environment Pipeline](https://www.project-piper.io/pipelines/abapEnvironment/introduction/).



</td>
</tr>
<tr>
<td valign="top">

**ABAP Service Plan**



</td>
<td valign="top">

-   ABAP systems for development/testing purposes are of type `abap/standard` and provisioned in the global development account
-   ABAP systems including the installed add-on are of type `abap/saas_oem` and provisioned in the global production account



</td>
<td valign="top">

All ABAP systems are of type `abap/standard` and provisioned in the same global development account



</td>
</tr>
<tr>
<td valign="top">

**System Landscape/Account Model**



</td>
<td valign="top">

-   Global development account and global production account
-   Software components are made available across these different global accounts by using add-ons
-   For execution of the add-on build pipeline, an add-on assembly system BLD and add-on installation test system ATI are \(temporarily\) required



</td>
<td valign="top">

-   •Single global development account because gCTS repositories are only shared among ABAP systems in the same region in the same global account
-   No additional ABAP systems are required to facilitate a build process



</td>
</tr>
<tr>
<td valign="top">

**Initial Deployment**



</td>
<td valign="top">

-   Add-ons are automatically installed during system provisioning of ABAP systems
-   Application content is available immediately in systems provisioned after subscription to the multitenant application



</td>
<td valign="top">

-   Application content is initially not available
-   Software components need to be cloned into the systems provisioned after subscription to the multitenant application using the *Manage Software Components* app locally. See [How to Clone Software Components](../50-administration-and-ops/How_to_Clone_Software_Components_18564c5.md).



</td>
</tr>
<tr>
<td valign="top">

**Update Deployment**



</td>
<td valign="top">

Add-on update can be triggered centrally in a system using the *Landscape Portal* application. See [Perform Add-on Updates](Perform_Add-on_Updates_8c5cb9e.md).



</td>
<td valign="top">

Latest changes can be pulled into a system by using the *Manage Software Components* app locally. See [How to Pull Software Components](../50-administration-and-ops/How_to_Pull_Software_Components_90b9b9d.md).



</td>
</tr>
</table>



<a name="loio438d7ebfdc4a41de82dcdb156f01857e__section_uv2_jzr_2rb"/>

## Add-On-Based Delivery Process

![](images/Add-On-Based_Delivery_Process_f47ed18.png)

An add-on is a bundle of software components. To create an add-on, a build process orchestrated by an add-on build pipeline has to be triggered.

With delivery tools, the software components are packaged into deliveries that are then further processed. Eventually, the deliveries are stored as delivery packages using the deployment tools provided by SAP.

Add-on deployment is either performed by using an add-on installation during system provisioning or as an add-on update triggered in the *Landscape Portal* application.

Delivery packages are of different types, which means that the build and deployment of these packages differ accordingly. For example, the import of a software component for an add-on installation package or delta-import for correction packages.

BLD and AMT systems are based on different service plans: `abap/standard` for a plain ABAP system and `abap/saas_oem` for an ABAP system with installed add-on. The usage of these service plans is separated in two different global accounts. Making software components available across different global accounts is only possible by using the add-on delivery process.

Once a first customer is using the SaaS solution, there is no migration path available to switch from add-on-based delivery to gCTS-based delivery.



<a name="loio438d7ebfdc4a41de82dcdb156f01857e__section_byp_kzr_2rb"/>

## gCTS-Based Delivery Process

![](images/gCTS-Based_Delivery_Process_f6dfab0.png)

The gCTS-based delivery process takes place in the global development account only. This is due to the fact that the underlying gCTS repository is only shared among systems in the same region in the same global account.

ABAP development objects are released with a transport request in a particular software component in the development system. The transport request release automatically exports the changes into an SAP-managed gCTS repository by creating a new commit. Once the changes are exported into the gCTS repository, they are centrally available and can be imported into any other systems in the same region in the same global account. By cloning a software component into a customer production system using the *Manage Software Components* app, implemented ABAP objects become available to customers subscribed to the multitenant application.

> ### Note:  
> The customer production system AMT of type `abap/standard` is provisioned during the initial subscription to the multitenant application. Since the SaaS solution needs to include the implemented software, software components have to be cloned right after the first subscription. As a SaaS solution operator, you can use a separate test subscription that is not related to a customer to trigger the creation of the system before the real customer subscribing to the solution. This initial system creation and import of the software components needs to be performed for each customer production system. If an ABAP solution is configured with `tenant_mode = single` \(see Define Your ABAP Solution\), a dedicated system is created per subscription. In that case, a gCTS-based delivery is only recommended if the SaaS solution is expecting a small set of customers or if the subscription is performed together with the customer.

