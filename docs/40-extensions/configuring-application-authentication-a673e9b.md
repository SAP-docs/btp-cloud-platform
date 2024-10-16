<!-- loioa673e9be155841c7a3c51b9d93e3e546 -->

# Configuring Application Authentication

Use this procedure to configure the authentication of the applications with which you want to extend your SAP SuccessFactors systems.



<a name="loioa673e9be155841c7a3c51b9d93e3e546__prereq_yzf_wb1_mdb"/>

## Prerequisites

You have the Cloud Foundry command line interface \(cf CLI\) downloaded and installed. See [Download and Install the Cloud Foundry Command Line Interface](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/afc3f643ec6942a283daad6cdf1b4936.html).



## Context

You need your own application router that connects your extension application to the centrally provided user account and authentication \(UAA\) service. This means that you need to create an application with an application router and configure it to route the requests to your extension application. Thus, the application router manages the user authentication for you.

> ### Note:  
> For Node.js extension applications, you can optionally deploy the application router as part of your extension application.



## Procedure

1.  Create an xsuaa service instance. See [Create a Service Instance from the xsuaa Service](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/7c64eb65a2ea42db93ff0ae722176b09.html).

2.  Bind the xsuaa service instance you have created to the extension application. See: [Bind the xsuaa Service Instance to the Application](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/d207931556134f08af388bbb2929de9b.html).

3.  Create an application with an application router and configure it to forward the requests to your extension application. See [Configure Application Router](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/01c5f9ba7d6847aaaf069d153b981b51.html).

4.  Verify that there is an authentication for your extension application and access the application using the application router URL.

    1.  Get the URL of the application router using the `cf apps` command.

    2.  Enter the application router URL in a browser.

    3.  You are redirected to the SAP SuccessFactors identity provider that you have already configured. See [Configure SAP SuccessFactors as a Trusted Identity Provider in SAP BTP](configure-sap-successfactors-as-a-trusted-identity-provider-in-sap-btp-80a3fd1.md).

    4.  After a successful login, you will get redirected to the welcome page of you extension application if you have defined one.



**Related Information**  


[Establish Trust and Federation with UAA Using Any SAML Identity Provider](../50-administration-and-ops/establish-trust-and-federation-with-uaa-using-any-saml-identity-provider-2ce3938.md#loio2ce3938c66d94479848bff3090999027 "Integrate trust between the SAP BTP subaccount and any SAML 2.0 identity provider.")

[Authentication for Applications](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/09f5bd3f346b4ee08b5ca084128e2e81.html)

