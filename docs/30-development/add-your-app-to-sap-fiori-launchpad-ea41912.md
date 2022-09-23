<!-- loioea41912278ea4525adc3ddd4e4f7988a -->

# Add Your App to SAP Fiori Launchpad



> ### Tip:  
> Check out the developer tutorial on how to integrate a list report application. See [Integrate List Report into ABAP Fiori Launchpad](https://developers.sap.com/tutorials/abap-environment-abap-flp.html#c821f420-092f-47eb-a724-6fd53dbe3a22).



<a name="loioea41912278ea4525adc3ddd4e4f7988a__section_p1q_dll_xrb"/>

## Prerequisites

-   Business role `SAP_BR_ADMINISTRATOR` is assigned to your user, which allows you to create a business role as well as spaces and pages. See [Tools and Prerequisites for Managing Spaces and Pages](https://help.sap.com/viewer/10fd1742ea914256abedb34bf15bd069/Cloud/en-US/a2638d49bf25487fb79a9d0296d3b8bd.html).
-   Business role `SAP_BR_BPC_EXPERT` Configuration Expert - Business Process Configuration is assigned to your user, which authorizes you to use the *Export Customizing Transports* app.

-   You have created a customizing request. See [Transport Business Configuration via Software Component of Type Business Configuration](transport-business-configuration-via-software-component-of-type-business-configuration-03a3611.md), [Transport Business Configuration via Software Components of Type Development](transport-business-configuration-via-software-components-of-type-development-d801854.md), and [Export Customizing Transports](../50-administration-and-ops/export-customizing-transports-a772a0f.md).

-   Spaces have been enabled for business users. See [Enabling Spaces](https://help.sap.com/viewer/10fd1742ea914256abedb34bf15bd069/Cloud/en-US/64a5e1675ce7413791a654d2228a90be.html "There are two parameters and one user setting that influence if the launchpad uses spaces or the home page for displaying the apps.") :arrow_upper_right:.



<a name="loioea41912278ea4525adc3ddd4e4f7988a__section_wzs_2ll_xrb"/>

## Launching an Application

![](images/Launch_Your_App_ABAP_d8b027c.png)

1.  As an administrator in the SAP Fiori launchpad of your ABAP system, create a business role in the *Maintain Business Roles* app to provide business users access to your IAM app. See [Maintain Business Roles](../50-administration-and-ops/maintain-business-roles-8980ad0.md).
2.  Add the business catalog that includes the IAM app to the business role. See [Develop an SAP Fiori Application UI and Deploy it to ABAP Using SAP Business Application Studio](develop-an-sap-fiori-application-ui-and-deploy-it-to-abap-using-sap-business-application-eaaeba4.md).
3.  Assign business users to the business role. See [Maintain Business Users](../50-administration-and-ops/maintain-business-users-e40e710.md).
4.  Create a launchpad space and page for your app. See [Managing Launchpad Spaces and Pages](https://help.sap.com/products/BTP/10fd1742ea914256abedb34bf15bd069/e55f5cc8ccec490f83a00284659bce9f.html).
    -   \(Option 1\) Use the *Manage Launchpad Spaces* and *Manage Launchpad Pages* app to create a space and page for your app, assign the customizing transport request you've created earlier, and save the space and page. Then, assign the created space and page to a business role by using the *Maintain Business Roles* app. See [How to Create and Assign Spaces and Pages](https://help.sap.com/products/BTP/10fd1742ea914256abedb34bf15bd069/a2318ca9a44b474daadaad85feb2f364.html).
    -   \(Option 2\) Use the *Maintain Business Roles* app to create a space and page for your app, and assign the space to your business role. The created space and page are automatically assigned to the open default customizing transport request. You can use the *Export Customizing Transport* app to change the default customizing transport request. See [Step by Step: Create a New Space and Page for a Business Role](https://help.sap.com/products/BTP/10fd1742ea914256abedb34bf15bd069/ab05d9e086554a08af88d6482deb1bcb.html?version=Cloud).

        > ### Note:  
        > If there is no customizing request, an error message is returned.


5.  In the *Manage Launchpad Pages* app, add your app to the page you've just created. See [Editing a Page](https://help.sap.com/products/BTP/10fd1742ea914256abedb34bf15bd069/7b42aad18c53439db2cce55719253674.html?version=Cloud).
6.  \(Optional\) If you want to transport your changes, select your transport request and release the corresponding task in the *Export Customizing Transports* app. See [Working in the Export Customizing Transports App](../50-administration-and-ops/working-in-the-export-customizing-transports-app-cc16fd0.md) and [Transporting Changes to Spaces and Pages](https://help.sap.com/viewer/10fd1742ea914256abedb34bf15bd069/Cloud/en-US/cc9914d702be4ec0b71b8a74d0549b36.html).
7.  As a business user, you can launch the app from the new space.

**Related Information**  


[Transporting Changes to Spaces and Pages](https://help.sap.com/viewer/10fd1742ea914256abedb34bf15bd069/Cloud/en-US/cc9914d702be4ec0b71b8a74d0549b36.html)

[Tutorial: Integrate List Report into ABAP Fiori Launchpad](https://developers.sap.com/tutorials/abap-environment-abap-flp.html)

[Tutorial: Managing Launchpad Spaces and Pages](https://education.hana.ondemand.com/education/pub/s4/index.html?library=library.txt&show=project!PR_4DFA77D97EA8389A)

