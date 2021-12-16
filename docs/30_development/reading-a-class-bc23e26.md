<!-- loiobc23e26f236042c48171d850e82843b9 -->

# Reading a Class

Given the following class

```lang-abap
CLASS zcl_xco_doc_cp_cs_class DEFINITION PUBLIC FINAL CREATE PUBLIC.
  PUBLIC SECTION.
    CLASS-METHODS:
      "! <p class="shorttext synchronized" lang="en">
      "!  Calculate the factorial for the given natural number
      "! </p>
      "!
      "! @parameter iv_n |
      "!  <p class="shorttext synchronized" lang="en">
      "!    The natural number for which to calculate the factorial
      "!  </p>
      "! @parameter rv_factorial_n |
      "!  <p class="shorttext synchronized" lang="en">
      "!    The factorial for the given natural number
      "!  </p>
      "! @raising cx_abap_invalid_value |
      "!  <p class="shorttext synchronized" lang="en">
      "!    If IV_N is less than 0
      "!  </p>
      factorial
        IMPORTING
          iv_n                  TYPE i
        RETURNING
          VALUE(rv_factorial_n) TYPE i
        RAISING
          cx_abap_invalid_value.
ENDCLASS.

CLASS zcl_xco_doc_cp_cs_class IMPLEMENTATION.
  METHOD factorial.
    IF iv_n LT 0.
      RAISE EXCEPTION TYPE cx_abap_invalid_value.
    ELSEIF iv_n EQ 0.
      rv_factorial_n = 1.
    ELSE.
      rv_factorial_n = iv_n * factorial( iv_n - 1 ).
    ENDIF.
  ENDMETHOD.
ENDCLASS.

```

its contents can be read and written to the console as follows

> ### Sample Code:  
> ```lang-abap
> CLASS zcl_xco_doc_cp_cs_read_clas DEFINITION PUBLIC FINAL
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
>       co_class_name  TYPE sxco_ao_object_name VALUE 'ZCL_XCO_DOC_CP_CS_CLASS'.
> 
>     METHODS:
>       write_parameters
>         IMPORTING
>           io_method TYPE REF TO if_xco_ao_c_method
>           out       TYPE REF TO if_xco_adt_classrun_out,
> 
>       write_exceptions
>         IMPORTING
>           io_method TYPE REF TO if_xco_ao_c_method
>           out       TYPE REF TO if_xco_adt_classrun_out,
> 
>       write_source
>         IMPORTING
>           io_class       TYPE REF TO if_xco_ao_class
>           iv_method_name TYPE sxco_clas_method_name
>           out            TYPE REF TO if_xco_adt_classrun_out.
> ENDCLASS.
> 
> CLASS zcl_xco_doc_cp_cs_read_clas IMPLEMENTATION.
>   METHOD constructor.
>     super->constructor( ).
>   ENDMETHOD.
> 
>   METHOD main.
>     DATA(lo_class) = xco_cp_abap=>class( co_class_name ).
> 
>     " DEFINITION.
>     DATA(ls_definition_content) = lo_class->definition->content( )->get( ).
>     out->write( |Definition of { lo_class->name }:| ).
>     out->write( ls_definition_content ).
> 
>     " PUBLIC class methods.
>     DATA(lt_public_methods) = lo_class->definition->section-public->components->class_method->all->get( ).
> 
>     LOOP AT lt_public_methods INTO DATA(lo_public_method).
>       out->write( |\nClass method { lo_public_method->name }:| ).
> 
>       DATA(ls_public_method) = lo_public_method->content( )->get( ).
>       out->write( ls_public_method ).
> 
>       out->write( |\nParameters:| ).
>       write_parameters(
>         io_method = lo_public_method
>         out       = out
>       ).
> 
>       out->write( |\nExceptions:| ).
>       write_exceptions(
>         io_method = lo_public_method
>         out       = out
>       ).
> 
>       out->write( |\nSource:| ).
>       write_source(
>         io_class       = lo_class
>         iv_method_name = lo_public_method->name
>         out            = out
>       ).
>     ENDLOOP.
>   ENDMETHOD.
> 
>   METHOD write_parameters.
>     " IMPORTING parameters.
>     DATA(lt_importing_parameters) = io_method->importing_parameters->all->get( ).
> 
>     LOOP AT lt_importing_parameters INTO DATA(lo_importing_parameter).
>       out->write( lo_importing_parameter->name ).
> 
>       DATA(ls_importing_parameter) = lo_importing_parameter->content( )->get( ).
>       out->write( ls_importing_parameter ).
>     ENDLOOP.
> 
>     " RETURNING parameters.
>     DATA(lt_returning_parameters) = io_method->returning_parameters->all->get( ).
> 
>     LOOP AT lt_returning_parameters INTO DATA(lo_returning_parameter).
>       out->write( lo_returning_parameter->name ).
> 
>       DATA(ls_returning_parameter) = lo_returning_parameter->content( )->get( ).
>       out->write( ls_returning_parameter ).
>     ENDLOOP.
>   ENDMETHOD.
> 
>   METHOD write_exceptions.
>     DATA(lt_exceptions) = io_method->exceptions->all->get( ).
> 
>     LOOP AT lt_exceptions INTO DATA(lo_exception).
>       out->write( lo_exception->name ).
> 
>       DATA(ls_exception) = lo_exception->content( )->get( ).
>       out->write( ls_exception ).
>     ENDLOOP.
>   ENDMETHOD.
> 
>   METHOD write_source.
>     DATA(ls_implementation) = io_class->implementation->method( iv_method_name
>       )->content( )->get( ).
> 
>     DATA(lv_source) = xco_cp=>strings( ls_implementation-source
>       )->join( |{ cl_abap_char_utilities=>cr_lf }|
>       )->value.
>     out->write( lv_source ).
>   ENDMETHOD.
> ENDCLASS.
> ```

