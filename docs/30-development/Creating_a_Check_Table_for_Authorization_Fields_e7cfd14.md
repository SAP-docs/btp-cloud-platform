<!-- loioe7cfd14ae7d442d6ae553867ba7acd37 -->

# Creating a Check Table for Authorization Fields

Create a check table that you can provide to the administrator as value help during business role maintenance.



## Context

The advantage of having a check table is that the administrator has a value help when maintaining business roles with restricted access. As a developer, you provide access to a table where the field values are stored. When administrators create business roles and assign them to business users, they can call up the check table in the format of a value help and select the relevant values from the table.

In the bonus calculation example, the check table contains the bonus variants.



## Procedure

1.  In ABAP Development Tools, in the project explorer, right-click on the relevant package node.

2.  In the context menu, choose *New* \> *Other ABAP Repository Object*.

3.  In the following popup, choose *Core Data Services* \> *Data Definition* and *Next*.

4.  Enter a name, description, and, as referenced object, enter the table where the values are stored that you want to provide for the administrator. In the bonus calculation example, this table is the table where the bonus variants are stored for the app. Choose *Next*.

5.  Select a transport request and choose *Next*.

6.  From the list of templates, choose *Define View* and choose *Finish*.

7.  In the coding, choose the fields that you need to expose.

    For the CDS view, it's sufficient that you use only those fields that are needed for a field help.

8.  To provide some UI texts for the field help, add `@EndUserText.label` with a good label for each field that is exposed as part of the CDS view. The labels will be displayed as column headings in the field help of the business role maintenance.

9.  Make sure that the annotation `@AbapCatalog.sqlViewName` is added at the beginning of the CDS view code.

    For example, the code of such a CDS view can look as follows:

    > ### Sample Code:  
    > ```
    > @AbapCatalog.sqlViewName: 'ZVARCHECK'
    > @AbapCatalog.compiler.compareFilter: true
    > @AbapCatalog.preserveKey: true
    > @AccessControl.authorizationCheck: #CHECK
    > @EndUserText.label: 'Check Table for bonus variants'
    > define view Z_VARIANTS_CHECK_TABLE as select from zbonusvar {
    > 
    >   @EndUserText.label: 'Bonus Variant'
    >   key variant as BonusVariant,
    >   
    >   @EndUserText.label: 'Category'
    >   category as Category,
    >   
    >   @EndUserText.label: 'Description'
    >   description as Description,
    >   
    >   @EndUserText.label: 'Created By'
    >   createdby as Createdby,
    >   
    >   @EndUserText.label: 'Created At'
    >   createdat as Createdat
    > 
    > }
    > ```

10. Copy the SQL view name from `@AbapCatalog.sqlViewName` for later use \(see [Defining an Authorization Field](Defining_an_Authorization_Field_a151c75.md)\).


