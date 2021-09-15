<!-- loiob04a9ae412894725a2fc539bfb1ca055 -->

# Test Integration \(SAP\_COM\_0510\)

The communication scenario SAP\_COM\_0510 enables you to create Continuous Integration pipelines for SAP BTP, ABAP environment systems. With the APIs belonging to this communication scenario, you can import your ABAP code to the SAP BTP, ABAP environment system and check your code with the ABAP Test Cockpit \(ATC\).

To make the setup of Continuous Integration pipelines as easy as possible, the open source project "Piper" was created. In general, there are various functions \("Library steps"\), as well as whole pipelines, available to reuse. There, you can find various steps that implement the functionality of the APIs of SAP\_COM\_0510.

Additionally, there is an example pipeline for a Continuous Integration process that covers the following:

-   creating an SAP BTP, ABAP environmentsystem

-   setting up a communication arrangement for the APIs

-   importing a software component / Git repository

-   running ATC checks

-   deprovisioning the SAP BTP, ABAP environment system


Please find the documentation regarding project "Piper" here: [https://sap.github.io/jenkins-library/](https://sap.github.io/jenkins-library/).

-   **[API to Manage Git Repositories](API_to_Manage_Git_Repositories_c45f01f.md "")**  

-   **[Executing ABAP Test Cockpit \(ATC\) Check Runs](Executing_ABAP_Test_Cockpit_(ATC)_Check_Runs_d8cec78.md "")**  


