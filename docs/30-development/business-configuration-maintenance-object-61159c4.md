<!-- loio61159c4dc45b45619b46b4620615c357 -->

# Business Configuration Maintenance Object

The business configuration maintenance object can be maintained via API or ADT. You can find more information on how to work with the business configuration maintenance object via ADT, in the *ABAP Development User Guide*.



<a name="loio61159c4dc45b45619b46b4620615c357__section_ndb_slr_xqb"/>

## Prerequisites

You have created a business configuration by following [this tutorial](https://developers.sap.com/mission.abap-dev-factory-calendar.html). Please note that only one level of sub nodes is supported. This means that your root entity can have associations to an arbitrary amount of entities, but these sub entities can't have associations to further sub entities. The data model must consist only of client-dependent tables.



<a name="loio61159c4dc45b45619b46b4620615c357__section_ejg_zlr_xqb"/>

## Provide Authorizations for a Business Configuration

To grant frontend users the rights to use a business configuration, first create an *Identity and Access Management \(IAM\) App* and assign it to an *IAM Business Catalog*. Follow [this user guide](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/032faaf4f9184484ba9295c81756e831.html) but make sure to select the IAM App Type *Business Configuration App*.

Once you have created the IAM Business Catalog, assign the catalog to a business role on the Fiori Launchpad by following [this user guide](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/8980ad05330b4585ab96a8e09cef4688.html). Finally, follow [this user guide](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/e40e710321c74f28916affa9ae984bce.html) to assign the business role to business users to grant the rights to use your business configuration inside the *Maintain Business Configurations* Fiori app.

**Related Information**  


[Working with Business Configuration Maintenance Objects](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/latest/en-US/e570fee3db344358926ad11ba3b3a531.html)

