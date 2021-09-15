<!-- loiob93df3e5e48848688d3b82369fa53937 -->

# Select Your Text Sources



<a name="loiob93df3e5e48848688d3b82369fa53937__section_w21_qmk_m3b"/>

## Context

Select the text sources that you want to have translated.



<a name="loiob93df3e5e48848688d3b82369fa53937__section_ptf_2sq_hpb"/>

## Procedure

1.  In the *Maintain Translations*app, open the project you want to add text sources to.
2.  Scroll down to *Text Sources* and click *Add*.
3.  Here you can select which objects to add. There are eight objects that are supported: Data definitions, data elements, domains, message classes, text tables \(see below\), metadata extensions, application log objects and business configuration objects. It’s also possible to specify a package from which all supported translatable elements will be pulled into the translation project. Please note that translatable elements in sub packages are not included.
4.  Once you select your *Type*, you can either enter a *Name* or open the value help to see a list of available objects and select one. Click *Add* to add your object.

    > ### Note:  
    > Objects that can be translated by a translation project need to reside in the same software component as the translation project.

5.  Repeat this step until you have added all objects you want to translate.



> ### Note:  
> **Text Tables**
> 
> Text tables are database tables that were created as part of a busines object and in which language-dependent texts are stored.
> 
> A database table needs to fulfil the following requirements to be considered a text table by the*Maintain Translations* app:
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
> In this tutorial \([Create Business Configuration for Factory Calendar](https://developers.sap.com/tutorials/abap-environment-service-binding.html)\) on how to create a business configuration application to maintain holidays, for instance, the language-dependent texts for the respective holidays are stored as entries in the database table ZCAL\_HOLIDAY\_XXX. The non-key field for which translations can be maintained is field FCAL\_DESCRIPTION.

**Related Information**  


[Select your Source and Target Language\(s\)](Select_your_Source_and_Target_Language(s)_85823ef.md)

