<!-- loiob1f6ffa4cf6c45708f89040ec3a2fa07 -->

# Get an Exception

Similar to all other items, an exception can be read from the application log using methods `GET_ITEM` and `GET_ALL_ITEMS` of interface `IF_BALI_LOG`. The exception object, which is returned by these methods, uses interface `IF_BALI_EXCEPTION_GETTER`.

The interface supports all attributes and methods of interface `IF_BALI_ITEM_GETTER`.

Interface `IF_BALI_EXCEPTION_GETTER` contains the following additional attributes:

-   EXCEPTION\_CLASS: The name of the exception class.

-   EXCEPTION\_ID\_NAME: Name of the text ID of the ABAP exception.


> ### Example:  
> Load a single log from the database which uses log handle l\_handle and output some attributes of the first item, if it is an exception:
> 
> > ### Sample Code:  
> > ```
> > 
> > ...
> >  DATA l_handle TYPE if_bali_log=>ty_handle.
> > 
> >  TRY.
> >      DATA(l_log) = cl_bali_log_db=>get_instance( )->load_log( handle = l_handle ).
> >      DATA(l_item) = l_log->get_item( log_item_number = '1' ).
> > 
> >      IF l_item->category = if_bali_constants=>c_category_exception.
> >        DATA(l_exception_ref) = CAST if_bali_exception_getter( l_item ).
> >        out->write( |{ l_exception_ref->exception_class } { l_exception_ref->exception_id_name }| ).
> >      ENDIF.
> >    CATCH cx_bali_runtime INTO DATA(l_exception).
> >      out->write( l_exception->get_text(  ) ).
> >  ENDTRY.
> > ...
> > ```

