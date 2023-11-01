<!-- loioc34f02daa1824f96a9a9e2cb2017d80f -->

# Reading Change Documents

Use class `CL_CHDO_READ_TOOLS` to read change documents.

Method `CHANGEDOCUMENT_READ` reads the change documents for one change document object. You can restrict the search by various parameters \(such as changed by, date, or time\).

**Import Parameters**


<table>
<tr>
<th valign="top">

Parameter Name

</th>
<th valign="top">

Field Name

</th>
<th valign="top">

Value Help

</th>
</tr>
<tr>
<td valign="top">

ET\_CDREDADD\_TAB

</td>
<td valign="top">

 

</td>
<td valign="top">

Table type for structure `CDREDADD`, change documents return table

</td>
</tr>
<tr>
<td valign="top">

I\_OBJECTCLAS

</td>
<td valign="top">

 

</td>
<td valign="top">

Name of change document object

</td>
</tr>
<tr>
<td valign="top">

IT\_OBJECTID

</td>
<td valign="top">

 

</td>
<td valign="top">

Range table of application object IDs

</td>
</tr>
<tr>
<td valign="top">

I\_DATE\_OF\_CHANGE

</td>
<td valign="top">

 

</td>
<td valign="top">

From-change date for search. All change documents are selected written on the specified date or later are found.

</td>
</tr>
<tr>
<td valign="top">

I\_TIME\_OF\_CHANGE

</td>
<td valign="top">

 

</td>
<td valign="top">

From-change time for search. If no change time is specified, a selection is made from the time '000000'.

</td>
</tr>
<tr>
<td valign="top">

I\_DATE\_UNTIL

</td>
<td valign="top">

 

</td>
<td valign="top">

Change date up to which you want to search. All change documents are selected written up to and including this date.

</td>
</tr>
<tr>
<td valign="top">

I\_TIME\_UNTIL

</td>
<td valign="top">

 

</td>
<td valign="top">

Latest change time in search. Time to which change documents are read on the "To" change date. If no time is passed, all change documents on the "To" change date are read.

</td>
</tr>
<tr>
<td valign="top">

IT\_USERNAME

</td>
<td valign="top">

 

</td>
<td valign="top">

Username of the person responsible in change document. Only those change documents are selected that document changes made by this user. If no user name is passed, change documents are read for all users.

</td>
</tr>
<tr>
<td valign="top">

IS\_READ\_OPTIONS

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

local\_time

</td>
<td valign="top">

If it is set, the date and time information in the formatted change documents is displayed in the local time of the user.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

time\_zone

</td>
<td valign="top">

It contains the time zone in which the change documents were written. If it’s not set UTC applies.

If it contains a time zone, this zone is used as the time zone in which the change documents were saved.

If the change documents were saved in CET, the parameter must be set to CET.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

it\_changenr

</td>
<td valign="top">

Range table for change document number. Change document numbers were created internally as part of key of change documents. The key of change document is represented by Object name, Object ID of the application object and a change number. During creation of change documents using the write method of class `<name space>CL_<change document object name>_CHDO`

Change documents numbers were received by export paramter `CHANGENUMBER`.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

only\_headers

</td>
<td valign="top">

Only return the change document header information without the position

</td>
</tr>
<tr>
<td valign="top">

IV\_READ\_ARCHIVE

</td>
<td valign="top">

 

</td>
<td valign="top">

Control the interface to read change documents from the archive, too

</td>
</tr>
</table>

**Export Parameter**


<table>
<tr>
<th valign="top">

Parameter Name

</th>
<th valign="top">

Field Name

</th>
<th valign="top">

Value Help

</th>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

OBJECTCLAS

</td>
<td valign="top">

Name of Change Document Object

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

OBJECTID

</td>
<td valign="top">

Object ID of application object

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

OBJECTID\_DB

</td>
<td valign="top">

Object value

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

CHANGENR

</td>
<td valign="top">

Change Number of Document

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

OBJECTTXT

</td>
<td valign="top">

Object Description

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

USERNAME

</td>
<td valign="top">

Username of the person responsible in change document

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

USERNAME\_DB

</td>
<td valign="top">

Username of the person responsible in change document

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

UDATE

</td>
<td valign="top">

Creation date of the change document

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

UDATE\_DB

</td>
<td valign="top">

Creation date of the change document

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

UTIME

</td>
<td valign="top">

Time changed

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

UTIME\_DB

</td>
<td valign="top">

Time changed

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

TCODE

</td>
<td valign="top">

Transaction in which a change was made

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

APPLNAME

</td>
<td valign="top">

Application Object

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

APPLTYPE

</td>
<td valign="top">

Application Type

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

TABNAME

</td>
<td valign="top">

Change document creation: Table name

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

TABNAME\_DB

</td>
<td valign="top">

Change document creation: Table name

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

TABKEY

</td>
<td valign="top">

Key of Changed Table Line

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

TABKEY\_DB

</td>
<td valign="top">

Key of Changed Table Line

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

KEYLEN

</td>
<td valign="top">

Table key length

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

CHNGIND

</td>
<td valign="top">

Type of Change

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

FNAME

</td>
<td valign="top">

Field Name

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

FNAME\_DB

</td>
<td valign="top">

Field Name

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

FTEXT

</td>
<td valign="top">

Explanatory Short Text

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

TEXTART

</td>
<td valign="top">

Create change document: Text type

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

SPRACHE

</td>
<td valign="top">

Language Key

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

TEXT\_CASE

</td>
<td valign="top">

Text change flag \('X'\)

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

OUTLEN

</td>
<td valign="top">

Output length of the old and new value

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

F\_OLD

</td>
<td valign="top">

Old contents of changed field

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

F\_NEW

</td>
<td valign="top">

New contents of changed field

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

F\_NEW\_DB

</td>
<td valign="top">

New contents of changed field

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

VALUE\_OLD

</td>
<td valign="top">

Old Extended Value \(Long\)

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

VALUE\_OLD\_DB

</td>
<td valign="top">

Old Extended Value \(Long\)

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

VALUE\_NEW

</td>
<td valign="top">

New Extended Value \(Long\)

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

VALUE\_NEW\_DB

</td>
<td valign="top">

New Extended Value \(Long\)

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

VALUE\_RAWSTR\_OLD

</td>
<td valign="top">

Old Change Document Value for RAWSTRING Variable

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

VALUE\_RAWSTR\_OLD\_DB

</td>
<td valign="top">

Old Change Document Value for RAWSTRING Variable

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

VALUE\_RAWSTR\_NEW

</td>
<td valign="top">

New Change Document Value for RAWSTRING Variable

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

VALUE\_RAWSTR\_NEW\_DB

</td>
<td valign="top">

New Change Document Value for RAWSTRING Variable

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

VALUE\_SHSTR\_OLD

</td>
<td valign="top">

Old Extended Value \(Short\)

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

VALUE\_SHSTR\_OLD\_DB

</td>
<td valign="top">

Old Extended Value \(Short\)

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

VALUE\_SHSTR\_NEW

</td>
<td valign="top">

New Extended Value \(Short\)

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

VALUE\_SHSTR\_NEW\_DB

</td>
<td valign="top">

New Extended Value \(Short\)

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

KEYGUID

</td>
<td valign="top">

KEYGUID for Link to CDPOS\_UID

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

TABKEY254

</td>
<td valign="top">

Key of Modified Table Row

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

TABKEY254\_DB

</td>
<td valign="top">

Key of Modified Table Row

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

EXT\_KEYLEN

</td>
<td valign="top">

Table key length

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

KEYGUID\_STR

</td>
<td valign="top">

KEYGUID for Link to CDPOS\_STR

</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

VERSION

</td>
<td valign="top">

3-Byte field

</td>
</tr>
</table>

> ### Sample Code:  
> Read all change documents for object class `ZCHDO_TEST`
> 
> ```abap
> 
> CLASS zcl_chdo_read DEFINITION
>   PUBLIC
>   FINAL
>   CREATE PUBLIC .
> 
>   PUBLIC SECTION.
>    INTERFACES if_oo_adt_classrun.
>   PROTECTED SECTION.
>   PRIVATE SECTION.
> ENDCLASS.
> 
> CLASS zcl_chdo_read IMPLEMENTATION.
>   METHOD if_oo_adt_classrun~main.
> 
>     DATA: rt_cdredadd TYPE cl_chdo_read_tools=>TT_CDREDADD_TAB,
>           lr_err      TYPE REF TO cx_chdo_read_error.
> 
>     TRY.
>       cl_chdo_read_tools=>changedocument_read(
>         EXPORTING
>           i_objectclass    = 'ZCHDO_TEST'  " change document object name 
> *          it_objectid      =              
> *          i_date_of_change =
> *          i_time_of_change =
> *          i_date_until     =
> *          i_time_until     =
> *          it_username      =
> *          it_read_options  =
>         IMPORTING
>           et_cdredadd_tab  = rt_cdredadd    " result returned in table 
>       ).
>        CATCH cx_chdo_read_error into lr_err.
>         out->write( |Exception occurred: { lr_err->get_text( ) }| ).
>     ENDTRY.
>   ENDMETHOD.
> ENDCLASS.
> 
> ```

> ### Sample Code:  
> Read all change documents for object class `ZCHDO_TEST` including the archive.
> 
> ```abap
> CLASS zcl_chdo_read DEFINITION
>   PUBLIC
>   FINAL
>   CREATE PUBLIC .
> 
>   PUBLIC SECTION.
>     INTERFACES if_oo_adt_classrun.
>   PROTECTED SECTION.
>   PRIVATE SECTION.
> ENDCLASS.
> 
> CLASS zcl_chdo_read IMPLEMENTATION.
>   METHOD if_oo_adt_classrun~main.
> 
>     DATA: rt_cdredadd TYPE cl_chdo_read_tools=>tt_cdredadd_tab,
>           lr_err      TYPE REF TO cx_chdo_read_error.
>     DATA lt_cdredadd TYPE cl_chdo_read_tools=>tt_cdredadd_tab.
> 
>     TRY.
> 
>         DATA(lt_files) = cl_arch_read_api=>get_files_to_read( iv_archiving_object = 'ZAOBJ_TEST' ).
>         SORT lt_files BY creation_date DESCENDING creation_time DESCENDING.
>         READ TABLE lt_files ASSIGNING FIELD-SYMBOL(<ls_file>) INDEX 1.
>         CHECK sy-subrc = 0. " no files
> 
>         DATA(lo_read) = cl_arch_read_api=>get_instance( iv_archiving_object = 'ZAOBJ_TEST'
>                                                         iv_archive_key = <ls_file>-archive_key ).
>         DO.
>           lo_read->get_next_data_object( IMPORTING ev_end_of_file = DATA(lv_end_of_file)
>                                                    ev_archive_key = DATA(lv_archive_key)
>                                                    ev_object_offset = DATA(lv_offset) ).
>           IF lv_end_of_file = abap_true.
>             EXIT.
>           ENDIF.
> *          no application data
> *          lo_read->get_data_records( EXPORTING iv_record_structure = 'XXX'
> *                                     IMPORTING et_data_records = lt_data ).
> *          APPEND LINES OF lt_data TO lt_data_all.
>           TRY.
>               cl_chdo_read_tools=>changedocument_read(
>                 EXPORTING
>                   i_objectclass    = 'ZCHDO_TEST'
>                   iv_read_archive  = lo_read
>                 IMPORTING
>                   et_cdredadd_tab  = DATA(lt_cd)
>               ).
>             CATCH cx_chdo_read_error INTO DATA(ls_read_err).
>               out->write( |Exception occurred: { ls_read_err->get_text( ) }| ).
>           ENDTRY.
>           APPEND LINES OF lt_cd TO lt_cdredadd.
> 
>         ENDDO.
>         lo_read->close( ).
>       CATCH cx_arch_api INTO DATA(lx_error).
>         out->write( |Exception occurred: { lx_error->get_text( ) }| ).
>     ENDTRY.
> 
>   ENDMETHOD.
> 
> ```

