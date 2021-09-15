<!-- loio5661881f0bb54bd7a1e45111584f0961 -->

# Patching a Message Class

The following code sample illustrates how PATCH operations can be used to change parts of an existing messages class:

> ### Sample Code:  
> ```lang-abap
> "! <p class="shorttext synchronized" lang="EN">
> "!  XCO Documentation CP: Generation PATCH
> "! </p>
> "!
> "! Code sample for executing PATCH operations for messages classes (MSAGs).
> "!
> "! IMPORTANT: The values of the constants CO_PACKAGE and CO_TRANSPORT must be replaced
> "! with an existing package and a modifiable Workbench transport matching the transport
> "! target of the package.
> CLASS zcl_xco_doc_cp_cs_gen_patch DEFINITION PUBLIC FINAL
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
>       co_package            TYPE sxco_package VALUE 'ZXCO_CP_PACKAGE',
>       co_transport          TYPE sxco_transport VALUE 'X08K900164',
>  
>       co_message_class_name TYPE sxco_mc_object_name VALUE 'ZXCO_DEMO_MSG_CLS'.
>  
>     DATA:
>       mo_environment TYPE REF TO if_xco_cp_gen_env_dev_system.
>  
>     METHODS:
>       put_msag,
>  
>       patch_msag_1,
>  
>       patch_msag_2,
>  
>       read_msag
>         IMPORTING
>           out TYPE REF TO if_xco_adt_classrun_out.
> ENDCLASS.
>  
> CLASS zcl_xco_doc_cp_cs_gen_patch IMPLEMENTATION.
>   METHOD constructor.
>     super->constructor( ).
>  
>     mo_environment = xco_cp_generation=>environment->dev_system( co_transport ).
>   ENDMETHOD.
>  
>   METHOD main.
>     put_msag( ).
>     read_msag( out ).
>  
>     patch_msag_1( ).
>     read_msag( out ).
>  
>     patch_msag_2( ).
>     read_msag( out ).
>   ENDMETHOD.
>  
>   METHOD put_msag.
>     DATA(lo_put_operation) = mo_environment->for-msag->create_put_operation( ).
>  
>     DATA(lo_specification) = lo_put_operation->add_object( co_message_class_name
>       )->set_package( co_package
>       )->create_form_specification( ).
>     lo_specification->set_short_description( 'Generated message class' ).
>  
>     lo_specification->add_message( '000'
>       )->set_short_text( 'First message' ).
>  
>     lo_put_operation->execute( ).
>   ENDMETHOD.
>  
>   METHOD patch_msag_1.
>     DATA(lo_patch_operation) = mo_environment->for-msag->create_patch_operation( ).
>  
>     DATA(lo_object) = lo_patch_operation->add_object( co_message_class_name ).
>  
>     " Update existing message.
>     lo_object->for-update->message( '000' )->set_short_text( 'First message (UPDATED)' ).
>  
>     " Insert new message.
>     lo_object->for-insert->add_message( '001' )->set_short_text( 'Second message' ).
>  
>     " Modify non-existing message (will insert the message).
>     lo_object->for-modify->add_message( '002' )->set_short_text( 'Third message' ).
>  
>     lo_patch_operation->execute( ).
>   ENDMETHOD.
>  
>   METHOD patch_msag_2.
>     DATA(lo_patch_operation) = mo_environment->for-msag->create_patch_operation( ).
>  
>     DATA(lo_object) = lo_patch_operation->add_object( co_message_class_name ).
>  
>     " Modify non-existing message (will update the message).
>     lo_object->for-modify->add_message( '002' )->set_short_text( 'Third message (UPDATED)' ).
>  
>     " Delete message
>     lo_object->for-delete->add_message( '000' ).
>  
>     lo_patch_operation->execute( ).
>   ENDMETHOD.
>  
>   METHOD read_msag.
>     DATA(lo_message_class) = xco_cp_abap_repository=>object->msag->for( co_message_class_name ).
>  
>     out->write( |Messages of message class { lo_message_class->name }:| ).
>  
>     LOOP AT lo_message_class->messages->all->get( ) INTO DATA(lo_message).
>       out->write( |Message { lo_message->number }:| ).
>  
>       DATA(ls_message) = lo_message->content( )->get( ).
>       out->write( ls_message ).
>     ENDLOOP.
>   ENDMETHOD.
> ENDCLASS.
> ```

