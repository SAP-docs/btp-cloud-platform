<!-- loio6f0e26492b854627ac19a9a34205a546 -->

# ADT Class Execution

Easily execute ABAP classes directly in ABAP Development Tools \(ADT\) without having to launch a service.

> ### Sample Code:  
> ```lang-abap
> CLASS zcl_example_class DEFINITION
>   PUBLIC
>   FINAL
>   CREATE PUBLIC .
>  
>   PUBLIC SECTION.
>     INTERFACES if_oo_adt_classrun.
>   PROTECTED SECTION.
>   PRIVATE SECTION.
> ENDCLASS.
>  
> CLASS zcl_example_class IMPLEMENTATION.
>   METHOD if_oo_adt_classrun~main.
>     out->write( 'Hello World!' ).
>   ENDMETHOD.
> ENDCLASS.
> ```

For more information, see the ABAP Doc comments of the `IF_OO_ADT_CLASSRUN` interface in ABAP Development Tools \(ADT\).

