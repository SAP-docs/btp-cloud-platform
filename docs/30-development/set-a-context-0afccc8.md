<!-- loio0afccc862a8a4e1aab9f633df6fa0835 -->

# Set a Context

There may be the requirement to store application-specific data in the log. For example, a message may only be meaningful if you have information about the context in which a message was generated. An example of the context is the number of the order which was processed when the message was written into the log.

You can set a context for the complete log in the log header, and for each individual item of the log. To do this, the following steps are necessary:

-   You need a structure which can store the context data. It must meet the following requirements:

    -   The structure must either use a database table type, or a structure type which is defined in the data dictionary.

    -   The structure type must be flat \(which means that no internal tables or nested structures are allowed\).

    -   The structure type must be character-like \(which means that no integer fields are allowed\).

    -   The total length of the complete structure must not be larger than 256 characters.


-   Now, you can fill the structure fields with the application data which you want to store as context in the log or item.

-   To transfer the structure with the context data to the log, you can use the method `SET_CONTEXT` of the header or item object.


> ### Sample Code:  
> ```abap
> ...
>  DATA: l_context TYPE ADDRESS_1. " it can be any application structure that fulfils the requirements
>  l_context = VALUE #( name1 = 'Test' name2 = 'Data' ). " fill the structure with the context data
>  TRY.
>      DATA(l_header) = cl_bali_header_setter=>create( object = 'ZOBJECT'
>                                                      subobject = 'ZSUBOBJECT' ).
>      l_header->set_context( l_context ).
>    CATCH cx_bali_runtime INTO DATA(l_runtime_exception).
>      out->write( l_runtime_exception->get_text(  ) ).
>  ENDTRY.
> ...
> ```

