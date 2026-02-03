<!-- loio08b3a2fdda8148768fbf1311ab7d0764 -->

# Fiori Elements Integration OData V4

You can implement the reusable component from the *Reuse Library* in a `Fiori Elements` app in order to display an application log.



## Context

To implement the reusable component in a Fiori Elements app, you first have to add the application log reuse component to your manifest.



## Procedure

1.  Open the `manifest.json` file of the application and locate the `sap.ui5` section.

2.  Add the `sap.nw.core.applogs.lib.reuse` library under dependencies:

    > ### Sample Code:  
    > ```
    > "sap.ui5": {
    >     "dependencies": {
    >       "libs": {
    >         "sap.nw.core.applogs.lib.reuse": {
    >         "lazy": true
    >         }
    >     }
    >   }
    > }
    > ```

3.  Next, you need to add a reuse component as embedded component to your manifest. Each reuse component instance is defined for an object page belonging to an app based on SAP Fiori elements. The reuse component is realized by a section that contains a custom subsection, which in turn contains the content of the reuse component. These sections, like any other custom sections, can be placed as described here: [Extension Points for Sections on the Object Page](https://sapui5.hana.ondemand.com/#/topic/92ad9968e41748aeb74971f7a08a91c8).

4.  Open the `manifest.json` file of the application and locate the object page within your `targets` section.

    > ### Sample Code:  
    > ```
    > "ZTS_APL_C_APPL_LOG_OVERVIEWObjectPage": {
    >   "type": "Component",
    >   "id": "ZTS_APL_C_APPL_LOG_OVERVIEWObjectPage",
    >   "name": "sap.fe.templates.ObjectPage",
    >   "options": {
    >     "settings": {
    >       "editableHeaderContent": false,
    >       "contextPath": "/ZTS_APL_C_APPL_LOG_OVERVIEW",
    >       "content": {
    >         "body": {
    >             "sections": {
    >                 "customSectionReuse": {
    >                     "title": "Log Reuse Component",
    >                     "embeddedComponent": {
    >                         "name": "sap.nw.core.applogs.lib.reuse.applogs",
    >                         "settings": {
    >                             "logHandle": "{log_handle}",
    >                             "tableType": "ResponsiveTable"
    >                           }
    >                     },
    >                     "position": {
    >                         "placement": "After",
    >                         "anchor": "someOtherSection"                                           
    >                       }
    >                 }
    >             }
    >         }
    >     }
    >     }
    >   }
    > }
    > ```

5.  **Settings**:

    -   **persistencyKey**: The component you embed uses the *SmartFilter* and *SmartTable* control. Both controls allow you to configure them interactively. You can also store a current set of configuration settings as a named variant. By providing a value for the `persistencyKey` parameter, you make sure that the variants that get created in your application become visible only to the users of your application, and not to all users of the component in all applications.
    -   **showHeader**: Display or hide the header with information about the log object, the log subobject, the creator, and the creation date.
    -   **showFilterBar**: Display or hide the *SmartFilter* bar.
    -   **tableType**: Specifies the type of table that you can create in the *SmartTable* control. Possible values are: `Table` \(default\), which shows a grid table, and `ResponsiveTable`, which shows a responsive table. If you use the `tableType` setting within an object page, it's recommended to use the `ResponsiveTable` value. This value doesn't work in combination with the tree view.
    -   **showAsTree**: Display log messages as a tree. Make sure the *Level of Detail* is maintained for all log messages. The table supports up to 9 expandable levels.
    -   **detailLevel**: Filter out less relevant log messages. If set, only log messages of the log levels you've specified are displayed. An example: if you've specified the `detailLevel: "1,2,3"`, then only log messages with detail level 1, 2, or 3 are displayed.
    -   **showContextFields**: By default, the dynamic context fields of a log are not visible in the reuse component. If this parameter is set to `true`, the context fields will also be displayed. Be aware, however, that an additional second round trip is needed to fetch the metadata of the context fields.
    -   **sortOrder**: Possible values of the sort order are: *ASC* \(Ascending. The oldest log is shown first. This is the default\) and *DESC* \(Descending. The newest log is shown first\)
    -   **tableTitle**: Set the table title. The default title is *Log Details*.

6.  Now, you need to create a new *IAM App*. Follow the instructions described here: [Defining an IAM App for the Business Service](defining-an-iam-app-for-the-business-service-3fb85a8.md).

7.  Once created, you need to maintain the *Application Log* OData Service to call your application log data. To do this, go to the *Service* tab and add the *Application Log OData Service* by naming the service type `OData V2` and add the following service name: `APL_LOG_MANAGEMENT_SRV 0001`. Please make sure to add all 13 spaces in between `SRV` and `0001`. Now, go to the *Authorization* tab and maintain your *log objects / sub objects* for the authorization object `S_APPL_LOG`.

8.  Finally, you need to create a new *Business Catalog*. Please follow the procedure described here: [Creating a Business Catalog](creating-a-business-catalog-d120838.md) 

    Having created the business catalog, you have successfully implemented a reusable component to display your application logs.


