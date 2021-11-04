<!-- loio72b0b1130ee243179b0905ea2cd5adb1 -->

# Enabling SaaS Applications for Customers

You can provide an application to multiple customers as a SaaS solution in the ABAP environment. This process comprises the following steps: the build of an add-on version, its deployment to the cloud with a multitarget application, its ordering and provisioning, and a possible updating process. The following concrete example guides you step by step through this process.

 <a name="loio73ebc486aa7f46eb9783799c924b7556"/>

<!-- loio73ebc486aa7f46eb9783799c924b7556 -->

## Build

**Build a first version of your add-on. See [Build](Develop,_Test,_Build_3bf575a.md#loio25049720bde447e395b3df0bc05e5a50)**



<a name="loio73ebc486aa7f46eb9783799c924b7556__section_ykk_bjt_hrb"/>

## Prerequisites

-   You've set up the following accounts:
    -   **Global development account** with a *01 Develop* subaccount for development, a *02 Test* subaccount for testing, and a *03 Build/Assemble* subaccount \(for example with the Cloud Foundry organization name `saas-build-assemble` and a development space with the name `Build/Assemble`\) for assembling the add-on product. See [Set Up a Development Account](Develop,_Test,_Build_3bf575a.md#loio9f2150f2b15e414aacd46c1723ce48fb).
    -   **Global production account** with a *04 Build/Test* subaccount \(for example with the Cloud Foundry organization name `saas-build-test` and a development space with the name `Build/Test`\) for installing and testing the add-on, a *05 Provide* subaccount \(for example with Region `cf-eu10`\) for providing the add-on to customers, and a *06 Consume* subaccount \(for example with the subdomain `my consumer subdomain`\) to access the solution as a customer. See [Set Up a Production Account](Develop,_Test,_Build_3bf575a.md#loio2e7b4b631e814de1b8fe3959af4105bc).

-   You've purchased entitlements that are necessary for the account setup. See [Prepare](Develop,_Test,_Build_3bf575a.md#loio4338854e3133407abb47d3a281dbd1e1).
-   You've registered a namespace at SAP, for example /NAMESPC/. See [Register a Namespace](Develop,_Test,_Build_3bf575a.md#loiocc5a3c6f78cf4889960c314dd09a5060).
-   You've registered your add-on at SAP, for example /NAMESPC/PRODUCTX. See [Build](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/3bf575a3dc5043f895f8bd411d2a86a1.html#loio25049720bde447e395b3df0bc05e5a50).
-   You've set up Jenkins build pipeline and have ensured that an external Git repository is available for the pipeline definition. See [ABAP Environment Pipeline](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/9482e7eef4634cb993a4ae296b2029fa.html#loio2398b874f7c5445db188b780ff0cef89).
    -   You've created a technical communication user, for example with the credentials ID `TechUserAAKaaS`.
    -   You've created a technical platform user, for example with the credentials ID `CFPlatform`.

-   You've developed your software component /NAMESPC/COMPONENT1 in the development system of your *01 Develop* subaccount.
    -   For more information on software components, see [Manage Software Components](../50-administration-and-ops/Manage_Software_Components_3dcf76a.md).
    -   For more information on the ABAP RESTful Application Programming Model, see [ABAP RESTful Application Programming Model](ABAP_RESTful_Application_Programming_Model_33a301e.md) or [Develop a Fiori App Using the ABAP RESTful Programming Model \(Managed Scenario\)](https://developers.sap.com/group.abap-env-restful-managed.html).
    -   For more information on how to develop a user interface for the application, see [Develop an SAP Fiori Application UI and Deploy it to ABAP Using SAP Business Application Studio](Develop_an_SAP_Fiori_Application_UI_and_Deploy_it_to_ABAP_Using_SAP_Business_Application_Studio_eaaeba4.md).


-   You've subscribed to SAP Business Application Studio in your *01 Develop* subaccount.

    > ### Note:  
    > We recommend using SAP Business Application Studio for developing user interfaces. You can also use other tools, such as Visual Studio Code. This guide relies on SAP Business Application Studio.

-   You've tested the application in your software component in the test system of your *02 Test* subaccount. See [Test](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/3bf575a3dc5043f895f8bd411d2a86a1.html#loio023cf9d301b1479484e70b17cd5cf587).
-   You've assigned the `LandscapePortalAdminRoleCollection` in your *05 Provide* subaccount under *Role Collections*. See [Access to Landscape Portal](Order_and_Provide_975bd3e.md#loio195a685a71f84953813e7b3bd255e849).
-   You've assigned a technical Cloud Foundry platform user as space developer in the *Provide* space of the *05 Provide* subaccount. See [Creating New Space Members and Assigning Space Developer Roles to Them](../20-getting-started/Creating_New_Space_Members_and_Assigning_Space_Developer_Roles_to_Them_967fc4e.md).
-   You've configured an ASP\_CC destination for cloud controller access in the *05 Provide* subaccount based on the credentials of the technical Cloud Foundry platform user. See [Create a Destination for the Cloud Foundry Cloud Controller Access](Create_a_Destination_for_the_Cloud_Foundry_Cloud_Controller_Access_35b5acb.md).



1.  To capture the current state of your software component, create a branch in the development system of your *01 Develop* subaccount. See [How to Work with Branches](../50-administration-and-ops/How_to_Work_with_Branches_6b2f0bf.md)

    > ### Recommendation:  
    > We recommend naming this first branch v1.0.0 and to create a new branch when updating the application with a support package \(v1.1.0\) or a new release \(v2.0.0\).

2.  Configure the Jenkins pipeline in your pipeline Git repository by creating the following files:

    -   Create a folder `.pipeline` with the following `config.yml` file:

        ```
        general:
          addonDescriptorFileName: 'addon.yml'
          abapAddonAssemblyKitCredentialsId: 'TechUserAAKaaS'
          cfCredentialsId: 'CFPlatform'
          cfApiEndpoint: 'https://api.cf.sap.hana.ondemand.com'
          cfOrg : 'saas-build-assemble'
          cfSpace: 'Build/Assemble'
          cfServiceInstance: 'BLD_BONUS'
          cfServiceKeyName: 'SAP_COM_0510'
        stages:
          Prepare System:
            cfService: 'abap'
            cfServicePlan: 'standard'
            abapSystemAdminEmail: 'administrator@example.com'
            abapSystemDescription: 'Partner SaaS on ABAP (Development)'
            abapSystemIsDevelopmentAllowed: false
            abapSystemID: 'BLD'
            abapSystemSizeOfPersistence: 4
            abapSystemSizeOfRuntime: 1
            includeAddon: false
            cfServiceKeyConfig: 'sap_com_0510.json'
          Clone Repositories:
            repositories: 'addon.yml'
            strategy: 'Clone'
          ATC:
            atcConfig: 'atcConfig.yml'
          Build:
            cfServiceKeyName: 'SAP_COM_0582'
            cfServiceKeyConfig: 'sap_com_0582.json'
          Integration Tests:
            cfOrg : 'saas-build-test'
            cfSpace: 'Build/Test'
            cfService: 'abap-oem'
            cfServicePlan: 'saas_oem'
            cfServiceInstance: 'ATI_BONUS'
            abapSystemAdminEmail: 'administrator@example.com'
            abapSystemDescription: 'Partner SaaS on ABAP (Production)'
            abapSystemIsDevelopmentAllowed: false
            abapSystemID: 'ATI'
            abapSystemSizeOfPersistence: 4
            abapSystemSizeOfRuntime: 1
            includeAddon: true
            confirmDeletion: true
          Publish:
            targetVectorScope: 'P'
          Post:
            confirmDeletion: true
            cfDeleteServiceKeys: true
        ```


    Section general:

    -   Imperatively adapt the following parameters:

        -   For **abapAddonAssemblyKitCredentialsId**, enter the credentials ID of your technical communication user.

        -   For **cfCredentialsId**, enter the credentials ID of your technical platform user.

            > ### Note:  
            > You find the credentials ID of your technical communication user and your technical platform user in your Jenkins pipeline repository under *Manage Jenkins* \> *Manage Credentials*.

        -   For **cfApiEndpoint**, enter the link to your API Endpoint.

        -   For **cfOrg**, enter the Cloud Foundry organization name.

        -   For **cfSpace**, enter the name of the development space you want to use.

            > ### Note:  
            > You find the API Endpoint, the Cloud Foundry organization name displayed as Org Name, and the name of your development space in your *03 Build/Assemble* subaccount under *Overview*.



    Section stages:

    -   Imperatively adapt the following parameters:

        -   For **abapSystemAdminEmail**, enter the e-mail address of your administrator.

        -   For **cfOrg**, enter the Cloud Foundry organization name.

        -   For **cfSpace**, enter the name of the development space you want to use.

            > ### Note:  
            > You find the Cloud Foundry organization name displayed as Org Name and the name of your development space in your *04 Build/Test* subaccount under *Overview*.



    Keep all other parameters as set in the example.

    -   Create the following `addon.yml` file:

        ```
        addonProduct: /NAMESPC/PRODUCTX
        addonVersion: 1.0.0
        repositories:
           - name: /NAMESPC/COMPONENT1
             branch: v1.0.0
             version: 1.0.0
             commitID: abcd1234
        ```

        -   For **addonProduct**, enter the reserved development namespace /NAMESPC/ and your product name PRODUCTX.

        -   For the name of the repository, enter the name of the respective software component /NAMESPC/COMPONENT1.

        -   Enter the required commitID of the software component state that shall be used.

            > ### Note:  
            > You find the latest **commitID** in the development system of your *01 Develop* subaccount in the *Manage Software Components* app. To view a history of all commits and their IDs, click the required branch.



    -   Create the following `atcConfig.yml` file in the root folder:

        ```
        checkvariant: SAP_CLOUD_PLATFORM_ATC_DEFAULT
        atcobjects:
          softwarecomponent:
            - name: "/NAMESPC/COMPONENT1"
        ```

    -   Create the following `Jenkinsfile` file in the root folder:

        ```
        @Library('piper-lib-os') _
        
        abapEnvironmentPipeline script: this
        
        ```

    -   Create the following `sap_com_0510.json` file in the root folder:

        ```
        {
          "scenario_id": "SAP_COM_0510",
          "type": "basic"
        }
        ```

    -   Create the following `sap_com_0582.json` file in the root folder:

        ```
        {
          "scenario_id": "SAP_COM_0582",
          "type": "basic"
        }
        ```


    The final structure should look like this:

     ![](images/Pipeline_definition_8a9a4e5.png) 

3.  Start the build pipeline.
4.  Once the build was successful, publish your initial add-on version: hover over the *Publish* stage in your pipeline and click *confirm*.

 <a name="loio7e91d5f55e5e4a6aa723b8282ad804fe"/>

<!-- loio7e91d5f55e5e4a6aa723b8282ad804fe -->

## Deploy

**Deploy your add-on to the Cloud Foundry infrastructure by creating a multitarget application in SAP Business Application Studio**.



1.  To prepare the creation of your multitarget application, navigate to your dev space in SAP Business Application Studio. Select *Start from Template* \> *Basic Multitarget Application*.

    -   In the automatically created descriptor file `mta.yaml`, enter the following content:

        ```
        _schema-version: "3.1"
        ID: product1-saas-solution
        version: 1.0.0
        
        parameters:
          app-domain: ${default-domain}
          route-prefix: -${appname}
          appname: 
          addon-product-name:
          provider-admin-email: 
          saas-display-name: 
          saas-description: 
          tenant-mode: 
          enable-parallel-deployments: true
        
        modules:
          - name: approuter
            type: javascript.nodejs
            path: approuter
            parameters:
              keep-existing-routes: true
              routes:
                - route: cis${route-prefix}.${app-domain}
              app-name: ${appname}
              memory: 1024MB
            properties:
              TENANT_HOST_PATTERN: (.*)${route-prefix}.${app-domain}
              XS_APP_LOG_LEVEL: error
              SAP_JWT_TRUST_ACL:
                - clientid: "*"
                  identityzone: sap-provisioning
            requires:
              - name: xsuaa
              - name: saas-registry
              - name: abap-solution
              - name: application-log
        
        resources:
          - name: xsuaa
            type: com.sap.xs.uaa
            requires:
              - name: abap-solution
            parameters:
              service-plan: application
              service-name: xsuaa
              config:
                xsappname: ${appname}
                tenant-mode: shared
                scopes:
                  - name: $XSAPPNAME.Callback
                    description: With this scope set, the callbacks for tenant onboarding, offboarding and getDependencies can be called.
                    grant-as-authority-to-apps:
                      - $XSAPPNAME(application,sap-provisioning,tenant-onboarding)
                foreign-scope-references:
                  - uaa.user
                role-collections:
                  - name: ${appname}-admin
                    role-template-references:
                      - $XSSERVICENAME(abap-solution).SolutionAdmin
        
          - name: saas-registry
            type: org.cloudfoundry.managed-service
            parameters:
              service: saas-registry
              service-plan: application 
              service-name: saas-registry
              config:
                xsappname: ${appname}
                appName: ${appname}
                appUrls:
                  getDependencies: https://cis${route-prefix}.${app-domain}/callback/v1.0/dependencies
                  onSubscription: https://cis${route-prefix}.${app-domain}/callback/v1.0/tenants/{tenantId}
                displayName: ${saas-display-name}
                description: ${saas-description}
        
          - name: abap-solution
            type: org.cloudfoundry.managed-service
            parameters: 
              service: abap-solution
              service-plan: standard
              service-name: abap-solution
              config:
                name: ${appname}
                addon_product_name: ${addon-product-name}
                size_of_runtime: 1
                size_of_persistence: 4
                tenant_mode: ${tenant-mode}
                consumer_id_pattern: ([^-]*).*
                provider_admin_email: ${provider-admin-email}
                usage: prod
                xs-security:
                  xsappname: ${appname}
        
          - name: application-log
            type: org.cloudfoundry.managed-service
            parameters:
              service: application-logs
              service-plan: lite
              service-name: application-log
        
        ```

    -   To define the open parameters of the `mta.yaml` file, create a new folder `extensions` that contains the following `dev.mtaext` file:

        ```
        ID: product1-saas-solution-dev
        _schema-version: "3.1"
        extends: product1-saas-solution
        
        modules:  
          - name: approuter
            properties: 
              XS_APP_LOG_LEVEL: debug
        
        parameters:
          appname: product1-saas-solution-dev
          addon-product-name: /NAMESPC/PRODUCTX
          provider-admin-email: administrator@example.com
          saas-display-name: "SaaS Solution (Multitenancy)"
          saas-description: "ABAP based SaaS solution with an ABAP tenant per subscription"
          tenant-mode: multi
        
        ```

        -   The **appname** is a technical name that defines the SaaS solution and appears, for example, as prefix in the service instance of your *05 Provide* subaccount.

            > ### Note:  
            > You can only use ASCII letters and digits. Do not use a hyphen in the beginning or end of the appname.

        -   For **addon-product-name**, enter the registered name of the addon product.

            > ### Note:  
            > This must be the same name as defined in the `addon.yml` file in step 1b.

        -   For **provider-admin-email**, enter the e-mail address of the initial provider user.
        -   The **saas-display-name** defines the name of the tile in the cloud.
        -   The **saas-description** is displayed as a short description of the application in the cloud.

        -   The **tenant-mode** defines the tenant mode \(multi or single\).

        > ### Note:  
        > Once you switch the approuter to the production phase, create and use a new extension file \(see [Production Descriptor](Production_Descriptor_38ff6d0.md).\)

    -   Create a folder `approuter` with the following files \(see also [Develop the Approuter Application](Develop_the_Approuter_Application_44dbd0a.md)\):

        -   a `package.json` file with the following content:

            ```
            {
              "name": "saas-ar",
              "version": "1.0.0",
              "description": "This component provides dependency management for ABAP based SaaS Solutions",
              "dependencies": {
                "@sap/approuter": "^8.3.1",
                "@sap/asp-middleware": "^1.0.6",
                "@sap/xsenv": "^3.0.0"
              },
              "scripts": {
                "start": "node --inspect start.js"
              }
            }
            ```

        -   a `start.js file` with the following content:

            ```
            const approuter = require('@sap/approuter');
            const ar = approuter();
            
            ar.start({
                extensions: [
                    require('@sap/asp-middleware')
                ]
            });
            
            ```

        -   an `xs-app.json` file with the following content:

            ```
            {
            	"authenticationMethod": "route",
            	"welcomeFile": "/ui",
            	"logout": {
            		"logoutEndpoint": "/sap/public/bc/icf/logoff",
                		"logoutPage": "/ui"
            	},
              	"routes": [
            		{
            			"source": "^/sap/(.*)$",
            			"target": "/sap/$1",
            			"authenticationType": "xsuaa",
            			"service": "com.sap.cloud.abap.solution",
            			"csrfProtection": false
            		},
            		{
            			"source": "^/ui(.*)$",
            			"target": "/ui$1",
            			"authenticationType": "xsuaa",
            			"service": "com.sap.cloud.abap.solution",
            			"csrfProtection": false
            		}
            	]
            }
            ```



    The final structure looks like this:

     ![](images/Folder_structure_multitarget_application_894aa3f.png) 

    > ### Note:  
    > Depending on the setup of your development environment, you need to run command `npm install` within the approuter folder to install the dependencies in the local `node_modules` folder.

2.  To create the multitarget application, right-click the folder `mta.yaml` and select *Build MTA Project*.
3.  To deploy the multitarget application with extensions to the *05 Provide* subaccount in your global production account, open a new terminal for the project and enter:

    ```
    cf deploy mta_archives/product1-saas-solution_1.0.0.mtar -e extensions/dev.mtaext
    ```


> ### Note:  
> During the MTA build, an MTA archive file is automatically created with the MTA ID acting as the file name. For example, `product1-saas-solution_1.0.0.mtar` is created for MTA ID `product1-saas-solution`.

 <a name="loio1d90459d98ca4ba0bc8857c24e328c03"/>

<!-- loio1d90459d98ca4ba0bc8857c24e328c03 -->

## Order and Provide

**Order and provide your solution**. See [Order and Provide](Order_and_Provide_975bd3e.md#loio975bd3e54cbe4e52af346740658d1a4a).



1.  To define a new route to the solution, open your *05 Provide* subaccount and navigate to *Cloud Foundry* \> *Spaces*. Select your Space and navigate to *Routes*. Click *New Route* and enter the following information in the dialogue:

    ```
    Domain: cfapps.eu10.hana.ondemand.com
    Hostname: my-consumer-subdomain-product1-saas-solution-dev
    ```

    > ### Note:  
    > For a consumer to be able to access the SaaS solution after subscription, a consumer-specific route pointing to the approuter application needs to be created. See [Create Routes](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/9fddeea396b34b528bc8d286f3d5d9cf.html).
    > 
    > This route needs to match the property `TENANT_HOST_PATTERN` defined in the `mta.yaml` file.
    > 
    > **`TENANT_HOST_PATTERN: (.*)${route-prefix}.${app-domain}`**
    > 
    > The pattern includes a placeholder for the subdomain of a consumer subaccount and a route prefix. The route prefix consists of a separator ***-***, and the defined appname.
    > 
    > The subdomain can only contain letters, digits, and hyphens, see [Create Subaccount](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/05280a123d3044ae97457a25b3013918.html).
    > 
    > When you create the route, you have to provide a hostname and domain.
    > 
    > Domain: ***cfapps.eu10.hana.ondemand.com***
    > 
    > Hostname: ***my-consumer-subdomain-product1-saas-solution-dev***
    > 
    > The hostname can include no more than 63 characters.
    > 
    > In this example, the consumer subaccount is created with subdomain ***my-consumer-subdomain***. The defined appname is ***product1-saas-solution-dev***, resulting in the hostname ***my-consumer-subdomain-product1-saas-solution-dev*** of the route. The domain `cfapps.eu10.hana.ondemand.com` is set as parameter `app-domain` in the `mta.yaml` file.
    > 
    > Once you switch to the production phase of the approuter configuration and define a route with wildcard hostname. this sub-step is no longer required . See [Configure the Approuter Application](Configure_the_Approuter_Application_3725815.md).

    -   For **Domain**, enter the appropriate domain by changing the default domain **cfapps.<region\>.hana.ondemand.com** according to the region of your *05 Provide* subaccount.

    -   For **Hostname**, enter the subdomain as displayed in your *06 Consume* subaccount under *Overview* and the appname as defined in your `dev.mtaext` file.

2.  Assign the route to the deployed approuter application.
3.  Subscribe to the solution: Navigate to *Service Marketplace* in your *06 Consume* subaccount and search for your service. Click *create* \> *Create*.
4.  To enable the creation of the initial administrator user in the consumer tenant, in the *06 Consume* subaccount under *Security* \> *Role Collections*, assign the role colletion <app name\>-admin with the role `SolutionAdmin` to your user.
5.  Open the application URL provided by the subscription with the user that shall be onboarded as initial administrator user. This is the same user that was assigned to the `<app name>-admin` role collection.

    After triggering initial user onboarding, you are redirected to the SAP Fiori launchpad of the SaaS solution.


 <a name="loio874dd6060ac64c56a1741d3b6401cf1e"/>

<!-- loio874dd6060ac64c56a1741d3b6401cf1e -->

## Maintain

**Maintain your solution**. See [Maintain](Maintain_9721f0f.md#loio9721f0fb92a84e2a95309acf445cb0a9).

> ### Note:  
> You can update your solution with patches, support packages, or new releases. Create a new branch from the main branch in your *01 Develop* subaccount for every support package or new release. For minor changes, continue developing in the respective active branch.
> 
> The following example shows how to update your solution with a support package.



1.  Continue the development in the main branch.
2.  To test the development, pull the new state of the main branch to the software component in your *02 Test* subaccount in the *Manage Software Components* app.
3.  Create a new branch v1.1.0 from the main branch for your software component in your *01 Develop* subaccount.
4.  Prepare the build process of your Jenkins pipeline by adjusting the `addon.yml` file as follows:

    ```
    addonProduct: /NAMESPC/PRODUCTX
    addonVersion: 1.1.0
    repositories:
       - name: /NAMESPC/COMPONENT1
         branch: v1.1.0
         version: 1.1.0
         commitID: abcd1234
    ```

5.  *Commit Changes* and start the build pipeline.
6.  To provide the new version 1.1.0 to customers, open the *Landscape Portal* in your *05 Provide* subaccount. Select the system in question and click *Add-On Update*.

**Related Information**  


[Developing and Operating SaaS Applications Using Add-Ons](Developing_and_Operating_SaaS_Applications_Using_Add-Ons_e3c38eb.md "Learn how to develop and operate SaaS applications by using add-ons in the ABAP environment.")

[Overview](Overview_9640543.md "")

