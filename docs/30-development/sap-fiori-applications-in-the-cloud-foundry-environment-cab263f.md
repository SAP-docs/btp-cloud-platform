<!-- loiocab263f1f20448b59845705442dec16d -->

# SAP Fiori Applications in the Cloud Foundry Environment

If you want to deploy an SAP Fiori application to the Cloud Foundry environment, the following users are involved:

-   A UI developer implements the SAP Fiori application against the OData service as part of a multi-target application \(MTA\).

    An MTA is logically a single application comprised of multiple parts created with different technologies, which share the same lifecycle. The developers of the MTA describe the desired result using the MTA model, which contains MTA modules, MTA resources, and interdependencies between them.

-   The developer defines the tile as part of the application. Once this is done, the MTA is deployed to the Cloud Foundry space. By doing so, the SAP Fiori application of the MTA is deployed to the HTML5 application repository. The developer can deploy the MTA either manually or as part of a CI/CD pipeline. See [Continuous Integration and Delivery \(CI/CD\)](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/fe74df55b0f54e99bf6e13a3b53e1db0.html?version=Cloud).

    The HTML5 application repository is an SAP BTP service that enables central storage of HTML5 applications' static content on the SAP BTP, Cloud Foundry environment. See [HTML5 Application Repository](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/f8520f572a6445a7bfaff4a1bbcbe60a.html?version=Cloud).

-   An administrator in the ABAP environment provides access to the OData service via a business role. A launchpad administrator enables access to the tile via a role collection.
-   A business user that is assigned to the business role and role collection can access the tile from SAP Fiori launchpad and launch the application.

![](images/UI_Development_in_the_Cloud_Foundry_Environment_6f98219.png) 

