<!-- loio4ed3b27d41ba4e93a9d9fed8afdaca30 -->

# Read Application Logs from the Database

You can use interface `IF_BALI_LOG_DB` to read one or more application logs from the database. To get an instance of the interface, method `GET_INSTANCE` of class `CL_BALI_LOG_DB` is available.

Interface `IF_BALI_LOG_DB` contains the following methods which can be used to read the logs from the database:

-   LOAD\_LOG / LOAD\_LOG\_WITH\_ITEMS: Load one application log from the database.

    -   The log is identified by the log handle.

    -   The method returns an object of interface `IF_BALI_LOG`.

    -   With method `LOAD_LOG_WITH_ITEMS`, the complete log including all items is read from the database. If you use method `LOAD_LOG` and set the optional parameter `READ_ONLY_HEADER`, only the log header is read from the database. The log items are not read yet.


-   LOAD\_LOGS\_VIA\_FILTER / LOAD\_LOGS\_W\_ITEMS\_VIA\_FILTER: Load one or more logs from the database.

    -   The logs are identified by a filter object of interface `IF_BALI_LOG_FILTER`.

    -   The method returns an internal table of objects of interface `IF_BALI_LOG`.

    -   With method `LOAD_LOG_W_ITEMS_VIA_FILTER`, the complete logs including all items are read from the database. If you use method `LOAD_LOGS_VIA_FILTER` and set the optional parameter `READ_ONLY_HEADER`, only the log headers are read from the database. The log items are not read yet.



The following authorization is checked before a log is read from the database:

Authorization object: `S_APPL_LOG`, with

-   `ALG_OBJECT`: Object name of the application log

-   `ALG_SUBOBJ`: Subobject of the application log

-   `ACTVT`: 03


> ### Example:  
> Load a log from the database:
> 
> > ### Sample Code:  
> > ```abap
> > 
> > CLASS zcl_test_read DEFINITION
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
> > CLASS zcl_test_read IMPLEMENTATION.
> >   METHOD if_oo_adt_classrun~main.
> > 
> >     TRY.
> >         " Create a filter which selects all logs of the current user from the last hour
> >         DATA(l_filter) = cl_bali_log_filter=>create( ).
> >         l_filter->set_create_info( user = sy-uname ).
> > 
> >         DATA(l_timestamp_now) = utclong_current( ).
> >         DATA(l_timestamp_minus_1_hour) = utclong_add( val = l_timestamp_now
> >                                                       hours = '1-' ).
> >         l_filter->set_time_interval( start_time = l_timestamp_minus_1_hour
> >                                      end_time = l_timestamp_now ).
> > 
> >         " Read all Application Logs from the database which fit to the filter
> >         DATA(log_table) = cl_bali_log_db=>get_instance( )->load_logs_w_items_via_filter( filter = l_filter ).
> > 
> >         LOOP AT log_table INTO DATA(l_log).
> >           " Output log handle
> >           out->write( |Handle: { l_log->get_handle( ) }| ).
> > 
> >           " Get log header and output attributes of the header
> >           DATA(l_header) = l_log->get_header( ).
> >           out->write( |{ l_header->object } { l_header->subobject } { l_header->external_id } { l_header->log_user }| ).
> > 
> >           " Get all items and output some data which exist in all item categories
> >           DATA(l_item_table) = l_log->get_all_items( ).
> >           LOOP AT l_item_table INTO DATA(l_item_entry).
> >             out->write( |{ l_item_entry-log_item_number } { l_item_entry-item->get_message_text( ) }| ).
> > 
> >             " Output attributes which are specific for messages and exceptions
> >             IF l_item_entry-item->category = if_bali_constants=>c_category_message.
> >               DATA(l_message_ref) = CAST if_bali_message_getter( l_item_entry-item ).
> >               out->write( |{ l_message_ref->id } { l_message_ref->number }| ).
> >             ELSEIF l_item_entry-item->category = if_bali_constants=>c_category_exception.
> >               DATA(l_exception_ref) = CAST if_bali_exception_getter( l_item_entry-item ).
> >               out->write( |{ l_exception_ref->exception_class } { l_exception_ref->exception_id_name }| ).
> >             ENDIF.
> >           ENDLOOP.
> >         ENDLOOP.
> > 
> >       CATCH cx_bali_runtime INTO DATA(l_runtime_exception).
> >         out->write( l_runtime_exception->get_text(  ) ).
> >     ENDTRY.
> > 
> >   ENDMETHOD.
> > ENDCLASS.
> > ```

> ### Example:  
> Load a single log from the database which uses log handle l\_handle. Only read the log header:
> 
> > ### Sample Code:  
> > ```abap
> > 
> > ...
> >     DATA l_handle TYPE if_bali_log=>ty_handle.
> >     ...
> >     TRY.
> >         DATA(l_log) = cl_bali_log_db=>get_instance( )->load_log( handle = l_handle
> >                                                                  read_only_header = abap_true ).
> >       CATCH cx_bali_runtime INTO DATA(l_exception).
> >         out->write( l_exception->get_text(  ) ).
> >     ENDTRY.
> > ...
> > ```
> 
> Load all logs from the database which were created by the current user:
> 
> > ### Sample Code:  
> > ```abap
> > 
> > ...
> >     TRY.
> >         DATA(l_filter) = cl_bali_log_filter=>create( )->set_create_info( user = sy-uname ).
> >         DATA(log_table) = cl_bali_log_db=>get_instance( )->load_logs_w_items_via_filter( filter = l_filter ).
> >       CATCH cx_bali_runtime INTO DATA(l_exception).
> >         out->write( l_exception->get_text(  ) ).
> >     ENDTRY.
> > ...
> > ```

