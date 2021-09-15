<!-- loio670d6d47164840d6a0717c6f9f38ab75 -->

# Get a Message

Similar to all other items, a message can be read from the application log using methods `GET_ITEM` and `GET_ALL_ITEMS` of interface `IF_BALI_LOG`. The message object, which is returned by these methods, uses interface `IF_BALI_MESSAGE_GETTER`.

The interface supports all attributes and methods of interface `IF_BALI_ITEM_GETTER`.

Interface `IF_BALI_MESSAGE_GETTER` contains the following additional attributes:

-   ID: Message ID

-   NUMBER: Message Number

-   VARIABLE\_1: Variable 1 of the message

-   VARIABLE\_2: Variable 2 of the message

-   VARIABLE\_3: Variable 3 of the message

-   VARIABLE\_4: Variable 4 of the message

-   COUNT: The count of the message. It is increased, if method `CUMULATE_ITEM` of interface `IF_BALI_LOG` is used to add a message to the log and if the log already contains a message with the same message attributes \(severity, message ID, message number and variables\).


> ### Example:  
> Load a single log from the database which uses log handle l\_handle and output some attributes of the first item, if it is a message:
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
> > 
> >      IF l_item->category = if_bali_constants=>c_category_message.
> >        DATA(l_message_ref) = CAST if_bali_message_getter( l_item ).
> >        out->write( |{ l_message_ref->id } { l_message_ref->number }| ).
> >      ENDIF.
> >    CATCH cx_bali_runtime INTO DATA(l_exception).
> >      out->write( l_exception->get_text(  ) ).
> >  ENDTRY.
> > ...
> > ```

