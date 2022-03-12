<!-- loio772eee221ee743e887964b0ea8eb8507 -->

# Generation Error Handling

Any errors that occur during the execution of a PUT or DELETE operation are communicated via exceptions of types CX\_XCO\_GEN\_PUT\_EXCEPTION and CX\_XCO\_GEN\_DELETE\_EXCEPTION. The following code sample shows how the findings of a failed PUT operation can be extracted:

> ### Sample Code:  
> ```abap
> "! Code sample for handling errors of a PUT operation.
> "!
> "! IMPORTANT: The values of the constants CO_PACKAGE and CO_TRANSPORT must be replaced
> "! with an existing package and a modifiable Workbench transport matching the transport
> "! target of the package.
> CLASS zcl_xco_doc_cp_cs_gen_error DEFINITION PUBLIC FINAL
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
>       co_package   TYPE sxco_package VALUE 'ZXCO_CP_PACKAGE',
>       co_transport TYPE sxco_transport VALUE 'X08K900164',
> 
>       co_doma_name TYPE sxco_ad_object_name VALUE 'ZXCO_CP_NON_EXISTENT_DOMAIN',
>       co_dtel_name TYPE sxco_ad_object_name VALUE 'ZXCO_CP_INVALID_DTEL',
>       co_ttyp_name TYPE sxco_ad_object_name VALUE 'ZXCO_CP_INVALID_TTYP'.
> 
>     DATA:
>       mo_environment TYPE REF TO if_xco_cp_gen_env_dev_system.
> ENDCLASS.
> 
> CLASS zcl_xco_doc_cp_cs_gen_error IMPLEMENTATION.
>   METHOD constructor.
>     super->constructor( ).
> 
>     mo_environment = xco_cp_generation=>environment->dev_system( co_transport ).
>   ENDMETHOD.
> 
>   METHOD main.
>     DATA(lo_put_operation) = mo_environment->create_put_operation( ).
> 
>     " Add an invalid data element
>     DATA(lo_dtel_specification) = lo_put_operation->for-dtel->add_object( co_dtel_name
>       )->set_package( co_package
>       )->create_form_specification( ).
>     lo_dtel_specification->set_short_description( 'My data element' ).
>     lo_dtel_specification->set_data_type( xco_cp_abap_dictionary=>domain( co_doma_name ) ).
> 
>     " Add an invalid table type
>     DATA(lo_ttyp_specification) = lo_put_operation->for-ttyp->add_object( co_ttyp_name
>       )->set_package( co_package
>       )->create_form_specification( ).
>     lo_ttyp_specification->set_short_description( 'My table type' ).
>     lo_ttyp_specification->set_row_type( xco_cp_abap_dictionary=>data_element( co_dtel_name ) ).
> 
>     TRY.
>         lo_put_operation->execute( ).
>       CATCH cx_xco_gen_put_exception INTO DATA(lx_put_exception).
>         " Get all findings.
>         out->plain->write( |Findings:| ).
>         out->write_news( lx_put_exception ).
> 
>         " Get only the TTYP findings.
>         out->plain->write( |Table type findings:| ).
>         out->write_news( lx_put_exception->findings->for->ttyp ).
>     ENDTRY.
>   ENDMETHOD.
> ENDCLASS.
> ```

