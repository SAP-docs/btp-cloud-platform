<!-- loio7621fc27ea2747e98255a8563b25310d -->

# Reload Archived Data into the Database

Reloading is optional and should only be used in exceptional cases. The application must decide if a reload is necessary or not.

In the standard process, a reloading of archived data is not required, as archived data and direct access to individual data objects can be performed by using the [Read API](read-archived-data-df7f035.md).

There are two cases which need to be distinguished:

1.  Data must be reloaded shortly after deleting data from the database within the archiving process. An example for this case would be if selection criteria were set wrongly for the archiving process.

2.  Reload of archived data after a long period of time. In this case it must be ensured that references to and within the reloaded data are still available in database. Furthermore, it needs to be guaranteed that no table key conflicts exist. Since this is not a real error, it's strongly recommended not to reload the data in this case.


The runtime to reload archived data from an external storage system back into the database should be implemented in a central ABAP class. This ABAP class has to register interface `IF_ARCH_RELOAD_API` to be able to be selected in an archiving object definition in ADT.


<table>
<tr>
<th valign="top" colspan="3">

`CL_ARCH_RELOAD_API` \(API to reload archived data\)

</th>
</tr>
<tr>
<td valign="top">

*Method*

</td>
<td valign="top">

*Parameter*

</td>
<td valign="top">

*Description*

</td>
</tr>
<tr>
<td valign="top" rowspan="4">

<code><i>GET_INSTANCE</i></code>

Returns an instance of the delete API. Reference to interface `IF_ARCH_RELOAD_API`

</td>
<td valign="top">

Importing: <code><i>IV_ARCHIVING_OBJECT</i></code>

</td>
<td valign="top">

Name of the archiving object which will be used

</td>
</tr>
<tr>
<td valign="top">

Importing:<code><i>IV_ARCHIVING_SESSION</i></code>

</td>
<td valign="top">

Sessions of the archiving object which will be used

</td>
</tr>
<tr>
<td valign="top">

Importing:<code><i>IV_TESTMODE</i></code>

</td>
<td valign="top">

Reload program runs in test mode

</td>
</tr>
<tr>
<td valign="top">

Returning:<code><i>RO_RELOAD_INSTANCE</i></code>

</td>
<td valign="top">

Instance of the reload API for further processing

</td>
</tr>
<tr>
<td valign="top" rowspan="4">

<code><i>GET_SESSIONS_TO_RELOAD</i></code>

Read a data object from an archive file

</td>
<td valign="top">

Importing: <code><i>IT_DATA_SELECTION</i></code>

</td>
<td valign="top">

Range on dates on which archive files have been created

</td>
</tr>
<tr>
<td valign="top">

Importing: <code><i>IT_USER_SELECTION</i></code>

</td>
<td valign="top">

Range on users which have created archive files

</td>
</tr>
<tr>
<td valign="top">

Importing: <code><i>IV_ARCHIVING_OBJECT</i></code>

</td>
<td valign="top">

Archiving object which will be used

</td>
</tr>
<tr>
<td valign="top">

Returning: <code><i>RT_SESSION_ATTRIBUTES</i></code>

</td>
<td valign="top">

Archiving sessions' attributes

</td>
</tr>
</table>


<table>
<tr>
<th valign="top" colspan="3">

`IF_ARCH_RELOAD_API` \(Interface to reload archived data\)

</th>
</tr>
<tr>
<td valign="top">

*Method*

</td>
<td valign="top">

*Parameter*

</td>
<td valign="top">

*Description*

</td>
</tr>
<tr>
<td valign="top" rowspan="2">

<code><i>GET_DATA_RECORDS</i></code>

Read records by structure from the current data object

</td>
<td valign="top">

Importing: <code><i>IV_RECORDS_STRUCTURE</i></code>

</td>
<td valign="top">

Name of a structure of all data records in the table

</td>
</tr>
<tr>
<td valign="top">

Exporting:<code><i>ET_DATA_RECORDS</i></code>

</td>
<td valign="top">

Table containing the data records

</td>
</tr>
<tr>
<td valign="top" rowspan="4">

<code><i>GET_NEXT_DATA_OBJECT</i></code>

Read data object from the archive file

</td>
<td valign="top">

Exporting: <code><i>EV_ARCHIVE_KEY</i></code>

</td>
<td valign="top">

Archive key according to archive management

</td>
</tr>
<tr>
<td valign="top">

Exporting: <code><i>EV_END_OF_FILE</i></code>

</td>
<td valign="top">

Boolean values:

*TRUE* \(=’X’\)

*FALSE* \(= ‘ ‘\)

</td>
</tr>
<tr>
<td valign="top">

Exporting: <code><i>EV_ARCHIVING_SESSION</i></code>

</td>
<td valign="top">

Sessions of the archiving object which will be used

</td>
</tr>
<tr>
<td valign="top">

Exporting: <code><i>EV_OBJECT_OFFSET</i></code>

</td>
<td valign="top">

Offset of data object in the archive

</td>
</tr>
<tr>
<td valign="top">

<code><i>RELOAD_DATA_FOR_OBJECT</i></code>

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" rowspan="2">

<code><i>RELOAD_DATA_FOR_TABLE</i></code>

Reloading the data of an internal table

</td>
<td valign="top">

Importing: <code><i>IV_TABLE_NAME</i></code>

</td>
<td valign="top">

DDIC structure name of an internal table

</td>
</tr>
<tr>
<td valign="top">

Tables: <code><i>IT_TABLE_NAME</i></code>

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

<code><i>FINALIZE</i></code>

Open archive files will be closed

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
</table>

A typical flow of the archiving reload process would be as follows:

1.  Determine archiving sessions which are still available for reload by using the method `CL_ARCH_RELOAD_API=> GET_SESSIONS_TO_RELOAD`, with filter options on creating user and creation date of the archive file.

2.  Create an instance of the reload API and open the archiving reload session for one of the selected archiving sessions by using the method `CL_ARCH_RELOAD_API=>GET_INSTANCE`.

3.  Open the next data object via method `GET_NEXT_DATA_OBJECT`. If the method returns `EV_END_OF_FILE = TRUE (‘X’)`, continue with step 6 to call the method `FINALIZE`.

4.  Reload the data of the object from the external storage system back into your database tables, either by:

    -   Use of the method `RELOAD_DATA_FOR_OBJECT`

    -   Or use of the method `RELOAD_DATA_FOR_TABLE`. This method needs to be called once for each table.

    -   Use of the method `GET_DATA_RECORDS`. With this method, the result needs to be used to perform your own `INSERT` statements.


5.  Continue with the next data object. See step 3.

6.  Finish the archiving reload session by calling the method `FINALIZE`.


An example coding snippet:

> ### Sample Code:  
> ```abap
> 
> CONSTANTS: lc_object TYPE if_arch_api_types=>ty_object_name VALUE 'MY_OBJECT'.
> DATA: 	lv_test TYPE abap_bool VALUE abap_true,
> lt_data TYPE STANDARD TABLE OF my_header_table,
> lv_session TYPE sarch_session_number.
> 
> 
> 
>  
>             " get newest complete archiving session
>               DATA(lt_sessions) = cl_arch_reload_api=>get_sessions_to_reload(           iv_archiving_object = lc_object ).
>               SORT lt_sessions BY creation_date DESCENDING creation_time DESCENDING.
>               READ TABLE lt_sessions ASSIGNING FIELD-SYMBOL(<ls_session>) INDEX 1.
>             DATA(lo_reload) = cl_arch_reload_api=>get_instance
> ( iv_archiving_object =   lc_object
>                                                        iv_archiving_session = lv_session
>                                                        iv_testmode = lv_test ).
>             " read next data object from archive file into internal memory
>             DO.
>               lo_reload->get_next_data_object( IMPORTING ev_end_of_file = DATA(lv_end_of_file)
>                                                          ev_archive_key = DATA(lv_archive_key)
>                                                          ev_object_offset = DATA(lv_offset) ).
>               IF lv_end_of_file = abap_true.
>                 EXIT.
>               ENDIF.
>               " optional: remove
>               " read archived data for table ZADK_SFLIGHT
>               lo_reload->get_data_records( EXPORTING iv_record_structure = 'MY_HEADER_TABLE'
>                                            IMPORTING et_data_records = lt_data ).
> 
>               " reload the data into the data base
>               lo_reload->reload_data_for_object( ).
> 
>               " optional: delete data from customer owned index
>               DELETE FROM <my_index_table>
>                 WHERE archive_key = @lv_archive_key.
> 
>             ENDDO.
>             COMMIT WORK.
>             lo_reload->finalize( ).
> 
> ```

