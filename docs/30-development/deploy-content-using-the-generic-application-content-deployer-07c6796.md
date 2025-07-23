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

1.  Create an MTA development descriptor \(mta.yaml file\).

    See [Defining Multitarget Application Development Descriptors](defining-multitarget-application-development-descriptors-c2d31e7.md).

2.  In the MTA development descriptor \(mta.yaml file\), define the deployer module:

    This is an example for an MTA that contain a folder for an application "app1" and an application "app2":

    > ### Sample Code:  
    > ```
    > ID: testdeployer
    > _schema-version: '3.1'
    > modules:
    > # GACD Deployer Module
    >  name: html5-apps-content
    >   type: com.sap.application.content
    >   path: .
    >   requires:
    >     - name: html5-apps-xsuaa
    >     - name: html5-apps-html5-repo-host
    >     parameters:
    >       content-target: true
    >   build-parameters:
    >     build-result: resources
    >     requires:
    >     - name: app1
    >       artifacts:
    >       - app1.zip
    >       target-path: resources/
    >     - name: app2
    >       artifacts:
    >       - app2.zip
    >       target-path: resources/
    > 
    > # HTML5 Modules
    > - name: app1
    >   type: html5
    >   path: app1
    >   build-parameters:
    >     build-result: dist
    >     builder: custom
    >     commands:
    >     - npm install
    >     - npm run build:cf
    >     supported-platforms: []
    > 
    > - name: app2
    >   type: html5
    >   path: app2
    >   build-parameters:
    >     build-result: dist
    >     builder: custom
    >     commands:
    >     - npm install
    >     - npm run build:cf
    >     supported-platforms: []
    > 
    > resources:
    > # HTML5 Application Repository service instance
    > - name: html5-apps-html5-repo-host
    >   type: org.cloudfoundry.managed-service
    >   parameters:
    >     service: html5-apps-repo
    >     service-name: html5-apps-html5-repo-host-service
    >     service-plan: app-host
    > # SAP Authorization and Trust Management service (technical name: xsuaa)
    > - name: html5-apps-xsuaa
    >   type: org.cloudfoundry.managed-service
    >   parameters:
    >     path: ./xs-security.json
    >     service: xsuaa
    >     service-name: html5-apps-xsuaa
    >     service-plan: application
    > 
    > 
    > ```

3.  To create an MTA archive \(mtar file\), build your content with the[MTA Build Tool \(MBT\)](https://sap.github.io/cloud-mta-build-tool/).

    Run the following command:

    > ### Sample Code:  
    > ```
    > mbt build
    > ```

    For more information on MBT build options, see: [How to build an MTA archive from the project sources](https://sap.github.io/cloud-mta-build-tool/usage/#how-to-build-an-mta-archive-from-the-project-sources)

4.  Deploy the MTA archive \(mtar file\) using the CLI command cf deploy.

    Run the following command:

    > ### Sample Code:  
    > ```
    > cf deploy <path-to-mtar-file>
    > ```

    For example, from the directory where your mtar file is located, run `cf deploy myapp_0.0.1.mtar`.


**Related Information**  


[Deploying Content with Generic Application Content Deployment](deploying-content-with-generic-application-content-deployment-d3e2319.md "This approach provides a mechanism for direct content deployment from SAP Cloud Deployment service to the content backend without the need for an intermediate Cloud Foundry application.")

