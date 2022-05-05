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

    -   P \(Ready for production\)
    -   G \(Not ready\)
    -   T \(Ready for test\)

5.  Select a version to see more detailed information on the check results:

    -   **Components**: View whether a system downtime is required when your software components are imported. Click one of the components to view its attributes \(package, delivery status, branch, commit ID\) and its import conditions.
    -   **Checks**: View whether the delivery check for the product version was successful.
    -   **Object Lists**: View a complete list of all objects.

6.  If the checks were successful and your product version is ready for delivery, you can click the *Schedule Update* button in the top right corner to navigate to the *Update Product Version* app.


