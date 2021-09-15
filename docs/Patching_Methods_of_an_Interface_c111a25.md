<!-- loioc111a250d99b4b2882ada78eb7e5af6c -->

# Patching Methods of an Interface

The code sample below illustrates how PATCH operations of the XCO Generation APIs can be used to patch methods of an interface. The MAIN method will execute one of four phases depending on the current state of the interface. To see each phase in action simply execute the class several times in a row.

> ### Sample Code:  
> ```lang-abap
> "! Code sample for patching methods of an interface.
> "!
> "! IMPORTANT: The value of the constant CO_PACKAGE  must be replaced with an existing
> "! development package.
> CLASS zcl_xco_doc_cp_cs_patch_in_me DEFINITION PUBLIC FINAL
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
>       co_package       TYPE sxco_package VALUE 'ZMY_PACKAGE',
>  
>       co_interface_name TYPE sxco_ao_object_name VALUE 'ZIF_XCO_DMO_GEN_INTF_PATCH_MTD',
>  
>       co_first_method  TYPE sxco_ao_component_name VALUE 'FIRST_METHOD',
>       co_second_method TYPE sxco_ao_component_name VALUE 'SECOND_METHOD',
>       co_third_method  TYPE sxco_ao_component_name VALUE 'THIRD_METHOD'.
>  
>     DATA:
>       mo_interface TYPE REF TO if_xco_ao_interface.
>  
>     METHODS:
>       phase_1
>         IMPORTING
>           out TYPE REF TO if_xco_adt_classrun_out,
>  
>       phase_2
>         IMPORTING
>           out TYPE REF TO if_xco_adt_classrun_out,
>  
>       phase_3
>         IMPORTING
>           out TYPE REF TO if_xco_adt_classrun_out,
>  
>       phase_4
>         IMPORTING
>           out TYPE REF TO if_xco_adt_classrun_out,
>  
>       get_environment
>         IMPORTING
>           out                  TYPE REF TO if_xco_adt_classrun_out
>         RETURNING
>           VALUE(ro_environment) TYPE REF TO if_xco_cp_gen_env_dev_system,
>  
>       get_transport_request
>         IMPORTING
>           out                        TYPE REF TO if_xco_adt_classrun_out
>         RETURNING
>           VALUE(ro_transport_request) TYPE REF TO if_xco_cp_tr_request.
> ENDCLASS.
>  
> CLASS zcl_xco_doc_cp_cs_patch_in_me IMPLEMENTATION.
>   METHOD constructor.
>     super->constructor( ).
>  
>     mo_interface = xco_cp_abap=>interface( co_interface_name ).
>   ENDMETHOD.
>  
>   METHOD main.
>     IF mo_interface->exists( ) EQ abap_false.
>       " In the first phase the interface is created via a PUT operation.
>       phase_1( out ).
>  
>       out->write( |Executed phase 1| ).
>     ELSEIF mo_interface->component->method( 'FIRST_METHOD' )->exists( ) EQ abap_false.
>       " In the second phase two new methods are inserted into the interface
>       " via a single PATCH operation.
>       phase_2( out ).
>  
>       out->write( |Executed phase 2| ).
>     ELSEIF mo_interface->component->method( 'SECOND_METHOD' )->exists( ) EQ abap_true.
>       " In the third phase one method is deleted, a new method is inserted and
>       " an existing method is updated via a single PATCH operation.
>       phase_3( out ).
>  
>       out->write( |Executed phase 3| ).
>     ELSE.
>       " In the fourth phase the interface is deleted via a DELETE operation.
>       phase_4( out ).
>  
>       out->write( |Executed phase 4| ).
>     ENDIF.
>   ENDMETHOD.
>  
>   METHOD phase_1.
>     DATA(lo_put_operation) = get_environment( out )->create_put_operation( ).
>  
>     DATA(lo_specification) = lo_put_operation->for-intf->add_object( mo_interface->name
>       )->set_package( co_package
>       )->create_form_specification( ).
>     lo_specification->set_short_description( 'My interface' ).
>  
>     " Data
>     lo_specification->add_data( 'ID'
>       )->set_type( xco_cp_abap=>type-built_in->i
>       )->set_read_only( ).
>  
>     lo_put_operation->execute( ).
>   ENDMETHOD.
>  
>   METHOD phase_2.
>     DATA(lo_patch_operation) = get_environment( out )->for-intf->create_patch_operation( ).
>  
>     DATA(lo_patch_operation_object) = lo_patch_operation->add_object( mo_interface->name ).
>  
>     " Insert first method
>     DATA(lo_first_method) = lo_patch_operation_object->for-insert->add_method( co_first_method
>       )->set_default_ignore( ).
>  
>     lo_first_method->add_importing_parameter( 'IMP_1'
>       )->set_type( xco_cp_abap=>type-built_in->string ).
>     lo_first_method->add_importing_parameter( 'IMP_2'
>       )->set_type( xco_cp_abap=>type-built_in->string ).
>     lo_first_method->add_changing_parameter( 'CHA_1'
>       )->set_type( xco_cp_abap=>interface( 'IF_XCO_NEWS' ) ).
>  
>     lo_first_method->add_exception( 'CX_ABAP_INVALID_VALUE' ).
>  
>     " Insert second method
>     DATA(lo_second_method) = lo_patch_operation_object->for-insert->add_method( co_second_method
>       )->set_default_fail( ).
>  
>     lo_patch_operation->execute( ).
>   ENDMETHOD.
>  
>   METHOD phase_3.
>     DATA(lo_patch_operation) = get_environment( out )->for-intf->create_patch_operation( ).
>  
>     DATA(lo_patch_operation_object) = lo_patch_operation->add_object( mo_interface->name ).
>  
>     " Update first method.
>     DATA(lo_first_method) = lo_patch_operation_object->for-update->add_method( co_first_method
>       )->set_default_fail( ).
>  
>     lo_first_method->for-update->add_importing_parameter( 'IMP_1'
>       )->set_pass_by_value(
>       )->set_optional( ).
>  
>     lo_first_method->for-delete->add_importing_parameter( 'IMP_2' ).
>  
>     lo_first_method->for-insert->add_importing_parameter( 'IMP_3'
>       )->set_type( xco_cp_abap_dictionary=>data_element( 'SXCO_AO_OBJECT_NAME' ) ).
>  
>     lo_first_method->for-update->add_exception( 'CX_ABAP_INVALID_VALUE'
>       )->set_resumable( ).
>  
>     " Delete second method.
>     lo_patch_operation_object->for-delete->add_method( co_second_method ).
>  
>     " Insert third method.
>     lo_patch_operation_object->for-insert->add_method( co_third_method
>       )->set_default_fail( ).
>  
>     lo_patch_operation->execute( ).
>   ENDMETHOD.
>  
>   METHOD phase_4.
>     DATA(lo_delete_operation) = get_environment( out )->for-intf->create_delete_operation( ).
>     lo_delete_operation->add_object( mo_interface->name ).
>     lo_delete_operation->execute( ).
>   ENDMETHOD.
>  
>   METHOD get_environment.
>     DATA(lo_transport_request) = get_transport_request( out ).
>  
>     ro_environment = xco_cp_generation=>environment->dev_system( lo_transport_request->value ).
>   ENDMETHOD.
>  
>   METHOD get_transport_request.
>     DATA(lo_lock) = mo_interface->if_xco_cts_changeable~get_object(
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
>       DATA(lo_transport_target) = xco_cp_abap_repository=>package->for( co_package
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

