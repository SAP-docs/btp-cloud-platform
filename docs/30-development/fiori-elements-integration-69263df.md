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
    >             "logNumber": "<your content>",
    >             "logHandle": "{LogHandle}",
    >             "logFilterFieldName": "<your content>",
    >             "logFilterFieldValue": "<your content>",
    >             "persistencyKey": "<your content>",
    >             "showContextFields": false
    >         }
    >     }
    > }
    > ```

4.  You can set the following parameters:

    -   **log handle**: The application log handle

    -   **Optional logNumber**: The application log number. This is evaluated only if the logHandle is not provided.

        Please be aware that an additional backend roundtrip will be done in order to get the logHandle, which is the key in the OData Service of the application log. To avoid this additional roundtrip, we recommend using LogHandle. If you don't have the LogHandle, you can the use function module `BAL_DB_SEARCH` to retrieve it.

    -   **Optional persistencyKey**: Set a personalization key which is then used to set app-specific variants for `SmartFilterBar` or `SmartTable`. This parameter is optional. The default value is defined in the *Application Log* app.

        Make sure not to change the key value again, since users might lose their variants.


5.  You can set optional parameters to filter the data. These parameters can be combined with `LogHandle` or `LogNumber`:

    -   **logFilterFieldName**: The name of the field that is used to filter the data

    -   **logFilterFieldValue**: The value of the field that is used to filter the data


    > ### Note:  
    > Example
    > 
    > The application log for a purchase order can be filtered by a line item. In that case, a separate customer field has to be added to the log data, such as `LINE_ITEM`. After that, it's possible to navigate with `LogFilterFieldName=LINE_ITEM` and `LogFilterFieldValue=<line_item_xyz>`.

    -   The values must be added as a comma-separated list \(see the example\). Also, the values of the parameters `FilterFieldName` and `FilterFieldValue` must be in the same order.

    -   It's also possible to add two values to the same field name:

        -   `logFilterFieldName`: \[ "KEY,KEY" \]

        -   `logFilterFieldValue`: \[ "005056BA23B61EE5BC854FAE29111111,005056BA23B61EE5BC854FAE29122222" \]



    -   **Optional showContextFields**: By default, the dynamic context fields of a log are not visible in the reuse component. If this parameter is set to true, the context fields will also be displayed.


6.  Here are some examples for binding:

    -   `logHandle`: `{myOdataServiceLogHandle}`

    -   `logHandle`: `{path: 'myOdataServiceLogHandle'}`



