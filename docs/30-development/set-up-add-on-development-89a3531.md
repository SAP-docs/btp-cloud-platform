<!-- loio89a353151e534380a03b2a572a227731 -->

# Set Up Add-On Development

Learn how to set up add-on development by creating and importing software components. Furthermore, read about configuring ABAP Test Cockpit checks and check variants, as well as enabling transport blocking to fix issues early on during development.

**Create and Import Software Components**

To transport new developments from system to system, the add-on development is structured by software components. Software components are independent development containers.

To create a new software component for add-on development, as an add-on admin user, use the *Manage Software Components* app and create a new component of type `Development`. The name of the software component begins with a namespace that was activated in the development system. By default, all namespaces of the global account owner are enabled in the systems. See [How to Create Software Components](https://help.sap.com/docs/btp/sap-business-technology-platform/how-to-create-software-components?version=Cloud&q=how%20to%20create%20software%20components).

Clone the main branch of the software component to the development and test system.

Software components in the development and test system should always stay on the main branch. If you want to work on maintenance branches to develop bug fixes and other maintenance deliveries, create a dedicated hotfix development and test system \(maintenance codeline\).

> ### Tip:  
> For in-depth information about versioning and branches, check out [Versioning and Branches](https://help.sap.com/docs/btp/sap-business-technology-platform/concepts?version=Cloud#versioning-and-branches). In case you are creating software components with dependencies to each other, make sure to declare these dependencies in software component relations. Refer to [Software Component Relations](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/software-component-relations).

**Configure ABAP Test Cockpit Checks, Check Variants**

By default, a check variant `ABAP_CLOUD_DEVELOPMENT_PARTNER` is generated in ABAP environment systems. You should use this variant for ABAP Test Cockpit check runs or create a custom check variant based on it. See [Creating ATC Check Variants](https://help.sap.com/docs/btp/sap-abap-development-user-guide/creating-atc-check-variants?version=Cloud). You can also create custom ABAP Test Cockpit checks. See [Creating ATC Checks](https://help.sap.com/docs/btp/sap-abap-development-user-guide/creating-atc-checks?version=Cloud).

Custom ABAP Test Cockpit checks and check variants are created as part of a software component, whereas the default check variant is generated locally.

> ### Note:  
> We recommend running ATC checks using at least those checks included in the `ABAP_CLOUD_DEVELOPMENT_PARTNER` check variant. Depending on your use case, it makes sense to add additional ATC checks to a custom check variant instead.

**Configure ABAP Test Cockpit to Interrupt Transport Releases**

We recommend enabling the blocking of transport releases in case of priority 1 \(error\) and priority 2 \(warning\) findings using the default check variant `ABAP_CLOUD_DEVELOPMENT_DEFAULT` or a custom check variant. You can enable transport blocking in the ABAP Test Cockpit Configurator app. See [ABAP Test Cockpit Configurator](https://help.sap.com/docs/btp/sap-business-technology-platform/abap-test-cockpit-configurator?version=Cloud&q=ABAP%20Test%20Cockpit%20Configurator.).

Interrupting a transport release in case of severe findings can help to fix issues early on during development. The later errors are detected in the development process, the more costly it is to resolve them. See [Launching ATC Check Implicitly](https://help.sap.com/docs/btp/sap-abap-development-user-guide/launching-atc-check-implicitly?version=Cloud).

