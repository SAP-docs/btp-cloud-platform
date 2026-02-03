<!-- loio4d6e84a201cd4b5092ec038073b58344 -->

# Transport Handling



<a name="loio4d6e84a201cd4b5092ec038073b58344__section_ekf_3pb_pvb"/>

## Context

Business configuration content is usually not directly maintained in a productive system, but created in a development system, and then transported to the test system and productive system. As the developer of a business configuration app, you need to ensure that changes to the business configuration content is recorded onto a transport request of type *Customizing* and the user has the option to select the correct transport request.



### Recording Changes on Transport Request

With the factory class *MBC\_CP\_API* you can instantiate a transport API to validate and record entity keys of a RAP business object on a transport request.

> ### Sample Code:  
> ```
>   DATA(api) = mbc_cp_api=>rap_tdat_cts(
>                tdat_name = '/ITAPC1/CODE' 
>                table_entity_relations = VALUE #( ( entity = '/ITAPC1/I_Status' table = '/ITAPC1/STATUS' )
>                                                  ( entity = '/ITAPC1/I_StatusText' table = '/ITAPC1/STATUST' ) ) 
>               ).
> ```

In the behavior implementation define an [Additional Save Implementation](https://help.sap.com/doc/abapdocu_cp_index_htm/CLOUD/en-US/index.htm?file=abenbdl_saving.htm) in the header directly after the keyword managed. In the `save_modified` method you can record the changes on the transport request with the method `record_changes` of this API. Check the ABAP Doc of `record_changes` for more information and example implementation.

For each entity of the RAP BO define a [Validation](https://help.sap.com/docs/abap-cloud/abap-rap/validations?version=s4hana_cloud) on save for create, update and delete. In the validation implementation call the method `validate_changes` of the API. Check the ABAP Doc of validate\_changes for more information and example implementation.



### Transport Selection

The before mentioned API methods require a transport request to be passed. For the transport selection define an action with Abstract CDS Entity *D\_SelectCustomizingTransptReqP* as the parameter. This CDS Entity returns all modifiable transport request of type *Customizing* where the user either owns the request or owns at least one open task. The transport request must have the attribute `SAP_CUS_TRANSPORT_CATEGORY` set to `MANUAL_CUST` or `DEFAULT_CUST`.

Save the result of the action in a virtual field of the draft entity. When recording or validating the changes the previously selected transport request can then be retrieved from the draft entity.



### No Transport

When using the [ADT wizard](generating-a-business-configuration-maintenance-object-with-the-generate-abap-repository-047e01c.md) to generate a business configuration maintenance object, you can choose *No Transport* for *Transport Selection* for an app without transport option. Suitable for configurations that are to be adjusted in the production client. For more information read this [blog post](https://community.sap.com/t5/technology-blog-posts-by-sap/how-to-create-a-rap-bo-to-change-the-content-of-a-customizing-table-in-the/ba-p/13723087).

For more information read this blog post.

