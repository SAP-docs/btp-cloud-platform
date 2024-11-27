<!-- loio936599fa36a643619fb577ff54cf9f78 -->

# Invalid "redirect\_uri"



## Symptom

After logging on, you are redirected to a *Where-To?*page with one of the following error messages:

-   The *redirect\_uri* is invalid
-   The *redirect\_uri* has an invalid domain
-   Invalid redirect: *\{URI\}* does not match one of the registered values
-   Client registration is missing *redirect\_uri*
-   Client registration contains *invalid redirect\_uri*



## Reason and Prerequisites

The `redirect_uris` configuration value for the used service instance has not been properly configured.



## Solution

1.  Identify the affected application. The affected application is the application on which you want to be redirected after the logon process.
2.  Identify the affected service instance of the *xsuaa* type.
    -   Cloud Cockpit: Find out which service instance of the *xsuaa* type was bound to the application.
    -   CF CLI: Check the environment of the application, and then find *xsuaa* to retrieve the name of the service instance: *cf env <application-name\>*

3.  Identify the *xsappname* of the service instance \(which is mandatory for *xs-security.json*\).
    -   Existing *xs-security.json*: You can find the *xsappname* of the *xs-security.json* file that was used to create the service instance.
    -   Cloud Cockpit: Create a service key and retrieve the *xsappname* from it; remove the section after the exclamation mark - for example, *myapp!b123 -\> xsappname: myapp*. For more information, see [SAP Note 3319310](https://me.sap.com/notes/3319310/E).
    -   CF CLI: Check the environment of the application \(see step 2\), retrieve the *xsappname* from the corresponding service, and then remove the section after the exclamation mark.

4.  Prepare the security descriptor \(*xs-security.json*\).
    -   For more information, see [Application Security Descriptor Configuration Syntax](https://help.sap.com/docs/btp/sap-business-technology-platform/application-security-descriptor-configuration-syntax?version=Cloud).

5.  Update the *redirect\_uris* attribute of the corresponding service instance \(within *oauth2-configuration*\).
    -   Cloud Cockpit: Click **Update** in the service, and then provide the *xs-security.json* file, as required.
    -   CF CLI: Use *cf update-service* to update the service instance and provide the required *xs-security.json* file: *cf update-service <instance-name\> -c <path-to-xs-security.json\>*


**Note**: It is important to provide the complete *xs-security.json* file during the update as partial updates are not supported.

