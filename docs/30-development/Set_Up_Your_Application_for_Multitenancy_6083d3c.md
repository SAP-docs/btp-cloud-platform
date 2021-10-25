<!-- loio6083d3cf8f354415be4f5d0f2364fbdf -->

# Set Up Your Application for Multitenancy

Learn how to add multitenancy to your application and make it available for other subaccounts using the SaaS Provisioning service and the SAP Authorization and Trust Management service.



## Context

You’ve created an application in your subaccount that is secured by the SAP Authorization and Trust Management service. You now want to make that application available to other subaccounts \(tenants\). You’ll use the SaaS Provisioning service to make your application available to a consumer subaccount within your global trial account.

You declare your application security descriptor with JSON syntax and store it in a flat file on the filesystem. The standard name for this file is `xs-security.json`.



## Procedure

1.  Enable multitenancy in the application security descriptor file.

    1.  Go to the folder where the `xs-security.json` file is stored.

    2.  Change the value of the `tenant-mode` parameter to `shared`.

    3.  Under the `scopes` element, add access to the SaaS Provisioning service to call the product list callback API directly. You’ll implement the callbacks in Step 3.

        > ### Sample Code:  
        > ```
        > "scopes": [
        >                 {
        >                    "name": "$XSAPPNAME.read",
        >                    "description": "With this scope, USER can read products."
        >           },
        >           {
        >               "name": "$XSAPPNAME.Callback",
        >               "description": "With this scope set, the callbacks for tenant onboarding, offboarding and getDependencies can be called.",
        >               "grant-as-authority-to-apps": [
        >                   "$XSAPPNAME(application,sap-provisioning,tenant-onboarding)"
        >               ]
        >           }
        >        ],
        > ```

    4.  Save the file.


2.  Update the manifest.

    In this step, you need to complete the following tasks:

    -   Add a new routing pattern.

    -   Add the service binding for the SaaS Provisioning service.


    1.  Go to your application folder and open the `manifest.yml` file.

    2.  For the application router, add the `TENANT_HOST_PATTERN` parameter under the `env` parameter.

        This parameter specifies a generic route for all tenants to call the application over the approuter.

        > ### Sample Code:  
        > ```
        > env:
        >   destinations: >
        >     [
        >       {"name":"hw-dest",
        >        "url":"https://product-list-ap25.cfapps.eu10.hana.ondemand.com",
        >        "forwardAuthToken": true}
        >     ]
        >   TENANT_HOST_PATTERN: "^(.*)-approuter-product-list-ap25.cfapps.eu10.hana.ondemand.com"
        > ```

        > ### Restriction:  
        > The value of the `TENANT_HOST_PATTERN` parameter must be in lowercase.

    3.  Add the service binding for the SaaS Provisioning service to your application.

        Adding the service binding of the SaaS Provisioning service in the `manifest.yml` file will automatically bind the service instance to your application, when deploying it.

        > ### Sample Code:  
        > ```
        > services:
        >   - xsuaa-service-tutorial
        >   - saas-registry-tutorial
        > ```


3.  Implement the subscribe/unsubscribe endpoints.

    To enable other subaccounts to subscribe to your application, you need to implement an endpoint for the SaaS registration manager to subscribe/unsubscribe.

    1.  Go to the `myapp` folder and open the `index.js` file.

    2.  Add the following lines of code after the `checkReadScope` function. \(Replace the `ap25` string with the string that you used when deploying your application security model. Adapt the region code if your trial isn’t in the eu10 region.\)

        > ### Sample Code:  
        > ```
        >   app.put('/callback/v1.0/tenants/*', function (req, res) {
        >       var consumerSubdomain = req.body.subscribedSubdomain;
        >       var tenantAppURL = "https:\/\/" + consumerSubdomain + "-approuter-product-list-ap25." + "cfapps.eu10.hana.ondemand.com/products";
        >       res.status(200).send(tenantAppURL);
        >     });
        > 
        >   app.delete('/callback/v1.0/tenants/*', function (req, res) {
        >       var consumerSubdomain = req.body.subscribedSubdomain;
        >       var tenantAppURL = "https:\/\/" + consumerSubdomain + "-approuter-product-list-ap25." + "cfapps.eu10.hana.ondemand.com/products";
        >       res.status(200).send(tenantAppURL);
        >   });
        > ```

    3.  To be able to read the body of those calls, add the body parser module at line 9 of the `index.js` file.

        > ### Sample Code:  
        > ```
        > const bodyParser = require('body-parser')
        > app.use(bodyParser.json())
        > ```

    4.  Add the body parser module as a dependency to the `product list/myapp/package.json` file.

        > ### Sample Code:  
        > ```
        > "dependencies": {
        >   "express": "^4.17.1",
        >   "@sap/xsenv": "^2.2.0",
        >   "@sap/xssec": "^3.0.0",
        >   "passport": "^0.4.1",
        >   "body-parser": "^1.19.0"   
        > }
        > ```


4.  Create a SaaS configuration file.

    To make your multitenant application endpoints available for subscription to consumer subaccounts, you need to register the application in the Cloud Foundry environment by using the SaaS Provisioning service.

    To register your application, you need a configuration file called `config.json`. In this file, you specify the subscription URL, the name, and description of your application. The `xsappname` must be the same as the `xsappname` in the `xs-security.json` file.

    1.  Go to your application folder and create the `config.json` file.

    2.  Insert the following lines.

        > ### Sample Code:  
        > ```
        > {
        >   "xsappname":"product-list",
        >   "appUrls": {
        >     "onSubscription" : "https://product-list-ap25.cfapps.eu10.hana.ondemand.com/callback/v1.0/tenants/{tenantId}"
        >   },
        >   "displayName" : "Product List MTA",
        >   "description" : "Product list MTA sample application",
        >   "category" : "Custom SaaS Applications"
        > }
        > ```


5.  Delete the old service instance of the SAP Authorization and Trust Management service.

    When you change the tenant mode from `dedicated` to `shared` like you did in step 1, it’s not enough to update the service instance. You have to first unbind and delete the old service instance, to be able to later recreate it with the updated tenant mode settings.

    1.  Unbind the existing service instance from your application.

        ```nocode
        cf unbind-service <APP_NAME> <SERVICE_INSTANCE>
        ```

        > ### Sample Code:  
        > ```nocode
        > cf unbind-service product-list xsuaa-service-tutorial
        > ```

    2.  Unbind the existing service instance from the application router.

        ```nocode
        cf unbind-service <APP_NAME> <SERVICE_INSTANCE>
        ```

        > ### Sample Code:  
        > ```nocode
        > cf unbind-service approuter xsuaa-service-tutorial
        > ```

    3.  Delete the existing service instance.

        ```nocode
        cf delete-service <SERVICE_INSTANCE>
        ```

        > ### Sample Code:  
        > ```nocode
        > cf delete-service xsuaa-service-tutorial
        > ```


6.  Create service instances and redeploy your application.

    1.  Log in to your Cloud Foundry account with the Cloud Foundry CLI.

    2.  Go to your application folder and create the service instance with the `xs-security.json` security descriptor file.

        ```nocode
        cf create-service <SERVICE> <PLAN> <SERVICE_INSTANCE> -c xs-security.json
        ```

        > ### Sample Code:  
        > ```nocode
        > cf create-service xsuaa application xsuaa-service-tutorial -c xs-security.json
        > ```

    3.  Create the SaaS Provisioning service instance with the `config.json` file.

        > ### Sample Code:  
        > ```nocode
        > cf create-service <SERVICE> <PLAN> <SERVICE_INSTANCE> -c config.json
        > ```
        > 
        > ```nocode
        > cf create-service saas-registry application saas-registry-tutorial -c config.json
        > ```

    4.  Redeploy the application with the updated `manifest.yml` file.

        > ### Sample Code:  
        > ```nocode
        > cf push
        > ```


7.  Create a route for a consumer subaccount.

    Make your application reachable for consumer subaccounts by adding a new route in the Cloud Foundry CLI. The route is composed of the subdomain of the subscribing subaccount and the `TENANT_HOST_PATTERN` of the application router that you defined in the `manifest.yml` file. You have to create a new route for every subaccount \(tenant\) that subscribes to the application.

    1.  Log in to the Cloud Foundry account where the application is deployed with the Cloud Foundry CLI.

    2.  Create a route for the consumer subaccount.

        ```nocode
        cf map-route <APP_NAME> <DOMAIN> --hostname <APPLICATION_HOSTNAME>
        ```

        > ### Note:  
        > The `APPLICATION_HOSTNAME` is the combined string of the subdomain ID of the consumer subaccount and the `TENANT_HOST_PATTERN` from the `manifest.yml` file.

        > ### Sample Code:  
        > ```nocode
        > cf map-route approuter cfapps.eu10.hana.ondemand.com --hostname consumer-tenant-ap25-approuter-product-list-ap25
        > ```


8.  Access the application with the consumer subaccount.

    To access the application you need to subscribe to it. Follow these steps to subscribe to the SaaS application with the consumer subaccount and call the application URL.

    1.  Open the SAP BTP trial.

    2.  Navigate to your consumer subaccount.

    3.  Choose *Subscriptions*.

    4.  Choose *Product List MTA*.

    5.  Choose *Subscribe*.

    6.  Choose *Go to Application*.


    You’ll now see the application with the message `no data` because you have to assign the role collection to your user in the consumer subaccount.

9.  Assign the role collection.

    Assign the `ProductListViewer` role collection to your user. This role collection contains the necessary role to view the products in your application.

    1.  Open the SAP BTP cockpit.

    2.  Navigate to your consumer subaccount.

    3.  Choose *Security* \> *Role Collections*.

    4.  Choose the `ProductListViewer` role collection.

    5.  Use the chevron at the right side to expand the role collection.

    6.  Go to the *Users* section and choose *Edit*.

    7.  Enter the e-mail address of the user that you want to assign to the role collection. Take care that your user's identity provider is SAP ID service.

    8.  Save your changes.

    9.  Clear your cache and reload the application URL.

        > ### Sample Code:  
        > ```
        > https://consumer-tenant-ap25-approuter-product-list-ap25.cfapps.eu10.hana.ondemand.com/products
        > ```


    The application will now show you the products.


**Related Information**  


[Add Multitenancy to a Node.js Application Secured by the SAP Authorization and Trust Management service](https://developers.sap.com/tutorials/cp-cf-security-xsuaa-multi-tenant.html)

