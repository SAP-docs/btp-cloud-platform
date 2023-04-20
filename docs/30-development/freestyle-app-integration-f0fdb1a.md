<!-- loiof0fdb1a176704bf6a18b14aa655d99a7 -->

# Freestyle App Integration

You can implement the reusable component from the *Reuse Library* in a freestyle app in order to display an application log.



## Context

To be able to use the reusable components, you need to adapt the code that can be found in your view definition file and your controller file.



## Procedure

1.  In the view definition file \(*<MY\_LOG\_DISPLAY\_VIEW.view.xml\>*\), the log display must be positioned on the page. Prepare a container control that will hold the log display component:

    > ### Sample Code:  
    > ```
    > <!-- xmlns:core="sap.ui.core" --> 
    > <core:ComponentContainer id="LogMessagesControlContainer" />
    > ```

2.  In the controller file \(*<MY\_LOG\_DISPLAY\_VIEW.controller.js\>*\), the relevant coding goes into the handler for the *onlnit* event. Create the component and place it into the container control:

    > ### Note:  
    > Make sure to replace the string *<MY\_LOG\_DISPLAY\_VIEW\>* with your own view's name!

    > ### Sample Code:  
    > ```
    > var that = this;
    > 							
    > this.getOwnerComponent().createComponent({
    > usage: "ApplicationLogs",
    > id: "LogMessagesControlComponent",
    > settings: {
    > "persistencyKey": "MY_LOG_DISPLAY_VIEW",
    > "showHeader": false,
    > "showFilterBar": false,
    > "showAsTree": false
    > }
    > }).then(function (oComp) {
    > that.byId("LogMessagesControlContainer").setComponent(oComp);
    > oComp.setLogHandle("<LogHandle>");
    > oComp.refresh();
    > });
    > ```

    > ### Note:  
    > The component you embed makes use of the *SmartFilter* and the *SmartTable* control. Both controls enable a user to configure the components interactively, and also to store a current set of configuration settings as a named variant. By providing a value for the `persistencyKey` parameter, you make sure that the variants that get created in your application become visible only to the users of your application, and not to all users of the component in all applications.

3.  Adapt your *<manifest.json\>* file and add the *sap.nw.core.applogs.lib.reuse* library under the `dependencies` section:

    > ### Sample Code:  
    > ```
    > "dependencies": {
    > "libs": {
    > "sap.nw.core.applogs.lib.reuse": {
    > "lazy": true
    > }
    > }
    > }
    > ```

    After your app was deployed successfully to an SAP BTP, ABAP environment system, the *BSP application* and the *SAP Fiori Launchpad* app descriptor item will appear under your created package in Eclipse.

    ![](images/Eclipse_ABAP_Environment_e0a96c5.png) 

4.  Now, you need to create a new *IAM App*. Follow the instructions described here: [Defining an IAM App for the Business Service](defining-an-iam-app-for-the-business-service-3fb85a8.md).

5.  Once created, you need to maintain the *Application Log* OData Service to call your application log data. To do this, go to the *Service* tab and add the *Application Log OData Service* by naming the service type `OData V2` and add the following service name: `APL_LOG_MANAGEMENT_SRV             0001`. Mind that all 13 spaces between `SRV` and `0001` are required. Now, go to the *Authorization* tab and maintain your *log objects / sub objects* for the authorization object `S_APPL_LOG`.

6.  Finally, you need to create a new *Business Catalog*. Please follow the procedure described here: [Creating a Business Catalog](creating-a-business-catalog-d120838.md) 

    Having created the business catalog, you have successfully implemented a reusable component to display your application logs.


