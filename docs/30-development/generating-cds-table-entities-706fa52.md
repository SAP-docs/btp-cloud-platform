<!-- loio706fa52cf0c44811b2d548ffa355247a -->

# Generating CDS Table Entities

The XCO Generation APIs allow to generate CDS table entities through `PUT` operations.

The following code sample demonstrates how to generate a CDS table entity using the XCO library by running a `PUT` operation:

> ### Sample Code:  
> ```abap
> DATA(lo_put_operation) = xco_cp_generation=>environment->dev_system( '$TRANSPORT_REQUEST$'
>   )->create_put_operation( ).
> 
> DATA(lo_form_specification) = lo_put_operation->for-ddls->add_object( 'ZMY_CDS_TABLE_ENTITY'
>   )->set_package( 'ZMY_PACKAGE'
>   )->create_form_specification( ).
> 
> DATA(lo_table_entity) = lo_form_specification->set_short_description( 'XCO Generated CDS Table Entity'
>   )->add_table_entity( ).
> 
> lo_table_entity->add_annotation( 'EndUserText.label'
>   )->value->build( )->add_string( 'My Table Entity' ).
> 
> lo_table_entity->add_annotation( 'ClientHandling.type'
>   )->value->build(
>   )->add_enum( 'CLIENT_INDEPENDENT' ).
> 
> lo_table_entity->add_annotation( 'AbapCatalog.deliveryClass'
>   )->value->build(
>   )->add_enum( 'LOCAL_DATA' ).
> 
> lo_table_entity->add_field( xco_cp_ddl=>field( 'key_field' )
>   )->set_type( xco_cp_abap_dictionary=>built_in_type->int1
>   )->set_key( ).
> 
> lo_table_entity->add_field( xco_cp_ddl=>field( 'data_field' )
>   )->set_type( xco_cp_abap_dictionary=>built_in_type->int1
>   )->set_null( ).
> 
> lo_put_operation->execute( ).
> ```

Running this `PUT` operation generates the CDS external entity `ZMY_CDS_TABLE_ENTITY` with the following source code:

> ### Sample Code:  
> ```
> @EndUserText.label: 'My Table Entity'
> @ClientHandling.type: #CLIENT_INDEPENDENT
> @AbapCatalog.deliveryClass: #LOCAL_DATA
> define table entity ZMY_CDS_TABLE_ENTITY
> {
>   key key_field : abap.int1;
>   data_field : abap.int1 null;
> }
> ```

