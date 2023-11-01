<!-- loio69263dfde8814ed19646a68675bb5143 -->

# Fiori Elements Integration

You can implement the reusable component from the *Reuse Library* in a `Fiori Elements` app in order to display an application log.



## Context

In order to implement the reusable component in a Fiori Elements app, you first have to add the application log reuse component to your manifest.



## Procedure

1.  Open the `manifest.json` file of the application and locate the `sap.ui5` section.

2.  Add the `sap.nw.core.applogs.lib.reuse.smarttemplate` component:

    > ### Sample Code:  
    > ```
    > "sap.ui5": {
    >     "dependencies": {
    >       "libs": {
    >         "sap.nw.core.applogs.lib.reuse": {
    >         "lazy": true
    >         }
    >     },
    >       "components": {}
    >     },
    >     "componentUsages": {
    >         "ApplicationLogs": {
    >             "name": "sap.nw.core.applogs.lib.reuse.smarttemplate",
    >             "lazy": true
    >             }
    >         }
    > ```

3.  Next, you need to add the smarttemplate component of the application log reuse library to an `ObjectPage`. In the `manifest.json` file, you have to add the application log reuse component as an embedded component to your `ObjectPage`:

    > ### Sample Code:  
    > Snippet \(embeddedComponents\)
    > 
    > ```
    > "embeddedComponents": {
    >     "appLog": {
    >         "id": "<enter an ID>",
    >         "componentUsage": "ApplicationLogs",
    >         "title": "<the name of the tab>",
    >         "settings": {
    >             "logHandle": "{LogHandle}",
    >             "persistencyKey": "<your content>"
    >         }
    >     }
    > }
    > ```

4.  You can set the following parameters:

    -   **log handle**: The application log handle

    -   **Optional persistencyKey**: Set a personalization key which is then used to set app-specific variants for `SmartTable`. This parameter is optional. The default value is defined in the *Application Log* app.

        Make sure not to change the key value again, since users might lose their variants.


5.  Here are some examples for binding:

    -   `logHandle`: `{myOdataServiceLogHandle}`

    -   `logHandle`: `{path: 'myOdataServiceLogHandle'}`


    After your app was deployed successfully to an SAP BTP, ABAP environment system, the *BSP application* and the *SAP Fiori Launchpad* app descriptor item will appear under your created package in Eclipse.

    ![](images/Eclipse_ABAP_Environment_e0a96c5.png)

6.  Now, you need to create a new *IAM App*. Follow the instructions described here: [Defining an IAM App for the Business Service](defining-an-iam-app-for-the-business-service-3fb85a8.md).

7.  Once created, you need to maintain the *Application Log* OData Service to call your application log data. To do this, go to the *Service* tab and add the *Application Log OData Service* by naming the service type `OData V2` and add the following service name: `APL_LOG_MANAGEMENT_SRV 0001`. Please make sure to add all 13 spaces in between `SRV` and `0001`. Now, go to the *Authorization* tab and maintain your *log objects / sub objects* for the authorization object `S_APPL_LOG`.

8.  Finally, you need to create a new *Business Catalog*. Please follow the procedure described here: [Creating a Business Catalog](creating-a-business-catalog-d120838.md) 

    Having created the business catalog, you have successfully implemented a reusable component to display your application logs.


