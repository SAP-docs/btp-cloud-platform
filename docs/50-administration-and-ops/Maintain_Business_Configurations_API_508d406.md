<!-- loio508d406ac92043dba95f694144803c26 -->

# Maintain Business Configurations API



<a name="loio508d406ac92043dba95f694144803c26__section_ygr_l3x_clb"/>

## Prerequisites

You have created a business configuration by following [this tutorial](https://developers.sap.com/mission.abap-dev-factory-calendar.html). Please note that the Maintain Business Configurations API only supports one level of sub nodes, i.e. your root entity can have associations to an arbitrary amount of entities but these sub entities cannot have associations to further sub entities. The data model must consist only of client-dependent tables.



<a name="loio508d406ac92043dba95f694144803c26__section_qhs_hjx_clb"/>

## Maintain Business Configurations Cloud Platform API

The ABAP API *mbc\_cp\_api* offers methods for creating, updating, deleting and reading business configuration registrations. After a business configuration has been registered, it will be shown on the list of all maintainable business configurations in the Fiori App *Maintain Business Configurations* if the user has the necessary authorizations regarding the service of the business configuration \(see **Provide Authorizations for a Business Configuration** below\) . The end user can then maintain data for the registered business configuration from the frontend.

Before using any of the following methods, first obtain an interface handle by calling `mbc_cp_api=>business_configuration` with your namespace and an identifier for your business configuration.

-   The namespace is the development namespace that was assigned to you for ABAP development in the SAP BTP ABAP environment.
-   The identifier is used to identify a single business configuration in the registration table. The following rules apply:
    -   It must not exceed 20 characters in length.
    -   It must start with a letter and can only contain letters, numbers and underscores. The API uppercases the identifier before storing it in the metadata table.

If an error occurs while calling the following methods, an exception of type `cx_mbc_api_exception` will be raised. Use the method `if_xco_news~get_messages` to retrieve all messages that the exception carries.



### Create a Business Configuration registration

Use the `create` method of the obtained business configuration interface handle to create a new registration. Supply the following mandatory parameters, as illustrated in the code sample below.

-   A name that is shown on the frontend list of all registered business configurations.

-   A description for the business configuration that is shown on the frontend.

    > ### Note:  
    > The name and description are language dependent. The translations can be maintained using the *Maintain Translations* app.

-   The OData V4 - UI Service Binding that is used to maintain the business configuration data. The service must be draft enabled.

-   The name of the service to be used \(as defined in the Service Binding\).

-   The name of an entity set as exposed by the service definition. This entity set is used as the root node for the UI. Only for this root entity set and its associations a UI is shown. Keep in mind that only one level of sub nodes is supported.

-   A transport request of type Workbench to write the business configuration registration to. An entry of type "SMBC" \(Business Configuration Object\) will be written to that transport request.


> ### Sample Code:  
> ```lang-abap
> CLASS zcl_ys_register_bc DEFINITION PUBLIC FINAL CREATE PUBLIC
>     INHERITING FROM cl_xco_cp_adt_simple_classrun.
>   PROTECTED SECTION.
>     METHODS:
>       main REDEFINITION.
> ENDCLASS.
> 
> CLASS zcl_ys_register_bc IMPLEMENTATION.
>   METHOD main.
>     DATA(lo_business_configuration) = mbc_cp_api=>business_configuration(
>       iv_identifier = 'HOLIDAY_CALENDAR'
>       iv_namespace  = '/Y123456/'
>     ).
> 
>     TRY.
>         lo_business_configuration->create(
>           iv_name            = 'Holiday Calendar'
>           iv_description     = 'A calendar for holidays'
>           iv_service_binding = '/Y123456/CAL_I_HOLIDAY_SB'
>           iv_service_name    = 'Holiday'
>           iv_service_version = 0001
>           iv_root_entity_set = 'HolidayRoot'
>           iv_transport       = 'X02K900025'
>         ).
>       CATCH cx_mbc_api_exception INTO DATA(lx_mbc_api_exception).
>         DATA(lt_messages) = lx_mbc_api_exception->if_xco_news~get_messages( ).
> 
>         LOOP AT lt_messages INTO DATA(lo_message).
>           " Use lo_message->get_text( ) to get the error message.
>         ENDLOOP.
>     ENDTRY.
>   ENDMETHOD.
> ENDCLASS.
> 
> ```

The supplied information plus an application component is stored in the registration table. The application component is derived from the package that contains the registered service binding. It will be shown within a message on the frontend if an error occurs while using the business configuration.

The create method also has two optional parameters:

-   skip root entity list report: If abap\_true, the UI automatically navigates to the object page of the root entity skipping the list report. Exactly one root entity must exist.
-   app configuration: Configuration of root entity list report and object pages. It is sufficient to maintain only those attributes that should deviate from the standard behavior.



### Update a Business Configuration registration

You can only update the name and the description of your business configuration by using the respective methods `update_name` and `update_decription`. A transport request of type Workbench must be supplied to transport the updated registration.



### Delete a Business Configuration registration

To delete a business configuration registration, use the method `delete`. A transport request of type Workbench must be supplied to transport the deletion.



### Check if a Business Configuration registration exists

To check the existence of a business configuration registration, use the method `exists`. The method has no parameters. It returns `abap_true` if a registration exists, `abap_false` if it doesn't.

For an overview of registered business configurations use CDS view `I_CustABAPObjDirectoryEntry` with `ABAPObjectType = 'SMBC'`.



### Read a Business Configuration registration

To retrieve the details of a business configuration registration, use the method `read`. The method has no parameters. The returned structure contains all the metadata of the business configuration registration.



<a name="loio508d406ac92043dba95f694144803c26__section_pyj_gsx_clb"/>

## Provide Authorizations for a Business Configuration

To grant frontend users the rights to use a business configuration, first create an *Identity and Access Management \(IAM\) App* and assign it to an *IAM Business Catalog*. Follow [this user guide](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/032faaf4f9184484ba9295c81756e831.html) but make sure to select the IAM App Type *Business Configuration App*.

Once you have created the IAM Business Catalog, assign the catalog to a Business Role on the Fiori Launchpad by following [this user guide](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/8980ad05330b4585ab96a8e09cef4688.html). Finally, follow [this user guide](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/e40e710321c74f28916affa9ae984bce.html) to assign the Business Role to Business Users to grant the rights to use your business configuration inside the *Maintain Business Configurations* Fiori App.

