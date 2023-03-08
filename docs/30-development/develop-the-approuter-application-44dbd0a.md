<!-- loio44dbd0ae4d4b4d9c9c8371d711c22bfe -->

# Develop the Approuter Application

To authenticate business users of the application at runtime, use the tenant-aware approuter application and the xsuaa service in SAP Business Technology Platform. This will also provide the necessary callbacks for the SaaS Provisioning Service. For more details on the application router, see [Application Router](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/01c5f9ba7d6847aaaf069d153b981b51.html).

In addition, we provide the middleware `@sap/asp-middleware` component \(see [here\)](https://www.npmjs.com/package/@sap/asp-middleware) as a library \(npm module\) that enhances the approuter to also take care of automatically routing the consumer to their ABAP tenant.



<a name="loio44dbd0ae4d4b4d9c9c8371d711c22bfe__section_i3p_x1t_fnb"/>

## Prerequisites

-   Please ensure that you have [Node.js](https://nodejs.org/en/) \(LTS version\) and npm installed.




<a name="loio44dbd0ae4d4b4d9c9c8371d711c22bfe__section_m5r_1bt_fnb"/>

## Process Steps

1.  Create an initial Node.js project for the router:

    1.  Create a new folder called “router” and open a commant prompt \(terminal/cmd\) in this folder.
    2.  Create a new project by executing `npm init`. In the upcoming wizard flow you can leave the defaults or define you own values if preferred.

    Result: After the project is initialized, the following two files are created in your “router” folder:

    -   package.json
    -   package-lock.json

    The package.json should look as follows \(if the defaults are kept\):

    ```json
    {
      "name": "router",
      "version": "1.0.0",
      "description": "",
      "main": "index.js",
      "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
      },
      "author": "",
      "license": "ISC"
    }
    
    ```

2.  Install the necessary dependencies.

    The `@sap/approuter` and the `@sap/asp-middleware` must be installed so that they can be used in the start script. Supported `@sap/approuter` versions: ^8.0.0.

    1.  Execute `npm install @sap/approuter @sap/asp-middleware` in the command prompt to install `@sap/approuter` and `@sap/asp-middleware`.

    Result: The two modules will be listed in the package.json as “dependencies” and are downloaded into the node\_modules folder. Excerpt from `package.json` \(versions might differ\):

    ```json
    "dependencies": {
        "@sap/approuter": "^8.5.2",
        "@sap/asp-middleware": "^1.0.1"
      }
    
    ```

3.  Add a start script.

    A start script needs to be added to prepare the application for execution in the Cloud Foundry Environment. To do this, make sure the scripts section of the package.json looks as follows:

    ```json
    "scripts": {
       "start": "node index.js"
    },
    
    ```

4.  Create the start script \(index.js\).

    Create the file index.js. The JavaScript code for the application must be written here. The minimum code required is the following:

    ```js
    const approuter = require('@sap/approuter');
    const ar = approuter();
    
    ar.start({
      extensions: [ require('@sap/asp-middleware') ]
    });
    
    ```

    It will load the approuter and the asp-middleware and ensures that both components are wired. Additionally, the approuter is started.

5.  Configure the routes \(xs-app.json\).

    To make sure that the approuter routes all relevant requests to the ABAP Solution, a routing configuration file needs to be created and configured: Create a file named `xs-app.json` next to the `index.js` file. It should have the following content:

    ```json
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
    			"csrfProtection": false,
    			"endpoint": "abap"
    		},
    		{
    			"source": "^/ui(.*)$",
    			"target": "/ui$1",
    			"authenticationType": "xsuaa",
    			"service": "com.sap.cloud.abap.solution",
    			"csrfProtection": false,
    			"endpoint": "abap"
    		}
    	]
    }
    ```

    For more details on the parameters of this file, see [Routing Configuration File](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/c103fb414988447ead2023f768096dcc.html).

6.  Test it.

    To test that everything works, execute `npm start` in your command prompt. As a result, you should see the following error message: “*Error: No ABAP Solution credentials found in environment*”. This tells us that the middleware was loaded as a dependency and that the start command is correct.


