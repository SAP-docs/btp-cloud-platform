<!-- loioccf0c1ef30ce4d6aa6e39bb583fb8ba1 -->

# Set Up Add-On Build



The following section explains how to build the initial version of the add-on product. The result is a delivery of type AOI \(Add-on Installation\) for the initial release 1.0.0 of both the software component and the add-on product.

The add-on build process is orchestrated by an automated pipeline. Before the pipeline can be configured, the following steps need to be performed.



### Add Technical Platform User to Space in Subaccount *03 Build/Assemble*

As an operator, assign a technical Cloud Foundry platform user as a space developer in subaccount 03 Build/Assemble. This technical user will be used to provision the assembly system. See [Creating New Space Members and Assigning Space Developer Roles to Them](https://help.sap.com/docs/btp/sap-business-technology-platform/creating-new-space-members-and-assigning-space-developer-roles-to-them?version=Cloud).

> ### Note:  
> If you used the [Booster for Landscape Portal](booster-for-landscape-portal-8d34e0f.md) to set up your landscape, then this is already configured.



### Add Technical Platform User to Space in Subaccount *04 Build/Test*

As an operator, assign a technical Cloud Foundry platform user as a space developer in the space in subaccount 04 Build/Test. This technical user will be used to provision the installation test system. See [Creating New Space Members and Assigning Space Developer Roles to Them](https://help.sap.com/docs/btp/sap-business-technology-platform/creating-new-space-members-and-assigning-space-developer-roles-to-them?version=Cloud).

> ### Note:  
> If you used the [Booster for Landscape Portal](booster-for-landscape-portal-8d34e0f.md) to set up your landscape, then this is already configured.



### Create a Technical Communication User for Access to AAKaaS

As part of the add-on build process, the Add-on Assembly Kit is used. With AAKaaS, the on-premise tooling is now available as a cloud service that is used by the build pipeline.

To access the service that is offered via SAP Support Launchpad, a technical communication user is used. See SAP note [2532813](https://me.sap.com/notes/2532813).

In the *Support User Management* app in SAP ONE Support Launchpad, as an S-user, request a new technical communication user. After the technical communication user has been generated, activate the user.

> ### Note:  
> To create technical communication users in SAP Support Launchpad, you have to assign the user administrator function to the logged on user.
> 
> Make sure that this technical communication user is assigned to the customer number under which the ABAP environment tenants are licensed and for which the development namespace was reserved.

See SAP note [2174416](https://me.sap.com/notes/2174416) for more information on how to create and activate technical communication users.



### Add credentials to credential store

The credentials of the three technical communication users need to be maintained in the Build Product Version app. See [Maintain Credentials](https://help.sap.com/docs/btp/sap-business-technology-platform/maintain-credentials?version=Cloud).

If you are using your own Jenkins server, the Jenkins administrator needs to add the credentials of the three technical communication users to the Jenkins Credentials store.



### Register Add-On Product for Installation in Global Accounts

The registration of a new add-on product is a manual step. Your add-on product should only be installed in ABAP systems in your global accounts for development and production. Therefore, the product needs to be created and global accounts need to be registered with SAP using Landscape Portal. See [Register Product](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/7b5e33f3e62e4cf2984385759dfc61f8.html).



### Configure ABAP Environment Pipeline

As a DevOps engineer, you have the choice between using the Build Product Version app in the Landscape Portal or creating a pipeline configuration for the add-on build scenario from scratch.

We strongly recommend using the Build Product Version app, as it greatly reduces both the initial configuration and the maintenance effort:

-   the user-friendly tooling hides the complexity of configuring a pipeline definition and removes the need for an external repository,

-   the app automatically delegates the execution of the pipeline to the CI/CD service on SAP BTP, removing the need for a partner-owned Jenkins server.


Creating a custom pipeline configuration allows you to modify parameters of the ABAP Environment pipeline that are not exposed in the Build Product Version app; however, the app should cover all common use cases.

> ### Note:  
> Currently there are two features available in the pipeline that the app does not support:
> 
> It is not possible to define a manual confirmation step before the target vector is published productively. This option allows you to perform integration tests in the ATI system before your final release decision. The pipeline executed by the app will simply check if the new version was installed successfully and will then automatically proceed to the publishing step.



### Build Product Version app \(recommended\)

The Build Product Version app allows you to configure the pipeline directly in a Fiori UI. See [Build Product Version](https://help.sap.com/docs/btp/sap-business-technology-platform/build-product-version?version=Cloud).

As a Landscape Portal Administrator, configure the Release Delivery pipeline template to be able to build your initial version. You can also configure the Test Release Delivery template in case you wish to perform a test execution, without releasing the new version.



### Manual Configuration

As a Jenkins administrator, create a new pipeline in Jenkins pointing to the Jenkins file of the pipeline configuration for the add-on build scenario. See [Configuration](https://www.project-piper.io/pipelines/abapEnvironment/configuration/).

The add-on build scenario of the ABAP environment pipeline is described in detail in [Build and Publish Add-on Products on SAP BTP ABAP Environment](https://www.project-piper.io/scenarios/abapEnvironmentAddons/).

