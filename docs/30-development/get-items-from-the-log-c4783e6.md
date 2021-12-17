<!-- loioc4783e6d6675422aa0ddbe981ac51189 -->

# Get Items from the Log

After an application log was read from the database, the items stored in the log must be accessed. To read one or more items from an application log, interface `IF_BALI_LOG` provides the following methods:

-   GET\_ITEM: Read a single item from the application log.

    -   The item is identified by the *Log Item Number* which is a serial number containing the position of the item in the log.

    -   The method returns the reference to the item object.


-   GET\_ALL\_ITEMS: Read all items from the application log.

    -   The method returns an internal table with the following structure:

        -   The *Log Item Number* of the item

        -   The reference to the item object




The item object contains all attributes of the item, for example the severity. Each item object uses interface `IF_BALI_ITEM_GETTER`.

Public attributes of all log items:

-   CATEGORY: Identifies the category of the item \(see below\).

-   LOG\_ITEM\_NUMBER: The log item number which is the position of the item in the log.

-   SEVERITY: Severity, such as 'Error', 'Warning', 'Information'. Possible values of the severity are defined as constants in interface`IF_BALI_CONSTANTS`.

-   DETAIL\_LEVEL: If the application outputs the items of the application log, the detail level can be used to define at which level of detail the item shall be visible.

-   TIMESTAMP: A UTC timestamp which contains the creation time of the item.


Method of all log items is `GET_MESSAGE_TEXT`: It returns the message text of the item.

-   The output of ABAP command ***MESSAGE*** for a message item

-   The text of a free text item

-   The output of method `GET_TEXT` of the exception object for an exception item


The category of the item restricts which other attributes of the item are available. For example, the message number is only available for a message, because a free text does not have a message number. To get additional attributes, a down cast to the more specific interface of the item category is required. The following item categories are supported:

-   Message

    -   Attribute `CATEGORY` contains the value `IF_BALI_CONSTANTS=>C_CATEGORY_MESSAGE`.

    -   Interface of a message is `IF_BALI_MESSAGE_GETTER`.


    For more information, see [Get a Message](get-a-message-670d6d4.md).

-   Free Text

    -   Attribute CATEGORY contains the value IF\_BALI\_CONSTANTS=\>C\_CATEGORY\_FREE\_TEXT.

    -   Interface of a free text is IF\_BALI\_FREE\_TEXT\_GETTER.


    For more information, see [Get a Free Text](get-a-free-text-08f1c7d.md).

-   Exception

    -   Attribute CATEGORY contains the value IF\_BALI\_CONSTANTS=\>C\_CATEGORY\_EXCEPTION.

    -   Interface of an exception is IF\_BALI\_EXCEPTION\_GETTER.


    For more information, see [Get an Exception](get-an-exception-b1f6ffa.md).


> ### Example:  
> Load a single log from the database which uses log handle l\_handle and output all items of the log:
> 
> > ### Sample Code:  
> > ```
> > 
> > ...  
> >  DATA l_handle TYPE if_bali_log=>ty_handle.
> >  ...
> >  TRY.
> >      DATA(l_log) = cl_bali_log_db=>get_instance( )->load_log( handle = l_handle ).
> >      DATA(l_item_table) = l_log->get_all_items( ).
> > 
> >      LOOP AT l_item_table INTO DATA(l_item_entry).
> >        out->write( |{ l_item_entry-log_item_number } { l_item_entry-item->get_message_text( ) }| ).
> >        IF l_item_entry-item->category = if_bali_constants=>c_category_message.
> >          DATA(l_message_ref) = CAST if_bali_message_getter( l_item_entry-item ).
> >          out->write( |{ l_message_ref->id } { l_message_ref->number }| ).
> >        ELSEIF l_item_entry-item->category = if_bali_constants=>c_category_exception.
> >          DATA(l_exception_ref) = CAST if_bali_exception_getter( l_item_entry-item ).
> >          out->write( |{ l_exception_ref->exception_class } { l_exception_ref->exception_id_name }| ).
> >        ENDIF.
> >      ENDLOOP.
> >    CATCH cx_bali_runtime INTO DATA(l_exception).
> >      out->write( l_exception->get_text(  ) ).
> >  ENDTRY.
> > ...
> > ```

