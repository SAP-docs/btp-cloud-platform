<!-- loiob37b2935287c4dd8ada5c44f538695d7 -->

# SAP Fiori Applications in the ABAP Environment

If you want to deploy an SAP Fiori application to the ABAP environment, the following users are involved:

-   A UI developer implements the SAP Fiori application against the OData service and defines the tile as part of the application. Once this is done, the developer deploys the SAP Fiori application to the SAPUI5 ABAP repository.

    The SAPUI5 ABAP repository is part of the ABAP environment and is the umbrella term for the single SAPUI5 repository of each application. Technically, the SAPUI5 ABAP repository is based on the Business Server Page \(BSP\) repository. Each SAPUI5 repository is represented by an individual BSP application. The SAPUI5 ABAP repository is also used for delivering SAPUI5 apps of the ABAP environment.

-   An administrator in the ABAP environment provides access to the OData service and the tile via a business role.
-   A business user that is assigned to the business role can access the tile from SAP Fiori launchpad and launch the application.

![](images/UI_Development_in_the_ABAP_Environment_f758148.png) 

