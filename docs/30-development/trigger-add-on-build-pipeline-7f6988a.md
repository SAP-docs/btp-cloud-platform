<!-- loio7f6988a9a9f94845825d8c7ff66990fb -->

# Trigger Add-On Build Pipeline

![](images/Pipeline_add-on_build_d36cfe1.png)

Similar to the build of the initial add-on version, as an add-on administrator, you need to trigger the execution of the configured ABAP environment pipeline for an add-on build. You can do this using the Build Product Version button in the corresponding app. After a successful build, the new add-on version is technically available for deployment to the ABAP environment. See [Build Product Version](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/0c40cc527b15450c9211c3cff0188296.html). If you are configuring the add-on build pipeline manually, then you need to trigger its execution in your Jenkins server. For in-depth information about the ABAP environment pipeline, check out [ABAP Environment Pipeline](https://help.sap.com/docs/btp/sap-business-technology-platform/concepts?version=Cloud#abap-environment-pipeline).

> ### Note:  
> If you are using gCTS instead of add-ons for delivering software components into production systems, an add-on build is not required.
> 
> Please ensure that the add-on product version to be published is properly tested before confirming the release decision. This includes testing in SAP Fiori launchpad and the ABAP Test Cockpit. See [Test in the ABAP Environment SAP Fiori Launchpad](test-in-the-abap-environment-sap-fiori-launchpad-8c5b4d7.md) and [Test in the ABAP Test Cockpit](test-in-the-abap-test-cockpit-f0b71a1.md).
> 
> During add-on build a new semantic version API snapshot will automatically be created for each add-on software component. In the assembly system BLD semantic version snapshots are automatically created and set to check-relevant during add-on build. Do not perform manual actions on API snapshots in these systems. You also have the option to download a created API snapshot for use in other systems. See [Downloading API snapshots](https://help.sap.com/docs/sap-btp-abap-environment/abap-environment/downloading-api-snapshots?version=Cloud).

