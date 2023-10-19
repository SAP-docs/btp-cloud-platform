<!-- loio6efb5242a2b44625b6c42e14de6c1c9d -->

# Create a New Product Version

The *Build Product Version* app lets you create new product versions from scratch in case of new releases or based on parent ones if you are creating a patch delivery or support package stack.

> ### Note:  
> You need to have configured the templates for a product to create new product versions using this app. See [Configure a Pipeline Template](configure-a-pipeline-template-dac47ae.md).

Find out how to create a new product version:

1.  Log in to the *Landscape Portal* and click on the tile *Build Product Version*.

2.  Select one of your products from the list. You will be forwarded to the *Product Versions* tab. Here, you can see a table listing all the existing versions of this product, their type \(see a table overview of the types [here](https://help.sap.com/docs/btp/sap-business-technology-platform/configure-pipeline-template?version=Cloud), or read more about [The Add-On Product](https://www.project-piper.io/scenarios/abapEnvironmentAddons/#add-on-product-version)\), when they were created, as well as their delivery status:

    -   **Not ready**: The product version is currently being built and is not available for test or production use yet.

    -   **Ready for test**: The product version has been build but has not yet been released for production use. However, the version may be used for \(automated\) testing.

    -   **Ready for production**: The product version is ready for production use. An ABAP environment production system can now be updated to this product version.


3.  To create a new product version, click the *Create* button, choose *Delivery* or *Test* and select the desired type. The resulting product version will be calculated automatically.

4.  Select software components to be included in your new product version. To add additional software components, click the *Add* button on the right. For each software component, define a component version, enter the desired branch and commit ID as seen in the Manage Software Components app, and select in which languages your product version should be built. You can change the order of how the software components are imported via drag and drop in the table or by selecting a component and moving it using the arrows on the right. For more information, see [Manage Software Components.](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/3dcf76a072c9450eb46b99db947dab46.html?version=Cloud)

    > ### Note:  
    > The leading software component \(software component is exclusively used as part of one add-on product\) should be the first, whereas a reuse software component \(software component is used as part of multiple add-on products\) would be the last in order.

5.  Click the *Build Product Version* button to trigger the build of the pipeline for your new product version.

6.  \(Optional\): You can use the *Cancel* button on the lower right to leave the screen. Please be aware that after confirming the cancellation, all changes will be lost.

7.  You will be redirected to the Pipeline Status screen, where you can track the progress of your build. See [View Details on a Product Version’s Pipeline Progress](view-details-on-a-product-version-s-pipeline-progress-7713509.md).


> ### Note:  
> Product versions can only be deleted if their status is ‘*In Configuration*’ because then the build was not yet started. In this case, the delete button will be enabled once the product version is selected. Please be aware that the deletion cannot be reversed.

> ### Note:  
> The column Log Availability can have the following status:
> 
> ****
> 
> 
> <table>
> <tr>
> <th valign="top">
> 
> Log Availability
> 
> 
> 
> </th>
> <th valign="top">
> 
> Definition
> 
> 
> 
> </th>
> </tr>
> <tr>
> <td valign="top">
> 
> Not built in LP
> 
> 
> 
> </td>
> <td valign="top">
> 
> The product version you built did not originate from the Build Product Version app.
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> Not yet triggered
> 
> 
> 
> </td>
> <td valign="top">
> 
> The configuration for your build has been set in the Build Product Version app.
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> Wrong Subaccount
> 
> 
> 
> </td>
> <td valign="top">
> 
> The subaccount you want to use is not the one in which the current build has been started.
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> Log expired
> 
> 
> 
> </td>
> <td valign="top">
> 
> Your product version log expired and is not available anymore.
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> Unknown
> 
> 
> 
> </td>
> <td valign="top">
> 
>  
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> Build running
> 
> 
> 
> </td>
> <td valign="top">
> 
> There is currently a running build assembling your product version.
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> Build failed
> 
> 
> 
> </td>
> <td valign="top">
> 
> Your recent build ran into an error and failed.
> 
> 
> 
> </td>
> </tr>
> <tr>
> <td valign="top">
> 
> Build success
> 
> 
> 
> </td>
> <td valign="top">
> 
> Your recent build ran successfully and is finished now.
> 
> 
> 
> </td>
> </tr>
> </table>

