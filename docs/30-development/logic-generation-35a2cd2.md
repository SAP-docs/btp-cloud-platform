<!-- loio35a2cd2c04464cc2aafb077e5653b873 -->

# Logic Generation

The following code sample illustrates the generation of classes and interfaces:

> ### Sample Code:  
> ```abap
> "! <p class="shorttext synchronized" lang="EN">
> "!  XCO Documentation CP: Logic generation
> "! </p>
> "!
> "! Code sample for generating an interface along with a class that implements it.
> "!
> "! IMPORTANT: The values of the constants CO_PACKAGE and CO_TRANSPORT must be replaced
> "! with an existing package and a modifiable Workbench transport matching the transport
> "! target of the package.
> CLASS zcl_xco_doc_cp_cs_gen_logic DEFINITION PUBLIC FINAL
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
>       co_package        TYPE sxco_package VALUE 'ZXCO_CP_PACKAGE',
>       co_transport      TYPE sxco_transport VALUE 'X08K900164',
> 
>       co_interface_name TYPE sxco_ao_object_name VALUE 'ZIF_CUSTOMER',
>       co_class_name     TYPE sxco_ad_object_name VALUE 'ZCL_CUSTOMER'.
> 
>     DATA:
>       mo_environment TYPE REF TO if_xco_cp_gen_env_dev_system.
> 
>     METHODS:
>       add_intf
>         IMPORTING
>           io_put_operation TYPE REF TO if_xco_cp_gen_d_o_put,
> 
>       add_clas
>         IMPORTING
>           io_put_operation TYPE REF TO if_xco_cp_gen_d_o_put.
> ENDCLASS.
> 
> CLASS zcl_xco_doc_cp_cs_gen_logic IMPLEMENTATION.
>   METHOD constructor.
>     super->constructor( ).
> 
>     mo_environment = xco_cp_generation=>environment->dev_system( co_transport ).
>   ENDMETHOD.
> 
>   METHOD main.
>     DATA(lo_put_operation) = mo_environment->create_put_operation( ).
> 
>     add_intf( lo_put_operation ).
>     add_clas( lo_put_operation ).
> 
>     lo_put_operation->execute( ).
> 
>     out->write( |PUT operation executed successfully.| ).
>   ENDMETHOD.
> 
>   METHOD add_intf.
>     DATA(lo_specification) = io_put_operation->for-intf->add_object( co_interface_name
>       )->set_package( co_package
>       )->create_form_specification( ).
>     lo_specification->set_short_description( 'Customer' ).
> 
>     lo_specification->add_type( 'TV_PRODUCT' )->for( xco_cp_abap=>type-built_in->c( 10 ) ).
>     lo_specification->add_type( 'TT_PRODUCTS' )->for_table_type(
>       io_row_type = lo_specification->own->type( 'TV_PRODUCT' )
>       io_access   = xco_cp_table_type=>access->standard_table
>     ).
>     lo_specification->add_type( 'TV_ID' )->for( xco_cp_abap=>type-built_in->c( 10 ) ).
>     lo_specification->add_data( 'ID' )->set_type( lo_specification->own->type( 'TV_ID' )
>       )->set_read_only( ).
> 
>     DATA(lo_get_favorite_products) = lo_specification->add_method( 'GET_FAVORITE_PRODUCTS' ).
>     lo_get_favorite_products->add_returning_parameter( 'RT_FAVORITE_PRODUCTS'
>       )->set_type( lo_specification->own->type( 'TT_PRODUCTS' ) ).
>   ENDMETHOD.
> 
>   METHOD add_clas.
>     DATA(lo_specification) = io_put_operation->for-clas->add_object( co_class_name
>       )->set_package( co_package
>       )->create_form_specification( ).
>     lo_specification->set_short_description( 'Customer implementation' ).
>     lo_specification->definition->set_create_visibility( xco_cp_abap_objects=>visibility->private ).
>     lo_specification->definition->add_interface( co_interface_name ).
> 
>     lo_specification->definition->section-public->add_alias( 'TV_ID'
>       )->set_component( 'TV_ID'
>       )->set_interface( co_interface_name ).
> 
>     " CREATE factory method.
>     DATA(lo_create) = lo_specification->definition->section-public->add_class_method( 'CREATE' ).
>     lo_create->add_importing_parameter( 'IV_ID' )->set_type( lo_specification->own->type( 'TV_ID' ) ).
>     lo_create->add_returning_parameter( 'RO_INSTANCE' )->set_type( xco_cp_abap=>interface( co_interface_name ) ).
> 
>     lo_specification->implementation->add_method( 'CREATE' )->set_source( VALUE #(
>       ( |ro_instance = new { co_class_name }( iv_id ).| )
>     ) ).
> 
>     " CONSTRUCTOR.
>     DATA(lo_constructor) = lo_specification->definition->section-private->add_method( 'CONSTRUCTOR' ).
>     lo_constructor->add_importing_parameter( 'IV_ID' )->set_type( lo_specification->own->type( 'TV_ID' ) ).
> 
>     lo_specification->implementation->add_method( 'CONSTRUCTOR' )->set_source( VALUE #(
>       ( |{ co_interface_name }~id = iv_id.| )
>     ) ).
> 
>     " Implementation of GET_FAVORITE_PRODUCTS interface method.
>     lo_specification->implementation->add_method( |{ co_interface_name }~GET_FAVORITE_PRODUCTS|
>       )->set_source( VALUE #(
>         ( |" Source code goes here...| )
>     ) ).
>   ENDMETHOD.
> ENDCLASS.
> ```

Note that the XCO Generation APIs for classes also allow the specification of local types and local test classes:

-   Method `ADD_LOCAL_CLASS` on `IF_XCO_CP_GEN_CLAS_S_FORM` can be used to add a local type to the generated class. The content of the local class can be fully specified via the returned local class specification `IF_XCO_GEN_CLAS_S_FO_LCL_CLASS`

-   Method `ADD_TEST_CLASS` on `IF_XCO_CP_GEN_CLAS_S_FORM` can be used to add a local test class to the generated class. The content of the local test class can be fully specified via the returned test class specification `IF_XCO_GEN_CLAS_S_FO_TST_CLASS`. Note that the API `XCO_CP_ABAP_UNIT` offers XCO enumeration constants for ABAP Unit durations and risk levels


