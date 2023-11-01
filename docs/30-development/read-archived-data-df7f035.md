<!-- loiodf7f035c135c46bda6513146d09bd2b3 -->

# Read Archived Data

Applications can use the ADK read API to read the data which is contained in an archive file stored in an external storage system.

There are two possible ways to access the data:

-   Read the data for entire archive files sequentially
-   Read the data by index access


To optimize the reading access on archive files, an index solution can be established in the application. For an index-based read access, the archive key and the offset of a data object are needed. ADK API provides this information within methods `IF_ARCH_DELETE_API->GET_NEXT_DATA_OBJECT` and `IF_ARCH_READ_API->GET_NEXT_DATA_OBJECT`.

A typical index-based solution needs a transparent table containing columns for application attributes, a column for the archive key and a column for the offset. The archive key is the ID of the archive file, which contains the application attribute. The offset is the offset in the archive file at which the data for the application attribute starts. Usually, the initial construction of an archive index will be established by [deleting archived data from the database](delete-data-from-the-database-c5758c7.md). In case the index should be constructed at a later point in time, the ADK read API can be used to determine archive key and offset \(returned by method `IF_ARCH_READ_API->GET_NEXT_DATA_OBJECT`\).


<table>
<tr>
<th valign="top" colspan="3">

`CL_ARCH_READ_API` \(API to read archived data\)

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

<code><i>GET_FILES_TO_READ</i></code>

Selection of archiving sessions and files

</td>
<td valign="top">

Importing: <code><i>IT_DATE_SELECTION</i></code>

</td>
<td valign="top">

Range on dates on which archive files have been created

</td>
</tr>
<tr>
<td valign="top">

Importing:<code><i>IT_USER_SELECTION</i></code>

</td>
<td valign="top">

Range on users which have created archive files

</td>
</tr>
<tr>
<td valign="top">

Importing:<code><i>IT_ARCHIVING_OBJECT</i></code>

</td>
<td valign="top">

Archiving object which will be used

</td>
</tr>
<tr>
<td valign="top">

Returning:<code><i>RT_ARCHIVING_FILE_ATTRIBUTES</i></code>

</td>
<td valign="top">

Archiving sessions' attributes

</td>
</tr>
<tr>
<td valign="top" rowspan="4">

<code><i>GET_INSTANCE</i></code>

Returns an instance of the delete API. Reference to interface `IF_ARCH_READ_API`

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

Importing: <code><i>IV_ARCHIVING_SESSION</i></code>

</td>
<td valign="top">

Sessions of the archiving object which will be used

</td>
</tr>
<tr>
<td valign="top">

Importing: <code><i>IT_ARCHIVE_KEY</i></code>

</td>
<td valign="top">

Archive key for which data should be read

</td>
</tr>
<tr>
<td valign="top">

Returning: <code><i>RO_READ_INSTANCE</i></code>

</td>
<td valign="top">

Instance of the read API for further processing

</td>
</tr>
</table>


<table>
<tr>
<th valign="top" colspan="3">

`IF_ARCH_READ_API` \(Interface to read archived data\)

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

Name of the structure of all data records in the table

</td>
</tr>
<tr>
<td valign="top">

Exporting:<code><i>EV_DATA_RECORDS</i></code>

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

<code><i>CLOSE</i></code>

Open archive files will be closed

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
</table>

As mentioned before, there are two different ways to acceess the data. A typical procedure for the sequential read access would be as follows:

1.  Determine files which are available for evaluation by using the method `CL_ARCH_READ_API=>GET_FILES_TO_READ`, with filter options on creating user and creation date of the archive file.

2.  Create an instance of the read API and open the archiving read session for one of the selected archive files by using the method `CL_ARCH_READ_API=>GET_INSTANCE`.

3.  Open the next data object with the method `GET_NEXT_DATA_OBJECT`. If the method returns `EV_END_OF_FILE = TRUE (‘X’)`, continue with step 6.

4.  Read the data with the method `GET_DATA_RECORDS`.

5.  Continue with the next data object. See step 3.

6.  Finish the read operation by calling method `CLOSE`.


A typical flow of the index-based read access would be as follows:

1.  Determine the archive key and the offset of the data object by selecting the relevant entry from your index table.

2.  Create an instance of the read API and open the archiving read session for the data object by using the method `CL_ARCH_READ_API=>GET_INSTANCE_BY_OFFSET`.

3.  Read the data by using the method `GET_DATA_RECORDS`.

4.  Finish the read operation by calling method `CLOSE`.


An example code for the index-based read operation:

> ### Sample Code:  
> ```abap
> CONSTANTS: lc_object TYPE if_arch_api_types=>ty_object_name VALUE 'MY_OBJECT'.
> DATA: lt_data TYPE STANDARD TABLE OF my_item_table.
> DATA: lt_index TYPE STANDARD TABLE OF my_index_table.
> 
>     " let's assume, we want to read the archived bookings for flight AA/0040 on 20010110
>     TRY.
>         " get archive key and offset for the given flight from the index table
>         SELECT * FROM my_index_table WHERE carrid = 'AA' AND connid = '0040' AND fldate = '20010110'
>          INTO TABLE @lt_index.
>         SORT lt_index BY archive_key DESCENDING.
>         READ TABLE lt_index ASSIGNING FIELD-SYMBOL(<ls_index>) INDEX 1.
>         IF NOT <ls_index> IS ASSIGNED.
>           RETURN.
>         ENDIF.
>         " open a read instance for the archive key and offset found
>         DATA(lo_read) = cl_arch_read_api=>get_instance_by_offset
> ( iv_archiving_object = lc_object
>                                                        iv_archive_key = <ls_index>-archive_key
>                                                iv_object_offset = <ls_index>-archive_offset ).
>         " get all archived booking entries for this flight
>         lo_read->get_data_records( EXPORTING iv_record_structure = ‘MY_ITEM_TABLE1’
>                                    IMPORTING et_data_records = lt_data ).
>         " close the read instance
>         lo_read->close( ).
> 
> ```

