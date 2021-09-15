<!-- loio08f1c7d9ce4b4d5694f55434adb49b79 -->

# Get a Free Text

Similar to all other items, a free text can be read from the application log using methods `GET_ITEM` and `GET_ALL_ITEMS` of interface `IF_BALI_LOG`. The free text object, which is returned by these methods, uses interface `IF_BALI_FREE_TEXT_GETTER`.

The interface supports all attributes and methods of interface `IF_BALI_ITEM_GETTER`.

Interface `IF_BALI_FREE_TEXT_GETTER` contains no additional attributes.

> ### Example:  
> Load a single log from the database which uses log handle l\_handle and output the text of the first item:
> 
> > ### Sample Code:  
> > ```
> > 
> > ... 
> >  DATA l_handle TYPE if_bali_log=>ty_handle.
> >  ...
> >  TRY.
> >      DATA(l_log) = cl_bali_log_db=>get_instance( )->load_log( handle = l_handle ).
> >      DATA(l_item) = l_log->get_item( log_item_number = '1' ).
> >      out->write( |{ l_item->get_message_text( ) }| ).
> >    CATCH cx_bali_runtime INTO DATA(l_exception).
> >      out->write( l_exception->get_text(  ) ).
> >  ENDTRY.
> > ...
> > ```

