<!-- loio61159c4dc45b45619b46b4620615c357 -->

# Business Configuration Maintenance Object



<a name="loio61159c4dc45b45619b46b4620615c357__section_ugh_txt_4sb"/>

## Purpose

A business configuration maintenance object declares a service binding as relevant for business configuration. It will be shown on the list of all maintainable business configurations in the Fiori app [Custom Business Configurations App](../50-administration-and-ops/custom-business-configurations-app-76384d8.md). The business configuration maintenance object can be maintained via API or ADT. For more information, see also[Creating Business Configuration Apps with ABAP RESTful Application Programming Model and Custom Business Configurations App](https://help.sap.com/docs/btp/sap-business-technology-platform/creating-business-configuration-apps-with-abap-restful-application-programming-model-and-custom-business-configurations-app?version=Cloud).



<a name="loio61159c4dc45b45619b46b4620615c357__section_ndb_slr_xqb"/>

## Prerequisites

-   The service binding must be of type OData V4 - UI and exposing CDS root entity with draft enabled behavior definition.

-   The following two business object composition tree structures are supported:

    -   the height of the tree is less or equal than 2.

        Example: Root entity A has two child entities B and C. Entity C has one child entity D. D can't have further child entities

    -   the height of the tree is less equal than 3 and the option skip root entity list report is enabled. The root entity must be a singleton and have exactly one child entity.

        Example: Root entity S has one child entity A. Entity A has two child entities B and C. Entity C has one child entity D. D can't have further child entities.


-   The data model must consist only of client-dependent tables.




<a name="loio61159c4dc45b45619b46b4620615c357__section_ejg_zlr_xqb"/>

## Provide Authorizations for a Business Configuration

To grant frontend users the rights to use a business configuration maintenance object, first create an *Identity and Access Management \(IAM\) App* and assign it to an *IAM Business Catalog*. Follow [this user guide](https://help.sap.com/docs/btp/sap-abap-development-user-guide/consuming-services-in-ui?version=Cloud) but make sure to select the IAM app type *Business Configurations* app. In the service tab of the IAM app, select OData V4 as service type and the service binding name of the business configuration maintenance object as service name. In the authorizations tab maintain the authorization object used by the RAP BO for authorization control.

Once you have created the IAM business catalog, assign the catalog to a business role on the Fiori launchpad by following [this user guide](https://help.sap.com/docs/btp/sap-business-technology-platform/maintain-business-roles-new-preview?version=Cloud). Finally, follow [this user guide](https://help.sap.com/docs/btp/sap-business-technology-platform/maintain-business-users?version=Cloud) to assign the business role to business users to grant the rights to use your business configuration inside the *Custom Business Configurations* Fiori app.

**Related Information**  


[Creating a Business Configuration Maintenance Object in ADT](creating-a-business-configuration-maintenance-object-in-adt-1196530.md "Find out how to create a business configuration maintenance object using the ABAP Development Tools (ADT).")

[Business Configuration Maintenance Object Cloud Platform API](business-configuration-maintenance-object-cloud-platform-api-508d406.md "Use the ABAP API mbc_cp_api to create, update, delete, and read business configuration maintenance objects.")

[Generating a Business Configuration Maintenance Object with the Generate ABAP Repository Objects Wizard](generating-a-business-configuration-maintenance-object-with-the-generate-abap-repository-047e01c.md "You can create a business configuration maintenance object together with all related development objects on the basis of a database table by using the Generate ABAP Repository Objects Wizard.")

