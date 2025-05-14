<!-- loioafbcbba49abe47969a9f2753f0f18247 -->

# Assembling a Software Package



<a name="loioafbcbba49abe47969a9f2753f0f18247__prereq_ksl_h54_qmb"/>

## Prerequisites

-   You have fulfilled all prerequisites mentioned in

    [Build and Publish Add-on Products on SAP Cloud Platform ABAP Environment](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentAddons)

-   Ideally, you have set up and configured a pipeline with stages and steps as recommended in [ABAP Environment Pipeline](https://sap.github.io/jenkins-library/pipelines/abapEnvironment/introduction/), and [Configuration](https://sap.github.io/jenkins-library/pipelines/abapEnvironment/configuration/).


In doing so, the following activities are performed automatically:

-   You have an ABAP environment system.

-   You’ve created a *Communication User* as described in [How to Create Communication Users](../50-administration-and-ops/how-to-create-communication-users-0377ade.md).

-   You’ve created a *Communication System* as described in [How to Create Communication Systems](https://help.sap.com/docs/SAP_S4HANA_CLOUD/0f69f8fb28ac4bf48d2b57b9637e81fa/1bfe32ae08074b7186e375ab425fb114.html).
-   You’ve created a *Communication Arrangement* as described in [How to Create a Communication Arrangement](../50-administration-and-ops/how-to-create-a-communication-arrangement-a0771f6.md).

-   You have selected the communication scenario*SAP\_COM\_0582* for your communication arrangement and have mapped it to your communication system.
-   You have pulled a repository to the SAP Cloud Platform ABAP Environment system using communication scenario *SAP\_COM\_0948*.

-   You have provided information on build essentials in an addon.yml file which has already been validated by the Add-On Assembly Kit as a Service \(AAKaaS\).




<a name="loioafbcbba49abe47969a9f2753f0f18247__steps_psn_kcr_4nb"/>

## Procedure

1.  During the build pipeline run, the step **abapEnvironmentAssemblePackages** is executed \(see [abapEnvironmentAssemblePackages](https://sap.github.io/jenkins-library/steps/abapEnvironmentAssemblePackages/)\). This step runs the assembly of a list of provided installations, support packages or patches in an SAP Cloud Platform ABAP Environment system and saves the corresponding SAR archive to the pipeline.

2.  An example for the configuration in config.yml as well as input arguments and values can be found here: [Examples](https://sap.github.io/jenkins-library/steps/abapEnvironmentAssemblePackages/#examples).


