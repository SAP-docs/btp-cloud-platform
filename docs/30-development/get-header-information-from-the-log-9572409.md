<!-- loio9572409179b4420e9bd05a43f2f6bb31 -->

# Get Header Information from the Log

An application log contains header information and several attributes which identify the log. To read the header from a log, method `GET_HEADER` of interface `IF_BALI_LOG` can be used. It returns an object which uses interface`IF_BALI_HEADER_GETTER`.

Interface `IF_BALI_HEADER_GETTER` contains the following attributes:

-   OBJECT: Log object which identifies the application to which the log belongs.

-   SUBOBJECT: Log subobject which is the subcategory of an application log object.

-   EXTERNAL\_ID: A free text which is usually used by the application to identify the log. It contains, for example, the application document number.

-   LOG\_TIMESTAMP: UTC time stamp of the log \(usually the creation time\).

-   LOG\_USER: Log user \(usually the user who created the log\).

-   EXPIRY\_DATE: It defines the date when the log expires and can be deleted from the database.

-   KEEP\_UNTIL\_EXPIRY: A flag which defines whether or not it is allowed to delete the log before the expiry date. If the flag is set, the standard reports which delete application logs do not delete the log before the expiry date. The application is still able to delete the log before this date.

-   CONTEXT\_STRUCTURE\_NAME: The name of the dictionary structure which was used to set the context. See [Get the Context](get-the-context-80b6442.md).

-   NUMBER\_ALL\_ITEMS: Total number of items which are stored in the log.

-   NUMBER\_ABORT\_ITEMS: Number of abort items which are stored in the log.

-   NUMBER\_ERROR\_ITEMS: Number of error items which are stored in the log.

-   NUMBER\_WARNING\_ITEMS: Number of warning items which are stored in the log.

-   NUMBER\_INFORMATION\_ITEMS: Number of information items which are stored in the log.

-   NUMBER\_STATUS\_ITEMS: Number of status items which are stored in the log.


Interface `IF_BALI_HEADER_GETTER` contains the following methods:

-   GET\_OBJECT\_DESCRIPTION: Returns the description text of the log object in the logon language.

-   GET\_SUBOBJECT\_DESCRIPTION: Returns the description text of the log subobject in the logon language.

-   GET\_CONTEXT: Get the context of the log. See [Get the Context](get-the-context-80b6442.md).


> ### Note:  
> The header object contains the header attributes that were valid when the method GET\_HEADER was called. If the log is changed after this call \(for example, when new items are added to the log\), these changes are not automatically visible in the header object. To refresh the header object it's necessary to call the method GET\_HEADER again.

> ### Example:  
> Load a single log from the database which uses log handle l\_handle, and output some fields of the log header:
> 
> > ### Sample Code:  
> > ```abap
> > 
> > ...
> >  DATA l_handle TYPE if_bali_log=>ty_handle.
> >  ...
> >  TRY.
> >      DATA(l_log) = cl_bali_log_db=>get_instance( )->load_log( handle = l_handle ).
> >      DATA(l_header) = l_log->get_header( ).
> >      out->write( |{ l_header->object } { l_header->get_object_description( ) } {
> >                     l_header->subobject } { l_header->external_id } { l_header->log_user }| ).
> >    CATCH cx_bali_runtime INTO DATA(l_exception).
> >      out->write( l_exception->get_text(  ) ).
> >  ENDTRY.
> > ...
> > ```

