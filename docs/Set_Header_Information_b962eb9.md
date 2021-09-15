<!-- loiob962eb9ce95048eea479e6e7b38fb481 -->

# Set Header Information

An application log contains header information and attributes to identify the log. During log creation, the following header information can be set:

-   Log Object \(required\): Identifies the application to which the log belongs.

-   Log Subobject: An application can define subcategories of its log object. These subcategories are called subobjects and must be set if the application defined them.

-   External Identifier: We recommend to enter your preferred identifier containing, for example, the application document number.

-   Expiry Date: It defines the date when the log expires and can be deleted from the database. The default value is the creation date of the log + 7 days.

-   A flag defining whether it should not be allowed to delete the log before the expiry date by a standard report. The application is still able to delete the log before this date.


To define the log header, an instance of the `IF_BALI_HEADER_SETTER` interface is required. To create this instance, you can use method `CREATE` of class `CL_BALI_HEADER_SETTER`. It allows to set the object, subobject and the external identifier of the application log.

Interface `IF_BALI_HEADER_SETTER` contains the following methods to set or change the header attributes:

-   `SET_DESCRIPTOR`: Changes the object, subobject and external identifier.

-   `SET_EXPIRY`: Sets the expiry date and the *keep until expiry* flag.


> ### Note:  
> You have two options to transfer the header to the application log object:
> 
> -   Using method `CREATE_WITH_HEADER` of class `CL_BALI_LOG` when the log object is created.
> 
> -   Using method `SET_HEADER` of interface `IF_BAL_LOG`.
> 
> 
> If the header was already written to the log \(for example, using method `SET_HEADER` of interface `IF_BAL_LOG`\) and if the header object is changed afterwards \(for example, using method `SET_DESCRIPTOR`\), you must call method `SET_HEADER` to make these changes visible in the log.

> ### Sample Code:  
> ```
> 
> ...
>  TRY.
>      DATA(l_header) = cl_bali_header_setter=>create( object = 'ZOBJECT'
>                                                      subobject = 'ZSUBOBJECT'
>                                                      external_id = 'External ID' ).
>      l_header->set_expiry( expiry_date = CONV #( cl_abap_context_info=>get_system_date(  ) + 5 )
>                            keep_until_expiry = abap_true ).
>    CATCH cx_bali_runtime INTO DATA(l_runtime_exception).
>      out->write( l_runtime_exception->get_text(  ) ).
>  ENDTRY.
> ...
> ```

