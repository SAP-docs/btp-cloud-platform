<!-- loiof1d44d73a13147acbbabc0b71f42ddc1 -->

# Reading a Transformation

Given a transformation \(i.e. an XSLT object\), its contents can be read and written to the console as follows:

> ### Sample Code:  
> ```abap
> "! Code sample for reading the contents of a transformation (XSLT object).
> "!
> "! IMPORTANT: The value of the constant CO_TRANSFORMATION_NAME must be replaced with
> "! the name of an existing transformation for which the content shall be read.
> CLASS zcl_xco_doc_cp_read_trnsfrmtn DEFINITION PUBLIC FINAL
>     INHERITING FROM cl_xco_cp_adt_simple_classrun CREATE PUBLIC.
>   PROTECTED SECTION.
>     METHODS:
>       main REDEFINITION.
>  
>   PRIVATE SECTION.
>     CONSTANTS:
>       co_transformation_name TYPE sxco_tf_object_name VALUE 'ZMY_TRANSFORMATION'.
> ENDCLASS.
>  
> CLASS zcl_xco_doc_cp_read_trnsfrmtn IMPLEMENTATION.
>   METHOD main.
>     DATA(lo_transformation) = xco_cp_abap_repository=>object->xslt->for( co_transformation_name ).
>     out->write( lo_transformation ).
>  
>     " LS_TRANSFORMATION will contain both the short description and the source code of the
>     " transformation.
>     DATA(ls_transformation) = lo_transformation->content( )->get( ).
>     out->write( ls_transformation ).
>  
>     " The source code of the transformation is represented as an object of type IF_XCO_TF_SOURCE_CODE.
>     " Via the IF_XCO_TEXT~GET_LINES method the source code can also be easily obtained as a string_table.
>     DATA(lt_source_code) = ls_transformation-source_code->if_xco_text~get_lines( )->value.
>     out->write( lt_source_code ).
>   ENDMETHOD.
> ENDCLASS.
> ```

