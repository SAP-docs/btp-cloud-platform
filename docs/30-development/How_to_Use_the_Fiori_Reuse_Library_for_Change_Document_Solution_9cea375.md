<!-- loio9cea375b32884a4aad561eebd9f2484d -->

# How to Use the Fiori Reuse Library for Change Document Solution

You can use the *Reuse Library* to implement a reusable component that can display change documents.



## Context

To be able to use the reusable components, you need to adapt the code that can be found in your `manifest.json` file.



## Procedure

1.  Adapt your `<manifest.json>` file and add the `sap.nw.core.changedocs.lib.reuse` library under the `sap.ui5` section:

    > ### Sample Code:  
    > ```lang-abap
    > `
    > "sap.ui5": {
    >         "resources": {
    >             "js": [],
    >             "css": []
    >         },
    >         **"componentUsages": \{
    >             "ChangedocReuseComponent": \{
    >                 "name": "sap.nw.core.changedocs.lib.reuse.changedocscomponent"**
    >             }
    >         },
    >         "dependencies": {
    >             "minUI5Version": "1.65.0",
    >             "libs": {
    >                 "sap.ui.core": {
    >                     "lazy": false
    >                 },
    >                 "sap.ui.generic.app": {
    >                     "lazy": false
    >                 },
    >                 "sap.suite.ui.generic.template": {
    >                     "lazy": false
    >                 },
    >                 "sap.ui.comp": {
    >                     "lazy": false
    >                 }
    >             },
    >             **"components": \{
    >                 "sap.nw.core.changedocs.lib.reuse": \{
    >                     "lazy": true
    > **
    >                 }
    >             }
    >         },
    > `
    > ```

2.  Adapt your `<manifest.json>` file and add the component as section on your page:

    > ### Sample Code:  
    > ```lang-abap
    > `
    > "pages": {
    >     "ObjectPage|TravelProcessor": {
    >         "entitySet": "TravelProcessor",
    >         "defaultLayoutTypeIfExternalNavigation": "MidColumnFullScreen",
    >         "component": {
    >             "name": "sap.suite.ui.generic.template.ObjectPage"
    >         },
    >         **"embeddedComponents": \{
    >             "changedoccomponent": \{
    >                 "id": "changedoccomponent",
    >                 "componentUsage": "ChangedocReuseComponent",
    >                 "title": "\{\{reuseTitle\}\}",
    >                 "settings": \{
    >                     "objectClass": \[
    >                         "<MY\_CHANGE\_DOC\>"
    >                                     \],
    >                     "objectId": "\{parts: \[\{path: '<MY\_OBJECTID\>'\}\], formatter: 'sap.nw.core.changedocs.lib.reuse.changedocscomponent.arrayFormatter'\}",
    >                     "startDate": "1900-01-01T00:00:00"**
    >                 }
    >             }
    >         }
    >     }
    > }
    > `
    > ```

    > ### Note:  
    > Make sure to replace strings `<MY_CHANGE_DOC>` with your own change document object and `<MY_OBJECTID>` with your own Object id which were also used to create change documents.

3.  Adapt your `<i18n.properties>` file and add:

    > ### Sample Code:  
    > ```lang-abap
    > `
    > …
    > #XTIT: Reuse component title
    > reuseTitle =Change Documents
    > …
    > `
    > ```

    > ### Note:  
    > Manual tests of the reuse library using *SAP Business Application Studio* is not possible. Create and test your app finally before implementing the reuse app. Test the reuse app after deployment.
    > 
    > After your app was deployed successfully to an SAP Business Technology Platform system, the updated BSP application and the SAP Fiori Launchpad app descriptor item will appear under your created package in Eclipse.

4.  Update your IAM App. For more information, see [Defining an IAM App for the Business Service](Defining_an_IAM_App_for_the_Business_Service_d0249dd.md)

5.  Once created, maintain the *Change Document OData Service*. Go to the *Service* tab and add the *Change Document Log OData Service* by naming the *OData V2* service type and add the following service name: `APS_CHANGE_DOCUMENTS_SRV`` `` `` `` `` `` ``0001` \(**Note: make sure to add all 11 spaces in between 'SRV' and '0001'**\).

6.  Create a new Business Catalog. For more information, see [Creating a Business Catalog](Creating_a_Business_Catalog_d120838.md)

    Having created the business catalog, you have successfully implemented a reusable component to display your change documents.


