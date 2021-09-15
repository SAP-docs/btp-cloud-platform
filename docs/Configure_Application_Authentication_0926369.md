<!-- loio0926369928ce4e89ac22c847e4a51662 -->

# Configure Application Authentication

Use this procedure to configure the application with which you want to extend your SAP S/4HANA Cloud system.



<a name="loio0926369928ce4e89ac22c847e4a51662__prereq_yzf_wb1_mdb"/>

## Prerequisites

-   Have the Cloud Foundry command line interface \(cf CLI\) downloaded and installed. See [Download and Install the Cloud Foundry Command Line Interface](Download_and_Install_the_Cloud_Foundry_Command_Line_Interface_4ef907a.md).

-   Have Node.JS including its NPM Packager Manager installed. See [https://nodejs.org/en/](https://nodejs.org/en/).




<a name="loio0926369928ce4e89ac22c847e4a51662__context_z53_tvb_b2b"/>

## Context

You need your own application router that connects your extension application to the centrally provided user account and authentication \(UAA\) service. This means that you need to deploy an approuter as part of your application that manages the user authentication for you.

The approuter has these main functions:

-   Handles authentication for all apps of the application

-   Serves static resources

-   Performs route mapping \(URL mapping\)

-   In case of multitenancy, it derives the tenant information from the URL and provides it to the extended services for the Authorization and Trust Management service to redirect the authentication request to the tenant-specific identity provider. See [SAP Authorization and Trust Management Service in the Cloud Foundry Environment](SAP_Authorization_and_Trust_Management_Service_in_the_Cloud_Foundry_Environment_6373bb7.md).




<a name="loio0926369928ce4e89ac22c847e4a51662__steps_os3_tvb_b2b"/>

## Procedure

1.  To set up the application router as part of your application, execute the following command in cf CLI:

    ```
    npm config set @sap:registry=https://registry.npmjs.org
    ```

2.  Create a service instance of the Authorization and Trust Management service. See [Creating Service Instances](Creating_Service_Instances_8221b74.md).

3.  Add an application router. See [Application Router and Destination](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/3cc788ebc00e40a091505c6b3fa485e7.html)

4.  Update the extension application by using the `cf push` command in the cf CLI.

5.  Verify that there is an authentication for your application and access the application using the approuter URL.

    1.  Get the url of the approuter using the `cf apps` command.

    2.  Enter the approuter URL in a browser.

    3.  You are redirected to the Identity Authentication service that you have already configured. See [Configure Single Sign-On with the Identity Authentication Service](Configure_Single_Sign-On_with_the_Identity_Authentication_Service_8d3c376.md).

    4.  After a successful login, you will get redirected to the welcome page of you extension application if you have defined one.


