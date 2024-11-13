<!-- loioab110b5a75d64d92a0bb51891dc9deb2 -->

# Generating CDS External Entities

The following code sample shows how you can generate a CDS external entity with the XCO library by running a `PUT` operation:

> ### Sample Code:  
> ```abap
> DATA(lo_put_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
>   )->create_put_operation( ).
>  
> DATA(lo_form_specification) = lo_put_operation->for-ddls->add_object( 'ZMY_CDS_EXT_ENTITY'
>   )->set_package( 'ZMY_PACKAGE'
>   )->create_form_specification( ).
>  
> DATA(lo_external_entity) = lo_form_specification->set_short_description( 'Generated CDS External Entity'
>   )->add_external_entity( ).
>  
> lo_external_entity->set_with_federated_data(
>   )->set_dynamic_access(
>   )->set_on_unlinked_fail( ).
>  
> lo_external_entity->add_annotation( 'EndUserText.label' ##NO_TEXT
>   )->value->build( )->add_string( 'My external entity' ).
>  
> lo_external_entity->data_source->set_remote_object_name( 'My remote object name' ).
>  
> lo_external_entity->add_field( xco_cp_ddl=>field( 'key_field' )
>   )->set_key(
>   )->set_type( xco_cp_abap_dictionary=>built_in_type->int1 ).
>  
> lo_external_entity->add_field( xco_cp_ddl=>field( 'field' )
>   )->set_type( xco_cp_abap_dictionary=>built_in_type->char( 10 )
>   )->set_external_name( 'My field external name' ).
>  
> lo_put_operation->execute( ).
> ```

Running this `PUT` operation will produce the CDS external entity `ZMY_CDS_EXT_ENTITY` with the following source:

> ### Sample Code:  
> ```
> @EndUserText.label: 'My external entity'
> define external entity ZMY_CDS_EXT_ENTITY external name "My remote object name"
> {
>   key key_field : abap.int1;
>   field : abap.char(10) external name "My field external name";
> }
> WITH FEDERATED DATA
> PROVIDED AT RUNTIME
> ON UNLINKED FAIL
> ```

To connect to an external system, you will also need a logical external schema. It can be generated like this:

> ### Sample Code:  
> ```abap
> DATA(lo_put_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
>   )->create_put_operation( ).
>    
> DATA(lo_form_specification) = lo_put_operation->for-desd->add_object( 'ZMY_LOGICAL_EXT_SCHEMA'
>   )->set_package( 'ZMY_PACKAGE'
>   )->create_form_specification( ).
>  
> lo_form_specification->set_short_description( 'Generated Logical External Schema'
>   )->set_default_remote_schema_name( 'My Schema Name' ).
>  
> lo_put_operation->execute( ).
> ```

**Related Information**  


[CDS External Entities](https://help.sap.com/docs/abap-cloud/abap-data-models/cds-external-entities)

