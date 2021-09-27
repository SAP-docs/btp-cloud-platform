<!-- loio26b8df5435c649aa8ea7b3688ad5bb0a -->

# Software Assembly Integration \(SAP\_COM\_0582\)

The communication scenario SAP\_COM\_0582 enables partners to assemble a software product via integration in Build pipelines for SAP BTP, ABAP environment systems. With the APIs belonging to this communication scenario, you can assemble a software package, upload the assembly and export logs to the Build pipeline, and upload the software package for registration in the Add-on Assembly Kit as a Service \(AAKaaS\).

To make the setup of Build pipelines as easy as possible, the open source project "Piper" was created. In general, there are various functions \("Library steps"\), as well as whole pipelines, available to reuse. There, you can find the step **abapEnvironmentAssemblePackages** \(see [abapEnvironmentAssemblePackages](https://sap.github.io/jenkins-library/steps/abapEnvironmentAssemblePackages/)\), that implements the functionality of the APIs belonging to SAP\_COM\_0582. The step **abapEnvironmentAssemblePackages** is embedded in a sequence of steps which are needed to produce and distribute software packages, see the Library steps on [Project "Piper"](https://sap.github.io/jenkins-library/) and [Build and Publish Add-on Products on SAP BTP ABAP Environment](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentAddons/).

Additionally, there is an example pipeline for a Build process \(see [ABAP Environment Pipeline](https://sap.github.io/jenkins-library/pipelines/abapEnvironment/introduction)\) that comprises the following:

• performing the Addon.yml and AAKaaS steps

• creating a SAP BTP, ABAP environment system

• setting up Communication Arrangement for the APIs

• importing a software component / Git repository

• building software package

• registering the software package in AAKaaS

• deprovisioning the SAP BTP, ABAP environment system

Please find the documentation regarding project "Piper" here: [Project "Piper"](https://sap.github.io/jenkins-library/)

-   **[Assembling a Software Package](Assembling_a_Software_Package_afbcbba.md "")**  


