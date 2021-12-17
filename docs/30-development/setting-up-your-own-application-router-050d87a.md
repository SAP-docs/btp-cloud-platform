<!-- loio050d87a61faa4fb88f687abd7bdf16ce -->

# Setting Up Your Own Application Router

This section describes how you can set up your own application router.



<a name="loio050d87a61faa4fb88f687abd7bdf16ce__prereq_mjz_tyl_pgb"/>

## Prerequisites

-   cf CLI is installed locally, see [Download and Install the Cloud Foundry Command Line Interface](../50-administration-and-ops/download-and-install-the-cloud-foundry-command-line-interface-4ef907a.md).

-   [Node.js](https://nodejs.org/) is installed and configured locally, see [npm documentation](https://docs.npmjs.com/misc/config).

-   The SAP npm registry, which contains the Node.js package for the application router, is configured:

    `npm config set @sap:registry https://registry.npmjs.org`




## Context

The application router is configured in the `xs-app.json` file. The `package.json` file contains the start command for the application router and a list of package dependencies.



<a name="loio050d87a61faa4fb88f687abd7bdf16ce__steps_xly_smq_xs"/>

## Procedure

1.  Create the application resource-file structure.

    For example, `/path/*<myAppName\>*/`

2.  Create a subfolder for the static Web resources module.

    The subfolder for the Web-resources module must be located in the application root folder, for example, `/path/*<myAppName\>*/web`.

    > ### Tip:  
    > The Web-resource module uses `@sap/approuter` as a dependency; the Web-resources module also contains the configuration and static resources for the application.

3.  Create the subfolder for the application's static resources.

    Static resources can, for example, include the following file and components: `index.html`, style sheets \(`.css` files\), images and icons. Typically, static resouces for a Web application are placed in a subfolder of the Web module, for example, `/path/*<myAppName\>*/web/resources`.

4.  Create the application-router configuration file.

    The application router configuration file `xs-app.json` must be located in the application's Web-resources folder, for example, `/path/*<MyAppName\>*/web`.

    > ### Sample Code:  
    > ```
    > *<myAppName\>*
    > |- web/                         # Application descriptors
    > **|  |- xs-app.json               \# Application routes configuration**
    > |  |- package.json              # Application router details/dependencies
    > |  \- resources/ 
    > 
    > ```

5.  Define details of the application's routes, destinations, and security scopes.

    The contents of the `xs-app.json` file must use the required JSON syntax. For more information, see [Routing Configuration File](routing-configuration-file-c103fb4.md).

    1.  Create the required destinations configuration.

        > ### Sample Code:  
        > `/path/*<myAppName\>*/web/xs-app.json`.
        > 
        > ```
        > { 
        > 	"welcomeFile": "index.html", 
        > 	"routes": [ 
        > 		{ 
        > 			"source": "/sap/ui5/1(.*)", 
        > 			"target": "$1", 
        > 			"localDir": "sapui5" 
        > 		}, 
        > 		{ 
        > 			"source": "/rest/addressbook/testdataDestructor", 
        > 			"destination": "backend", 
        > 			"scope": "node-hello-world.Delete" 
        > 		}, 
        > 		{ 
        > 			"source": "/rest/.*", 
        > 			"destination": "backend" 
        > 		}, 
        > 		{ 
        > 			"source": "^/(.*)", 
        > 			"localDir": "resources" 
        > 		} 
        > 	] 
        > } 
        > ```

    2.  Add the routes \(destinations\) for the specific application \(for example, `node-hello-world`\) to the `env` section of the application’s deployment manifest \(`manifest.yml`\).

        Every route configuration that forwards requests to a micro service has property destination. The destination is a name that refers to the same name in the destinations configuration. The destinations configuration is specified in an environment variable passed to the approuter application.

        > ### Sample Code:  
        > `*<myAppName\>*/manifest.yml`
        > 
        > ```
        > - name: node-hello-world
        > 	host: myHost-node-hello-world 
        > 	domain: xsapps.acme.ondemand.com 
        > 	memory: 100M 
        > 	path: web 
        > 	env: 
        > 	**    destinations: \> 
        > 		\[ 
        > 			\{ 
        > 				"name":"backend", 
        > 				"url":"http://myHost-node-hello-world-backend.xsapps.acme.ondemand.com", 
        > 				"forwardAuthToken": true 
        > 			\} **
        > 		] 
        > ```


6.  Add a package descriptor \(`package.json`\) for the application router to the root folder of your application's Web resources module \(`web/`\) and execute `npm install` to download the approuter npm module from the SAP npm registry.

    The package descriptor describes the prerequisites and dependencies that apply to the application router and starts the application router, too.

    > ### Sample Code:  
    > ```
    > *<myAppName\>*
    > |- web/                         # Application descriptors
    > |  |- xs-app.json               # Application routes configuration
    > **|  |- package.json              \# Application router details/dependencies**
    > |  \- resources/ 
    > 
    > ```

    The basic `package.json` file for your Web-resources module \(`web/`\) should look similar to the following example:

    > ### Sample Code:  
    > ```
    > {
    >   "name": "node-hello-world-approuter",  
    >   "dependencies": {
    >      "@sap/approuter": "5.1.0"
    >   },
    >   "scripts": {
    >      "start": "node node_modules/@sap/approuter/approuter.js"
    >   } 
    > } 
    > ```

    > ### Tip:  
    > The start script \(for example, `approuter.js`\) is mandatory; the start script is executed after application deployment.


**Related Information**  


[Managed Application Router](managed-application-router-589a239.md "")

