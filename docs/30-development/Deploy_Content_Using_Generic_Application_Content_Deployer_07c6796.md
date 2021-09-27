<!-- loio07c679672e5f423e9dc631fc85b51da3 -->

# Deploy Content Using Generic Application Content Deployer

Deploy content from the HTML5 Application Repository using the Generic Application Content Deployer \(GACD\).



<a name="loio07c679672e5f423e9dc631fc85b51da3__prereq_ksl_xjb_kdb"/>

## Prerequisites

-   `cf CLI` is installed locally, see [Download and Install the Cloud Foundry Command Line Interface](../50-administration-and-ops/Download_and_Install_the_Cloud_Foundry_Command_Line_Interface_4ef907a.md).

-   The multitarget application \(MTA\) plug-in for the Cloud Foundry command-line interface to deploy MTAs is installed locally. For more information, see [Install the MultiApps CLI Plugin in the Cloud Foundry Environment](../50-administration-and-ops/Install_the_MultiApps_CLI_Plugin_in_the_Cloud_Foundry_Environment_27f3af3.md).




<a name="loio07c679672e5f423e9dc631fc85b51da3__context_bqj_b4j_43b"/>

## Context

You can deploy your content to the HTML5 Application Repository using the GACD \(Generic Application Content Deployer\) module. The GACD module has the module type `com.sap.application.content`. This module type enables the deploy plug-in generic application content deploy support. It means that when a module is processed in the cf deploy flow, the deploy service locates the service resource that is required as a target for the deploy and deploys the corresponding `content.zip` file.



<a name="loio07c679672e5f423e9dc631fc85b51da3__steps_nxt_t4j_43b"/>

## Procedure

1.  Create a nested `content.zip` file that contains a zip file for each HTML5 application.

    Example of a nested content.zip file

    > ### Sample Code:  
    > ```
    > content.zip
    >     app1.zip
    >        manifest.json
    >        xs-app.json
    >        …..
    >     app2.zip
    >     …..
    > 
    > ```

2.  Create an \*.mtar file with following structure:

    > ### Sample Code:  
    > ```
    > myMtar.mtar
    >     …
    >     mydeployer
    >          content.zip
    >     META-INF
    >           mtad.yaml
    >           MANIFEST.MF
    > 
    > ```

3.  3. In the `MANIFEST.MF` file, define the following section for the deployer:

    > ### Sample Code:  
    > ```
    > Manifest-Version: 1.0
    > Created-By: SAP WebIDE
    > 
    > Name: mydeployer/content.zip
    > MTA-Module: ui_deployer
    > Content-Type: application/zip
    > 
    > ```

4.  In the `mtad.yaml` file, define the deployer module:

    > ### Sample Code:  
    > ```
    > ID: testdeployer
    > _schema-version: '3.1'
    > modules:
    >  - name: ui_deployer
    >    type: com.sap.application.content
    >    requires:
    >     - name: uideployer_html5_repo_host
    >       parameters:
    >         content-target: true
    > resources:
    >  - name: uideployer_html5_repo_host
    >    parameters:
    >       service-plan: app-host
    >       service: html5-apps-repo
    >    type: org.cloudfoundry.managed-service
    > version: 0.0.1
    > ```

5.  Deploy the `*.mtar` using the CLI command cf deploy.


**Related Information**  


[Content Deployment](Content_Deployment_d3e2319.md "Direct content deployment provides a mechanism for deploying content to services without the need for an application-specific deployer.")

