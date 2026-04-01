<!-- loio26b8df5435c649aa8ea7b3688ad5bb0a -->

# Software Assembly Integration \(SAP\_COM\_0582\)

The communication scenario SAP\_COM\_0582 enables you to assemble software products via integration into build pipelines. With the APIs belonging to this communication scenario, you can check software components, assemble software packages, and upload the assembly as well as the export logs to the build pipeline. The pipeline then will upload the software package for registration in the SAP Add-on Assembly Kit as a Service.



<a name="loio26b8df5435c649aa8ea7b3688ad5bb0a__section_lrp_rxv_x2c"/>

## Software Component Assembly

The assembly of software packages happens on software component level. The build pipeline has to orchestrate the API calls in case the software product consists out of multiple software components. Depending on the kind of package to be assembled \(installation, support or patch\) different steps are executed including the following:

-   Check for a valid producer license of the used namespace\(s\)
-   The object list is calculated. For installation packages these are all objects currently existing in the Git repository and optionally in the list of deleted objects compared to the predecessor release. For maintenance packages \(component support package or correction package\) this is the list of changed \(including added and deleted\) objects since the predecessor package. Comparisons are done by evaluating the current Git repository state with the one of the predecessor packages \(indicated by the commit ID used for assembling the predecessor package\)
-   The delivery transport is created, objects are inserted, object list checks are executed and finally the delivery transport is exported
-   Further metadata is gathered \(e.g. current system software levels, DDIC extensibility quotas, software component relations\) and combined with the delivery transport
-   Logs are gathered and compressed

    > ### Caution:  
    > The logs might be needed in case of support inquiries or for compliance requirements. The build system automatically deletes the `DELIVERY_LOGS.ZIP` archive, like other build results, after a grace period. We recommend you transfer this file to long-term storage.

-   The API snapshot of the predecessor semantic version is selected and set to check relevant \(if found\)
    -   For add-on installation \(AOI\) software packages the following snapshot is selected: `X.*.*` with X representing the previous release version
    -   For Component Support Package \(CSP\) software packages the following snapshot is selected: `Y.X.*` with X representing the current release version and Y representing the previous support package level
    -   For Correction Package \(CPK\) software packages the following snapshot is selected: `Y.Y.X` with Y representing the current release and support package level and X representing the previous patch level
    -   For the initial version 1.0.0 there will never be a predecessor version, and since no snapshot will be found in this case, no snapshot will be set to check-relevant.
    -   If no semantic version API snapshot can be found in the assembly system but a different API snapshot is set to check-relevant, the API compatibility check will be done based on such a snapshot instead.

-   Mandatory ABAP Test Cockpit Checks are run, including

    -   Consistency of software component dependencies - Virus Check of MIME objects using SAP Malware Scanning Service. See What Is SAP Malware Scanning Service
    -   Released API Compatibility. See [Compatibility Checks for Released APIs](https://help.sap.com/doc/abapdocu_cp_index_htm/CLOUD/en-US/abenrestricted_apis_atc_compa.html)

    > ### Note:  
    > The Released API Compatibility ABAP Test Cockpit check can only function properly if there is an API snapshot available in the assembly system. Therefore, make sure to use a permanent system for the assembly if you need to fulfill consistency and stability criteria for your released APIs. For more information, see [Checking the Compatibility of Released APIs](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/checking-compatibility-of-released-apis).
    > 
    > In some cases where the assembly of a software package version needs to be repeated with a different commit ID in the [software component](https://help.sap.com/docs/btp/sap-business-technology-platform/software-components?version=Cloud), you should delete any API snapshot that was already created in the assembly system for the semantic version, so that the snapshot is recreated during the reassembly.

-   A new API snapshot for the current assembled semantic version is created. See [Creating API Snapshots](https://help.sap.com/docs/sap-btp-abap-environment/abap-environment/creating-api-snapshots?version=Cloud) .

-   Generation and Syntax Check of the complete software component



<a name="loio26b8df5435c649aa8ea7b3688ad5bb0a__section_znc_cty_y2c"/>

## Build Pipeline

The build pipeline used to call this communication scenario has to orchestrate the assembly of the individual software components of the build software product and has to integrate with the SAP Add-On Assembly Kit as a Service as well as SAP Business Technology Platform and several other communication scenarios of the build and the acceptance test / integration test system to achieve a meaningful continuous integration and delivery \(CI/CD\) level.

We strongly recommend using the SAP Landscape Portals Build Product Version app as build pipeline and for SAP S/4 HANA Cloud Public Edition based software products it is mandatory. For more information, see [Access to Landscape Portal](https://help.sap.com/docs/sap-btp-abap-environment/abap-environment/access-to-landscape-portal?version=Cloud) and [Build](https://help.sap.com/docs/sap-btp-abap-environment/abap-environment/build?version=Cloud).

To make the setup of build pipelines as easy as possible, the open source project "Piper" has been created. In general, there are various functions \("Library steps"\), as well as whole pipelines, available to reuse. There, you can find the step `abapEnvironmentAssemblePackages` \(see[ abapEnvironmentAssemblePackages](https://www.project-piper.io/steps/abapEnvironmentAssemblePackages/)\), that implements the functionality of the APIs belonging to SAP\_COM\_0582. The step `abapEnvironmentAssemblePackages` is embedded in a sequence of steps which are needed to produce and distribute software packages, see the Library steps on [Project "Piper"](https://www.project-piper.io/)  and [Build and Publish Add-on Products on SAP BTP ABAP Environment](https://www.project-piper.io/scenarios/abapEnvironmentAddons/) .

> ### Note:  
> Project 'Piper' is expected to be archived on December 31st 2026. No further maintenance will be done as of this date.

For more information, see

-   [Developing and Operating SaaS Applications](https://help.sap.com/docs/sap-btp-abap-environment/abap-environment/developing-and-operating-saas-applications?version=Cloud) in the [Landscape Portal](https://help.sap.com/docs/sap-btp-abap-environment/abap-environment/landscape-portal?version=Cloud) for SAP BTP ABAP Environment.
-   [Scalable Delivery](https://help.sap.com/docs/SAP_S4HANA_CLOUD/6aa39f1ac05441e5a23f484f31e477e7/bcdc44683ece4f11a399b3f148a8bb22.html?version=2602.500) in the [Landscape Portal for SAP S/4HANA Cloud Public Edition](https://help.sap.com/docs/LANDSCAPEPORTAL_S4ABAP/bbef3473740144d38c8485d26871a1f0/b28b1d7e8919446e8a3b54cd54f74538.html).

