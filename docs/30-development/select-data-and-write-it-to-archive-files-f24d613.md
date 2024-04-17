<!-- loiof24d6138d5f8472582d02df58af18e4c -->

# Select Data and Write It to Archive Files

The runtime to write archived data to an external storage should be implemented in a central ABAP class. This ABAP class must register the interface `IF_ARCH_WRITE_API` to be able to be selected in an archiving object definition in ADT. This ABAP class can be [performed within an application job](perform-data-archiving-894f952.md).

The purpose of the ABAP class is the selection of application data which will be archived from the database. By using the ADK write API, this application data can be handed over to create a data object. A data object can contain entries of different tables that have been listed in the definition of the archiving object in ADT. Typically, these are all tables belonging to one business object instance, but there is no technical restriction. The application is free to group the tables according to their needs.

As soon as the data object is completed, the object will be transferred as an archiving file to the related storage manager implementation to store data in the related external storage.

The following table shows the write API to collect the data that will be archived:


<table>
<tr>
<th valign="top" colspan="3">

`CL_ARCH_WRITE_API`

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
<td valign="top" rowspan="3">

<code><i>GET_INSTANCE</i></code>

Static method which returns an instance of the write API via parameter `RO_WRITE_INSTANCE`

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

Importing:<code><i>IV_TESTMODE</i></code>

</td>
<td valign="top">

*True*: no storage takes place

*False*: Archive content is written, and storage is requested

</td>
</tr>
<tr>
<td valign="top">

Returning:<code><i>RO_WRITE_INSTANCE</i></code>

</td>
<td valign="top">

Instance of the write API for further processing

</td>
</tr>
</table>

The following table shows the interface for writing archived data:


<table>
<tr>
<th valign="top" colspan="3">

`IF_ARCH_WRITE_API`

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
<td valign="top">

<code><i>OPEN_DATA_OBJECT</i></code>

Opens a new data object for the data of the business object instance

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top" rowspan="2">

<code><i>PUT_DATA_RECORDS</i></code> 

Writes the data for a specific table to the open data object

</td>
<td valign="top">

Importing:<code><i>IV_TABLE_NAME</i></code>

</td>
<td valign="top">

Name of the table which will be archived

</td>
</tr>
<tr>
<td valign="top">

Importing:<code><i>IT_RECORDS</i></code>

</td>
<td valign="top">

Records of the table

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

<code><i>CLOSE_DATA_OBJECT</i></code>

Closes the data object and writes it to the archive file

</td>
<td valign="top">

Exporting:<code><i>EV_OBJECT_OFFSET</i></code>

</td>
<td valign="top">

Offset at which the data of the data object starts \(can be used to build application owned indices for the archived data\)

</td>
</tr>
<tr>
<td valign="top">

Exporting:<code><i>EV_ARCHIVE_KEY</i></code>

</td>
<td valign="top">

Archive key of the archive file to which the data was written \(can be used to build application owned indices for the archived data\)

</td>
</tr>
<tr>
<td valign="top">

Exporting:<code><i>EV_ARCHIVING_SESSION</i></code>

</td>
<td valign="top">

Sessions of the archiving object to be used

</td>
</tr>
<tr>
<td valign="top">

<code><i>FINALIZE</i></code>

Finalizes processing and closes the archiving session

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
</table>

Typical flow of the archiving write process:

1.  Create an instance of the write API and open the archiving write session by using method `CL_ARCH_WRITE_API=>GET_INSTANCE`.

2.  Select the data from your application DB tables.

3.  For each data object you want to archive, call method `OPEN_DATA_OBJECT`.

4.  For each table you want to archive entries from, call method `PUT_DATA_RECORDS`.

5.  As soon as all tables of your data object are passed to the API, call method `CLOSE_DATA_OBJECT`.

6.  Either start with the next data object \(step 3\) or finish the archiving write session by calling method `FINALIZE`.


> ### Sample Code:  
> ```abap
> CONSTANTS: lc_object TYPE sarch_object VALUE ‘MY_OBJECT’. 
> " Replace with the name of your ADT archiving object
> " select flight data (leading table) from the database (replace table names with your names of your own tables)
>         SELECT * FROM my_header_table
>                  WHERE carrid     IN @lt_range_carrid
>                    AND connid     IN @lt_range_connid
>                    AND fldate     IN @lt_range_fldate
>           INTO TABLE @DATA(lt_flights).
>         " open a new archiving session to archive data
>         TRY.
>             DATA(lo_write) = cl_arch_write_api=>get_instance( iv_archiving_object = lc_object 								  iv_testmode = lv_test ).
> 
>             LOOP AT lt_flights ASSIGNING FIELD-SYMBOL(<ls_flight>).
>  " select data of dependent tables (replace table names with your names of your own tables)
>               INSERT <ls_flight> INTO lt_flights.
>               SELECT * FROM my_item_table1
>                  WHERE carrid     = @<ls_flight>-carrid
>                    AND connid     = @<ls_flight>-connid
>                    AND fldate     = @<ls_flight>-fldate
>                INTO TABLE @DATA(lt_bookings).
>               SELECT * FROM my_item_table2
>                  WHERE carrid     = @<ls_flight>-carrid
>                    AND connid     = @<ls_flight>-connid
>                    AND fldate     = @<ls_flight>-fldate
>                INTO TABLE @DATA(lt_tickets).
>               SELECT * FROM my_item_table3
>                  WHERE carrid     = @<ls_flight>-carrid
>                    AND connid     = @<ls_flight>-connid
>                    AND fldate     = @<ls_flight>-fldate
>                INTO TABLE @DATA(lt_invoices).
> 
>               " open new ADK data object
>               lo_write->open_data_object( ).
> 
>               " write data of header table
>               lo_write->put_data_records( iv_table_name = ‘<MY_HEADER_TALBE>’ it_records = lt_sflight_arch ).
>               CLEAR lt_sflight_arch.
> 
>               " write data of depending tables
>               lo_write->put_data_records( iv_table_name = ‘<MY_ITEM_TABLE1>’ it_records = lt_bookings ). " bookings
>               CLEAR lt_sflight_arch.
>               Lo_write->put_data_records( iv_table_name = ‘<MY_ITEM_TABLE2>’ it_records = lt_tickets ). " tickets
>               CLEAR lt_sflight_arch.
>               Lo_write->put_data_records( iv_table_name = ‘<MY_ITEM_TABLE3>’ it_records = lt_invoices ). " invoices
>               CLEAR lt_sflight_arch.
> 
>               " write data object into the archive file
>               lo_write->close_data_object( ).
> 
>             ENDLOOP.
> 
>             " finalize and end writing
>             lo_write->finalize( ).
> 
> ```

