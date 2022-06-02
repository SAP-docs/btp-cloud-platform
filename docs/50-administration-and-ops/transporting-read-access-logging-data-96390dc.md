<!-- loio96390dc5fd024a81ab7155abc0314969 -->

# Transporting Read Access Logging Data

RAL objects that you’ve created can be transported from a Q system to a P system with the *Export Customizing Transports* app



In your RAL application, you can create different customizing objects like configurations or recordings. These objects are added to the default customizing request that you can export from a Q system and import into a P system. The objects that come from the RAL application are:

-   Configurations

-   Log domains

-   Purposes

-   Recordings


To transport your changes from the development system to the productive system, perform the following steps:



### In your development system:

1.  Use the *Manage Software Components* app to make sure there is a cloned business configuration software component. See [Manage Software Components](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/3dcf76a072c9450eb46b99db947dab46.html?version=Cloud).

    In case it is not available yet, you need to create a business configuration software component and clone it. See [How to Create Software Components](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/67e2f2e1fbcf48a4801bad004133e0a7.html?version=Cloud) and [How to Clone Software Components](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/18564c54f529496ba420d4c83545a2ce.html?version=Cloud).

2.  Make sure that there is an open customizing transport request for your system and that the customizing transport request belongs to the cloned business configuration software component.

    To create a customizing transport request, you use the *Export Customizing Transport* app. You need the `SAP_BR_BPC_EXPERT` role to access this app. See [Export Customizing Transports](export-customizing-transports-fa7366c.md).

    If a software component of the type Business Configuration is available in the system, the created request will target this software component. If no such software component is available, the request will be created without any target. See [Working in the Export Customizing Transports App](working-in-the-export-customizing-transports-app-cc16fd0.md).

3.  Make the actual changes to the RAL objects.
4.  Release the task and customizing transport request in the *Export Customizing Transport* app.



### In your productive system:

1.  In the Manage Software Components app, pull the changes for the business configuration. See [How to Pull Software Components](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/90b9b9d5219c4875825be35137d9128f.html?version=Cloud).

2.  Check in the *Read Access Logging Configuration* app if the changes are visible.

**Related Information**  


[Working in the Export Customizing Transports App](working-in-the-export-customizing-transports-app-cc16fd0.md "Find out how to create, release, or merge customizing requests using the Export Customizing Transports app.")

