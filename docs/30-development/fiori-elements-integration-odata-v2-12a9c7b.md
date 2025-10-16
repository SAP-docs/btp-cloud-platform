<!-- loio12a9c7be19984e00bcca9c0129fffba9 -->

# Fiori Elements Integration OData V2

You can implement the reusable component from the Reuse Library in a Fiori Elements app in order to display change documents.



<a name="loio12a9c7be19984e00bcca9c0129fffba9__section_k52_kf5_lfc"/>

## Context

To be able to use the reusable components, you need to adapt the code that can be found in your manifest.json file.



<a name="loio12a9c7be19984e00bcca9c0129fffba9__section_z2m_mf5_lfc"/>

## Procedure

1.  Adapt your `<manifest.json>` file and add the `sap.nw.core.changedocs.lib.reuse` library under the sap.ui5 section:

    > ### Sample Code:  
    > ```
    > sap.ui5": {
    >     "dependencies": {
    >       "libs": {
    >         " sap.nw.core.changedocs.lib.reuse": {
    >         "lazy": true
    >         }
    >     },
    >       "components": {}
    >     }
    > 
    > ```

2.  Adapt your`<manifest.json>` file and add the component as section on your page:

    > ### Sample Code:  
    > ```
    > "pages": {
    >     "ObjectPage|TravelProcessor": {
    >         "entitySet": "TravelProcessor",
    >         "defaultLayoutTypeIfExternalNavigation": "MidColumnFullScreen",
    >         "component": {
    >             "name": "sap.suite.ui.generic.template.ObjectPage"
    >         },
    >         "embeddedComponents": {
    >             "changedoccomponent": {
    >                 "id": "changedoccomponent",
    >                 "componentUsage": "ChangedocReuseComponent",
    >                 "title": "{{reuseTitle}}",
    >                 "settings": {
    >                     "objectClass": [
    >                         "<MY_CHANGE_DOC>"
    >                                     ],
    >                     "objectId": "{parts: [{path: '<MY_OBJECTID>'}], formatter: 'sap.nw.core.changedocs.lib.reuse.changedocscomponent.arrayFormatter'}",
    >                     "startDate": "1900-01-01T00:00:00"
    >                 }
    >             }
    >         }
    >     }
    > }
    > 
    > ```

    > ### Note:  
    > Make sure to replace strings`<MY_CHANGE_DOC>` with your own change document object and `<MY_OBJECTID>` with your own Object id which were also used to create change documents.

3.  Adapt your `<i18n.properties>` file and add:

    > ### Sample Code:  
    > ```
    > …
    > #XTIT: Reuse component title
    > reuseTitle =Change Documents
    > …
    > 
    > ```

    > ### Note:  
    > Manual tests of the reuse library using **SAP Business Application Studio** is not possible. Create and test your app finally before implementing the reuse app. Test the reuse app after deployment.
    > 
    > After your app was deployed successfully to an SAP Business Technology Platform system, the updated BSP application and the SAP Fiori Launchpad app descriptor item will appear under your created package in Eclipse.

4.  Update your IAM App. For more information, see [Defining an IAM App for the Business Service](https://help.sap.com/docs/btp/sap-business-technology-platform-internal/defining-iam-app-for-business-service?locale=en-US&state=DRAFT&version=Internal).
5.  Once created, maintain the **Change Document OData Service**. Go to the **Service** tab and add the **Change Document Log OData Service** by naming the **OData V2** service type and add the following service name: `APS_CHANGE_DOCUMENTS_SRV 0001` 

    > ### Note:  
    > make sure to add all 11 spaces in between 'SRV' and '0001'

6.  Create a new Business Catalog. For more information, see [Creating a Business Catalog](https://help.sap.com/docs/btp/sap-business-technology-platform-internal/creating-business-catalog-d120838ba15c433ea6f15446dfe6ecf9?locale=en-US&state=DRAFT&version=Internal)

    Having created the business catalog, you have successfully implemented a reusable component to display your change documents.


