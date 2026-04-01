<!-- loio023cf9d301b1479484e70b17cd5cf587 -->

# Test



Once development has been completed, you can test the solution in the test subaccount that you have previously set up. The software components that make up the solution are imported into a provisioned test system, while any additionally required configuration has to be carried out by you. This may entail creating suitable business roles, maintaining communication arrangements, or other administrative tasks performed via the SAP Fiori launchpad of your ABAP system.

You can also use a CI/CD server and a Jenkins pipeline to automate the test process. This allows you to schedule regular tests and to be notified as soon as issues arise within the solution.

If the solution is successfully tested and works correctly, you can proceed with the add-on build.



<a name="loio023cf9d301b1479484e70b17cd5cf587__section_t5k_vt4_drb"/>

## Prerequisites

-   For testing in SAP Fiori launchpad in your ABAP environment, you need a business user in the test system that has the required authorizations to use the *Manage Software Components* app as well as authorizations that are required as a test user.
-   For testing in the ABAP Test Cockpit, you need a developer user using ABAP Development Tools. See [Getting Started as a Developer in the ABAP Environment](../20-getting-started/getting-started-as-a-developer-in-the-abap-environment-4b896c9.md).
-   \(Optional\) For running ATC checks as part of the ABAP environment pipeline, you have to create a pipeline in a Jenkins CI/CD server. See [Jenkins](https://www.jenkins.io/) and [Custom Jenkins Setup](https://www.project-piper.io/infrastructure/customjenkins/).

