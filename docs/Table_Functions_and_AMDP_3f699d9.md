<!-- loio3f699d90a6114ccfb1a4ec3205646120 -->

# Table Functions and AMDP

The code sample below provides a self-contained example for the generation of a CDS table function. The CDS table function is generated together with the class providing the AMDP implementation and the underlying database table in a single PUT operation.

> ### Sample Code:  
> ```lang-abap
> "! Code sample for generating a CDS table function together with an AMDP class
> "! and database table.
> "!
> "! IMPORTANT: The values of the constants CO_PACKAGE and CO_TRANSPORT must be replaced
> "! with an existing package and a modifiable Workbench transport request matching the
> "! transport target of the package.
> CLASS zcl_xco_doc_cp_cs_gen_tbl_fnc DEFINITION PUBLIC FINAL
>     INHERITING FROM cl_xco_cp_adt_simple_classrun CREATE PUBLIC.
>   PROTECTED SECTION.
>     METHODS:
>       main REDEFINITION.
> 
>   PRIVATE SECTION.
>     CONSTANTS:
>       co_package             TYPE sxco_package VALUE 'ZXCO_CP_PACKAGE',
>       co_transport           TYPE sxco_transport VALUE 'X08K900164',
> 
>       co_database_table_name TYPE sxco_dbt_object_name VALUE 'ZXCO_TF_DBT',
>       co_table_function_name TYPE sxco_cds_object_name VALUE 'ZXCO_TABLE_FUNCTION',
>       co_amdp_class_name     TYPE sxco_ao_object_name VALUE 'ZCL_XCO_AMDP_CLASS',
> 
>       co_amdp_method_name    TYPE sxco_ao_component_name VALUE 'GET_VALUES'.
> 
>     METHODS:
>       add_database_table
>         IMPORTING
>           io_put_operation TYPE REF TO if_xco_cp_gen_d_o_put,
> 
>       add_table_function
>         IMPORTING
>           io_put_operation TYPE REF TO if_xco_cp_gen_d_o_put,
> 
>       add_class
>         IMPORTING
>           io_put_operation TYPE REF TO if_xco_cp_gen_d_o_put.
> ENDCLASS.
> 
> CLASS zcl_xco_doc_cp_cs_gen_tbl_fnc IMPLEMENTATION.
>   METHOD main.
>     DATA(lo_put_operation) = xco_cp_generation=>environment->dev_system( co_transport
>       )->create_put_operation( ).
> 
>     add_database_table( lo_put_operation ).
>     add_table_function( lo_put_operation ).
>     add_class( lo_put_operation ).
> 
>     lo_put_operation->execute( ).
> 
>     out->write( |Table function { co_table_function_name } generated successfully.| ).
>   ENDMETHOD.
> 
>   METHOD add_database_table.
>     DATA(lo_specification) = io_put_operation->for-tabl-for-database_table->add_object( co_database_table_name
>       )->set_package( co_package
>       )->create_form_specification( ).
>     lo_specification->set_short_description( 'GENERATED' ).
> 
>     lo_specification->add_field( 'CLIENT'
>       )->set_type( xco_cp_abap_dictionary=>built_in_type->clnt
>       )->set_key_indicator(
>       )->set_not_null( ).
> 
>     lo_specification->add_field( 'IDENTIFIER'
>       )->set_type( xco_cp_abap_dictionary=>built_in_type->char( 30 )
>       )->set_key_indicator(
>       )->set_not_null( ).
> 
>     lo_specification->add_field( 'START_DATE'
>       )->set_type( xco_cp_abap_dictionary=>built_in_type->dats ).
>   ENDMETHOD.
> 
>   METHOD add_table_function.
>     DATA(lo_form_specification) = io_put_operation->for-ddls->add_object( co_table_function_name
>       )->set_package( co_package
>       )->create_form_specification( ).
> 
>     DATA(lo_table_function) = lo_form_specification->set_short_description( 'GENERATED'
>       )->add_table_function( ).
> 
>     lo_table_function->add_annotation( 'AccessControl.authorizationCheck'
>       )->value->build( )->add_enum( 'NOT_REQUIRED' ).
> 
>     DATA(lo_parameter) = lo_table_function->add_parameter( 'p_identifier'
>       )->set_data_type( xco_cp_abap_dictionary=>data_element( 'char30' ) ).
> 
>     DATA(lo_client_field) = lo_table_function->add_field( xco_cp_ddl=>field( 'client' ) ).
>     lo_client_field->set_type( xco_cp_abap_dictionary=>built_in_type->clnt ).
> 
>     DATA(lo_val_identifier_field) = lo_table_function->add_field( xco_cp_ddl=>field( 'val_identifier' ) ).
>     lo_val_identifier_field->set_type( xco_cp_abap_dictionary=>built_in_type->char( 30 ) ).
> 
>     lo_val_identifier_field->add_annotation( 'EndUserText.label'
>       )->value->set( xco_cp_cds_annotation=>value->string( 'Identifier field' ) ) ##NO_TEXT.
> 
>     lo_table_function->set_amdp_class( co_amdp_class_name
>       )->set_amdp_method( co_amdp_method_name ).
>   ENDMETHOD.
> 
>   METHOD add_class.
>     DATA(lo_form_specification) = io_put_operation->for-clas->add_object( co_amdp_class_name
>       )->set_package( co_package
>       )->create_form_specification( ).
>     lo_form_specification->set_short_description( 'GENERATED' ).
> 
>     lo_form_specification->definition->add_interface( 'IF_AMDP_MARKER_HDB' ).
> 
>     DATA(lo_class_method) = lo_form_specification->definition->section-public->add_class_method( CONV #( co_amdp_method_name ) ).
>     lo_class_method->amdp->set_for_table_function( co_table_function_name ).
> 
>     lo_form_specification->implementation->add_method( CONV #( co_amdp_method_name )
>       )->set_source( VALUE #(
>         ( |RETURN| ) ##NO_TEXT
>         ( |SELECT CLIENT, IDENTIFIER AS val_identifier FROM { co_database_table_name }| ) ##NO_TEXT
>         ( |WHERE IDENTIFIER = :p_identifier;| ) ##NO_TEXT
>       ) )->amdp->mark_as_function(
>       )->set_database_type( xco_cp_amdp=>database_type->hdb
>       )->set_database_language( xco_cp_amdp=>database_language->sqlscript
>       )->set_database_options( VALUE #( ( xco_cp_amdp=>database_option->read_only ) )
>       )->set_database_entities( VALUE #( ( co_database_table_name ) ) ).
>   ENDMETHOD.
> ENDCLASS.
> ```

