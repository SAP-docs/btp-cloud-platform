<!-- loio751091d85e9f4c08ad6d119abdca9763 -->

# Patching Attributes of an Interface

The code sample below illustrates how the interface Read APIs can be combined with PATCH operations of the INTF Generation APIs to insert or delete an attribute of an interface depending on whether it exists or not:

> ### Sample Code:  
> ```lang-abap
> "! Code sample for using the interface Read APIs together with the INTF PATCH operation
> "! functionality to "toggle" a DATA attribute on an interface.
> "!
> "! IMPORTANT: The interface referred to by the constant CO_INTERFACE_NAME needs to
> "! exist prior to executing this code sample.
> CLASS zcl_xco_doc_cp_cs_chg_intf DEFINITION PUBLIC FINAL
>     INHERITING FROM cl_xco_cp_adt_simple_classrun CREATE PUBLIC.
>   PUBLIC SECTION.
>     METHODS:
>       constructor.
>  
>   PROTECTED SECTION.
>     METHODS:
>       main REDEFINITION.
>  
>   PRIVATE SECTION.
>     CONSTANTS:
>       co_interface_name TYPE sxco_ao_object_name VALUE 'ZIF_INTERFACE',
>  
>       co_numeric_id    TYPE sxco_ao_component_name VALUE 'NUMERIC_ID'.
>  
>     METHODS:
>       get_transport_request
>         IMPORTING
>           io_interface               TYPE REF TO if_xco_ao_interface
>           out                        TYPE REF TO if_xco_adt_classrun_out
>         RETURNING
>           VALUE(ro_transport_request) TYPE REF TO if_xco_cp_tr_request.
> ENDCLASS.
>  
> CLASS zcl_xco_doc_cp_cs_chg_intf IMPLEMENTATION.
>   METHOD constructor.
>     super->constructor( ).
>   ENDMETHOD.
>  
>   METHOD main.
>     DATA(lo_interface) = xco_cp_abap=>interface( co_interface_name ).
>  
>     DATA(lo_transport_request) = get_transport_request(
>       io_interface = lo_interface
>       out          = out
>     ).
>  
>     DATA(lo_environment) = xco_cp_generation=>environment->dev_system( lo_transport_request->value ).
>  
>     DATA(lo_patch_operation) = lo_environment->for-intf->create_patch_operation( ).
>     DATA(lo_object) = lo_patch_operation->add_object( co_interface_name ).
>  
>     IF lo_interface->component->data( co_numeric_id )->exists( ) EQ abap_false.
>       lo_object->for-insert->add_data( co_numeric_id
>         )->set_type( xco_cp_abap=>type-built_in->int8
>         )->set_read_only( ).
>  
>       out->write( |Inserting DATA { co_numeric_id }| ).
>     ELSE.
>       lo_object->for-delete->add_data( co_numeric_id ).
>  
>       out->write( |Deleting DATA { co_numeric_id }| ).
>     ENDIF.
>  
>     lo_patch_operation->execute( ).
>   ENDMETHOD.
>  
>   METHOD get_transport_request.
>     DATA(lo_lock) = io_interface->if_xco_cts_changeable~get_object(
>       )->get_lock( ).
>  
>     IF lo_lock->exists( ) EQ abap_true.
>       DATA(lv_transport) = lo_lock->get_transport( ).
>  
>       ro_transport_request = xco_cp_cts=>transport->for( lv_transport
>         )->get_request( ).
>  
>       out->write( |Using transport request { ro_transport_request->value } (Interface is already locked).| ).
>     ELSE.
>       DATA(lo_transport_target) = io_interface->if_xco_ar_object~get_package(
>         )->read(
>         )-property-transport_layer->get_transport_target( ).
>  
>       ro_transport_request = xco_cp_cts=>transports->workbench( lo_transport_target->value
>         )->create_request( 'Generated transport request' ).
>  
>       out->write( |Using newly generated transport request { ro_transport_request->value }.| ).
>     ENDIF.
>   ENDMETHOD.
> ENDCLASS.
> ```

