<!-- loio7713509c184443bd9e06d86627568def -->

# View Details on a Product Version’s Pipeline Progress

After you’ve used the *Build Product Version* app to trigger the build of a pipeline for your new product version, you can also view details on a version’s pipeline progress directly in the app.

Here's how this is done:

1.  Log in to the Landscape Portal and click on the tile *Build Product Version*.

2.  Select one of your products from the list. You will be forwarded to the *Product Versions* tab. Here, you can see a table listing all the existing versions of this product, their type \(*Release Delivery*, *Patch Delivery*, *Support Package Stack*\), when they were created, as well as their delivery status \(for more information on the delivery status, see [Create a New Product Version](create-a-new-product-version-6efb524.md)\).

3.  Click on the product version for which you would like to see the pipeline progress. You will be redirected to a screen showing the *Pipeline Status* for that product version.

4.  You can now click on the different stages in the pipeline to view the logs of each step. The stages that you switched off in the underlying template will not be selectable.


    <table>
    <tr>
    <th valign="top">

    Stage


    
    </th>
    <th valign="top">

    Description


    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Init


    
    </td>
    <td valign="top">
    
     


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Initial Checks


    
    </td>
    <td valign="top">
    
    This stage runs preliminary checks for the Build stage, validating add-on product/software component versions. See [Initial Checks.](https://www.project-piper.io/pipelines/abapEnvironment/stages/initialChecks/)


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Prepare System


    
    </td>
    <td valign="top">
    
    At this stage, the ABAP environment system for Add-On assembly is created \(service plan abap/standard\). `SAP_COM_0510` \(SAP BTP, ABAP Environment - Software Component Test Integration\) is created via a service key. With the creation of the communication arrangement, a user and password are created on the ABAP environment system for the APIs that are used in the following stages. See [Prepare System.](https://www.project-piper.io/pipelines/abapEnvironment/stages/prepareSystem/)


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Clone Repositories


    
    </td>
    <td valign="top">
    
    This stage pulls/clones the specified software components \(repositories\) to the ABAP environment system that are relevant for the Add-On build. [Clone Repositories.](https://www.project-piper.io/pipelines/abapEnvironment/stages/cloneRepositories/) 


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    ATC


    
    </td>
    <td valign="top">
    
    Check software components to be assembled as part of the add-on build via ABAP Test Cockpit. See [ATC.](https://www.project-piper.io/pipelines/abapEnvironment/stages/test/#atc)


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Build


    
    </td>
    <td valign="top">
    
    This stage is responsible for building the product version for the ABAP environment. The build process of the product version is done in the Add-On assembly system, with the help of the SAP Add-On Assembly Kit as a Service \(AAKaaS\). After this stage has been executed successfully, the product version is ready to be tested. See [Build.](https://www.project-piper.io/pipelines/abapEnvironment/stages/build/)


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Integration Tests


    
    </td>
    <td valign="top">
    
    This stage creates an ABAP environment system \(service plan abap/saas\_oem\) and installs the add-on product, that was built in the Build stage. See [Integration Tests.](https://www.project-piper.io/pipelines/abapEnvironment/stages/integrationTest/)


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Publish


    
    </td>
    <td valign="top">
    
    At this stage, the new product version for the ABAP environment is published. After publishing the new product version it becomes available for add-on installation/update. See [Publish.](https://www.project-piper.io/pipelines/abapEnvironment/stages/publish/)


    
    </td>
    </tr>
    </table>
    
    If a stage has successfully been completed, its icon will be blue; in case of errors it will be red. All stages that are still due are shown in grey and the stages that have been switched off in the template cannot be selected at all.

    If the pipeline is still running, you can update the view using the *Refresh* button in the upper right corner.


> ### Note:  
> *Important*: The logs will be deleted after 28 days. Up to 99 builds can be saved within this period. In case of further builds, the oldest ones will be deleted.

