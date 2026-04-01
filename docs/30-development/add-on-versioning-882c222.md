<!-- loio882c222035734ff39ffaf36f463a4cda -->

# Add-On Versioning



For the add-on delivery process, certain versioning principles apply. Learn how software components are combined to an add-on product and what versioning rules are used for both parts. Software components and add-on products follow a similar versioning pattern.



### Add-on Product Version

Instead of importing software components into productive systems, when providing a SaaS solution in the ABAP environment, software components are packaged and installed into ABAP systems based on so-called add-on products/software products.

You can only install one add-on product for each system using the ABAP environment `saas_oem` service plan instead of the `standard` service. During provisioning of this service, parameters `addon_product_name` and `addon_product_version` are used to install a certain add-on product version into the system, after the system has been provisioned. See [ABAP Solution Service](abap-solution-service-1697387.md).

The add-on product name includes a reserved development namespace to separate the name from other customers/partners. See SAP note [84282](https://me.sap.com/notes/84282).

The versioning pattern `<Release>.<Support Package Stack Level>.<Patch Level>` applies to the add-on product version.

> ### Note:  
> Only in a new release, you can change the bundled software components of the add-on product.

Technically, the allowed number range is 1.0.0 to 9999.9999.9999.

For the release, there are no technical restrictions regarding the number of new versions. You only have to consider that the version has to be ascending across builds and there must be no gaps between versions. The initial release is always 1.0.0.

The support package stack level count starts again from 0 with each release.

The patch level count starts again from 0 with each support package.

While providing a specific add-on version, leading zeroes should be omitted \(1.2.3 instead of 0001.0002.0003\).

The add-on product version should be increased analogous to the version of the leading software component. The leading software component is the software component that is, as opposed to a reuse software component, exclusively used as part of one add-on product.

An exception to this recommendation is the patch level in the add-on production version: In case of an add-on product with a reuse software component, the patch level of the add-on product version might be higher than the patch level of the leading software component version.

For more information about software product versioning, see [Add-On Product Version](https://www.project-piper.io/scenarios/abapEnvironmentAddons/#add-on-product-version).



### Software Component Version

Software components are self-contained and include packages as well as development objects. They are used in combination with a reserved development namespace to separate the name from other customers/partners. See [Software Components](software-components-58480f4.md).

The versioning pattern `<Release>.<Support Package Level>.<Patch Level>` also applies to the software component version.

> ### Note:  
> Software component versions are delivered with delivery packages. However, software component versions are not individual shipment entities. They can only be delivered to customers as part of a software product version.
> 
> Software component versions are only built once, independent from add-on product versions where the software component version was referenced. If an add-on product version is referring to a software component version that has already been created as part of a different add-on build, the created delivery package is reused.

Technically, the allowed number range is 1.0.0 to 9999.9999.9999.

For the release, there are no technical restrictions regarding the number of new versions. You only have to consider that the release has to be ascending across builds and there must be no gaps between versions. The initial release is always 1.0.0.

The support package level can only go up until 369 because of technical limitations. The support package level count starts again from 0 with each new release.

For the patch level, there is a technical limit of 36³, limited to 9999. The patch level count starts again from 0 with each support package.

For more information on software component versioning, see [Software Component Version](https://www.project-piper.io/scenarios/abapEnvironmentAddons/#software-component-version).

