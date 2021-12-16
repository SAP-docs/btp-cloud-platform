<!-- loio6715116a95a046a38c471e4979389c63 -->

# Function Module Generation

The following code sample illustrates the generation of function modules:

> ### Sample Code:  
> ```lang-abap
> "! Code sample for generating a function module along with a function group
> "! that contains it.
> "!
> "! IMPORTANT: The values of the constants CO_PACKAGE and CO_TRANSPORT must be replaced
> "! with an existing package and a modifiable Workbench transport request matching the
> "! transport target of the package.
> CLASS zcl_xco_doc_cp_cs_gen_fm DEFINITION PUBLIC FINAL
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
>       co_package              TYPE sxco_package VALUE 'ZXCO_CP_PACKAGE',
>       co_transport            TYPE sxco_transport VALUE 'X08K900164',
> 
>       co_function_group_name  TYPE sxco_fg_object_name VALUE 'ZXCO_GEN_FUGR_FG',
>       co_function_module_name TYPE sxco_fm_name VALUE 'ZXCO_GEN_FUGR_FM'.
> 
>     DATA:
>       mo_function_group  TYPE REF TO if_xco_function_group,
>       mo_function_module TYPE REF TO if_xco_function_module,
> 
>       mo_environment     TYPE REF TO if_xco_cp_gen_env_dev_system.
> 
>     METHODS:
>       set_up_function_group
>         IMPORTING
>           out TYPE REF TO if_xco_adt_classrun_out,
> 
>       post_function_group,
> 
>       delete_function_modules
>         IMPORTING
>           out TYPE REF TO if_xco_adt_classrun_out,
> 
>       insert_function_modules
>         IMPORTING
>           out TYPE REF TO if_xco_adt_classrun_out.
> ENDCLASS.
> 
> CLASS zcl_xco_doc_cp_cs_gen_fm IMPLEMENTATION.
>   METHOD constructor.
>     super->constructor( ).
> 
>     mo_function_group = xco_cp_abap=>function_group( co_function_group_name ).
>     mo_function_module = xco_cp_abap=>function_module( co_function_module_name ).
> 
>     mo_environment = xco_cp_generation=>environment->dev_system( co_transport ).
>   ENDMETHOD.
> 
>   METHOD main.
>     set_up_function_group( out ).
> 
>     delete_function_modules( out ).
>     insert_function_modules( out ).
>   ENDMETHOD.
> 
>   METHOD set_up_function_group.
>     IF mo_function_group->if_xco_ar_object~exists( ) EQ abap_true.
>       out->write( |Function group { mo_function_group->name } already exists.| ).
>     ELSE.
>       post_function_group( ).
> 
>       out->write( |Function group { mo_function_group->name } created successfully.| ).
>     ENDIF.
>   ENDMETHOD.
> 
>   METHOD post_function_group.
>     DATA(lo_post_operation) = mo_environment->for-fugr->create_post_operation( ).
> 
>     DATA(lo_form_specification) = lo_post_operation->add_object( xco_cp_name=>choice->fixed( co_function_group_name )
>       )->set_package( co_package
>       )->create_form_specification( ).
>     lo_form_specification->set_short_description( 'Generated FUGR' ).
> 
>     lo_post_operation->execute( ).
>   ENDMETHOD.
> 
>   METHOD delete_function_modules.
>     DATA(lo_patch_operation) = mo_environment->for-fugr->create_patch_operation( ).
> 
>     DATA(lt_function_module_names) = mo_function_group->function_modules->all->get_names( ).
> 
>     LOOP AT lt_function_module_names INTO DATA(lv_function_module_name).
>       lo_patch_operation->add_object( co_function_group_name
>         )->for-delete->add_function_module( lv_function_module_name ).
>     ENDLOOP.
> 
>     lo_patch_operation->execute( ).
> 
>     out->write( |Function modules of function group { mo_function_group->name } deleted succesfully.| ).
>   ENDMETHOD.
> 
>   METHOD insert_function_modules.
>     DATA(lo_patch_operation) = mo_environment->for-fugr->create_patch_operation( ).
> 
>     DATA(lo_function_module) = lo_patch_operation->add_object( co_function_group_name
>       )->for-insert->add_function_module( co_function_module_name ).
> 
>     " IMPORTING parameters.
>     lo_function_module->add_importing_parameter( 'IM_CLASS'
>       )->set_type( xco_cp_abap=>class( 'CL_XCO_AD_BUILT_IN_TYPE' )
>       )->set_optional( ).
> 
>     lo_function_module->add_importing_parameter( 'IM_INTERFACE'
>       )->set_type( xco_cp_abap=>interface( 'IF_XCO_NEWS' ) ).
> 
>     lo_function_module->add_importing_parameter( 'IM_ABAP_BUILT_IN_TYPE'
>       )->set_type( xco_cp_abap=>type-built_in->i
>       )->set_default_value( '5' ).
> 
>     lo_function_module->add_importing_parameter( 'IM_ABAP_BIT_REFERENCE'
>       )->set_type( xco_cp_abap=>type-built_in->i->reference( ) ).
> 
>     lo_function_module->add_importing_parameter( 'IM_ABAP_GENERIC_TYPE'
>       )->set_type( xco_cp_abap=>type-generic->c ).
> 
>     lo_function_module->add_importing_parameter( 'IM_ABAP_GT_REFERENCE'
>       )->set_type( xco_cp_abap=>type-generic->data->reference( ) ).
> 
>     lo_function_module->add_importing_parameter( 'IM_DATA_ELEMENT'
>       )->set_type( xco_cp_abap_dictionary=>data_element( 'SXCO_FM_NAME' ) ).
> 
>     " EXPORTING parameters.
>     lo_function_module->add_exporting_parameter( 'EX_STRING'
>       )->set_type( xco_cp_abap=>type-built_in->string ).
> 
>     " CHANGING parameters.
>     lo_function_module->add_exporting_parameter( 'CH_ANY'
>       )->set_type( xco_cp_abap=>type-generic->any ).
> 
>     " Exceptions.
>     lo_function_module->add_exception( 'CX_ABAP_INVALID_NAME' ).
> 
>     lo_function_module->add_exception( 'CX_ABAP_INVALID_VALUE'
>       )->set_resumable( abap_true ).
> 
>     " Source code.
>     lo_function_module->set_source_code( xco_cp=>strings( VALUE #(
>       ( |DATA lo_string TYPE REF TO if_xco_string.| )
>     ) ) ).
> 
>     lo_patch_operation->execute( ).
> 
>     out->write( |Inserted function module { mo_function_module->name } into function group { mo_function_group->name }.| ).
>   ENDMETHOD.
> ENDCLASS.
> ```

