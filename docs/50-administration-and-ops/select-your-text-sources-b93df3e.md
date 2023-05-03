<!-- loiob93df3e5e48848688d3b82369fa53937 -->

# Select Your Text Sources



<a name="loiob93df3e5e48848688d3b82369fa53937__section_w21_qmk_m3b"/>

## Context

Select the text sources that you want to have translated.



<a name="loiob93df3e5e48848688d3b82369fa53937__section_ptf_2sq_hpb"/>

## Procedure

1.  In the *Maintain Translations*app, open the project you want to add text sources to.
2.  Scroll down to *Text Sources* and click *Add*.
3.  Here you can select which text source types to add. The following text source types are supported:

    -   Domains

    -   Data Elements

    -   Data Definitions \(View Entities, Projection Views, Abstract Entities and Custom Entities\)

    -   Message Classes

    -   Metadata Extensions

    -   Application Log Objects

    -   Business Configuration Objects

    -   Text Pools

    -   Text Tables

    -   IAM Business Catalogs

    -   CDS Type Definitions


    It’s also possible to specify a package from which all supported translatable elements will be pulled into the translation project. Please note that translatable elements in sub packages are not included.

4.  Select *Add* to open the *Add Text Source* dialog which displays all text sources that can be added to the translation project. By filtering the type and name, you can choose the text sources you want to add. Select *Add* to add the text sources you selected to your translation project.

    > ### Note:  
    > Text sources that can be translated by a translation project need to reside in the same software component as the translation project.

    > ### Note:  
    > -   If you want to test the translated texts of IAM business catalogs directly in the Fiori launchpad of the development system, you have to publish the IAM business catalog once again locally in ADT.
    > 
    > -   If you want to test the translated texts of data definitions or metadata extensions directly in the development system with a Fiori app built on top of these objects, you should first reactivate the objects in ADT to ensure that all caches will be invalidated.




> ### Note:  
> **Text Tables**
> 
> Text tables are database tables that were created as part of a business object and in which language-dependent texts are stored.
> 
> A database table needs to fulfill the following requirements to be considered a text table by the *Maintain Translations* app:
> 
> -   The database table has exactly one key field of ABAP Dictionary Built-in Type LANG.
> 
> -   The database table is of delivery class C or S.
> 
> -   The database table is located in the same software component as the translation project.
> 
> 
> If these requirements are fulfilled, the database table can be added to a translation project as a text table. Additionally, the following rules apply:
> 
> -   Every non-key field of the text table that is of an ABAP Dictionary Build-in type that is character-like and has a minimum length of 1 will be interpreted as a text attribute for which translations can be maintained.
> 
> -   When the translations are published, the rows containing the texts in the target language will be added to the selected transport via R3TR TABU.
> 
> 
> In this tutorial \([Create an SAP Fiori-based Table Maintenance App with SAP BTP, ABAP Environment](https://developers.sap.com/group.abap-env-factory.html)\) on how to create a business configuration application to maintain error code definitions, for instance, the language-dependent texts for the respective error code definitions are stored as entries in the database table `ZERROR_CODE_T###` with `###` being replaced by a number chosen by the developer, such as `000`. The non-key field for which translations can be maintained is field `DESCRIPTION`.

> ### Note:  
> Please note that the translation of text table entries is only available in environments that support transporting client-specific data.

**Related Information**  


[Select Your Source and Target Language](select-your-source-and-target-language-85823ef.md)

