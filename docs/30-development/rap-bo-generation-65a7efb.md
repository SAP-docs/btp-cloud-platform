<!-- loio65a7efb4e3114e2aaaf95dc8612c0945 -->

# RAP BO Generation

The following code sample illustrates how a complete RAP business object, starting from domains for fixed values all the way up to a service binding, can be generated with the XCO Generation APIs:

> ### Sample Code:  
> ```lang-abap
> "! Code sample for executing PUT operations to generate a full RAP business object.
> "!
> "! IMPORTANT: The values of the constants CO_PACKAGE and CO_TRANSPORT must be replaced
> "! with an existing package and a modifiable Workbench transport matching the transport
> "! target of the package.
> CLASS zcl_xco_doc_cp_cs_gen_put DEFINITION PUBLIC FINAL
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
>       co_package               TYPE sxco_package VALUE 'ZXCO_CP_PACKAGE',
>       co_transport             TYPE sxco_transport VALUE 'X08K900164',
> 
>       co_doma_status           TYPE sxco_ad_object_name VALUE 'ZXCO_CP_VR_STATUS',
>       co_dtel_status           TYPE sxco_ad_object_name VALUE 'ZXCO_CP_VR_STATUS',
>       co_tabl_dbt_name         TYPE sxco_dbt_object_name VALUE 'ZXCO_CP_VAC_REQ',
>       co_ddls_interface_name   TYPE sxco_cds_object_name VALUE 'ZXCO_CP_I_VACATION_REQUEST',
>       co_ddls_consumption_name TYPE sxco_cds_object_name VALUE 'ZXCO_CP_C_VACATION_REQUEST',
>       co_ddlx_name             TYPE sxco_cds_object_name VALUE 'ZXCO_CP_VACATION_REQUEST_EXT',
>       co_dcls_name             TYPE sxco_cds_object_name VALUE 'ZXCO_CP_VACTION_REQUEST_AC',
>       co_clas_name             TYPE sxco_ad_object_name VALUE 'ZXCO_CP_BP_VACATION_REQUEST',
>       co_srvd_name             TYPE sxco_srvd_object_name VALUE 'ZXCO_CP_VAC_REQ_SRVD',
>       co_srvb_name             TYPE sxco_srvb_object_name VALUE 'ZXCO_CP_VAC_REQ_SRVB'.
> 
>     DATA:
>       mo_environment TYPE REF TO if_xco_cp_gen_env_dev_system.
> 
>     METHODS:
>       add_doma
>         IMPORTING
>           io_put_operation TYPE REF TO if_xco_cp_gen_d_o_put,
> 
>       add_dtel
>         IMPORTING
>           io_put_operation TYPE REF TO if_xco_cp_gen_d_o_put,
> 
>       add_tabl_dbt
>         IMPORTING
>           io_put_operation TYPE REF TO if_xco_cp_gen_d_o_put,
> 
>       add_ddls
>         IMPORTING
>           io_put_operation TYPE REF TO if_xco_cp_gen_d_o_put,
> 
>       add_ddlx
>         IMPORTING
>           io_put_operation TYPE REF TO if_xco_cp_gen_d_o_put,
> 
>       add_dcls
>         IMPORTING
>           io_put_operation TYPE REF TO if_xco_cp_gen_d_o_put,
> 
>       add_bdef
>         IMPORTING
>           io_put_operation TYPE REF TO if_xco_cp_gen_d_o_put,
> 
>       add_clas
>         IMPORTING
>           io_put_operation TYPE REF TO if_xco_cp_gen_d_o_put,
> 
>       add_srvd
>         IMPORTING
>           io_put_operation TYPE REF TO if_xco_cp_gen_d_o_put,
> 
>       put_srvb.
> ENDCLASS.
> 
> CLASS zcl_xco_doc_cp_cs_gen_put IMPLEMENTATION.
>   METHOD constructor.
>     super->constructor( ).
> 
>     mo_environment = xco_cp_generation=>environment->dev_system( co_transport ).
>   ENDMETHOD.
> 
>   METHOD main.
>     DATA(lo_put_operation) = mo_environment->create_put_operation( ).
> 
>     add_doma( lo_put_operation ).
>     add_dtel( lo_put_operation ).
>     add_tabl_dbt( lo_put_operation ).
>     add_ddls( lo_put_operation ).
>     add_ddlx( lo_put_operation ).
>     add_dcls( lo_put_operation ).
>     add_bdef( lo_put_operation ).
>     add_clas( lo_put_operation ).
>     add_srvd( lo_put_operation ).
> 
>     lo_put_operation->execute( ).
> 
>     put_srvb( ).
> 
>     out->write( |PUT operations executed successfully.| ).
>   ENDMETHOD.
> 
>   METHOD add_doma.
>     DATA(lo_specification) = io_put_operation->for-doma->add_object( co_doma_status
>       )->set_package( co_package
>       )->create_form_specification( ).
>     lo_specification->set_short_description( 'Vacation request status' ).
> 
>     lo_specification->set_format( xco_cp_abap_dictionary=>built_in_type->char( 10 ) ).
> 
>     lo_specification->fixed_values->add_fixed_value( 'APPROVED'
>       )->set_description( 'Approved' ).
>     lo_specification->fixed_values->add_fixed_value( 'DECLINED'
>       )->set_description( 'Declined' ).
>   ENDMETHOD.
> 
>   METHOD add_dtel.
>     DATA(lo_specification) = io_put_operation->for-dtel->add_object( co_dtel_status
>       )->set_package( co_package
>       )->create_form_specification( ).
>     lo_specification->set_short_description( 'Vacation request status' ).
> 
>     lo_specification->set_data_type( xco_cp_abap_dictionary=>domain( co_doma_status ) ).
>   ENDMETHOD.
> 
>   METHOD add_tabl_dbt.
>     DATA(lo_specification) = io_put_operation->for-tabl-for-database_table->add_object( co_tabl_dbt_name
>       )->set_package( co_package
>       )->create_form_specification( ).
>     lo_specification->set_short_description( 'Vacation request'
>       )->set_delivery_class( xco_cp_database_table=>delivery_class->a
>       )->set_data_maintenance( xco_cp_database_table=>data_maintenance->allowed ).
> 
>     lo_specification->add_field( 'CLIENT' )->set_type( xco_cp_abap_dictionary=>built_in_type->clnt
>       )->set_key_indicator(
>       )->set_not_null( ).
>     lo_specification->add_field( 'IDENTIFIER' )->set_type( xco_cp_abap_dictionary=>built_in_type->char( 30 )
>       )->set_key_indicator(
>       )->set_not_null( ).
>     lo_specification->add_field( 'START_DATE' )->set_type( xco_cp_abap_dictionary=>built_in_type->dats ).
>     lo_specification->add_field( 'END_DATE' )->set_type( xco_cp_abap_dictionary=>built_in_type->dats ).
>     lo_specification->add_field( 'STATUS' )->set_type( xco_cp_abap_dictionary=>data_element( co_dtel_status ) ).
>     lo_specification->add_field( 'IS_ACTIVE' )->set_type( xco_cp_abap_dictionary=>data_element( 'ABAP_BOOLEAN' ) ).
>   ENDMETHOD.
> 
>   METHOD add_ddls.
>     DATA(lo_interface_specification) = io_put_operation->for-ddls->add_object( co_ddls_interface_name
>       )->set_package( co_package
>       )->create_form_specification( ).
> 
>     DATA(lo_view_entity) = lo_interface_specification->set_short_description( 'Vacation request'
>       )->add_view_entity( ).
>     lo_view_entity->set_root( )->data_source->set_view_entity( CONV #( co_tabl_dbt_name ) ).
>     lo_view_entity->set_where( xco_cp_ddl=>field( 'is_active' )->eq( xco_cp_ddl=>literal->character( 'X' ) ) ).
> 
>     " View annotations.
>     lo_view_entity->add_annotation( 'AccessControl.authorizationCheck' )->value->build( )->add_enum( 'CHECK' ).
>     lo_view_entity->add_annotation( 'EndUserText.label' )->value->build( )->add_string( 'Vacation request view entity' ).
>     lo_view_entity->add_annotation( 'Metadata.allowExtensions' )->value->build( )->add_boolean( abap_true ).
> 
>     " Add fields.
>     DATA(lo_identifier) = lo_view_entity->add_field( xco_cp_ddl=>field( 'identifier' ) )->set_key( )->set_alias( 'Identifier' ).
>     lo_identifier->add_annotation( 'EndUserText.label' )->value->build( )->add_string( 'Identifier' ).
> 
>     lo_view_entity->add_field( xco_cp_ddl=>field( 'start_date' ) )->set_alias( 'StartDate' ).
>     lo_view_entity->add_field( xco_cp_ddl=>field( 'end_date' ) )->set_alias( 'EndDate' ).
>     lo_view_entity->add_field( xco_cp_ddl=>field( 'status' ) )->set_alias( 'Status' ).
> 
>     DATA(lo_consumption_specification) = io_put_operation->for-ddls->add_object( co_ddls_consumption_name
>       )->set_package( co_package
>       )->create_form_specification( ).
> 
>     DATA(lo_projection_view) = lo_consumption_specification->set_short_description( 'Vacation request projection'
>       )->add_projection_view( ).
>     lo_projection_view->set_root( ).
>     lo_projection_view->data_source->set_view_entity( co_ddls_interface_name ).
> 
>     lo_projection_view->add_field( xco_cp_ddl=>field( 'Identifier' ) )->set_key( ).
>     lo_projection_view->add_field( xco_cp_ddl=>field( 'StartDate' ) ).
>     lo_projection_view->add_field( xco_cp_ddl=>field( 'EndDate' ) ).
>     lo_projection_view->add_field( xco_cp_ddl=>field( 'Status' ) ).
>   ENDMETHOD.
> 
>   METHOD add_ddlx.
>     DATA(lo_specification) = io_put_operation->for-ddlx->add_object( co_ddlx_name
>       )->set_package( co_package
>       )->create_form_specification( ).
> 
>     lo_specification->set_short_description( 'Vacation request extension'
>       )->set_layer( xco_cp_metadata_extension=>layer->customer
>       )->set_view( co_ddls_interface_name ).
> 
>     " UI annotations.
>     TYPES:
>       BEGIN OF ts_field,
>         name  TYPE sxco_cds_field_name,
>         label TYPE string,
>       END OF ts_field,
> 
>       tt_field TYPE STANDARD TABLE OF ts_field WITH EMPTY KEY.
> 
>     DATA(lt_fields) = VALUE tt_field(
>       ( name = 'Identifier' label = 'Identifier' )
>       ( name = 'StartDate' label = 'Start Date' )
>       ( name = 'EndDate' label = 'End Date' )
>       ( name = 'Status' label = 'Status' )
>     ).
> 
>     LOOP AT lt_fields INTO DATA(ls_field).
>       DATA(lv_position) = sy-tabix * 10.
> 
>       DATA(lo_field) = lo_specification->add_field( ls_field-name ).
>       lo_field->add_annotation( 'UI.lineItem' )->value->build(
>         )->begin_array(
>           )->begin_record(
>             )->add_member( 'position' )->add_number( lv_position
>             )->add_member( 'label' )->add_string( ls_field-label
>           )->end_record(
>         )->end_array( ).
> 
>       lo_field->add_annotation( 'UI.identification' )->value->build(
>         )->begin_array(
>           )->begin_record(
>             )->add_member( 'position' )->add_number( lv_position
>             )->add_member( 'label' )->add_string( ls_field-label
>           )->end_record(
>         )->end_array( ).
>     ENDLOOP.
>   ENDMETHOD.
> 
>   METHOD add_dcls.
>     DATA(lo_specification) = io_put_operation->for-dcls->add_object( co_dcls_name
>       )->set_package( co_package
>       )->create_form_specification( ).
>     lo_specification->set_short_description( 'Vacation request access control' ).
> 
>     DATA(lo_role) = lo_specification->add_role( ).
>     lo_role->add_annotation( 'Mapping.Role' )->value->build(
>       )->add_boolean( abap_true ).
>     lo_role->add_access_rule( co_ddls_interface_name
>       )->set_where( xco_cp_dcl=>field( 'Identifier' )->is_not_initial( ) ).
>   ENDMETHOD.
> 
>   METHOD add_bdef.
>     DATA(lo_interface_specification) = io_put_operation->for-bdef->add_object( co_ddls_interface_name
>       )->set_package( co_package
>       )->create_form_specification( ).
>     lo_interface_specification->set_short_description( 'Vacation request behavior'
>       )->set_implementation_type( xco_cp_behavior_definition=>implementation_type->managed
>       )->set_implementation_class( co_clas_name ).
> 
>     DATA(lo_interface_behavior) = lo_interface_specification->add_behavior( ).
> 
>     " Characteristics.
>     lo_interface_behavior->characteristics->set_persistent_table( co_tabl_dbt_name
>       )->lock->set_master( ).
> 
>     " Fields.
>     lo_interface_behavior->add_mapping_for( co_tabl_dbt_name )->set_field_mapping( VALUE #(
>       ( cds_view_field = 'Identifier' dbtable_field = 'identifier' )
>       ( cds_view_field = 'StartDate' dbtable_field = 'start_date' )
>       ( cds_view_field = 'EndDate' dbtable_field = 'end_date' )
>       ( cds_view_field = 'Status' dbtable_field = 'status' )
>     ) ).
> 
>     " Standard operations.
>     lo_interface_behavior->add_standard_operation( xco_cp_behavior_definition=>standard_operation->create ).
>     lo_interface_behavior->add_standard_operation( xco_cp_behavior_definition=>standard_operation->update ).
>     lo_interface_behavior->add_standard_operation( xco_cp_behavior_definition=>standard_operation->delete ).
> 
>     " Action.
>     DATA(lo_action) = lo_interface_behavior->add_action( 'approve' ).
>     lo_action->set_external_name( 'Approve' ).
>     lo_action->result->set_cardinality( xco_cp_cds=>cardinality->one )->set_self( ).
> 
>     DATA(lo_consumption_specification) = io_put_operation->for-bdef->add_object( co_ddls_consumption_name
>       )->set_package( co_package
>       )->create_form_specification( ).
>     lo_consumption_specification->set_short_description( 'Vacation request behavior projection'
>       )->set_implementation_type( xco_cp_behavior_definition=>implementation_type->projection ).
> 
>     DATA(lo_consumption_behavior) = lo_consumption_specification->add_behavior( ).
>     lo_consumption_behavior->add_standard_operation( xco_cp_behavior_definition=>standard_operation->create
>       )->set_use( ).
>     lo_consumption_behavior->add_standard_operation( xco_cp_behavior_definition=>standard_operation->update
>       )->set_use( ).
>     lo_consumption_behavior->add_standard_operation( xco_cp_behavior_definition=>standard_operation->delete
>       )->set_use( ).
>   ENDMETHOD.
> 
>   METHOD add_clas.
>     DATA(lo_specification) = io_put_operation->for-clas->add_object( co_clas_name
>       )->set_package( co_package
>       )->create_form_specification( ).
>     lo_specification->set_short_description( 'Behavior implementation' ).
> 
>     lo_specification->definition->set_abstract(
>       )->set_for_behavior_of( co_ddls_interface_name ).
> 
>     DATA(lo_handler) = lo_specification->add_local_class( 'LCL_HANDLER' ).
>     lo_handler->definition->set_superclass( 'CL_ABAP_BEHAVIOR_HANDLER' ).
> 
>     " Action implementation.
>     DATA(lo_publish) = lo_handler->definition->section-private->add_method( 'APPROVE' ).
>     lo_publish->behavior_implementation->set_for_modify(
>       )->set_result( co_ddls_interface_name ).
>     lo_publish->add_importing_parameter( 'IT_VACATION_REQUESTS'
>       )->behavior_implementation->set_for_action(
>         iv_entity_name = co_ddls_interface_name
>         iv_action_name = 'approve'
>     ).
> 
>     lo_handler->implementation->add_method( 'APPROVE' ).
>   ENDMETHOD.
> 
>   METHOD add_srvd.
>     DATA(lo_specification) = io_put_operation->for-srvd->add_object( co_srvd_name
>       )->set_package( co_package
>       )->create_form_specification( ).
>     lo_specification->set_short_description( 'Service definition' ).
> 
>     lo_specification->add_annotation( 'EndUserText.label' )->value->build( )->add_string( 'Vacation request service definition' ).
>     lo_specification->add_exposure( co_ddls_consumption_name )->set_alias( 'VacationRequest' ).
>   ENDMETHOD.
> 
>   METHOD put_srvb.
>     DATA(lo_put_operation) = mo_environment->for-srvb->create_put_operation( ).
> 
>     DATA(lo_specification) = lo_put_operation->add_object( co_srvb_name
>       )->set_package( co_package
>       )->create_form_specification( ).
>     lo_specification->set_short_description( 'Service binding' ).
> 
>     lo_specification->set_binding_type( xco_cp_service_binding=>binding_type->odata_v2_ui ).
>     lo_specification->add_service( )->add_version( '0001' )->set_service_definition( co_srvd_name ).
> 
>     lo_put_operation->execute( ).
>   ENDMETHOD.
> ENDCLASS.
> ```

All objects generated with the previous code sample can also be deleted again:

> ### Sample Code:  
> ```lang-abap
> "! Code sample for executing DELETE operations to delete all objects of a full RAP business
> "! object.
> "!
> "! IMPORTANT: The value of the constant CO_TRANSPORT must be replaced with a modifiable Workbench
> "! transport matching the transport target of the package containing the objects.
> CLASS zcl_xco_doc_cp_cs_gen_delete DEFINITION PUBLIC FINAL
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
>       co_transport             TYPE sxco_transport VALUE 'X08K900164',
> 
>       co_doma_status           TYPE sxco_ad_object_name VALUE 'ZXCO_CP_VR_STATUS',
>       co_dtel_status           TYPE sxco_ad_object_name VALUE 'ZXCO_CP_VR_STATUS',
>       co_tabl_dbt_name         TYPE sxco_dbt_object_name VALUE 'ZXCO_CP_VAC_REQ',
>       co_ddls_interface_name   TYPE sxco_cds_object_name VALUE 'ZXCO_CP_I_VACATION_REQUEST',
>       co_ddls_consumption_name TYPE sxco_cds_object_name VALUE 'ZXCO_CP_C_VACATION_REQUEST',
>       co_ddlx_name             TYPE sxco_cds_object_name VALUE 'ZXCO_CP_VACATION_REQUEST_EXT',
>       co_dcls_name             TYPE sxco_cds_object_name VALUE 'ZXCO_CP_VACTION_REQUEST_AC',
>       co_clas_name             TYPE sxco_ad_object_name VALUE 'ZXCO_CP_BP_VACATION_REQUEST',
>       co_srvd_name             TYPE sxco_srvd_object_name VALUE 'ZXCO_CP_VAC_REQ_SRVD',
>       co_srvb_name             TYPE sxco_srvb_object_name VALUE 'ZXCO_CP_VAC_REQ_SRVB'.
> 
>     DATA:
>       mo_environment TYPE REF TO if_xco_cp_gen_env_dev_system.
> 
>     METHODS:
>       delete_srvb,
> 
>       delete_srvd,
> 
>       delete_clas,
> 
>       delete_bdef,
> 
>       delete_dcls,
> 
>       delete_ddlx,
> 
>       delete_ddls,
> 
>       delete_tabl_dbt,
> 
>       delete_dtel,
> 
>       delete_doma.
> ENDCLASS.
> 
> CLASS zcl_xco_doc_cp_cs_gen_delete IMPLEMENTATION.
>   METHOD constructor.
>     super->constructor( ).
> 
>     mo_environment = xco_cp_generation=>environment->dev_system( co_transport ).
>   ENDMETHOD.
> 
>   METHOD main.
>     DATA(lo_put_operation) = mo_environment->create_put_operation( ).
> 
>     delete_srvb( ).
>     delete_srvd( ).
>     delete_clas( ).
>     delete_bdef( ).
>     delete_dcls( ).
>     delete_ddlx( ).
>     delete_ddls( ).
>     delete_tabl_dbt( ).
>     delete_dtel( ).
>     delete_doma( ).
> 
>     out->write( |DELETE operations executed successfully.| ).
>   ENDMETHOD.
> 
>   METHOD delete_srvb.
>     DATA(lo_delete_operation) = mo_environment->for-srvb->create_delete_operation( ).
>     lo_delete_operation->add_object( co_srvb_name ).
>     lo_delete_operation->execute( ).
>   ENDMETHOD.
> 
>   METHOD delete_srvd.
>     DATA(lo_delete_operation) = mo_environment->for-srvd->create_delete_operation( ).
>     lo_delete_operation->add_object( co_srvd_name ).
>     lo_delete_operation->execute( ).
>   ENDMETHOD.
> 
>   METHOD delete_clas.
>     DATA(lo_delete_operation) = mo_environment->for-clas->create_delete_operation( ).
>     lo_delete_operation->add_object( co_clas_name ).
>     lo_delete_operation->execute( ).
>   ENDMETHOD.
> 
>   METHOD delete_bdef.
>     DATA(lo_delete_operation) = mo_environment->for-bdef->create_delete_operation( ).
>     lo_delete_operation->add_object( co_ddls_consumption_name ).
>     lo_delete_operation->add_object( co_ddls_interface_name ).
>     lo_delete_operation->execute( ).
>   ENDMETHOD.
> 
>   METHOD delete_dcls.
>     DATA(lo_delete_operation) = mo_environment->for-dcls->create_delete_operation( ).
>     lo_delete_operation->add_object( co_dcls_name ).
>     lo_delete_operation->execute( ).
>   ENDMETHOD.
> 
>   METHOD delete_ddlx.
>     DATA(lo_delete_operation) = mo_environment->for-ddlx->create_delete_operation( ).
>     lo_delete_operation->add_object( co_ddlx_name ).
>     lo_delete_operation->execute( ).
>   ENDMETHOD.
> 
>   METHOD delete_ddls.
>     DATA(lo_delete_operation) = mo_environment->for-ddls->create_delete_operation( ).
>     lo_delete_operation->add_object( co_ddls_consumption_name ).
>     lo_delete_operation->add_object( co_ddls_interface_name ).
>     lo_delete_operation->execute( ).
>   ENDMETHOD.
> 
>   METHOD delete_tabl_dbt.
>     DATA(lo_delete_operation) = mo_environment->for-tabl-for-database_table->create_delete_operation( ).
>     lo_delete_operation->add_object( co_tabl_dbt_name ).
>     lo_delete_operation->execute( ).
>   ENDMETHOD.
> 
>   METHOD delete_dtel.
>     DATA(lo_delete_operation) = mo_environment->for-dtel->create_delete_operation( ).
>     lo_delete_operation->add_object( co_dtel_status ).
>     lo_delete_operation->execute( ).
>   ENDMETHOD.
> 
>   METHOD delete_doma.
>     DATA(lo_delete_operation) = mo_environment->for-doma->create_delete_operation( ).
>     lo_delete_operation->add_object( co_doma_status ).
>     lo_delete_operation->execute( ).
>   ENDMETHOD.
> ENDCLASS.
> ```

