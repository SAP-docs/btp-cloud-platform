<!-- loioe7a0f57b00e24306aba025d3d455fb42 -->

# Reading a Function Module

Given the following function module

> ### Sample Code:  
> ```lang-abap
> FUNCTION z_xco_doc_cp_cs_fm
>   IMPORTING
>     VALUE(im_class) TYPE REF TO cl_xco_ad_built_in_type OPTIONAL
>     im_interface TYPE REF TO if_xco_news
>     VALUE(im_abap_built_in_type) TYPE i DEFAULT 5
>     VALUE(im_abap_gt_reference) TYPE REF TO data
>   EXPORTING
>     ex_p1 TYPE REF TO string
>     VALUE(ex_p2) TYPE c
>   CHANGING
>     ch_1 TYPE any
>     VALUE(ch_2) TYPE i
>   RAISING
>     cx_sy_zerodivide
>     RESUMABLE(cx_sy_assign_cast_error).
>  
>  
>  
>   IF im_class IS NOT INITIAL.
>     ch_1 = 'ABC'.
>   ENDIF.
>  
> ENDFUNCTION.
> ```

its contents can be read and written to the console as follows

> ### Sample Code:  
> ```lang-abap
> CLASS zcl_xco_doc_cp_cs_fnctn_mdle DEFINITION PUBLIC FINAL
>     INHERITING FROM cl_xco_cp_adt_simple_classrun CREATE PUBLIC.
>   PROTECTED SECTION.
>     METHODS:
>       main REDEFINITION.
>  
>   PRIVATE SECTION.
>     METHODS:
>       read_importing_parameters
>         IMPORTING
>           io_function_module TYPE REF TO if_xco_function_module
>           out               TYPE REF TO if_xco_adt_classrun_out,
>  
>       read_exporting_parameters
>         IMPORTING
>           io_function_module TYPE REF TO if_xco_function_module
>           out               TYPE REF TO if_xco_adt_classrun_out,
>  
>       read_changing_parameters
>         IMPORTING
>           io_function_module TYPE REF TO if_xco_function_module
>           out               TYPE REF TO if_xco_adt_classrun_out,
>  
>       read_exceptions
>         IMPORTING
>           io_function_module TYPE REF TO if_xco_function_module
>           out               TYPE REF TO if_xco_adt_classrun_out.
> ENDCLASS.
>  
> CLASS zcl_xco_doc_cp_cs_fnctn_mdle IMPLEMENTATION.
>   METHOD main.
>     DATA(lo_function_module) = xco_cp_abap=>function_module( 'Z_XCO_DOC_CP_CS_FM' ).
>     out->write( lo_function_module ).
>  
>     DATA(ls_function_module) = lo_function_module->content( )->get( ).
>     out->write( ls_function_module ).
>  
>     out->write( |\nIMPORTING parameters:| ) ##NO_TEXT.
>     read_importing_parameters(
>       io_function_module = lo_function_module
>       out                = out
>     ).
>  
>     out->write( |\nEXPORTING parameters:| ) ##NO_TEXT.
>     read_exporting_parameters(
>       io_function_module = lo_function_module
>       out                = out
>     ).
>  
>     out->write( |\nCHANGING parameters:| ) ##NO_TEXT.
>     read_changing_parameters(
>       io_function_module = lo_function_module
>       out                = out
>     ).
>  
>     out->write( |\nExceptions:| ) ##NO_TEXT.
>     read_exceptions(
>       io_function_module = lo_function_module
>       out                = out
>     ).
>   ENDMETHOD.
>  
>   METHOD read_importing_parameters.
>     DATA(lt_importing_parameters) = io_function_module->importing_parameters->all->get( ).
>  
>     LOOP AT lt_importing_parameters INTO DATA(lo_importing_parameter).
>       out->write( lo_importing_parameter ).
>  
>       DATA(ls_type) = lo_importing_parameter->content( )->get( ).
>       out->write( ls_type ).
>     ENDLOOP.
>   ENDMETHOD.
>  
>   METHOD read_exporting_parameters.
>     DATA(lt_exporting_parameters) = io_function_module->exporting_parameters->all->get( ).
>  
>     LOOP AT lt_exporting_parameters INTO DATA(lo_exporting_parameter).
>       out->write( lo_exporting_parameter ).
>  
>       DATA(ls_type) = lo_exporting_parameter->content( )->get( ).
>       out->write( ls_type ).
>     ENDLOOP.
>   ENDMETHOD.
>  
>   METHOD read_changing_parameters.
>     DATA(lt_changing_parameters) = io_function_module->changing_parameters->all->get( ).
>  
>     LOOP AT lt_changing_parameters INTO DATA(lo_changing_parameter).
>       out->write( lo_changing_parameter ).
>  
>       DATA(ls_type) = lo_changing_parameter->content( )->get( ).
>       out->write( ls_type ).
>     ENDLOOP.
>   ENDMETHOD.
>  
>   METHOD read_exceptions.
>     DATA(lt_exceptions) = io_function_module->exceptions->all->get( ).
>  
>     LOOP AT lt_exceptions INTO DATA(lo_exceptions).
>       out->write( lo_exceptions ).
>  
>       DATA(ls_type) = lo_exceptions->content( )->get( ).
>       out->write( ls_type ).
>     ENDLOOP.
>   ENDMETHOD.
> ENDCLASS.
> ```

