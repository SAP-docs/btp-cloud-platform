<!-- loio8120bf6d9eed465684d205ec48623490 -->

# Build Product Version

You can use the *Build Product Version*app to easily trigger the build of new product versions via pipelines based on templates that you can configure for different use cases such as new release deliveries, support packages or hotfixes/patch deliveries.

The app guides you through the creation of runs for your product versions and triggers them to be deployed on a system.

Since technical users are needed in various steps, the app can also be used to add and maintain credentials that can be reused in multiple products.

Previously, the scenario has been described in piper. For more information, see [Build and Publish Add-On Products on SAP BTP, ABAP Environment.](https://www.project-piper.io/scenarios/abapEnvironmentAddons/) We recommend to use the hereby described Build Product Version App which enables the Build Add-On Product scenario for you without needing to set up a Jenkins server.



<a name="loio8120bf6d9eed465684d205ec48623490__section_ird_tn5_ktb"/>

## Key Features

You can use the *Build Product Version* app to:

-   Choose prepared pipeline templates depending on your use case and configure them to create different types of pipelines for your product versions:
    -   Release Deliveries
    -   Support Package Stacks
    -   Patch Deliveries

-   View details on a product version’s pipeline progress
-   Maintain credentials for users that can be reused for different products



The standard user flow is described in the following diagram. Hover over the different steps to display additional information.

![](images/Map_BPV_6d3c880.png)

-   [Maintain Credentials](maintain-credentials-67b5aee.md)
-   [Configure a Pipeline Template](configure-a-pipeline-template-dac47ae.md)
-   [Create a New Product Version](create-a-new-product-version-6efb524.md)
-   [View Details on a Product Version’s Pipeline Progress](view-details-on-a-product-version-s-pipeline-progress-7713509.md)



<a name="loio8120bf6d9eed465684d205ec48623490__section_umt_xqz_1tb"/>

## Prerequisites

-   You need to have the “LandscapePortalAdmin” user role assigned to your user account to access this app.

-   Users need an active subscription for the CI/CD service in the BTP subacccount to be able to access the Landscape Portal. If this step is not maintained, the following error will occur: 'No subscription to CI/CD service found for this subaccount.'


