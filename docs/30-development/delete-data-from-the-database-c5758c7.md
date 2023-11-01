<!-- loioc5758c7240254dfc83a4dfca21ee3d54 -->

# Delete Data from the Database

The runtime to delete archived data from database should be implemented in a central ABAP class. This ABAP class must register interface `IF_ARCH_DELETE_API` to be able to be selected in an archiving object definition in ADT. This ABAP class can be [performed within an application job](perform-data-archiving-894f952.md).

There are different ways to delete archived data from the database:

-   Using a central delete API to delete all table entries of a data object

-   Using a central delete API to delete specified tables of a data object

-   Using a central delete API to get all table entries of a data object to perform an own deletion from the database



<table>
<tr>
<th valign="top" colspan="3">

`CL_ARCH_DELETE_API` \(API for deleting archived data from the database\)

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

Returns an instance of the delete API. Reference to interface `IF_ARCH_DELETE_API`

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

Importing:<code><i>IV_ARCHIVE_KEY</i></code>

</td>
<td valign="top">

Archive key for which data should be deleted

</td>
</tr>
<tr>
<td valign="top">

Importing:<code><i>IV_TESTMODE</i></code>

</td>
<td valign="top">

*True*: no storage takes place

*False*: Archive content is written, and storage is requested

</td>
</tr>
<tr>
<td valign="top">

Returning:<code><i>RO_DELETE_INSTANCE</i></code>

</td>
<td valign="top">

Instance of the delete API

</td>
</tr>
<tr>
<td valign="top" rowspan="4">

<code><i>GET_FILES_TO_DELETE</i></code>

Returns a table with archive keys which have not yet been processed by deletion

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

Importing: <code><i>IT_DATE_SELECTION</i></code>

</td>
<td valign="top">

Range of dates on which archive files have been created

</td>
</tr>
<tr>
<td valign="top">

Importing: <code><i>IT_USER_SELECTION</i></code>

</td>
<td valign="top">

Range of users which have created archive files

</td>
</tr>
<tr>
<td valign="top">

Returning: <code><i>RT_ARCHIVE_FILE_ATTRIBUTES</i></code>

</td>
<td valign="top">

Table of archive keys which fulfill the selection criteria for dates and users

</td>
</tr>
</table>


<table>
<tr>
<th valign="top" colspan="3">

`IF_ARCH_DELETE_API` \(Interface for deleting archived data from the database\)

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

<code><i>GET_NEXT_OBJECT</i></code>

Reads the next data object for the archived data

</td>
<td valign="top">

Exporting: <code><i>EV_OBJECT_OFSET</i></code>

</td>
<td valign="top">

Offset at which the data of the data object starts. This can be used to build application-owned indices for the archived data.

</td>
</tr>
<tr>
<td valign="top">

Exporting:<code><i>EV_ARCHIVE_KEY</i></code>

</td>
<td valign="top">

Archive key of the archive file to which the data was written. This can be used to build application-owned indices for the archived data.

</td>
</tr>
<tr>
<td valign="top">

Exporting:<code><i>EV_ARCHIVING_SESSION</i></code>

</td>
<td valign="top">

Sessions of the archiving object which will be used

</td>
</tr>
<tr>
<td valign="top">

Exporting:<code><i>EV_END_OF_FILE</i></code>

</td>
<td valign="top">

*True*: All data contained in the files is processed, and the application should finalize the deletion

*False*: The application should continue processing the next data object

</td>
</tr>
<tr>
<td valign="top" rowspan="2">

<code><i>GET_DATA_RECORDS</i></code>

</td>
<td valign="top">

Importing: <code><i>IV_RECORD_STRUCTURE</i></code>

</td>
<td valign="top">

Name of the table for which archived data should be returned

</td>
</tr>
<tr>
<td valign="top">

Exporting: <code><i>ET_DATA_RECORDS</i></code>

</td>
<td valign="top">

Records of the table

</td>
</tr>
<tr>
<td valign="top" rowspan="2">

<code><i>DELETE_DATA_FOR_TABLE</i></code>

Deletes the data for a specific table from the database

</td>
<td valign="top">

Importing: <code><i>IV_TABLE_NAME</i></code>

</td>
<td valign="top">

Name of the table for which archived data should be deleted

</td>
</tr>
<tr>
<td valign="top">

Importing: <code><i>IT_RECORDS</i></code>

</td>
<td valign="top">

Records of the table to be deleted

</td>
</tr>
<tr>
<td valign="top">

<code><i>DELETE_DATA_FOR_OBJECT</i></code>

Deletes all table entries contained in the data object

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

<code><i>FINALIZE</i></code>

Finalizes processing

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
</table>

Typical flow of the archiving delete process:

1.  Determine files which are still available for deletion by using the method `CL_ARCH_DELETE_API=> GET_FILES_TO_DELETE`, with filter options on creating user and creation date of the archive file.

2.  Create an instance of the delete API and open the archiving delete session for one of the selected archive files by using method `CL_ARCH_DELETE_API=>GET_INSTANCE`.
3.  Open the next data object with the method `GET_NEXT_DATA_OBJECT`. If the method returns `EV_END_OF_FILE = TRUE (‘X’)`, continue with step 6. Optional \(can be used for reading archived data via index access\): Update the index table with the data object archived.

4.  Delete the data of the object from your database tables either by:

    -   Use of the method `DELETE_DATA_FOR_OBJECT`

    -   Use of the method `DELETE_DATA_FOR_TABLE`. Call this method once for each table.

    -   Use of the method `GET_DATA_RECORDS`. Use the result to perform your own `DELETE` statements.


5.  Continue with the next data object. See step 3.

6.  Finish the archiving delete session by calling the method `FINALIZE`.


> ### Sample Code:  
> ```abap
> CONSTANTS: lc_object TYPE if_arch_api_types=>ty_object_name VALUE 'MY_OBJECT'.
> DATA:  lv_test TYPE abap_bool VALUE abap_true,
> lt_data TYPE STANDARD TABLE OF my_index_table,
> lv_arkey TYPE sarch_archive_key.
> DATA:   ls_index TYPE my_index_table.
>              
> 
>  “ get newest undeleted file
>       DATA(lt_files) = cl_arch_delete_api=>get_files_to_delete( iv_archiving_object =     lc_object ).
>               SORT lt_files BY creation_date DESCENDING creation_time DESCENDING.
>               READ TABLE lt_files ASSIGNING FIELD-SYMBOL(<ls_file>) INDEX 1.	
> 
>             DATA(lo_delete) = cl_arch_delete_api=>get_instance
> ( iv_archiving_object = lc_object                                                                                 iv_archive_key = lv_arkey
>                                                      iv_testmode = lv_test ).
>             “ read next data object from archive file into internal memory
>             DO.
>               lo_delete->get_next_data_object( IMPORTING ev_end_of_file = DATA(lv_end_of_file)
>                                                          ev_archive_key = DATA(lv_archive_key)
>                                                          ev_object_offset = DATA(lv_offset) ).
>               IF lv_end_of_file = abap_true.
>                 EXIT.
>               ENDIF.
>               “ optional: Create customer owned index for single document access during read
>               “ read archived data for table MY_HEADER_TABLE
>               lo_delete->get_data_records( EXPORTING iv_record_structure = ‘MY_HEADER_TABLE’
>                                            IMPORTING et_data_records = lt_data ).
>               “ map flight data to your index table MY_INDEX_TABLE
>               IF lv_test <> abap_true.
>                 LOOP AT lt_data ASSIGNING FIELD-SYMBOL(<ls_data>).
>                   MOVE-CORRESPONDING <ls_data> TO ls_index.
>                   Ls_index-archive_key = lv_archive_key.
>                   Ls_index-archive_offset = lv_offset.
>                   INSERT my_index_table FROM @ls_Index.
>                 ENDLOOP.
>               ENDIF.
>               “ delete the data from the data base
>               lo_delete->delete_data_for_object( ).
>             ENDDO.
>             COMMIT WORK.  
>             lo_delete->finalize( ).
> 
> ```

Example of a customer-owned index table for archived flights:

> ### Sample Code:  
> ```
> @EndUserText.label : 'Archiving Index: Flights'
> @AbapCatalog.enhancement.category : #NOT_EXTENSIBLE
> @AbapCatalog.tableCategory : #TRANSPARENT
> @AbapCatalog.deliveryClass : #A
> @AbapCatalog.dataMaintenance : #ALLOWED
> define table my_index_table {
> @EndUserText.label : 'Client'
> key mandt : abap.clnt not null;
> @EndUserText.label : 'Airline Code'
> key carrid : abap.char(3) not null;
> @EndUserText.label : 'Flight Connection Number'
> key connid : abap.numc(4) not null;
> @EndUserText.label : 'Flight date'
> key fldate : abap.dats not null;
> archive_key : sarch_archive_key;
> archive_offset : sarch_offset;
> 
> ```

