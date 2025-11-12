<!-- loio0033cbc46b8847b9813fc480633d1d79 -->

# Configuring Predefined Custom Fields

Get an overview of how to configure predefined custom fields, and how to publish your configured custom fields.



## Context

This process enables you to configure custom fields that were predefined by your application provider. They can be used to enhance applications which contain APIs and data sources that have been released by your software provider to configure custom fields.



## Procedure

1.  Open the *Configure Predefined Custom Fields* app. You can open the app either directly from the SAP Fiori launchpad, or from an extensible application by clicking *\+* *\(Add Custom Field\)* in the UI adaptation mode of an application.

    > ### Note:  
    > To use new fields from a predefined custom field in an SAP Fiori app, you have to restart the app and the UI adaptation mode. For more information about how to adapt SAP Fiori UIs during runtime,see [Adapting SAP Fiori UIs at Runtime](https://help.sap.com/viewer/3d99fdeadde04524bdd33d35f1e13777/Cloud/en-US/5c424437bf794f809087fdce391149f2.html)

2.  Create a new predefined custom field configuration in the business process where it is needed. To do so, select a business object, a business object node, and the technical type of the configuration. Complete this step by selecting the basic properties of this type. For example, if you selected the technical type `Character`, you need to choose one of the available field lengths your application provider has predefined for you.

3.  Next, you can adapt further properties of your custom field. Enter a label and a tooltip, and choose a semantic type for your field. For example, if you selected the semantic type `Email Address`, you will be able to open your email client directly from the link.

    > ### Caution:  
    > Once created, the semantic type of the custom field can't be changed anymore.

    You can translate your field label and your field tooltip. To do so, select *Translation* in your custom field. Now, you can proceed to making your custom field available in other languages.

    > ### Note:  
    > If your field is of type `Code List`, you can also translate the individual list value descriptions that belong to that field.

4.  Finally, you can decide whether you want to create and publish your configured field directly, or if you want to create and edit your custom field. By selecting *Create and Edit*, you will be able to define where and how your configured field should appear in the app before publishing it.

5.  You can decide which code values to enable for your custom field by using the toggles displayed in the table. Also, you can choose whether you want to make your new fields visible to the UI and app services. After you have finished editing your custom field, select *Publish*.

    > ### Caution:  
    > Once published, you won't be able to delete the code values from the type `Code List` anymore. However, you can still enable or disable your code values.

    > ### Note:  
    > If a change is made to the custom field after publishing, the status of the custom field will change to *Revised*. The changes in your custom field will only be visible in the system after selecting *Publish* once more.
    > 
    > You can only *Discard Changes* if the revised custom field hasn't been published yet. After publishing, you can still enable or disable specific code values in your custom field as described in step 5.
    > 
    > If a custom field is published or deleted, the extended application has to restart. This may result in a prolonged loading time of the extended application when it is launched for the first time.

    > ### Caution:  
    > When you publish a field with a certain length, you can't decrease the field length later on.

    Your configured custom fields will now appear in your applications and their UIs.

6.  There are applications that use remote OData services to fetch data. However, there might be extension fields which are not mapped in the standard service consumption model. You can also enable remote OData services and maintain the mapping between the internal field name and the field name in the remote OData service. To do this, you can either use an existing field or create a new one at the specific extension point. Find the available service consumption model entities in the *Services* section and enable the respective one. This navigates to the field mapping page, where you can maintain the entity data model field name. That field name corresponds to the OData extension field name on the remote service side. Finally, save and publish the field.


**Related Information**  


[Configure Predefined Custom Fields](configure-predefined-custom-fields-0eaa01c.md)

