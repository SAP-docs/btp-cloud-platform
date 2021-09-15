<!-- loioda6786e8afa348e6b107f21486677f96 -->

# Generating and Reading Global Temporary Tables

The following code sample illustrates how global temporary tables can be generated and read with the XCO Library:

```lang-abap
"! <p class="shorttext synchronized" lang="EN">
"!  XCO Documentation CP: Global temporary tables
"! </p>
"!
"! Code sample for generating and reading global temporary tables.
"!
"! IMPORTANT: The value of the constant CO_PACKAGE  must be replaced with an existing
"! development package.
CLASS zcl_xco_doc_cp_cs_abs_ent DEFINITION PUBLIC FINAL
    INHERITING FROM cl_xco_cp_adt_simple_classrun CREATE PUBLIC.
  PUBLIC SECTION.
    METHODS:
      constructor.
 
  PROTECTED SECTION.
    METHODS:
      main REDEFINITION.
 
  PRIVATE SECTION.
    CONSTANTS:
      co_package                    TYPE sxco_package VALUE 'ZMY_PACKAGE',
 
      co_global_temporary_table_name TYPE sxco_gtt_object_name VALUE 'ZXCO_GTT'.
 
    DATA:
      mo_global_temporary_table TYPE REF TO if_xco_global_temporary_table.
 
    METHODS:
      put_global_temporary_table
        IMPORTING
          out TYPE REF TO if_xco_adt_classrun_out,
 
      get_generation_environment
        IMPORTING
          out                             TYPE REF TO if_xco_adt_classrun_out
        RETURNING
          VALUE(ro_generation_environment) TYPE REF TO if_xco_cp_gen_env_dev_system,
 
      get_transport_request
        IMPORTING
          out                        TYPE REF TO if_xco_adt_classrun_out
        RETURNING
          VALUE(ro_transport_request) TYPE REF TO if_xco_cp_tr_request.
ENDCLASS.
 
CLASS zcl_xco_doc_cp_cs_abs_ent IMPLEMENTATION.
  METHOD constructor.
    super->constructor( ).
 
    mo_global_temporary_table = xco_cp_abap_dictionary=>global_temporary_table( co_global_temporary_table_name ).
  ENDMETHOD.
 
  METHOD main.
    put_global_temporary_table( out ).
    out->write( |PUT operation executed successfully.| ).
 
    DATA(ls_global_temporary_table) = mo_global_temporary_table->content( )->get( ).
    out->write( ls_global_temporary_table ).
 
    LOOP AT mo_global_temporary_table->fields->all->get( ) INTO DATA(lo_field).
      out->write( |Field { lo_field->name }:| ).
 
      DATA(ls_field) = lo_field->content( )->get( ).
      out->write( ls_field ).
    ENDLOOP.
  ENDMETHOD.
 
  METHOD put_global_temporary_table.
    DATA(lo_put_operation) = get_generation_environment( out )->create_put_operation( ).
 
    DATA(lo_form_specification) = lo_put_operation->for-tabl-for-global_temporary_table->add_object( mo_global_temporary_table->name
      )->set_package( co_package
      )->create_form_specification( ).
    lo_form_specification->set_short_description( 'Generated global temporary table' ).
 
    lo_form_specification->add_field( 'KEY_FIELD'
      )->set_type( xco_cp_abap_dictionary=>built_in_type->char( 10 )
      )->set_key_indicator(
      )->set_not_null( ).
 
    lo_form_specification->add_field( 'DATA_FIELD'
      )->set_type( xco_cp_abap_dictionary=>built_in_type->char( 60 ) ).
 
    lo_put_operation->execute( ).
  ENDMETHOD.
 
  METHOD get_generation_environment.
    DATA(lo_transport_request) = get_transport_request( out ).
 
    ro_generation_environment = xco_cp_generation=>environment->dev_system( lo_transport_request->value ).
  ENDMETHOD.
 
  METHOD get_transport_request.
    DATA(lo_lock) = mo_global_temporary_table->if_xco_cts_changeable~get_object(
      )->get_lock( ).
 
    IF lo_lock->exists( ) EQ abap_true.
      DATA(lv_transport) = lo_lock->get_transport( ).
 
      ro_transport_request = xco_cp_cts=>transport->for( lv_transport
        )->get_request( ).
 
      out->write( |Using transport request { ro_transport_request->value } (Global temporary table is already locked).| ).
    ELSE.
      DATA(lo_transport_target) = xco_cp_abap_repository=>package->for( co_package
        )->read(
        )-property-transport_layer->get_transport_target( ).
 
      ro_transport_request = xco_cp_cts=>transports->workbench( lo_transport_target->value
        )->create_request( 'Generated transport request' ).
 
      out->write( |Using newly generated transport request { ro_transport_request->value }.| ).
    ENDIF.
  ENDMETHOD.
ENDCLASS.
```

