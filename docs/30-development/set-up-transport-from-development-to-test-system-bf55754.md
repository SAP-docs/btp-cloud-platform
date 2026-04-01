<!-- loiobf557544f90f4bc88911c4865ec78207 -->

# Set Up Transport from Development to Test System

You can perform the import of your software components into a test system either manually by using the *Manage Software Components* app or in an automated way using the [ABAP Environment Pipeline](abap-environment-pipeline-2398b87.md).

**Manual Import into Test System**

As an add-on admin user, you can pull the latest released changes of a software component to the test system by using the main branch. You can test these changes in the test system independent from ongoing development. See [Pull Software Components](../50-administration-and-ops/pull-software-components-90b9b9d.md) and [ABAP Lifecycle Management](abap-lifecycle-management-5c7b17d.md).

**Automatic Import into Test System with ABAP Environment Pipeline**

> ### Tip:  
> For in-depth information about the ABAP environment pipeline used for automatic import into a test system, see [ABAP Environment Pipeline](abap-environment-pipeline-2398b87.md).

![](images/Pipeline_dev_to_test_8d52073.png)

As a DevOps engineer, you can configure the ABAP environment pipeline for an automated import of software components to test system TST. With the pipeline, the pulling of specified software components is automated and performed on a regular schedule.

The continuous testing scenario of the ABAP environment pipeline is described in detail in [Continuous Testing on SAP BTP ABAP Environment](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentTest/).

