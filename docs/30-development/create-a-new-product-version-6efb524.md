<!-- loio6efb5242a2b44625b6c42e14de6c1c9d -->

# Create a New Product Version

The *Build Product Version* app lets you create new product versions from scratch in case of new releases or based on parent ones if you are creating a patch delivery or support package stack.

> ### Note:  
> You need to have configured the templates for a product to create new product versions using this app. See [Configure a Pipeline Template](configure-a-pipeline-template-dac47ae.md).

Find out how to create a new product version:

1.  Log in to the *Landscape Portal* and click on the tile *Build Product Version*.

2.  Select one of your products from the list. You will be forwarded to the *Product Versions* tab. Here, you can see a table listing all the existing versions of this product, their type \(*Release Delivery*, *Patch Delivery*,*Support Package Stack* - see [The Add-On Product](https://www.project-piper.io/scenarios/abapEnvironmentAddons/#add-on-product-version)\), when they were created, as well as their delivery status:

    -   **In Configuration**: Configuration of build has started

    -   **In Initialisation**: Product version creation has started and the first stages are running

    -   **not supported**: Product version created or creation started outside of this app

    -   **In Build**: Build stage is running

    -   **In Testing**: Integration tests are running

    -   **Ready For Production**: Product version creation has finished and the product version is ready for deployment.


3.  To create a new product version of type *Release Delivery*, click on the *Create* button on the right and select *Release Delivery*.

    To create a product version of type *Patch Delivery* or *Support Package Stack*, first select a parent version from the list of product versions, then click the *Create* button on the right and select the desired type.

    The resulting product version will be calculated automatically.

4.  Select software components to be included in your new product version. To add additional software components, click the *Add* button on the right. For each software component, define a component version, enter the desired branch and commit ID as seen in the Manage Software Components app, and select in which languages your product version should be built. You can change the order of how the software components are imported via drag and drop in the table or by selecting a component and moving it using the arrows on the right. For more information, see [Manage Software Components.](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/3dcf76a072c9450eb46b99db947dab46.html?version=Cloud)

    > ### Note:  
    > The leading software component \(software component is exclusively used as part of one add-on product\) should be the first, whereas a reuse software component \(software component is used as part of multiple add-on products\) would be the last in order.

5.  Click the *Build Product Version* button to trigger the build of the pipeline for your new product version.

6.  \(Optional\): You can use the *Cancel* button on the lower right to leave the screen. Please be aware that after confirming the cancellation, all changes will be lost.

7.  You will be redirected to the Pipeline Status screen, where you can track the progress of your build. See [View Details on a Product Version’s Pipeline Progress](view-details-on-a-product-version-s-pipeline-progress-7713509.md).


> ### Note:  
> Product versions can only be deleted if their status is ‘*In Configuration*’ because then the build was not yet started. In this case, the delete button will be enabled once the product version is selected. Please be aware that the deletion cannot be reversed.



<a name="loio6efb5242a2b44625b6c42e14de6c1c9d__section_cqn_s2l_v5b"/>

## Assign Software Component Process Flow

When the user creates a new release, support package or patch delivery, it is possible to assign multiple software components to the build. The following tables show the process flow of the 'add software component' action.

Before the user is allowed to add, delete, build or reorder a product version with software components, several conditions must be met. The following matrixes show an overview of all conditions.

The first table shows an overview of conditions for creating new Product Versions.

<a name="loio6efb5242a2b44625b6c42e14de6c1c9d__table_jr4_1dl_v5b"/>Availability Matrix of add, delete and edit in Product Version Screen


<table>
<tr>
<th valign="top">

Condition Description



</th>
<th valign="top">

LP-Status



</th>
<th valign="top">

Toolbox Status



</th>
<th valign="top">

Edit



</th>
<th valign="top">

Delete



</th>
<th valign="top">

Create Release



</th>
<th valign="top">

Create Support Package



</th>
<th valign="top">

Create Patch Delivery



</th>
</tr>
<tr>
<td valign="top">

In Confiuration/ In Initialisation, but Pipeline aborted



</td>
<td valign="top">

I or T



</td>
<td valign="top">

none or G



</td>
<td valign="top">

allowed



</td>
<td valign="top">

allowed



</td>
<td valign="top">

allowed



</td>
<td valign="top">

forbidden



</td>
<td valign="top">

forbidden



</td>
</tr>
<tr>
<td valign="top">

Ready for Test, integration tests aborted



</td>
<td valign="top">

T



</td>
<td valign="top">

T



</td>
<td valign="top">

allowed



</td>
<td valign="top">

forbidden



</td>
<td valign="top">

allowed



</td>
<td valign="top">

allowed when template configured



</td>
<td valign="top">

allowed when template configured



</td>
</tr>
<tr>
<td valign="top">

Ready for Production, Pipeline running



</td>
<td valign="top">

any



</td>
<td valign="top">

P



</td>
<td valign="top">

forbidden



</td>
<td valign="top">

forbidden



</td>
<td valign="top">

allowed



</td>
<td valign="top">

allowed when template configured



</td>
<td valign="top">

allowed when template configured



</td>
</tr>
</table>

The following table shows an overview of conditions regarding the Build of a new Prodcuct Version.

<a name="loio6efb5242a2b44625b6c42e14de6c1c9d__table_hvy_d2l_v5b"/>Availability Matrix of add, delete and edit in Build Product Version Screen


<table>
<tr>
<th valign="top">

Condition Description



</th>
<th valign="top">

Move



</th>
<th valign="top">

Edit \(not yet implemented\)



</th>
<th valign="top">

Delete



</th>
<th valign="top">

Add



</th>
<th valign="top">

Build Product Version



</th>
</tr>
<tr>
<td valign="top">

In Confiuration/ In Initialisation, but Pipeline aborted



</td>
<td valign="top">

allowed



</td>
<td valign="top">

allowed



</td>
<td valign="top">

allowed



</td>
<td valign="top">

create allowed



</td>
<td valign="top">

allowed



</td>
</tr>
<tr>
<td valign="top">

Ready for Test, integration tests aborted



</td>
<td valign="top">

forbidden



</td>
<td valign="top">

forbidden



</td>
<td valign="top">

forbidden



</td>
<td valign="top">

forbidden



</td>
<td valign="top">

allowed



</td>
</tr>
<tr>
<td valign="top">

Ready for Production, Pipeline running



</td>
<td valign="top">

forbidden



</td>
<td valign="top">

forbidden



</td>
<td valign="top">

forbidden



</td>
<td valign="top">

forbidden



</td>
<td valign="top">

forbidden



</td>
</tr>
</table>

