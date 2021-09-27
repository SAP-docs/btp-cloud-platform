<!-- loiod15d974dfca34671ae3b62ddf0baf8ae -->

# Writing Application Logs to the Database

You can use interface `IF_BALI_LOG_DB` to write an application log to the database or to delete database entries. To get an instance of the interface, method `GET_INSTANCE` of class `CL_BALI_LOG_DB` is available.

To change the logs in the database, interface `IF_BALI_LOG_DB` contains the following methods:

-   SAVE\_LOG: Save an application log in the database. The log is identified by the log object \(which uses interface`IF_BAL_LOG`\).

    It may be required to commit the saving of the log immediately after the saving. It ensures that the log is stored, even if the application calls *ROLLBACK WORK* later on. Whether it is required depends on the application. Some applications want to keep the log entries after the rollback, others want to remove everything by the *ROLLBACK WORK*, including the log entries.

    To save an application log, the optional parameter `USE_2ND_DB_CONNECTION` is available. If the parameter is set, a second database connection is used for the saving. This second database connection is committed immediately after the save.

    In addition, the optional parameter `ASSIGN_TO_CURRENT_APPL_JOB` is available. If this parameter is set, and if the application runs in an application job, the connection between the application log and an application job is established. The application log is visible in the application job display.

-   DELETE\_LOG: Deletes an application log from the database. The log is identified by the log object \(which uses interface `IF_BAL_LOG`\).

-   ENQUEUE: If there is a parallel processing of the same application report, it may happen - depending on the application - that several reports try to change the same application log at the same time. In this case, one report overwrites the application log data of the other report. To avoid this, method `ENQUEUE` can be used to set an enqueue on the application log. The log is identified by the log object \(which uses interface `IF_BAL_LOG`\).

-   DEQUEUE: Clear the enqueue which was set via method ENQUEUE. The log is identified by the log object \(which uses interface`IF_BAL_LOG`\).


> ### Note:  
> You can quickly access a log stored in the database using the log handle. The log handle is the UUID of the log. To enable the application to store the log handle in one of the application tables, interface `IF_BAL_LOG` offers method `GET_HANDLE` which returns the log handle.

> ### Example:  
> Save a log in the database:
> 
> > ### Sample Code:  
> > ```
> > 
> > ...
> >     TRY.
> >         DATA(l_log) = cl_bali_log=>create_with_header( cl_bali_header_setter=>create( object = 'ZOBJECT'
> >                                                                                       subobject = 'ZSUBOBJECT'
> >                                                                                       external_id = 'External ID' ) ).
> >         MESSAGE ID 'ZTEST' TYPE 'I' NUMBER '315' WITH 'A' 'B' 'C' 'D' INTO DATA(l_text).
> >         l_log->add_item( cl_bali_message_setter=>create_from_sy( ) ).
> > 
> >         cl_bali_log_db=>get_instance( )->save_log( log = l_log ).
> >       CATCH cx_bali_runtime INTO DATA(l_exception).
> >         out->write( l_exception->get_text(  ) ).
> >     ENDTRY.
> > ...
> > ```
> 
> Save the same log using the second database connection:
> 
> > ### Sample Code:  
> > ```
> > 
> > ...
> >     TRY.
> >         cl_bali_log_db=>get_instance( )->save_log( log = l_log
> >                                                    use_2nd_db_connection = abap_true ).
> >       CATCH cx_bali_runtime INTO DATA(l_exception).
> >         out->write( l_exception->get_text(  ) ).
> >     ENDTRY.
> > ...
> > ```
> 
> Delete the same log from the database:
> 
> > ### Sample Code:  
> > ```
> > 
> > ...
> >     TRY.
> >         cl_bali_log_db=>get_instance( )->delete_log( log = l_log ).
> >       CATCH cx_bali_runtime INTO DATA(l_exception).
> >         out->write( l_exception->get_text(  ) ).
> >     ENDTRY.
> > ...
> > ```
> 
> Delete a log from the database which uses the handle l\_handle.
> 
> :
> 
> > ### Sample Code:  
> > ```
> > 
> > ...
> >     DATA l_handle TYPE if_bali_log=>ty_handle.
> >     l_handle = ...
> >     TRY.
> >         DATA(l_log_db) = cl_bali_log_db=>get_instance( ).
> >         DATA(l_log) = l_log_db->load_log( handle = l_handle
> >                                           read_only_header = abap_true ).
> >         l_log_db->delete_log( log = l_log ).
> >       CATCH cx_bali_runtime INTO DATA(l_exception).
> >         out->write( l_exception->get_text(  ) ).
> >     ENDTRY.
> > ...
> > ```

The following authorization is checked before a log is deleted from the database:

Authorization object: `S_APPL_LOG`, with

-   `ALG_OBJECT`: Object name of the application log

-   `ALG_SUBOBJ`: Subobject of the application log

-   `ACTVT`: 06


