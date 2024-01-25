<!-- loio488c7755572842a4bcdf40b240e73b3d -->

# Configure Application Authentication



<a name="loio488c7755572842a4bcdf40b240e73b3d__prereq_yzf_wb1_mdb"/>

## Prerequisites

-   Have the Cloud Foundry command line interface \(cf CLI\) downloaded and installed. See [Download and Install the Cloud Foundry Command Line Interface](../50-administration-and-ops/download-and-install-the-cloud-foundry-command-line-interface-4ef907a.md).

-   Have Node.JS including its NPM Packager Manager installed. See [https://nodejs.org/en/](https://nodejs.org/en/).




<a name="loio488c7755572842a4bcdf40b240e73b3d__context_z53_tvb_b2b"/>

## Context

You need your own application router that connects your extension application to the centrally provided user account and authentication \(UAA\) service. This means that you need to deploy an approuter as part of your application that manages the user authentication for you.

The approuter has these main functions:

-   Handles authentication for all apps of the application

-   Serves static resources

-   Performs route mapping \(URL mapping\)

-   In case of multitenancy, it derives the tenant information from the URL and provides it to the extended services for the Authorization and Trust Management service to redirect the authentication request to the tenant-specific identity provider. See [SAP Authorization and Trust Management Service](../60-security/sap-authorization-and-trust-management-service-6373bb7.md).




<a name="loio488c7755572842a4bcdf40b240e73b3d__steps_os3_tvb_b2b"/>

## Procedure

1.  To set up the application router as part of your application, execute the following command in cf CLI:

    ```
    npm config set @sap:registry=https://registry.npmjs.org
    ```

2.  Create a service instance of the Authorization and Trust Management service. See [Creating Service Instances](../30-development/creating-service-instances-8221b74.md).

3.  Add an application router. See [Application Router and Destination](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/3cc788ebc00e40a091505c6b3fa485e7.html)

4.  Update the extension application by using the `cf push` command in the cf CLI.

5.  Verify that there is an authentication for your application and access the application using the approuter URL.

    1.  Get the url of the approuter using the `cf apps` command.

    2.  Enter the approuter URL in a browser.

    3.  You are redirected to the Identity Authentication service that you have already configured. See [Setting Up Trust Between Identity Authentication and SAP Cloud for Customer](setting-up-trust-between-identity-authentication-and-sap-cloud-for-customer-2903a3c.md).

    4.  After a successful login, you will get redirected to the welcome page of you extension application if you have defined one.



