<!-- loio61159c4dc45b45619b46b4620615c357 -->

# Business Configuration Maintenance Object



<a name="loio61159c4dc45b45619b46b4620615c357__section_ugh_txt_4sb"/>

## Purpose

A business configuration maintenance object declares a service binding as relevant for business configuration. It will be shown on the list of all maintainable business configurations in the Fiori app . The business configuration maintenance object can be maintained via API or ADT.



<a name="loio61159c4dc45b45619b46b4620615c357__section_ndb_slr_xqb"/>

## Prerequisites

-   You have created a service binding that is used to maintain the business configuration data by following [this tutorial](https://developers.sap.com/mission.abap-dev-factory-calendar.html).

-   The service binding must be of type OData V4 - UI and exposing CDS root entity with draft enabled behavior definition.

-   The following two business object structures are supported:

    -   all child entities of the root entity must be leaf entities.
    -   when the option skip root entity list report is enabled, the root entity must have exactly one child entity. All child entities of the latter must be leaf entities.

-   The data model must consist only of client-dependent tables.




<a name="loio61159c4dc45b45619b46b4620615c357__section_ejg_zlr_xqb"/>

## Provide Authorizations for a Business Configuration

To grant frontend users the rights to use a business configuration, first create an *Identity and Access Management \(IAM\) App* and assign it to an *IAM Business Catalog*. Follow [this user guide](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/032faaf4f9184484ba9295c81756e831.html) but make sure to select the IAM App Type *Business Configuration App*.

Once you have created the IAM Business Catalog, assign the catalog to a business role on the Fiori Launchpad by following [this user guide](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/8980ad05330b4585ab96a8e09cef4688.html). Finally, follow [this user guide](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/e40e710321c74f28916affa9ae984bce.html) to assign the business role to business users to grant the rights to use your business configuration inside the *Maintain Business Configurations* Fiori app.

**Related Information**  


[Creating a Business Configuration Maintenance Object in ADT](creating-a-business-configuration-maintenance-object-in-adt-1196530.md "Find out how to create a business configuration maintenance object using the ABAP Development Tools (ADT).")

[Business Configuration Maintenance Object Cloud Platform API](business-configuration-maintenance-object-cloud-platform-api-508d406.md "Use the ABAP API mbc_cp_api to create, update, delete, and read business configuration maintenance objects.")

[Generating a Business Configuration Maintenance Object with the Generate ABAP Repository Objects Wizard](../50-administration-and-ops/generating-a-business-configuration-maintenance-object-with-the-generate-abap-repositor-047e01c.md "You can create a business configuration maintenance object together with all related development objects on the basis of a database table by using the Generate ABAP Repository Objects Wizard.")

