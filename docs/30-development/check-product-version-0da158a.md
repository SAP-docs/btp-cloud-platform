<!-- loio0da158a663c2431099e9ea1b3cec6e9a -->

# Check Product Version

The *Check Product Version* app lets you view the results of product version delivery infrastructure checks to see if your product version is ready for delivery. The app shows results for checks of the product version, its components and respective packages.



<a name="loio0da158a663c2431099e9ea1b3cec6e9a__section_umt_xqz_1tb"/>

## Prerequisites

You need to have the “LandscapePortalAdmin” user role assigned to your user account to access this app.



<a name="loio0da158a663c2431099e9ea1b3cec6e9a__section_vzk_yqz_1tb"/>

## Working in the Check Product Version app

1.  Log into the *Landscape Portal* from your provider subaccount.

2.  In the *Product* section, click on the *Check Product Version* tile to open the app.

3.  A list of all your products is displayed. Select one of the products from the list.

4.  You can now see general details on the product \(product name, namespace\) as well as a list of all its product versions and their current delivery status:

    -   G \(Not ready\): The product version is currently being built and is not available for test or production use yet.
    -   T \(Ready for test\): The product version has been build but has not yet been released for production use. However, the version may be used for \(automated\) testing.
    -   P \(Prod\): The product version is ready for production use. An ABAP environment production system can now be updated to this product version.

5.  Select a version to see more detailed information on the check results:

    -   **Delivery Requirements**: During the build process and depending on the integrated software components and involved objects in the dedicated product version, calculations are automatically made and mark whether the delivery of a product version can be done online or requires a downtime. This information is reflected under *Delivery Requirements* , and you can then expect to see one of two possible status messages
    -   **Components**: View whether a system downtime is required when your software components are imported. This information is calculated automatically by the infrastructure. Click one of the components to view its attributes \(package, delivery status, branch, commit ID\) and its import conditions. The import conditions describe which components and packages must be installed into the system as a prerequisite to install the particular software component version. They are calculated automatically during the build of a product version based on the software in the build system. The following conditions exist:

        -   Installed: The package/component needs to be installed in this exact version.

        -   At least: The package/component needs to be installed in this version or a newer version.

        -   Not installed: This version of the package/component must not be installed.


        All of the import conditions mentioned need to be fulfilled.

    -   **Checks**: View whether the delivery check for the product version was successful.
    -   **Object Lists**: View a complete list of all objects.

6.  If the checks were successful and your product version is ready for delivery \(i.e. has the delivery status P\), you can click the *Schedule Update* button in the top right corner to navigate to the *Update Product Version* app.


