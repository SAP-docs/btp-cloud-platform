<!-- loiof0b71a1c959842258772c27d292c43b0 -->

# Test in the ABAP Test Cockpit





### Manual Testing During Development

With the ABAP Test Cockpit, you can run a set of checks \(check variants\) on software component or package level. See [Checking Quality of ABAP Code with ATC](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/4ec5711c6e391014adc9fffe4e204223.html) and [ABAP Test Cockpit in the Cloud – What is already possible](https://blogs.sap.com/2020/08/14/abap-test-cockpit-in-the-cloud-what-is-already-possible/).

To fix and revalidate ABAP Test Cockpit findings, as a developer user, you can run ABAP Test Cockpit checks on developed software components explicitly via ABAP Development Tools in the DEV system. See [Launching ATC Check Run from the Project Explorer](https://help.sap.com/docs/btp/sap-abap-development-user-guide/launching-atc-check-run-from-project-explorer?version=Cloud) and [Launching ATC Check Run Explicitly](https://help.sap.com/docs/btp/sap-abap-development-user-guide/launching-atc-check-run-explicitly?version=Cloud).

If transport blocking in case of ABAP Test Cockpit findings is configured \(see [Set Up Add-On Development](https://help.sap.com/docs/btp/sap-business-technology-platform/prepare?version=Cloud#set-up-add-on-development)\), ABAP Test Cockpit checks are executed implicitly. See [Launching ATC Check Implicitly](https://help.sap.com/docs/btp/sap-abap-development-user-guide/launching-atc-check-implicitly?version=Cloud).



### Continuous Testing Using ABAp Environment Pipeline

> ### Tip:  
> For in-depth information about the ABAP environment pipeline used for continuous testing, see [ABAP Environment Pipeline](abap-environment-pipeline-2398b87.md).

![](images/Pipeline_dev_to_test_8d52073.png)

To schedule a regular execution of ABAP Test Cockpit checks for a software component in the test system, you can use a CI server and pipeline to automate this process. You can reuse the previously described setup of a transport from development to test system using the ABAP environment pipeline. See [Set Up Transport from Development to Test System](https://help.sap.com/docs/btp/sap-business-technology-platform/prepare?version=Cloud#set-up-transport-from-development-to-test-system).

As a DevOps engineer, configure the ABAP environment pipeline by using a static and preconfigured system. With the pipeline, the following steps are then automated, triggered by the pipeline execution of a Jenkins administrator:

-   Pulling the specified software components/Git repositories
-   Running the configured ABAP Test Cockpit checks

The continuous testing scenario of the ABAP environment pipeline is described in detail in [Continuous Testing on SAP BTP ABAP Environment](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentTest/).

