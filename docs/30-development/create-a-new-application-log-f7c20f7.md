<!-- loiof7c20f7b2fce4fbaba79ae0c5182d869 -->

# Create a new Application Log

If you want to create a new application log, you must first create an object of class `CL_BALI_LOG`. This object manages a single application log and allows to get and set the log header and all log items, such as messages or exceptions.

To create an object of class `CL_BALI_LOG`, the class provides two methods:

-   If the header information of the log, for example the external identifier, is already known when the application log is created, you can use the `CREATE_WITH_HEADER` method. In this case, you can set the log header during the call. For more information, see [Set Header Information](set-header-information-b962eb9.md).


> ### Example:  
> > ### Sample Code:  
> > ```abap
> > 
> > CLASS zcl_test_write DEFINITION
> >   PUBLIC
> >   FINAL
> >   CREATE PUBLIC .
> > 
> >   PUBLIC SECTION.
> >     INTERFACES if_oo_adt_classrun.
> >   PROTECTED SECTION.
> >   PRIVATE SECTION.
> > ENDCLASS.
> > 
> > 
> > CLASS zcl_test_write IMPLEMENTATION.
> >   METHOD if_oo_adt_classrun~main.
> > 
> >     TRY.
> >         " Create a new Application Log
> >         DATA(l_log) = cl_bali_log=>create( ).
> > 
> >         " Add a header to the log
> >         l_log->set_header( header = cl_bali_header_setter=>create( object = 'ZOBJECT'
> >                                                                    subobject = 'ZSUBOBJECT'
> >                                                                    external_id = 'External ID' ) ).
> > 
> >         " Add a message as item to the log
> >         DATA(l_message) = cl_bali_message_setter=>create( severity = if_bali_constants=>c_severity_error
> >                                                           id = 'PO'
> >                                                           number = '000' ).
> >         l_log->add_item( item = l_message ).
> > 
> >         " Add a second message, this time from system fields SY-MSGID, ...
> >         MESSAGE ID 'ZTEST' TYPE 'S' NUMBER '058' INTO DATA(l_text).
> > 
> >         l_log->add_item( item = cl_bali_message_setter=>create_from_sy( ) ).
> > 
> >         " Add a free text to the log
> > 
> >         DATA(l_free_text) = cl_bali_free_text_setter=>create( severity = if_bali_constants=>c_severity_error
> >                                                               text = 'Some Error Text' ).
> > 
> >         l_log->add_item( item = l_free_text ).
> > 
> >         " Add an exception to the log
> >         DATA: i TYPE i.
> >         TRY.
> >             i = 1 / 0.
> >           CATCH cx_sy_zerodivide INTO DATA(l_ref).
> >         ENDTRY.
> > 
> >         DATA(l_exception) = cl_bali_exception_setter=>create( severity = if_bali_constants=>c_severity_error
> >                                                               exception = l_ref ).
> >         l_log->add_item( item = l_exception ).
> > 
> >         " Save the log into the database
> >         cl_bali_log_db=>get_instance( )->save_log( log = l_log ).
> > 
> >       CATCH cx_bali_runtime INTO DATA(l_runtime_exception).
> >         out->write( l_runtime_exception->get_text(  ) ).
> >     ENDTRY.
> > 
> >   ENDMETHOD.
> > ENDCLASS.
> > 
> > ```

> ### Sample Code:  
> ```abap
> 
> ...
>     TRY.
>         DATA(l_log) = cl_bali_log=>create_with_header(
>                         header = cl_bali_header_setter=>create( object = 'ZOBJECT'
>                                                                 subobject = 'ZSUBOBJECT'
>                                                                 external_id = 'External ID' ) ).
>       CATCH cx_bali_runtime INTO DATA(l_exception).
>         out->write( l_exception->get_text(  ) ).
>     ENDTRY.
> ...
> ```

If the header information is not known when the application log is created, you can use the `CREATE` method. It creates an empty application log. In this case, the header should be set later using the `SET_HEADER` method. If no subobjects were defined for the application log object, an empty string should be used at the parameter `SUBOBJECT`.

> ### Sample Code:  
> ```abap
> 
> ...
>     TRY.
>         DATA(l_log) = cl_bali_log=>create( ).
>         ...
>         l_log->set_header( header = cl_bali_header_setter=>create( object = 'ZOBJECT'
>                                                                    subobject = 'ZSUBOBJECT'
>                                                                    external_id = 'External ID' ) ).
>       CATCH cx_bali_runtime INTO DATA(l_exception).
>         out->write( l_exception->get_text(  ) ).
>     ENDTRY.
> ...
> ```

If the application log is no longer needed in the memory, for example because it was saved into the database, it's possible to release its memory. This can be done using the method RELEASE\_MEMORY.

After calling the method RELEASE\_MEMORY, the log object is invalidated and can no longer be used. The method IS\_INVALIDATED can be used to check whether the memory of the log object was already released by a previous call of the method RELEASE\_MEMORY.

> ### Sample Code:  
> ```abap
> ...
>  TRY.
>      DATA(l_log) = cl_bali_log=>create( ).
>      ...
>      " Add items to the log and e.g. write the log to the database
>      ...
>      " Release the memory of the log
>      l_log->release_memory( ).  
>    CATCH cx_bali_runtime INTO DATA(l_exception).
>      out->write( l_exception->get_text(  ) ).
>  ENDTRY.
>  ...
> ```

> ### Sample Code:  
> ```abap
>  ...
>  TRY.
>      DATA(l_log) = cl_bali_log=>create( ).
>      ...
>      " Check whether the log was already invalidated
>      IF l_log->is_invalidated( ) = abap_true.
>        " Start some error handling
>      ENDIF.
>      ...
>    CATCH cx_bali_runtime INTO DATA(l_exception).
>      out->write( l_exception->get_text(  ) ).
>  ENDTRY.
>  ...
> ```

