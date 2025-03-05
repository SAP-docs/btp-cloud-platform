<!-- loio023cf9d301b1479484e70b17cd5cf587 -->

# Test



Once development has been completed, you can test the solution in the test subaccount that you have previously set up. The software components that make up the solution are imported into a provisioned test system, while any additionally required configuration has to be carried out by you. This may entail creating suitable business roles, maintaining communication arrangements, or other administrative tasks performed via the SAP Fiori launchpad of your ABAP system.

You can also use a CI/CD server and a Jenkins pipeline to automate the test process. This allows you to schedule regular tests and to be notified as soon as issues arise within the solution.

If the solution is successfully tested and works correctly, you can proceed with the add-on build.



<a name="loio023cf9d301b1479484e70b17cd5cf587__section_t5k_vt4_drb"/>

## Prerequisites

-   For testing in SAP Fiori launchpad in your ABAP environment, you need a business user in the test system that has the required authorizations to use the *Manage Software Components* app as well as authorizations that are required as a test user.
-   For testing in the ABAP Test Cockpit, you need a developer user using ABAP Development Tools. See [Getting Started as a Developer in the ABAP Environment](../20-getting-started/getting-started-as-a-developer-in-the-abap-environment-4b896c9.md).
-   \(Optional\) For running ATC checks as part of the ABAP environment pipeline, you have to create a pipeline in a Jenkins CI/CD server that is provisioned using the Cx Server tool. See [Jenkins](https://www.jenkins.io/) and [Cx Server](https://www.project-piper.io/infrastructure/overview/#cx-server-recommended).

<a name="loio8c5b4d76a05b4bed8df01937f4d8d487"/>

<!-- loio8c5b4d76a05b4bed8df01937f4d8d487 -->

## Test in the ABAP Environment SAP Fiori Launchpad

**Import Software Components**

Before testing new developments in a software component in the test system, as an add-on admin, you have to import the latest changes from the remote repository. After you have cloned a software component into the test system TST, you can import the latest changes by pulling the software component in the *Manage Software Components* app. See [Pull Software Components](../50-administration-and-ops/pull-software-components-90b9b9d.md).

**Create and Assign Business Roles**

Before creating and assigning business roles, you have to make sure that business users are already available. They can be created manually or automatically. See [User Provisioning](user-provisioning-ef52a68.md).

To test the developed business services, as a test user, create business roles from the role templates in the test system and assign them to your user. See [Maintain Business Roles](../50-administration-and-ops/maintain-business-roles-8980ad0.md).

**Create Launchpad Space and Pages for Business Roles**

To enable navigation to custom UIs via tiles, enable launchpad spaces and pages. Add spaces to the relevant business roles and add the needed SAP Fiori launchpad tiles to those spaces. Finally, enable spaces for business users in the system launchpad settings. See [How to Create Spaces and Pages for a Business Role](../50-administration-and-ops/how-to-create-spaces-and-pages-for-a-business-role-18cdb97.md).

**Create Communication Arrangements**

To test inbound and outbound communication, create communication arrangements in the test system TST based on the implemented communication scenarios. See [How to Create a Communication Arrangement](../50-administration-and-ops/how-to-create-a-communication-arrangement-a0771f6.md).

> ### Note:  
> Depending on whether you want to use an authentication method for outbound communication that requires a business user context \(Oauth2 SAML Bearer Assertion, Oauth2 User Token Exchange, JWT Principal Propagation\), you need to configure a destination in a communication arrangement instead of maintaining credentials by using an outbound communication user. See [Supported Protocols and Authentication Methods](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/supported-protocols-and-authentication-methods) and [Creating a Destination](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/creating-destination).

You can integrate the test system TST with on-premise systems. See [Integrating On-Premise Systems](integrating-on-premise-systems-c95327f.md).

In the subaccount of test system TST, the subaccount for testing, you can assign the Cloud Connector administrator role collection to the Cloud Connector administrator user to operate the data transmission tunnels used by the Cloud Connector.

**Create Business Configuration**

As a test user, you can adjust business configuration objects in the *Maintain Business Configurations* app to change and influence the system behavior. See [Custom Business Configurations App](../50-administration-and-ops/custom-business-configurations-app-76384d8.md).



**Configure Key User Extensibility**

Key user extensibility that is enabled in the SaaS solution can be configured and consumed in test systems.

> ### Note:  
> Key user extensibility provided in a SaaS solution can only be configured in tenants of particular types, for testing purposes in tenants of type Test Tenant.
> 
> These tenant types are provisioned in non-development systems, such as test system TST or quality assurance system QAS, where development is not allowed \(`is_development_allowed = false`\). The tenants are created independently from a subscription to the SaaS solution by using the *Landscape Portal* application. See [Manage Test Tenants](https://help.sap.com/docs/help/d91c4152c3d74c12bc9bd4ed92681902/acc85d68b6da441fa6349af3ae4e4bb4.html).

As a test user in a Test Tenant \(client \>= 200\), you configure key user extensibility in a test system.

-   See [Custom Logic \(Deprecated\)](../50-administration-and-ops/custom-logic-deprecated-05880c7.md) for guidance on how to use the *Custom Logic* app to create and maintain custom logic for business add-ins \(BAdIs\).
-   See [Configuring Predefined Custom Fields](../50-administration-and-ops/configuring-predefined-custom-fields-0033cbc.md) for guidance on how to configure predefined custom fields to customize applications and their UIs.

<a name="loiof0b71a1c959842258772c27d292c43b0"/>

<!-- loiof0b71a1c959842258772c27d292c43b0 -->

## Test in the ABAP Test Cockpit

With the ABAP Test Cockpit, you can run a set of checks \(check variants\) on software component or package level. See [Checking Quality of ABAP Code with ATC](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/4ec5711c6e391014adc9fffe4e204223.html) and [ABAP Test Cockpit in the Cloud – What is already possible](https://blogs.sap.com/2020/08/14/abap-test-cockpit-in-the-cloud-what-is-already-possible/).

To fix and revalidate ABAP Test Cockpit findings, as a developer user, you can run ABAP Test Cockpit checks on developed software components explicitly via ABAP Development Tools in the DEV system. See [Launching ATC Check Run from the Project Explorer](https://help.sap.com/docs/btp/sap-abap-development-user-guide/launching-atc-check-run-from-project-explorer?version=Cloud) and [Launching ATC Check Run Explicitly](https://help.sap.com/docs/btp/sap-abap-development-user-guide/launching-atc-check-run-explicitly?version=Cloud).

If transport blocking in case of ABAP Test Cockpit findings is configured \(see [Set Up Add-On Development](https://help.sap.com/docs/btp/sap-business-technology-platform/prepare?version=Cloud#set-up-add-on-development)\), ABAP Test Cockpit checks are executed implicitly. See [Launching ATC Check Implicitly](https://help.sap.com/docs/btp/sap-abap-development-user-guide/launching-atc-check-implicitly?version=Cloud).

**ATC Exemptions**

If you can't clear an ABAP Test Cockpit finding by correcting the underlying problem, you can still clear it by requesting an exemption. Exemptions are created as part of a specific software component. See [Working with ATC Exemptions](https://help.sap.com/docs/btp/sap-abap-development-user-guide/working-with-atc-exemptions?version=Cloud).

**Continuous Testing using ABAP Environment Pipeline**

> ### Tip:  
> For in-depth information about the ABAP environment pipeline used for continuous testing, see [ABAP Environment Pipeline](concepts-9482e7e.md#loio2398b874f7c5445db188b780ff0cef89).

![](images/Pipeline_dev_to_test_8d52073.png)

To schedule a regular execution of ABAP Test Cockpit checks for a software component in the test system, you can use a CI server and pipeline to automate this process. You can reuse the previously described setup of a transport from development to test system using the ABAP environment pipeline. See [Set Up Transport from Development to Test System](https://help.sap.com/docs/btp/sap-business-technology-platform/prepare?version=Cloud#set-up-transport-from-development-to-test-system).

As a DevOps engineer, configure the ABAP environment pipeline by using a static and preconfigured system. With the pipeline, the following steps are then automated, triggered by the pipeline execution of a Jenkins administrator:

-   Pulling the specified software components/Git repositories
-   Running the configured ABAP Test Cockpit checks

The continuous testing scenario of the ABAP environment pipeline is described in detail in [Continuous Testing on SAP BTP ABAP Environment](https://sap.github.io/jenkins-library/scenarios/abapEnvironmentTest/).

