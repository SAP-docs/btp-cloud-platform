<!-- loio8e17d0d93c1944edac6b56e6b1f6fe94 -->

# Define a Filter

If one or more application logs shall be read from the database and if the log handles are not known, you can identify the logs by defining a filter.

To create a filter, an instance of interface `IF_BALI_LOG_FILTER` is required. To create this instance, you can use method `CREATE` of class `CL_BALI_LOG_FILTER`. It creates an empty filter.

> ### Note:  
> Due to performance reasons, we recommend to set at least the object and subobject in the filter.

Interface `IF_BALI_LOG_FILTER` contains the following methods to set the filter parameters:

-   SET\_DESCRIPTOR: Set a filter for the log object, subobject and external identifier. It offers the following parameters:

    -   Select a single object

    -   Select a single subobject \(wildcards allowed\)

    -   Select a table of subobjects \(wildcards allowed\)

    -   Select a single external identifier \(wildcards allowed\)

    -   Select a table of external identifiers \(wildcards allowed\)


-   SET\_CREATE\_INFO: Set a filter for the attribute which identifies the creator of the log. It offers the following parameters:

    -   Select a single user \(wildcards allowed\)

    -   Select a table of users \(wildcards allowed\)


-   SET\_TIME\_INTERVAL: Set a time interval for the creation date and time of the log. The start and end time of the interval are set using UTC time stamps.

-   SET\_MAXIMUM\_LOG\_NUMBER: Set the maximum number of logs which shall be read from the database. If the parameter is not set, all logs are read \(which fulfill the other filter criteria\).


> ### Example:  
> Set a filter which selects up to 5 logs which were created in the last hour by the current user:
> 
> > ### Sample Code:  
> > ```
> > 
> > ...
> >     TRY.
> >         DATA(l_filter) = cl_bali_log_filter=>create( ).
> >         l_filter->set_create_info( user = sy-uname ).
> >    
> >         DATA(l_timestamp_now) = utclong_current( ).
> >         DATA(l_timestamp_minus_1_hour) = utclong_add( val = l_timestamp_now
> >                                                       hours = '1-' ).
> >         l_filter->set_time_interval( start_time = l_timestamp_minus_1_hour
> >                                      end_time = l_timestamp_now ).
> > 
> >         l_filter->set_maximum_log_number( max_log_number = 5 ).
> >       CATCH cx_bali_runtime INTO DATA(l_exception).
> >         out->write( l_exception->get_text(  ) ).
> >     ENDTRY.
> > ...
> > ```
> 
> Set a filter which reads all logs of the current user with object `ZOBJECT`, subobject `ZSUBOBJECT` and an external identifier which starts with an 'E':
> 
> > ### Sample Code:  
> > ```
> > 
> > ...
> >     TRY.
> >         DATA(l_filter) = cl_bali_log_filter=>create(
> >                                           )->set_create_info( user = sy-uname
> >                                           )->set_descriptor( object = 'ZOBJECT'
> >                                                              subobject = 'ZSUBOBJECT'
> >                                                              external_id = 'E*' ).
> >       CATCH cx_bali_runtime INTO DATA(l_exception).
> >         out->write( l_exception->get_text(  ) ).
> >     ENDTRY.
> > ...
> > ```

