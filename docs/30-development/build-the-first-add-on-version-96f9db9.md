<!-- loio96f9db9e6c784e5a89ede4d038daaa43 -->

# Build the First Add-On Version





### Create Maintenance Branch

> ### Recommendation:  
> For each release and support package level, as an add-on admin, create a maintenance branch that is used for development of bug fixes and maintenance deliveries. See [Versioning and Branches](versioning-and-branches-8c087bc.md).

In test system TST, create branch `v1.0.0` that is based on the main branch.



<a name="loio96f9db9e6c784e5a89ede4d038daaa43__section_sm1_rv2_gfc"/>

## Build New Product Version

Each version contains an add-on version number – 1.0.0 for the initial delivery – as well as the included software components, such as the corresponding names, branches, and software component versions to be used for the add-on build. You may also choose specific software component commit IDs \(as seen in the Manage Software Components app\) and select which languages should be included in the new product version. Add-on version numbers may not be used more than once.



### Build Using Product Version App \(recommended\)

New product versions for your registered add-on products can be de ned directly in the Build Product Version app. The initial product version will always be of type “Release Delivery”. See [Create a New Product Version](https://help.sap.com/docs/LANDSCAPEPORTAL_S4ABAP/bbef3473740144d38c8485d26871a1f0/d4c9f0877f1640bebe1f6fbe267bf9af.html).

The corresponding pipeline is executed automatically when the Build Product Version button is clicked on in the app. If the execution is successful, the initial version of the add-on will then be available for installation.



### Build Using Manual Configuration

If using a custom pipeline configuration and your own Jenkins server, create an add-on configuration file \(`addon.yml`\) in the corresponding Git repository. This file includes the metadata of the add-on product that is being built, such as versioning information and the included software component versions. Please follow the best practices on how to define the `addon.yml` file. See [Add-on Descriptor File](https://www.project-piper.io/scenarios/abapEnvironmentAddons/#add-on-descriptor-file).

Once the repository is updated, trigger the pipeline execution on your Jenkins server. If your pipeline includes manual confirmation steps, you will have to follow its progress and react accordingly. You may use the add-on installation test system ATI to confirm the success of the add-on installation before confirming its release. You can also use the system for additional tests, similar to the steps described in [Test in the ABAP Environment SAP Fiori Launchpad](https://help.sap.com/docs/btp/sap-business-technology-platform/test?version=Cloud#test-in-the-abap-environment-sap-fiori-launchpad). For testing in a consumer-like environment, you can create tenants of type Test Tenant using the Landscape Portal application. See [Use Test Tenants](https://help.sap.com/docs/btp/sap-business-technology-platform/use-test-tenants?version=Cloud).

> ### Tip:  
> For in-depth information about versioning and branches, check out [Versioning and Branches](versioning-and-branches-8c087bc.md).
> 
> To learn how software lifecycle management in the ABAP environment works with software components, see [Basic Concepts and Terms](basic-concepts-and-terms-fb3a076.md).

> ### Note:  
> Please make sure that the add-on product version to be published is properly tested before confirming the release decision. This includes testing in SAP Fiori launchpad and the ABAP Test Cockpit. See [Test in the ABAP Environment SAP Fiori Launchpad](test-in-the-abap-environment-sap-fiori-launchpad-8c5b4d7.md) and [Test in the ABAP Test Cockpit](test-in-the-abap-test-cockpit-f0b71a1.md).
> 
> During add-on build a new semantic version API snapshot will be automatically created for each add-on software component. In the assembly system BLD semantic version snapshots are automatically created and set to check-relevant during add-on build. Do not perform manual actions on API snapshots in such systems. For the initial software component version 1.0.0 no predecessor version is available and thus compatibility checks will not be performed due to the missing API snapshot. See [Released APIs and Snapshots](https://help.sap.com/docs/btp/sap-business-technology-platform/software-component-dependencies?version=Cloud#released-apis-and-snapshots).



### Check Add-on Build Result

Use the *Check Product Version* app in Landscape Portal to check whether the product version, its components, and respective packages are ready for delivery. See [Check Product Version](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/4de24e56f52d4ca4ae8971aae6861f8e.html).



### Download API Snapshot for use in other systems

In case of released APIs, download the API snapshot created for the initial version 1.0.0 from the add-on build system BLD. The snapshot is created automatically during the add-on build. Afterwards, upload the snapshot into the test system TST and the development System DEV. Set the new API snapshot as check-relevant so that it will be used as a reference for API compatibility checks.

> ### Note:  
> The API snapshot will also be uploaded into the correction system COR and quality assurance system QAS once the maintenance branch is checked out for the first time, usually during the first patch version creation.

