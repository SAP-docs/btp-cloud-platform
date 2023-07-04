<!-- loio31f564eb1a7a40d487be99a196bbf70d -->

# Add Items

To write items, such as messages or exceptions, to the log during runtime, the application requires an item object which contains all attributes of the item, such as the message number or the reference to the exception object.

The following categories of log items are provided:

-   Message \(for example, a message is displayed using ABAP command `MESSAGE`\). For more information, see [Create a Message](create-a-message-f6ca36b.md).

-   Free Text \(a text with a maximum length of 200 characters\). For more information, see [Create a Free Text](create-a-free-text-31f749f.md).

-   Exception \(for example, an exception is raised using ABAP command `RAISE EXCEPTION` and can be caught using ABAP command `CATCH`\). For more information, see [Create an Exception](create-an-exception-9a82de7.md).


To add a log item to an application log, the `IF_BALI_LOG` interface provides the following methods:

-   `ADD_ITEM`: Append an item to the application log

-   `CUMULATE_ITEM`: If the item is a message, it's checked whether the log already contains a message with the same message attributes \(severity, message ID, message number and variables\). If yes, the counter of the message is increased by 1. In all other cases, it works the same way as `ADD_ITEM`.

-   `ADD_MESSAGES_FROM_BAPIRETTAB`: Append several messages to the application log. The message attributes are stored in an internal table of type `BAPIRETTAB`.

-   `ADD_ABAP_BEHAVIOR_MESSAGE`: Append an ABAP behavior message, which uses the interface `IF_ABAP_BEHV_MESSAGE`, to the log.

-   `ADD_ALL_ITEMS_FROM_OTHER_LOG`: Read all items from another application log and append them to this log. This method can be used if the items of different application logs are merged into one log.

    Sometimes it's required to filter items which are put into an application log by using the method `ADD_ITEM`. For example, there may be an encapsulated application class which writes error and status messages into an application log, and the caller of this application class only requires the error messages. In this case, the caller can define an item filter \(see [Define a Filter](define-a-filter-8e17d0d.md)\). The caller can then add this item filter to the log using the method `SET_FILTER_FOR_ADD_ITEM`. If an item filter is set for a log object, only those items that pass this filter are added to the log object.


> ### Note:  
> If an item was already added to the application log, its attributes can't be changed any more. Therefore, if the attributes of the item object are changed after the item was added to the log, these changes are not transferred to the log.
> 
> When an item is added to the application log, it can probably be converted internally. For example, an exception which is based on a message \(which contains a message ID and message number\) is internally converted into a message.

> ### Sample Code:  
> ```abap
> 
> ...
>  TRY.
>      DATA(l_log) = cl_bali_log=>create( ).
>     
>      MESSAGE ID 'ZTEST' TYPE 'W' NUMBER '002' INTO DATA(l_text).
>      l_log->add_item( item = cl_bali_message_setter=>create_from_sy( ) ).
>      l_log->cumulate_item( item = cl_bali_message_setter=>create_from_sy( ) ).
> 
>      DATA: i TYPE i.
>      TRY.
>          i = 1 / 0.
>        CATCH cx_sy_zerodivide INTO DATA(l_ref).
>      ENDTRY.
>      l_log->add_item( item = cl_bali_exception_setter=>create( exception = l_ref ) ).
> 
>      DATA(l_bapirettab) = VALUE bapirettab( ( id = 'BL' type = 'I' number = '315'
>                                               message_v1 = 'A' message_v2 = 'B' message_v3 = 'C' message_v4 = 'D' )
>                                             ( id = 'BL' type = 'E' number = '319' ) ).
>      l_log->add_messages_from_bapirettab( message_table = l_bapirettab ).
>    CATCH cx_bali_runtime INTO DATA(l_exception).
>      out->write( l_exception->get_text(  ) ).
>  ENDTRY.
> 
> ...
> ```

> ### Sample Code:  
> ```abap
> ...
>  TRY.
>      DATA(l_log_target) = cl_bali_log=>create( ).
>     
>      MESSAGE ID 'ZTEST' TYPE 'W' NUMBER '002' INTO DATA(l_text).
>      l_log_target->add_item( item = cl_bali_message_setter=>create_from_sy( ) ).
> 
>      DATA(l_log_source) = cl_bali_log=>create( ).
>      DATA: i TYPE i.
>      TRY.
>          i = 1 / 0.
>        CATCH cx_sy_zerodivide INTO DATA(l_ref).
>      ENDTRY.
>      l_log_source->add_item( item = cl_bali_exception_setter=>create( exception = l_ref ) ).
> 
>      " add all items of l_log_source to l_log_target
>      l_log_target->add_all_items_from_other_log( source_log = l_log_source ).
>    CATCH cx_bali_runtime INTO DATA(l_exception).
>      out->write( l_exception->get_text(  ) ).
>  ENDTRY.
>  ...
> ```

> ### Sample Code:  
> ```abap
> ...
>  TRY.
>      DATA(l_log) = cl_bali_log=>create( ).
>     
>      " Add item filter to the log which only allows error messages
>      DATA(l_filter) = cl_bali_item_filter=>create( )->set_severity( severity_table = VALUE #( ( 'E' ) ) ).
>      l_log->set_filter_for_add_item( filter = l_filter ).
> 
>      MESSAGE ID 'ZTEST' TYPE 'W' NUMBER '002' INTO DATA(l_text).
>      l_log->add_item( item = cl_bali_message_setter=>create_from_sy( ) ).  " Message is not added, because it is a warning
> 
>      MESSAGE ID 'ZTEST' TYPE 'E' NUMBER '002' INTO l_text.
>      l_log->add_item( item = cl_bali_message_setter=>create_from_sy( ) ). " Message is added, because it is an error
> 
>      " Get the current item filter
>      data(l_item_filter) = l_log->get_filter_for_add_item( ).
>      
>      " Clear the current item filter
>      l_log->set_filter_for_add_item( filter = value #( ) ).
> 
>    CATCH cx_bali_runtime INTO DATA(l_exception).
>      out->write( l_exception->get_text(  ) ).
>  ENDTRY.
> ...
> ```

