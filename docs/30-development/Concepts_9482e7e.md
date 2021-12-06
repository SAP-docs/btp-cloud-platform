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

