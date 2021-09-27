<!-- loio5af9067322214e8dbf354daae44cef08 -->

# Configure the approuter Application

To authenticate business users of the application at runtime, use the tenant-aware `approuter` application and SAP Authorization and Trust Management service \(technical name: `xsuaa`\) in SAP BTP.



## Context

You deploy the `approuter` application as a Cloud Foundry application and as a logical part of the multitenant application. Then you configure `approuter` application as an external access point of the application. You need to deploy a separate application router for each multitenant application.



### How does the application router and multitenancy work?

When a consumer accesses the application, their consumer tenant calls the multitenant application via the application router with their tenant-specific URL \(`cf` route\).

-   **During a development phase** of your multitenant application, the following URL structure applies:

    `*<SUBSCRIBER\_TENANT\_SUBDOMAIN\>*-*<APPROUTER\_APPLICATION\_HOST\>*.*<SAP-PROVIDED\_STANDARD\_DOMAIN\>*`

    In each development landscape, SAP provides a different standard domain you can use to create URLs.

    Using that domain, and following the specified URL structure, a created URL would be:

    `tenant1-myapprouter.cfapps.sap.hana.ondemand.com`

    Where: `tenant1-myapprouter` is the hostname, and `cfapps.sap.hana.ondemand.com` is the SAP-provided standard domain for this development landscape.

    In this format, create a new URL for each new tenant.

-   **During a production phase** of your multitenant application, apply for a custom domain via the custom domain service, then create a URL using the following structure:

    `*.*<YOUR\_CUSTOM\_DOMAIN\>*`.

    Where: `*` is the wildcard hostname.

    In this format, since the wildcard is replaced by an actual tenant during runtime, there is no need to create a new URL for each new tenant.

    For more information, see [Using Custom Domains](../50-administration-and-ops/Using_Custom_Domains_2291aea.md)


In both cases, the application router then derives the tenant from the URL and calls the tenant-aware `xsuaa` \(containing the user account and authentication service\), which is responsible for the authentication of the business user. The `xsuaa` reads the tenant and gets the customer-specific identity provider \(IdP\) from the tenant-specific identity zone. Then, the `xsuaa` delegates the authentication to the configured IdP, and creates a JSON Web Token \(JWT\) that contains the tenant, the current user, and the authorization scopes of the user. The JWT is then sent back to the application router, and from there to the application.

To read and store tenant-specific data, the multitenant application needs to know the tenant ID. To read the tenant ID, use the Container Security API to enable the multitenant application to read the tenant, user, and scopes from the given JWT. The API also validates whether the JWT is valid. The tenant information is contained in the `identityZone` user attribute.

> ### Sample Code:  
> Java code for retrieving the identity zone
> 
> ```
> UserInfo userInfo = SecurityContext.getUserInfo(); 
> String identityZone = userInfo.getIdentityZone();
> 
> ```

For more information, see:

-   [Web Access Control](../60-security/Web_Access_Control_70a62d1.md)

-   [What Is the SAP Authorization and Trust Management Service?](../60-security/What_Is_the_SAP_Authorization_and_Trust_Management_Service_649961f.md)




## Procedure

1.  Create the application structure of the application router and configure it accordingly.

    For general instructions, see [Application Router](Application_Router_01c5f9b.md).

2.  Configure the application router with the destination of your multitenant application.

    If you are defining the destination as an environment variable for the `approuter` application, set the router information in the `env: destinations` section of the `manifest.yml`.

    -   `url`: Specify the URL of the multitenant application.

    -   `forwardAuthToken`: Set to `true`

    > ### Sample Code:  
    > manifest.yml for a development phase:
    > 
    > ```nocode
    > ---
    > applications:
    > 
    > - name: approuter-saas-app
    >   host: approuter_saas_app
    >   path: approuter
    >   buildpack: nodejs_buildpack
    >   memory: 256M
    >   env:
    >     TENANT_HOST_PATTERN: "^(.*)-cfapps.eu10.hana.ondemand.com 
    >     destinations: >
    >       [
    >         {"name":"saas-application",
    >          "url":"https://backend-saas-app.cfapps.sap.hana.ondemand.com",
    >          "forwardAuthToken": true}
    >       ]
    > 
    > ```

    > ### Sample Code:  
    > manifest.yml for a production phase:
    > 
    > ```nocode
    > ---
    > applications:
    > 
    > - name: approuter-saas-app
    >   host: approuter_saas_app
    >   path: approuter
    >   buildpack: nodejs_buildpack
    >   memory: 256M
    >   env:
    >     TENANT_HOST_PATTERN: "^(.*).mydomain.com
    >     destinations: >
    >       [
    >         {"name":"saas-application",
    >          "url":"https:// backend-saas-app.mydomain.com",
    >          "forwardAuthToken": true}
    >       ]
    > 
    > ```

    For more information, see [Application Routes and Destinations](Application_Routes_and_Destinations_3cc788e.md).

3.  Configure the routes in the application router security descriptor file \(`xs-app.json`\) so that application requests are forwarded to the multitenant application destination.

    > ### Sample Code:  
    > xs-app.json:
    > 
    > ```
    > {
    >   "routes": [{
    >     "source": "/",
    >     "target": "/",
    >     "destination": "saas-application"
    >   }]
    > }
    > ```

    For more information, see [Routing Configuration File](Routing_Configuration_File_c103fb4.md).

4.  Use the `push` command in the cf CLI to deploy the `approuter` application to the Cloud Foundry space where your multitenant is deployed.


