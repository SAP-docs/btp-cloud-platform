<!-- loio0bf9b10f88b445b485b6068925e7fdb8 -->

# ADT



By having a class implement the interface IF\_OO\_ADT\_CLASSRUN it is possible to easily write programs that can be run directly within ADT using the console as output.

The XCO library provides an abstract implementation of this interface via CL\_XCO\_CP\_ADT\_SIMPLE\_CLASSRUN that exposes all the original functionality of IF\_OO\_ADT\_CLASSRUN but adds several additional functionalities that enable a natural integration of XCO library abstractions with ADT classruns.

The following sample class illustrates how the OUT object provided by CL\_XCO\_CP\_ADT\_SIMPL\_CLASSRUN can be used to flexibly write complex data structures or even object references to the console. Using the interface IF\_XCO\_PRINTABLE any object can define a text that is used when the object is written to the console.

> ### Sample Code:  
> ```lang-abap
> CLASS zcl_xco_doc_cp_std_adt DEFINITION PUBLIC FINAL
>     INHERITING FROM cl_xco_cp_adt_simple_classrun CREATE PUBLIC.
>   PROTECTED SECTION.
>     METHODS:
>       main REDEFINITION.
> ENDCLASS.
> 
> CLASS zcl_xco_doc_cp_std_adt IMPLEMENTATION.
>   METHOD main.
>     TYPES:
>       BEGIN OF ts_address,
>         street       TYPE string,
>         house_number TYPE n LENGTH 2,
>         postal_code  TYPE n LENGTH 5,
>         city         TYPE string,
>       END OF ts_address,
> 
>       BEGIN OF ts_member,
>         first_name TYPE string,
>         last_name  TYPE string,
>         address    TYPE ts_address,
>       END OF ts_member,
> 
>       tt_member TYPE STANDARD TABLE OF ts_member WITH EMPTY KEY.
> 
>     " Print a JSON-style serialization (works for arbitrarily deep data structures)
>     DATA(lt_members) = VALUE tt_member(
>       ( first_name = 'John' last_name = 'Doe' address = VALUE #( street = 'Main street' house_number = 12 postal_code = 12345 city = 'City' ) )
>     ).
> 
>     " Will print: [{FIRST_NAME: John, LAST_NAME: Doe, ADDRESS: {STREET: Main street, HOUSE_NUMBER: 12, POSTAL_CODE: 12345, CITY: City}}]
>     out->write( lt_members ).
> 
>     " IF_XCO_PRINTABLE example: Will print "WARNING"
>     out->write( xco_cp_message=>type->warning ).
> 
>     " IF_XCO_PRINTABLE example: Will print "Field MY_FIELD of View entity MY_VIEW_ENTITY"
>     DATA(lo_field) = xco_cp_cds=>view_entity( 'MY_VIEW_ENTITY' )->field( 'MY_FIELD' ).
>     out->write( lo_field ).
>   ENDMETHOD.
> ENDCLASS.
> ```

On top of the rich console writing functionalities, any NO\_CHECK exception that is not caught by the MAIN method of a class implementing CL\_XCO\_CP\_ADT\_SIMPLE\_CLASSRUN will be caught and written to the console with maximum information. This includes the raise position, messages and even the stack trace if the exception is carrying one \(cf. explanation of CX\_XCO\_RUNTIME\_EXCEPTION above\).

