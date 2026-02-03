<!-- loiofa420dd6272b41858a7b31f8dc5090f8 -->

# Creating Business Configuration Apps with ABAP RESTful Application Programming Model and Custom Business Configurations App

As an ABAP Developer you can leverage the *ABAP RESTful Application Programming Model* \(RAP\) and the *Custom Business Configurations* \(CUBCO\) app to create a SAP Fiori UI to maintain customizing table data. You don’t need to create your own Fiori app. Everything can be implemented with ABAP repository objects.

For more information, see this [tutorial](https://developers.sap.com/group.abap-env-factory.html).

![](images/4b00a83e7bb84eb89e11277139af3ac3.image)

The development of a business configuration maintenance Fiori UI requires developers to perform the following fundamental activities:



<a name="loiofa420dd6272b41858a7b31f8dc5090f8__section_uhj_sjk_s5b"/>

## 1. Developing Business Object

Based on the customizing tables you define a data model and business object structure. Check the prerequisites of the business configuration maintenance object to see which kind of business object is supported. Using model-driven development approach, you develop actions, validations, and determinations for the entities of the business object to change, maintain and validate configuration entries.

You have the option to use the [Generate ABAP Repository Objects Wizard](generating-a-business-configuration-maintenance-object-with-the-generate-abap-repository-047e01c.md) to generate all required development objects based on a customizng table. If required, you can then add further functions or enhance the generated business object structure.

For more information, see [Developing a Ready-to-Run Business Object](https://help.sap.com/docs/abap-cloud/abap-rap/developing-ready-to-run-business-object?version=s4hana_cloud) and [Developing Business Logic](https://help.sap.com/docs/abap-cloud/abap-rap/developing-business-logic?version=s4hana_cloud).



<a name="loiofa420dd6272b41858a7b31f8dc5090f8__section_r5n_1nk_s5b"/>

## 2. Developing Business Service

Define the scope by exposing the entities of the business object in a service definition and bind the service to OData V4 UI protocol with a service binding. For more information on this, see [Working with Business Services](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/working-with-business-services?version=s4hana_cloud).



<a name="loiofa420dd6272b41858a7b31f8dc5090f8__section_fbx_gnk_s5b"/>

## 3. Developing Business Configuration Maintenance Object

Declare the service binding as relevant for business configuration by creating a [Business Configuration Maintenance Object](business-configuration-maintenance-object-61159c4.md).



<a name="loiofa420dd6272b41858a7b31f8dc5090f8__section_jf3_lnk_s5b"/>

## 4. Custom Business Configurations App

Based on the Business configuration maintenance object, the custom business configurations app renders a [Fiori Elements List Report Floorplan](https://experience.sap.com/fiori-design-web/list-report-floorplan-sap-fiori-element/) for the entities exposed by the service binding to maintain the configuration entries. For more information, see [Custom Business Configurations App](../50-administration-and-ops/custom-business-configurations-app-76384d8.md).

