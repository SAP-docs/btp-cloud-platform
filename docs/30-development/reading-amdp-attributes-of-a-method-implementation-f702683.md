<!-- loiof7026832be0a4e49847ddb53a902ff1c -->

# Reading AMDP Attributes of a Method Implementation

Given a class with an AMDP method implementation such as

> ### Sample Code:  
> ```abap
> CLASS zcl_xco_doc_cp_amdp DEFINITION PUBLIC FINAL CREATE PUBLIC.
>   PUBLIC SECTION.
>     INTERFACES:
>       if_amdp_marker_hdb.
>  
>     METHODS:
>       amdp_method.
> ENDCLASS.
>  
> CLASS zcl_xco_doc_cp_amdp IMPLEMENTATION.
>   METHOD amdp_method BY DATABASE PROCEDURE FOR HDB LANGUAGE SQLSCRIPT
>       OPTIONS
>         READ-ONLY
>       USING
>         zxco_amdp_dbt.
>     SELECT * FROM zxco_amdp_dbt WHERE id = '001';
>   ENDMETHOD.
> ENDCLASS.
> ```

the AMDP attributes of the method implementation can be read out as follows:

> ### Sample Code:  
> ```abap
> "! Code sample for reading the AMDP attributes of a method implementation.
> "!
> "! IMPORTANT: The values of the constants CO_CLASS_NAME and CO_METHOD_NAME
> "! must be replaced with the name of an existing class and a method that is
> "! implemented in this class.
> CLASS zcl_xco_doc_cp_read_amdp DEFINITION PUBLIC FINAL
>     INHERITING FROM cl_xco_cp_adt_simple_classrun CREATE PUBLIC.
>   PROTECTED SECTION.
>     METHODS:
>       main REDEFINITION.
>  
>   PRIVATE SECTION.
>     CONSTANTS:
>       co_class_name  TYPE sxco_ao_object_name VALUE 'ZCL_XCO_DOC_CP_AMDP',
>       co_method_name TYPE sxco_clas_method_name VALUE 'AMDP_METHOD'.
> ENDCLASS.
>  
> CLASS zcl_xco_doc_cp_read_amdp IMPLEMENTATION.
>   METHOD main.
>     DATA(lo_method_implementation) = xco_cp_abap=>class( co_class_name
>       )->implementation->method( co_method_name ).
>  
>     " LS_METHOD_IMPLEMENTATION will contain both the AMDP attributes and the source
>     " code of the method implementation.
>     DATA(ls_method_implementation) = lo_method_implementation->content( )->get( ).
>     out->write( ls_method_implementation ).
>  
>     " The AMDP database type is represented as an object of type CL_XCO_AMDP_DB_TYPE.
>     " Supported AMDP database types are available via XCO_CP_AMDP=>DATABASE_TYPE.
>     DATA(lo_amdp_database_type) = ls_method_implementation-amdp-database_type.
>     out->write( lo_amdp_database_type ).
>  
>     " The AMDP database language is represented as an object of type CL_XCO_AMDP_DB_LANGUAGE.
>     " Supported AMDP database languages are available via XCO_CP_AMDP=>DATABASE_LANGUAGE.
>     DATA(lo_amdp_database_language) = ls_method_implementation-amdp-database_language.
>     out->write( lo_amdp_database_language ).
>  
>     " The AMDP database options are represented as objects of type CL_XCO_AMDP_DB_OPTION.
>     " Supported AMDP database options are available via XCO_CP_AMDP=>DATABASE_OPTION.
>     DATA(lt_amdp_database_options) = ls_method_implementation-amdp-database_options.
>     out->write( lt_amdp_database_options ).
>  
>     " An AMDP database entity is represented as object of type IF_XCO_AMDP_DATABASE_ENTITY.
>     " The IF_XCO_PRINTABLE~GET_TEXT method can be used to obtain the string value for a database
>     " entity.
>     LOOP AT ls_method_implementation-amdp-database_entities INTO DATA(lo_amdp_database_entity).
>       DATA(lv_amdp_database_entity) = lo_amdp_database_entity->if_xco_printable~get_text(
>         )->get_lines(
>         )->join(
>         )->value.
>       out->write( lv_amdp_database_entity ).
>     ENDLOOP.
>   ENDMETHOD.
> ENDCLASS.
> ```

