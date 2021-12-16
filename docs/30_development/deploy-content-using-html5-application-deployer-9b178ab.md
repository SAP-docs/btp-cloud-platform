<!-- loio9b178ab3388c4647b0c52f2c85641844 -->

# Deploy Content Using HTML5 Application Deployer

Use the HTML5 application deployer module to deploy the content of the HTML5 applications to the HTML5 Application Repository.



<a name="loio9b178ab3388c4647b0c52f2c85641844__prereq_ksl_xjb_kdb"/>

## Prerequisites

-   `cf CLI` is installed locally, see [Download and Install the Cloud Foundry Command Line Interface](../50_administration_and_ops/download-and-install-the-cloud-foundry-command-line-interface-4ef907a.md).

-   The multi-target application \(MTA\) plug-in for the Cloud Foundry command line interface to deploy MTAs is installed locally. For more information, see [Install the MultiApps CLI Plugin in the Cloud Foundry Environment](../50_administration_and_ops/install-the-multiapps-cli-plugin-in-the-cloud-foundry-environment-27f3af3.md).


> ### Restriction:  
> Please note that application deployment using the HTML5 application deployer is limited to total of 10 MB.
> 
> For larger application content, please use the [Generic Application Content Deployer \(GACD\)](deploy-content-using-generic-application-content-deployer-07c6796.md).



## Context

You can deploy your content to the HTML5 Application Repository using the HTML5 application deployer npm module.



## Procedure

1.  Add the `html5-app-deployer` module as a dependency to your `package.json` file. To do so, navigate to your `package.json` file and execute `npm install` to download the `html5-app-deployer module` from the SAP npm registry.

    The basic `package.json` file should look similar to the following example:

    > ### Sample Code:  
    > ```
    > {
    >   "name": "myAppDeployer",
    >   "engines": {
    >     "node": ">=6.0.0"
    >   },
    >   "dependencies": {
    >     "@sap/html5-app-deployer": "2.0.1"
    >   },
    >   "scripts": {
    >     "start": "node node_modules/@sap/html5-app-deployer/index.js"
    >   }
    > }
    > 
    > ```

    The `start` script is mandatory as it is executed after the deployment of the application.

2.  In the `html5-app-deployer` structure, create a `resources` folder and add the static content that you want to deploy. In the `resources` folder, add one folder for each application you want to deploy. For each application you want to deploy, provide a `manifest.json` and `xs-app.json` file at root level.

    If you want to deploy more than one application to the same app host instance, you can add multiple zip archives to the resources folder.

    > ### Sample Code:  
    > ```
    > myAppsDeployer
    >   + node_modules
    >   - resources
    >     - app1
    >       index.html
    >       manifest.json
    >       xs-app.json
    >     - app2
    >       ...
    >   package.json
    >   manifest.yaml
    > ```

    1.  The `manifest.json` file contains `sap.app.id` and `sap.app.applicationVersion.version`, which are used in the HTML5 Application Repository as `applicationName` and `applicationVersion`.

        > ### Note:  
        > The format of the application version is `xx.xx.xx`.

        > ### Sample Code:  
        > ```
        > manifest.json
        > {
        >   "_version": "1.7.0",
        >   "sap.app": {
        >     "id": "app1",
        >     "type": "application",
        >     "i18n": "i18n/i18n.properties",
        >     "applicationVersion": {
        >       "version": "1.0.0"
        >     }
        >   }
        > }
        > ```

    2.  The `xs-app.json` file is used to support application routing.

        > ### Sample Code:  
        > ```
        > xs-app.json
        > {
        >  "welcomeFile": "index.html",
        >  "authenticationMethod": "route",
        >  "routes": [
        >   {
        >    "source": "^/be$",
        >    "destination": "simpleui_be",
        >    "authenticationType": "xsuaa"
        > 
        >   },
        >   {
        >    "source": "^/ui(/.*)",
        >    "target": "$1",
        >    "service": "html5-apps-repo-rt",
        >    "authenticationType": "xsuaa"
        >   }
        >  ]
        > }
        > ```


3.  Create an `mtad.yaml` file:

    -   Under `modules`, add your app.
    -   Add a dependency to the `html5-apps-repo` service and the `app-host` service instance.

    > ### Sample Code:  
    > ```
    > ID: html5.repo.deployer.myHTML5App
    > _schema-version: '2.0'
    > version: 0.0.3
    >  
    > modules:
    >  - name: myHTML5App_app-deployer
    >    type: com.sap.html5.application-content
    >    path: deployer/
    >    requires:
    >     - name: myHTML5App_app-host
    >  
    >  
    > resources:
    >  - name: myHTML5App_app-host            //Resource name
    >    type: org.cloudfoundry.managed-service
    >    parameters:
    >      service: html5-apps-repo            //Service name
    >      service-plan: app-host              //Service plan
    >      service-name: myHTML5App_app-host   //Service instance name
    > 
    > ```

    The `mtad.yaml` file acts as the deployment descriptor. For a general description of MTA descriptors, see [Multitarget Applications in the Cloud Foundry Environment](multitarget-applications-in-the-cloud-foundry-environment-d04fc0e.md).

4.  Create the `pom.xml` file for your project according to the multi-target application build \(MBT\) requirements.

5.  In the Cloud Foundry command line interface \(CLI\), navigate to your project root and enter the CLI command: `mvn clean install`.

    The `*.mtar` file is generated.

6.  Deploy the `*.mtar` file using the CLI command `cf deploy`.

    `cf deploy myHTML5App-deployer-assembly-0.0.1.mtar`

    The Cloud Foundry deploy plug-in uses the `mtad.yaml` file to configure the following:

    -   Create an HTML5 Application Repository service instance of the `app-host` service plan.

    -   Create an HTML5 application deployer application, which uses the HTML5 application deployer npm module.

    -   Bind the `app-host` service instance to the HTML5 application deployer application.

    -   Start the HTML5 application deployer application:

        -   Create a zip archive for each application in resources folder.

        -   Create a client credential token from the `app-host` service instance credentials.

        -   Deploy the content to the HTML5 application repository: passing on the zip archives and the client credential token.


    -   Stop the HTML5 application deployer application.



