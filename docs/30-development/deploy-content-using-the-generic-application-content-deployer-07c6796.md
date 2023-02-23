<!-- loio07c679672e5f423e9dc631fc85b51da3 -->

# Deploy Content Using the Generic Application Content Deployer

Deploy content from the HTML5 Application Repository using the Generic Application Content Deployer \(GACD\).



<a name="loio07c679672e5f423e9dc631fc85b51da3__prereq_ksl_xjb_kdb"/>

## Prerequisites

-   `cf CLI` is installed locally, see [Download and Install the Cloud Foundry Command Line Interface](../50-administration-and-ops/download-and-install-the-cloud-foundry-command-line-interface-4ef907a.md).

-   The multitarget application \(MTA\) plug-in for the Cloud Foundry command-line interface to deploy MTAs is installed locally. For more information, see [Install the MultiApps CLI Plugin in the Cloud Foundry Environment](../50-administration-and-ops/install-the-multiapps-cli-plugin-in-the-cloud-foundry-environment-27f3af3.md).

-   The Cloud MTA Build Tool \(MBT\) is installed, see [Cloud MTA Build Tool: Download](https://sap.github.io/cloud-mta-build-tool/download/)




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

2.  Create an MTA development descriptor \(mta.yaml file\).

    See [Defining Multitarget Application Development Descriptors](defining-multitarget-application-development-descriptors-c2d31e7.md).

3.  In the MTA development descriptor \(mta.yaml file\), define the deployer module:

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

4.  To create an MTA archive \(mtar file\), build your content with the[MTA Build Tool \(MBT\)](https://sap.github.io/cloud-mta-build-tool/).

    Run the following command:

    > ### Sample Code:  
    > ```
    > mbt build
    > ```

    For more information on MBT build options, see: [How to build an MTA archive from the project sources](https://sap.github.io/cloud-mta-build-tool/usage/#how-to-build-an-mta-archive-from-the-project-sources)

5.  Deploy the MTA archive \(mtar file\) using the CLI command cf deploy.

    Run the following command:

    > ### Sample Code:  
    > ```
    > cf deploy <path-to-mtar-file>
    > ```

    For example, from the directory where your mtar file is located, run `cf deploy myapp_0.0.1.mtar`.


**Related Information**  


[Content Deployment](content-deployment-d3e2319.md "Direct content deployment provides a mechanism for deploying content to services without the need for an application-specific deployer.")

