<!-- loio195031ff8f484b51af16fe392ec2ae6e -->

# Multitenant Applications

To make the software components in the ABAP System available for multiple different consumers, a multitenant application is deployed into the provider subaccount. This application can then be accessed by different tenants through a dedicated URL.

![](images/MT_Application_e366cdc.png)

For the multitenant application, different services and apps are used:

-   **Approuter application**: The application router is the single point-of-entry for the multitenant application and used to forward tenant-specific requests to the corresponding tenant in the ABAP system.

    See [Application Router](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/01c5f9ba7d6847aaaf069d153b981b51.html?locale=en-US&version=Cloud).

-   **ABAP Solution Service**: ABAP Solution service is required to create multitenant-enabled, ABAP environment-based SaaS solutions. Instead of a service binding from the approuter application to the ABAP environment business service, the approuter is bound to an ABAP Solution service instance. The service orchestrates the creation of ABAP systems upon consumer subscription as well as tenant provisioning/decommissioning. Requests routed via the approuter application to the ABAP solution service instance are automatically proxied to the corresponding ABAP tenant.

-   **SAP Authorization and Trust Management service \(XSUAA\)**: The `xsuaa` service instance acts as an OAuth 2.0 client to the multitenant application, and to the `ABAP Solution`service instance. The SAP Authorization and Trust Management service lets you manage user authorizations and trust to identity providers used for the multitenant application. The service instance is created with a corresponding security configuration. See [SAP Authorization and Trust Management Service in the Cloud Foundry Environment](https://help.sap.com/docs/CP_AUTHORIZ_TRUST_MNG/ae8e8427ecdf407790d96dad93b5f723/6373bb7a96114d619bfdfdc6f505d1b9.html?version=Cloud&locale=en-US).

-   **SaaS Provisioning Service**: The `SaaS Provisioning`service allows application providers to register multitenant applications and services in the Cloud Foundry environment in SAP Business Technology Platform. After a SaaS Provisioning service instance is created, the multitenant application becomes available for subscription in a consumer subaccount.

-   **ABAP System**: ABAP systems and tenants used to provide the multitenant application are not created manually but are managed by the ABAP Solution service: Upon first subscription the ABAP system is created as well the consumer tenant in the system. To be able to create the system, the ABAP solution service uses credentials of a technical platform user that is defined in the ASP\_CC destination. Depending on the configuration of the ABAP solution, for every subsequent subscription either a new tenant is created in the same ABAP system \(`consumer_tenant_limit` \> 1\) or a new system is created for every new subscription \(`consumer_tenant_limit` = 1\). A new ABAP system is also created if all the existing ones are "full" because the consumer tenant limit that you specified was reached. Note that an ABAP system can only be deleted if no consumer tenants exist.

    Consumer subscription-based multitenancy is only possible in those systems in which you provide your software as a service \(SaaS\) solution to consumers, i.e. your production and test systems. It is not available in development systems.

    See [Creating an ABAP System.](https://help.sap.com/docs/BTP/60f1b283f0fd4d0aa7b3f8cea4d73d1d/50b32f144e184154987a06e4b55ce447.html?state=DRAFT&version=Internal)

-   **Landscape Portal**: The Landscape Portal acts as a central tool to allow service providers to perform lifecycle management operations such as add-on updates, provisioning new consumers as new tenants, and more. A subscription to the Landscape Portal in the globalaccount where the multitenant application is deployed is required for the subscription flow to work.

    See [Landscape Portal.](https://help.sap.com/docs/BTP/60f1b283f0fd4d0aa7b3f8cea4d73d1d/5eb70fb003954619b09224167a0afaa4.html?state=DRAFT&version=Internal)

-   **ASP\_CC Destination**: An `OAuth2Password` destination pointing to the Cloud Foundry Cloud Controller API is required for the ABAP Solution service to create and access ABAP service instances. Credentials of a technical platform user, that is assigned as a space developer in the space where the multitenant application is deployed, are maintained.






### Multitarget Application

The multitenant application is deployed as a multitarget application \(MTA\), which is logically a single application comprised of multiple parts created with different technologies.

The MTA describes the desired result in an mta.yaml file which may be extended with mta extensions \(.mtaext\) using the MTA model which contains MTA modules, MTA resources and interdependencies between them. Afterwards, the MTA deployment service validates, orchestrates, and automates the deployment of the MTA, which results in Cloud Foundry \(CF\) applications, services and SAP-specific contents. For more information about the Multitarget Application model, see the official The Multitarget Application Model specification. For more details on how to use it in the CF Environment, which is the case here, see [Multitarget Applications in the Cloud Foundry Environment.](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/d04fc0e2ad894545aebfd7126384307c.html?locale=en-US&version=Cloud)

A complete reference example of the multitenant application MTA is provided in GitHub/SAPSamples: [ABAP SaaS Reference Solution for ABAP solution provider](https://github.com/sap-software/abap-saas-reference-solution) 



### MTA Parameters

Parameters are defined at the beginning of the mta.yaml file, so that the actual structure of the MTA model does not have to be changed but can be extended via extension files. The parameters are referenced in the subsequent sections of the MTA using the syntax `${parameter-name}`. For more details on parameters, see [Parameters and Properties](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/490c8f71e2b74bc0a59302cada66117c.html?locale=en-US&version=Cloud).

-   **Freely defined parameters:**

    -   app-domain: The domain that should be used for the approuter and therefore the SaaS application. In our example, this is the $\{default-domain\} \(equals to the cfapps-domain of the current landscapes\) for a development deployment; for production it should be the custom domain \(so here: `mydomain.com`\).

    -   appname: The value that should be used as xsappname and solution name \(here: `abap-saas-reference-solution)`.

    -   route-prefix: The value that should be used as a prefix in the route of the approuter, allowing it to deploy the same MTA to the same landscape muliple times using the default landscape domain.

    -   addon-product-name: Name of add-on product to be installed

    -   provider-admin-email: Provider administrator e-mail address used for provisioning of ABAP systems

    -   saas-display-name: Display name of SaaS application shown in subscription tile

    -   saas-description: Description of SaaS application shown in subscription tile

    -   tenant-mode: Whether to provide a `'single'` or `'multi'` tenancy solution


-   **Parameter with semantics to MTA deployer:**

    -   enable-parallel-deployments: If set to `true`, deploys multiple modules at the same time.





### MTA Extension Descriptors

The parameters defined in the MTA can be adapted for the corresponding landscape using MTA extension descriptor files. These files extend the original MTA descriptor file \(mta.yaml\) and provide certain deployment specific configurations/parameters/valuest. The descriptor files have the file extension \*.mtaext and are used during the deployment using CF CLI with MultiApps plugin, see [MultiApps CF CLI Plugin](https://github.com/cloudfoundry-incubator/multiapps-cli-plugin).

For more information on MTA extension descriptors, see: [Defining MTA Extension Descriptors.](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/50df803465324d36851c79fd07e8972c.html) 

The extension descriptor files are usually in the folder “extensions” next to the mta.yaml file.

Depending on the stage of implementation of the multitenant application, a different approuter configuration is used. This is controlled via different extension descriptor files used during MTA deployment:

-   Configuration for **Development Phase**:

    For development, test and demo purposes, MTA deployment can be done using the`${default-domain}` as `app-domain`and a `route-prefix`, which will avoid collisions due to the default domain. Additionally, we suggest setting the property `XS_APP_LOG_LEVEL` on the approuter module to `debug` to ensure that there is more detailed logging output.

-   Configuration for **Production Phase**:

    For purpose of providing a solution / solutions to applications consumers in a production scenario, the MTA deployment should be done using a custom domain configured with the app-domain parameter \(`app-domain`\) and an empty route-prefix \(`route-prefix.`\). Using the custom domain, a wildcard route for tenant access \("`*.${app-domain}`"\) can be created.




### MTA Build and Deploy

Before MTA deployment, the MTA project is built using the[Cloud MTA Build Tool \(MBT\)](https://sap.github.io/cloud-mta-build-tool/). Afterwards the deployment-ready multitarget application archive \(\*.mtar file\) is deployed in combination with the corresponding MTA extension descriptor file using the Cloud Foundry CLI with the MultiApps plugin: `cf deploy <path to .mtar file> -e <path to MTA extension descriptor>`



### Related Information

[Installing the cf CLI](https://docs.cloudfoundry.org/cf-cli/install-go-cli.html)

[MultiApps CF CLI Plugin - Download and Installation](https://github.com/cloudfoundry-incubator/multiapps-cli-plugin#download-and-installation)

[MultiApps CF CLI Plugin - Usage](https://github.com/cloudfoundry-incubator/multiapps-cli-plugin#usage)

