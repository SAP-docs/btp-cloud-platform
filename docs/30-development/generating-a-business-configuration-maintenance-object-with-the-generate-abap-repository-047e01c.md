<!-- loio047e01c3bcdd4303a60b61364bd5b31d -->

# Generating a Business Configuration Maintenance Object with the Generate ABAP Repository Objects Wizard

You can create a business configuration maintenance object together with all related development objects on the basis of a database table by using the *Generate ABAP Repository Objects Wizard*.



<a name="loio047e01c3bcdd4303a60b61364bd5b31d__section_ymn_sbj_zsb"/>

## Context

Creating a Fiori app to maintain customizing tables involves many different objects that need to be created manually. On the basis of a database table, this wizard creates all the development objects that are required so that the table content, and optionally, text table content, can be maintained with the *Custom Business Configurations* app. If required, you can then, for example, add further functions or enhance the generated business object structure.

For more information, see [Creating Business Configuration Apps with ABAP RESTful Application Programming Model and Custom Business Configurations App](creating-business-configuration-apps-with-abap-restful-application-programming-model-and-fa420dd.md). A tutorial on how to use this wizard and the *Custom Business Configurations* app is available here: [Factory Calendar](https://developers.sap.com/group.abap-env-factory.html).



<a name="loio047e01c3bcdd4303a60b61364bd5b31d__section_cqv_dcj_zsb"/>

## Prerequisites

The basis database table must fulfil the following requirements:

-   have a client key field

-   have delivery class C

-   allow data maintenance

-   have a timestamp field with data element `ABP_LASTCHANGE_TSTMPL`. For more information, see [RAP Reuse Data Elements](https://help.sap.com/viewer/e5522a8a7b174979913c99268bc03f1a/latest/en-US/84bd58e2b9354be4a7a1c91cb687815c.html)

-   have a timestamp field with data element `ABP_LOCINST_LASTCHANGE_TSTMPL`


An additional database table is considered as the text table by the wizard if the annotation `@AbapCatalog.foreignKey.keyType : #TEXT_KEY` is used.

The text table must fulfil the following requirements:

-   have a client key field

-   have delivery class C

-   allow data maintenance

-   have a timestamp field with data element `ABP_LOCINST_LASTCHANGE_TSTMPL`

-   have a language key field with type `LANG`

-   have a foreign key of type `#TEXT_KEY` that matches the basis table primary key \(except the language field\)


The software component of the target package must be changeable.



<a name="loio047e01c3bcdd4303a60b61364bd5b31d__section_isn_3dj_zsb"/>

## Procedure

The wizard can't overwrite existing objects or create only a subset of the objects. The generated objects will have the same ABAP language version as the target package.

1.  In your ABAP project, open the context menu fpr a database table and choose *Generate ABAP Repository Objects*.

2.  Enter the description and select *Business Configuration Maintenance Object* as the *Generator*. Once done select *Next*.

3.  In the *Configure Generator* page you can define the names and options for the generated objects. The wizard fills all required fields as a proposal based on the description of the basis table. Select *Next.*

4.  In the *Preview Generator Output* page, a preview list is available with the objects to be generated. Choose *Next*.

5.  Assign a transport request.

6.  Choose *Finish* to start the generation of the objects.

7.  After the generation process is complete, the generated *Business Configuration Maintenance Object* is shown.




### Behavior Implementation

The generated RAP business object has the following properties:

-   draft enabled, managed

-   authorization control based on authorization object `S_TABU_NAM` and the CDS view entity name of the basis table

-   concurrency control based on the table timestamp fields

-   integration of the BC transport API to validate and record changes on a customizing transport request

-   To enable mass editing and manual transport selection, a singleton root entity is part of the generated data model. For more information, see [here](https://help.sap.com/docs/BTP/923180ddb98240829d935862025004d6/f713ec52bcb8405ca9262918cffa5d25.html?version=latest).

-   internal numbering is used for key fields with `ABAP` type `raw(16) (UUID)`




<a name="loio047e01c3bcdd4303a60b61364bd5b31d__section_n5h_fmc_55b"/>

## Scenario Options



### Add Copy Action

Select this to include a *Copy* action in the generated app. With this factory action a copy of the selected entry will be created.



### Add Deprecate Actions

Select to include a Deprecate and Invalidate action in the generated app. The basis table must have a field `CONFIGDEPRECATIONCODE` with the data element `CONFIG_DEPRECATION_CODE`. With this action a selected entry can be deprecated or invalidated. If a foreign key check is executed on a deprecated or invalidated check table entry, the check returns a warning \(deprecated\) or error \(invalidated\). If this option is selected, the *Delete* action is set as internal.



### Add Data Consistency Check

Select this option to include a *Validation* for the *Prepare* draft action in the generated app, which checks the consistency of field inputs with:

-   domains with fixed values

-   foreign keys where `@AbapCatalog.foreignKey.screenCheck : true`




### Copy Parameter Entity

If the option *Add Copy Action* is selected, an abstract entity for the user input is generated. Provide a name for the abstract entity. This is not necessary if all key fields except the client field of the basis table have type `ABAP type raw(16)`.



### Transport Selection

Select *Manual* to include the action *Select Transport* in the generated app. With this action, you can select an existing customizing transport request before saving the configuration changes.

