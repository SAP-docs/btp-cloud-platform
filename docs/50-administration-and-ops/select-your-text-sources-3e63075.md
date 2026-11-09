<!-- loio3e63075b741c4d8aaf285401482faabd -->

# Select Your Text Sources



<a name="loio3e63075b741c4d8aaf285401482faabd__section_rcs_5dl_q5b"/>

## Context

Select the text sources that you want to have translated.



<a name="loio3e63075b741c4d8aaf285401482faabd__section_dwt_vdl_q5b"/>

## Procedure

1.  In the *Maintain Customizing Translations* app, open the project you want to add text sources to.
2.  Scroll down to *Text Sources* and click *Add*.
3.  Here you can select which text source types to add. The following text source types are supported:
    -   UI runtime adaptations

        > ### Note:  
        > Mind that only the translation of those UI runtime adaptations which have been recorded on a Customizing transport request are supported. UI runtime adaptations which have not been recorded at all or have been recorded on a workbench request will not be considered
        > 
        > For more information on how to work with UI runtime adaptations, see [Adapting SAP Fiori UIs at Runtime - Key User Adaptation](https://help.sap.com/docs/btp/sap-fiori-launchpad-for-sap-btp/adapting-sap-fiori-uis-at-runtime-key-user-adaptation)

    -   `SAP Fiori launchpad` Pages

    -   `SAP Fiori launchpad` Spaces

        > ### Note:  
        > For more information on how to manage launchpad pages and spaces, see [Manage Launchpad Pages](https://help.sap.com/docs/BTP/10fd1742ea914256abedb34bf15bd069/8a174e235493472095c0bcec957dfee0.html) and [Manage Launchpad Spaces](https://help.sap.com/docs/BTP/10fd1742ea914256abedb34bf15bd069/ad119b284f8249cfb4c3fc86c76404c5.html).

    -   Text tables

        > ### Note:  
        > **Text Tables**
        > 
        > Text tables are database tables in which language-dependent texts are stored. The translation of text table entries is only available in environments that support transporting client-specific data.
        > 
        > A database table needs to fulfill the following requirements to be considered a text table by the *Maintain Customizing Translations* app:
        > 
        > -   The database table is client-dependent, meaning the first key field of ABAP Dictionary built-in type `CLNT`.
        > 
        > -   The database table has exactly one key field of ABAP Dictionary built-in type`LANG`.
        > 
        > -   The database table is of delivery class C.
        > 
        > -   The translation of text tables that contain key fields of type p \(packed number\), i \(integer\) or x \(byte field\) is not supported. That includes any kind of UUID and raw types, such as `SYSUUID_X16`.
        > 
        > 
        > If these requirements are fulfilled, the database table can be added to a translation project as a text table. Additionally, the following rules apply:
        > 
        > -   Every non-key field of the text table that is of an ABAP Dictionary built-in type that is character-like and has a minimum length of 1 will be interpreted as a text attribute for which translations can be maintained.
        > 
        > -   When the translations are published, the rows containing the texts in the target language will be added to the selected transport via `R3TR TABU`.

        > ### Restriction:  
        > UI runtime adaptations, that means text sources of type *UI Flexibility: Views and Changes*, can't be translated in the parallel line. This is only possible in the main line via the *Maintain Translations* app.

        > ### Tip:  
        > For performance reasons, we recommend that a translation project shouldn't contain more than 1000 texts. Larger projects can cause a timeout during publishing. Be aware that a text source might contain more than one text.


4.  Select *Add* to open the *Add Text Source* dialog which displays all text sources that can be added to the translation project. By filtering the type and name, you can choose the text sources you want to add. Select *Add* to add the text sources you selected to your translation project.

**Related Information**  


[Select Your Source and Target Language](select-your-source-and-target-language-239abb9.md "")

