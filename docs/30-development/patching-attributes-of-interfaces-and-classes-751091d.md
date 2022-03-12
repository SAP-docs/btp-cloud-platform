<!-- loio751091d85e9f4c08ad6d119abdca9763 -->

# Patching Attributes of Interfaces and Classes

The code samples illustrate how the interface and class Read APIs can be combined with `PATCH` operations to conditionally change attributes of interfaces and classes.

In the first example an attribute is inserted into an interface if it's not yet part of it and deleted if it's already a part of the interface. By running the class several times in a row the attribute will be continuously inserted and deleted.

> ### Sample Code:  
> ```abap
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

The second example "moves" an attribute through all three sections of a class. By running the below class several times in a row the attribute will first move from the public section to the protected section, then to the private section and then back to the public section to repeat the cycle:

> ### Sample Code:  
> ```abap
> "! Code sample for using the class Read APIs together with the CLAS PATCH operation
> "! functionality to "move" a DATA attribute across the sections of the class.
> "!
> "! IMPORTANT: The class referred to by the constant CO_CLASS_NAME needs to
> "! exist prior to executing this code sample.
> CLASS zcl_xco_doc_cp_cs_chg_clas DEFINITION PUBLIC FINAL
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
>     TYPES:
>       BEGIN OF ts_section,
>         name             TYPE string,
>         class_definition TYPE REF TO if_xco_clas_definition_section,
>         for_delete       TYPE REF TO if_xco_gen_clas_s_de_d_section,
>         for_insert       TYPE REF TO if_xco_gen_clas_s_in_d_section,
>       END OF ts_section,
> 
>       tt_section TYPE STANDARD TABLE OF ts_section WITH EMPTY KEY.
> 
>     CONSTANTS:
>       co_class_name TYPE sxco_ao_object_name VALUE 'ZCL_CLASS',
> 
>       co_numeric_id TYPE sxco_ao_component_name VALUE 'NUMERIC_ID'.
> 
>     DATA:
>       mo_class TYPE REF TO if_xco_ao_class.
> 
>     METHODS:
>       get_generation_environment
>         IMPORTING
>           out                              TYPE REF TO if_xco_adt_classrun_out
>         RETURNING
>           VALUE(ro_generation_environment) TYPE REF TO if_xco_cp_gen_env_dev_system,
> 
>       get_transport_request
>         IMPORTING
>           out                         TYPE REF TO if_xco_adt_classrun_out
>         RETURNING
>           VALUE(ro_transport_request) TYPE REF TO if_xco_cp_tr_request,
> 
>       get_sections
>         IMPORTING
>           io_object          TYPE REF TO if_xco_cp_gen_clas_d_o_pat_obj
>         RETURNING
>           VALUE(rt_sections) TYPE tt_section.
> ENDCLASS.
> 
> CLASS zcl_xco_doc_cp_cs_chg_clas IMPLEMENTATION.
>   METHOD constructor.
>     super->constructor( ).
> 
>     mo_class = xco_cp_abap=>class( co_class_name ).
>   ENDMETHOD.
> 
>   METHOD main.
>     DATA(lo_patch_operation) = get_generation_environment( out )->for-clas->create_patch_operation( ).
>     DATA(lo_object) = lo_patch_operation->add_object( co_class_name ).
> 
>     DATA(lt_sections) = get_sections( lo_object ).
> 
>     LOOP AT lt_sections INTO DATA(ls_section).
>       DATA(lv_current_section) = sy-tabix.
> 
>       IF ls_section-class_definition->component->data( co_numeric_id )->exists( ) EQ abap_true.
>         ls_section-for_delete->add_data( co_numeric_id ).
> 
>         out->write( |Deleting DATA { co_numeric_id } from section { ls_section-name }.| ).
>         EXIT.
>       ENDIF.
>     ENDLOOP.
> 
>     " Insert attribute to next section.
>     DATA(ls_next_section) = lt_sections[ lv_current_section MOD 3 + 1 ].
> 
>     ls_next_section-for_insert->add_data( co_numeric_id
>       )->set_type( xco_cp_abap=>type-built_in->int8 ).
> 
>     out->write( |Inserting DATA { co_numeric_id } into section { ls_next_section-name }.| ).
> 
>     lo_patch_operation->execute( ).
>   ENDMETHOD.
> 
>   METHOD get_generation_environment.
>     DATA(lo_transport_request) = get_transport_request( out ).
> 
>     ro_generation_environment = xco_cp_generation=>environment->dev_system( lo_transport_request->value ).
>   ENDMETHOD.
> 
>   METHOD get_transport_request.
>     DATA(lo_lock) = mo_class->if_xco_cts_changeable~get_object(
>       )->get_lock( ).
> 
>     IF lo_lock->exists( ) EQ abap_true.
>       DATA(lv_transport) = lo_lock->get_transport( ).
> 
>       ro_transport_request = xco_cp_cts=>transport->for( lv_transport
>         )->get_request( ).
> 
>       out->write( |Using transport request { ro_transport_request->value } (Class is already locked).| ).
>     ELSE.
>       DATA(lo_transport_target) = mo_class->if_xco_ar_object~get_package(
>         )->read(
>         )-property-transport_layer->get_transport_target( ).
> 
>       ro_transport_request = xco_cp_cts=>transports->workbench( lo_transport_target->value
>         )->create_request( 'Generated transport request' ).
> 
>       out->write( |Using newly generated transport request { ro_transport_request->value }.| ).
>     ENDIF.
>   ENDMETHOD.
> 
>   METHOD get_sections.
>     DATA(ls_public_section) = VALUE ts_section(
>       name             = `PUBLIC`
>       class_definition = mo_class->definition->section-public
>       for_delete       = io_object->for-delete->definition->section-public
>       for_insert       = io_object->for-insert->definition->section-public
>     ).
>     APPEND ls_public_section TO rt_sections.
> 
>     DATA(ls_protected_section) = VALUE ts_section(
>       name             = `PROTECTED`
>       class_definition = mo_class->definition->section-protected
>       for_delete       = io_object->for-delete->definition->section-protected
>       for_insert       = io_object->for-insert->definition->section-protected
>     ).
>     APPEND ls_protected_section TO rt_sections.
> 
>     DATA(ls_private_section) = VALUE ts_section(
>       name             = `PRIVATE`
>       class_definition = mo_class->definition->section-private
>       for_delete       = io_object->for-delete->definition->section-private
>       for_insert       = io_object->for-insert->definition->section-private
>     ).
>     APPEND ls_private_section TO rt_sections.
>   ENDMETHOD.
> ENDCLASS.
> ```

