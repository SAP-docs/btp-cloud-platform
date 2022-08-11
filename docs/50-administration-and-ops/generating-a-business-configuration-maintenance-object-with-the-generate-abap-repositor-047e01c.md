<!-- loio047e01c3bcdd4303a60b61364bd5b31d -->

# Generating a Business Configuration Maintenance Object with the Generate ABAP Repository Objects Wizard

You can create a business configuration maintenance object together with all related development objects on the basis of a database table by using the *Generate ABAP Repository Objects Wizard*.



<a name="loio047e01c3bcdd4303a60b61364bd5b31d__section_ymn_sbj_zsb"/>

## Context

Creating a Fiori app to maintain customizing tables involves many different objects that need to be created manually. On the basis of a database table, this wizard creates all the development objects that are required so that the table content, and optionally, text table content, can be maintained with the *Custom Business Configurations* app. For more information, see [Custom Business Configurations App](custom-business-configurations-app-76384d8.md). A tutorial on how to use this wizard and the *Custom Business Configurations* app is available here: [Factory Calendar](https://developers.sap.com/mission.abap-dev-factory-calendar.html).



<a name="loio047e01c3bcdd4303a60b61364bd5b31d__section_cqv_dcj_zsb"/>

## Prerequisites

The basis database table should fulfil the following requirements:

-   have a client key field

-   have delivery class C

-   allow data maintenance

-   have a timestamp field with data element `ABP_LASTCHANGE_TSTMPL`. For more information, see [RAP Reuse Data Elements](https://help.sap.com/viewer/e5522a8a7b174979913c99268bc03f1a/latest/en-US/84bd58e2b9354be4a7a1c91cb687815c.html)

-   have a timestamp field with data element `ABP_LOCINST_LASTCHANGE_TSTMPL`


An additional database table is considered as the text table by the wizard if the annotation `@AbapCatalog.foreignKey.keyType : #TEXT_KEY` is used.

The text table should fulfil the following requirements:

-   have a client key field

-   have delivery class C

-   allow data maintenance

-   have a timestamp field with data element `ABP_LOCINST_LASTCHANGE_TSTMPL`

-   have a language key field with type `LANG`

-   have a foreign key of type `#TEXT_KEY` that matches the basis table primary key \(except the language field\)


The software component of the target package must be changeable.



<a name="loio047e01c3bcdd4303a60b61364bd5b31d__section_isn_3dj_zsb"/>

## Procedure

The wizard can't overwrite existing objects or create only a subset of the objects. The generated objects will have the same ABAP language version as the target package. In the *Configure Generator* page you can define the names and options for the generated objects. The wizard fills all required fields as a proposal based on the description of the basis table.



### Scenario Options

In *Transport Selection*, select *Manual* to include the action *Select Transport* in the generated app. With this action, you can select an existing customizing transport request before saving the configuration changes.



### Data Model

To enable mass editing and manual transport selection, a singleton root entity must be part of the generated data model. For more information, see [here](https://help.sap.com/viewer/923180ddb98240829d935862025004d6/latest/en-US/f713ec52bcb8405ca9262918cffa5d25.html).



### Behavior Implementation

The generated RAP business object has the following properties:

-   draft enabled, managed

-   authorization control based on authorization object `S_TABU_NAM` and the CDS view entity name of the basis table

-   concurrency control based on the table timestamp fields

-   integration of the BC transport API to validate and record changes on a customizing transport request

-   internal numbering is used for key fields with `ABAP` type `raw(16) (UUID)`


