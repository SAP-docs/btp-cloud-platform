<!-- loio31415328d5bb419aa3f66dfc09417884 -->

# Updating the Source Code of a Function Module

The following code sample illustrates the source code of an already existing function module that can be updated:

> ### Sample Code:  
> ```abap
> "! Code sample for updating the source code of an existing function module.
> "!
> "! IMPORTANT: The function module referred to by the constant CO_FUNCTION_MODULE_NAME needs to
> "! exist prior to executing this code sample and must not already be locked on a transport
> "! request.
> CLASS zcl_xco_doc_cp_cs_chg_fm DEFINITION PUBLIC FINAL
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
>       co_function_module_name TYPE sxco_fm_name VALUE 'ZMY_FUNCTION_MODULE'.
>  
>     DATA:
>       mo_function_module TYPE REF TO if_xco_function_module.
>  
>     METHODS:
>       generate_transport_request
>         IMPORTING
>           out                         TYPE REF TO if_xco_adt_classrun_out
>         RETURNING
>           VALUE(ro_transport_request) TYPE REF TO if_xco_cp_tr_request,
>  
>       release_transport_request
>         IMPORTING
>           io_transport_request TYPE REF TO if_xco_cp_tr_request
>           out                  TYPE REF TO if_xco_adt_classrun_out.
> ENDCLASS.
>  
> CLASS zcl_xco_doc_cp_cs_chg_fm IMPLEMENTATION.
>   METHOD constructor.
>     super->constructor( ).
>  
>     mo_function_module = xco_cp_abap=>function_module( co_function_module_name ).
>   ENDMETHOD.
>  
>   METHOD main.
>     DATA(lo_transport_request) = generate_transport_request( out ).
>  
>     DATA(lo_patch_operation) = xco_cp_generation=>environment->dev_system( lo_transport_request->value
>       )->for-fugr->create_patch_operation( ).
>  
>     DATA(lo_function_group) = mo_function_module->get_function_group( ).
>     lo_patch_operation->add_object( lo_function_group->name
>       )->for-update->add_function_module( mo_function_module->name
>       )->set_source_code( xco_cp=>strings( VALUE #(
>         ( `  " New source code goes here...` )
>       ) ) ).
>  
>     lo_patch_operation->execute( ).
>  
>     release_transport_request(
>       io_transport_request = lo_transport_request
>       out                  = out
>     ).
>   ENDMETHOD.
>  
>   METHOD generate_transport_request.
>     DATA(lo_transport_target) = mo_function_module->get_function_group(
>       )->if_xco_ar_object~get_package(
>       )->read(
>       )-property-transport_layer->get_transport_target( ).
>  
>     ro_transport_request = xco_cp_cts=>transports->workbench( lo_transport_target->value
>       )->create_request( 'Generated transport request' ).
>  
>     out->write( |Using newly generated transport request { ro_transport_request->value }.| ).
>   ENDMETHOD.
>  
>   METHOD release_transport_request.
>     DATA(lt_tasks) = io_transport_request->get_tasks( ).
>  
>     LOOP AT lt_tasks INTO DATA(lo_task).
>       lo_task->release( ).
>     ENDLOOP.
>  
>     io_transport_request->release( ).
>  
>     out->write( |Transport request { io_transport_request->value } has been released.| ).
>   ENDMETHOD.
> ENDCLASS.
> ```

