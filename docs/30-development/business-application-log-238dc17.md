<!-- loio238dc17aeea4498d8cf687f890f2194c -->

# Business Application Log

The XCO BAL module provides APIs and abstractions that allow a smooth integration of logging into application logic based on the standard Business Application Log \(BAL\). The module works seamlessly with other XCO library features.



<a name="loio238dc17aeea4498d8cf687f890f2194c__section_vs5_3yh_wrb"/>

## Terminology

Within the BAL module of the XCO Library, the following terminology is used:

-   **Log object**: The design time ABAP Repository object \(type APLO\) defining an application log object together with its subobjects.

-   **Log**: A single log instance for a given log object and subobject with an optional external ID into which messages can be written and read from. Represented by an object of type `IF_XCO_CP_BAL_LOG` and uniquely identified by a log handle.

-   **Log handle**: A unique identifier for a log \(UUID in CHAR22 format\) associated with a log \(available through attribute `LOG_HANDLE` of interface `IF_XCO_CP_BAL_LOG`.




<a name="loio238dc17aeea4498d8cf687f890f2194c__section_cbs_4mj_hmb"/>

## Persistence

The first and one of the central abstractions within the XCO BAL module is that of the persistence given by the interface `IF_XCO_CP_BAL_PERSISTENCE`. A persistence decides where logs are created \(or loaded from\) and where the messages and exceptions are written to \(or read from\).

The following two flavors are offered:

-   Memory: Logs are created only in memory and messages as well as exceptions are not written to the database

-   Database: Logs are created and loaded from the database and messages and exceptions are always saved to the database. Whenever a message or exception is added to the log a `COMMIT WORK` is performed on a secondary database connection




<a name="loio238dc17aeea4498d8cf687f890f2194c__section_pvc_wmj_hmb"/>

## Searching logs

In a style like that of the XCO ABAP Repository Query APIs, it's possible to easily locate existing logs based on filters for standard log attributes, like the object, subobject or external ID of a log:

> ### Sample Code:  
> ```abap
> DATA(lo_external_id_filter) = xco_cp_bal=>log_filter->external_id(
>   xco_cp_abap_sql=>constraint->contains_pattern( '*INVOICE*' )
> ).
> 
> DATA(lt_logs) = xco_cp_bal=>for->database( )->logs->where( VALUE #(
>   ( lo_external_id_filter )
> ) )->get( ).
> ```

In this example, all logs in the database whose external ID contains the fragment `INVOICE` will be located.



<a name="loio238dc17aeea4498d8cf687f890f2194c__section_ksd_1nj_hmb"/>

## Creating and loading logs

Once the desired persistence has been selected via `XCO_CP_BAL=>FOR`, a log can be created like

> ### Sample Code:  
> ```abap
> DATA(lo_log) = xco_cp_bal=>for->database( )->log->create(
>   iv_object      = 'MY_LOG_OBJECT'
>   iv_subobject   = 'MY_LOG_SUBOBJECT'
>   iv_external_id = 'MY_EXTERNAL_ID'
> ).
> ```

If a log already exists in the database, it can be loaded like

> ### Sample Code:  
> ```abap
> DATA(lo_log) = xco_cp_bal=>for->database( )->log->load( 'MY_LOG_HANDLE' ).
> ```

for a given log handle.



<a name="loio238dc17aeea4498d8cf687f890f2194c__section_mhv_dnj_hmb"/>

## Profiles

Associated with each `IF_XCO_CP_BAL_LOG` object is a profile \(`IF_XCO_CP_BAL_PROFILE`\) that influences how messages and exceptions are added to the log. For messages, a profile provides a default value for the level of detail that is used when messages are added to the log and no explicit level of detail is supplied.

For exceptions, the XCO BAL module offers a rich set of extra information that can be added along with the exception message to achieve maximum information that can be used for detailed error analysis.

The standard profile \(`XCO_CP_BAL=>PROFILE->STANDARD`\) defines a default level of detail of 4 and includes all possible exception additions as well as an automatic recursive descent for exceptions, so all the previous exceptions of an exception are added to the log as well.



<a name="loio238dc17aeea4498d8cf687f890f2194c__section_rrl_fnj_hmb"/>

## Adding and reading messages and exceptions



Messages can be added to a log in number of ways. They can be added directly via an explicit `SYMSG` value like

> ### Sample Code:  
> ```abap
> " Logging a plain SYMSG using the level of detail given by the underlying
> " profile.
> DATA(ls_symsg) = VALUE symsg(
>   msgty = 'W'
>   msgid = 'MSG_CLASS'
>   msgno = '001'
>   msgv1 = 'Item 1'
> ).
> 
> lo_log->add_message( ls_symsg ).
> 
> " Logging the same message but this time with an explicitly specified
> " level of detail.
> lo_log->add_message(
>   is_symsg           = ls_symsg
>   io_level_of_detail = xco_cp_bal=>level_of_detail->nine
> ).
> ```

or by resorting to the standard abstractions `IF_XCO_NEWS` and `IF_XCO_TEXT` from the XCO standard library:

> ### Sample Code:  
> ```abap
> " Support for IF_XCO_NEWS and IF_XCO_TEXT provides a high degree of integration with other
> " parts of the XCO library.
> MESSAGE w001(msg_class) WITH |Item 1| INTO DATA(lv_message). 
> lo_log->add_news( xco_cp=>sy ).
> 
> DATA(lv_string) = |MyStringValue|.
> lo_log->add_text( xco_cp=>string( lv_string ) ).
> ```

Following the pattern which is also used when reading the content of an object of the ABAP repository, it's easy to access all the messages contained in a log:

> ### Sample Code:  
> ```abap
> DATA(lt_messages) = lo_log->messages->all->get( ).
> ```

> ### Note:  
> Note that in order to be able to read from a log, an authorization is required for authorization object `S_APPL_LOG` for the following authorization field values:
> 
> -   `ALG_OBJECT`: The object of the application log that is being read
> -   `ALG_SUBOBJ`: The subobject of the application log that is being read
> -   `ACTVT`: 03

Adding and getting exceptions is identical to how messages are added to and read from the log: Exceptions are added via the `ADD_EXCEPTION` method and read via the `EXCEPTIONS` attribute of an `IF_XCO_CP_BAL_LOG` object.

Note that when an exception is added to a log, it will automatically be transformed into a message by the underlying business application log if it provides a T100 message. Only when an exception doesn't provide a T100 message will it be available via the `EXCEPTIONS` read attribute of `IF_XCO_CP_BAL_LOG`.

