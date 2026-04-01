<!-- loio9721f0fb92a84e2a95309acf445cb0a9 -->

# Maintain

After the initial add-on release has been shipped as a SaaS solution offering, the development of maintenance patches, support packages, and consequent add-on releases comes into play.

Once everything is implemented, built, and the maintenance delivery is deployed, the corresponding changes become available in the customer production system AMT.

> ### Note:  
> New features are developed on different code lines \(branches\). If you create a so-called maintenance branch to implement patches while new features are implemented in the main branch of a software component, you can implement new features and provide bug fixes at the same time. For more information, see [Versioning and Branches](https://help.sap.com/docs/btp/sap-business-technology-platform/concepts?version=Cloud#versioning-and-branches).



<a name="loio9721f0fb92a84e2a95309acf445cb0a9__section_qhv_tdp_drb"/>

## Prerequisites

-   To set up the maintenance system landscape, you need the relevant entitlements in the global account for development. See [Entitlements and Quotas](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/00aa2c23479d42568b18882b1ca90d79.html).
-   When using a maintenance system landscape, you require business users with authorization to use the Manage Software Components app and developer users using ABAP Development Tools must be available in the systems. See [Manage Software Components](../50-administration-and-ops/manage-software-components-3dcf76a.md) and [Getting Started as a Developer in the ABAP Environment](../20-getting-started/getting-started-as-a-developer-in-the-abap-environment-4b896c9.md).
-   To configure new add-on versions, you need the existing pipeline configuration for an add-on build pipeline. These can be the pipeline templates in the Build Product Version app or a manual configuration. See [Build Product Version](https://help.sap.com/docs/btp/sap-business-technology-platform/build-product-version?version=Cloud) and [Build and Publish Add-on Products on SAP BTP ABAP Environment](https://www.project-piper.io/scenarios/abapEnvironmentAddons/).
-   If you have configured the add-on build pipeline manually, you need a Jenkins server where you can execute it.
-   To use the Landscape Portal, you need a subscription to the Landscape Portal application and a user assigned to role collection `LandscapePortalAdminRoleCollection`.

