<!-- loio9c930d50f09e45f8b7f516bde4a8e96d -->

# Application Job Templates



You can use this app to create your own application job templates. The application job templates consist of a set of parameters that you can set for the assigned job catalog entry. This app is mandatory to create multi-step templates which can then be submitted via the *Application Jobs* app. A multi-step template consists of several other templates that run in a series, one after the other. Each step could be a single-step template, or another multi-step template that was created with the *Application Job Templates* app before.



## Key Features

You can use this app to:

-   Create and customize a job template

-   Create multi-step templates
-   Change the template parameters
-   Transport job templates, if supported: For more information, see [2999966](https://me.sap.com/notes/2999966)
-   Display a list of templates you have read access to
-   Display the layer code of the template:
    -   *Global:* a template with this layer code is predelivered by SAP and therefore can't be edited or deleted

    -   *Private:* a template with this layer code is visible for all users within the *Application Job Templates* and the *Application Jobs* apps, but only the author can edit or delete the template

        > ### Note:  
        > With the new restriction type, you can define a full authorization for job templates, such that a system administrator can display, change or delete private templates of other users

    -   *Shared:* a template with this layer code is visible to all users that have the required authorizations to use the *Application Job Templates* and the *Application Jobs* apps

    -   *Reference:* a template with this layer code is visible for all users within the *Application Job Templates* and the *Application Jobs* apps, but only the author can edit or delete the template. It can't be scheduled in the *Application Jobs* app. It can be used as a copy pattern to create other templates.



-   Delete a job template



<a name="loio9c930d50f09e45f8b7f516bde4a8e96d__supported_devices"/>

## Supported Device Types

-   Desktop

-   Tablet




<a name="loio9c930d50f09e45f8b7f516bde4a8e96d__customer_component"/>

## Component for Customer Incidents

If you need support or experience issues, please report an incident under component `BC-SRV-APS-APJ`.

**Related Information**  


[Creating an Application Job Template](creating-an-application-job-template-f5e8d24.md "Find out how to create your own application job templates in the Application Job Templates app.")

