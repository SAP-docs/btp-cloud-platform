<!-- loioc34f02daa1824f96a9a9e2cb2017d80f -->

# Reading Change Documents

Use class `CL_CHDO_READ_TOOLS` to read change documents.

Method `CHANGEDOCUMENT_READ` reads the change documents for one change document object. You can restrict the search by various parameters \(such as changed by, date, or time\).

<a name="loioc34f02daa1824f96a9a9e2cb2017d80f__table_dwd_kzv_2jb"/>Import Parameters


<table>
<tr>
<th>

Parameter Name



</th>
<th>

Field Name



</th>
<th>

Value Help



</th>
</tr>
<tr>
<td>

ET\_CDREDADD\_TAB



</td>
<td>

 



</td>
<td>

Table type for structure `CDREDADD`, change documents return table



</td>
</tr>
<tr>
<td>

I\_OBJECTCLAS



</td>
<td>

 



</td>
<td>

Name of change document object



</td>
</tr>
<tr>
<td>

IT\_OBJECTID



</td>
<td>

 



</td>
<td>

Range table of application object IDs



</td>
</tr>
<tr>
<td>

I\_DATE\_OF\_CHANGE



</td>
<td>

 



</td>
<td>

From-change date for search. All change documents are selected written on the specified date or later are found.



</td>
</tr>
<tr>
<td>

I\_TIME\_OF\_CHANGE



</td>
<td>

 



</td>
<td>

From-change time for search. If no change time is specified, a selection is made from the time '000000'.



</td>
</tr>
<tr>
<td>

I\_DATE\_UNTIL



</td>
<td>

 



</td>
<td>

Change date up to which you want to search. All change documents are selected written up to and including this date.



</td>
</tr>
<tr>
<td>

I\_TIME\_UNTIL



</td>
<td>

 



</td>
<td>

Latest change time in search. Time to which change documents are read on the "To" change date. If no time is passed, all change documents on the "To" change date are read.



</td>
</tr>
<tr>
<td>

IT\_USERNAME



</td>
<td>

 



</td>
<td>

Username of the person responsible in change document. Only those change documents are selected that document changes made by this user. If no user name is passed, change documents are read for all users.



</td>
</tr>
<tr>
<td>

IT\_READ\_OPTIONS



</td>
<td>

 



</td>
<td>



</td>
</tr>
<tr>
<td>

 



</td>
<td>

local\_time



</td>
<td>

If it is set, the date and time information in the formatted change documents is displayed in the local time of the user.



</td>
</tr>
<tr>
<td>

 



</td>
<td>

time\_zone



</td>
<td>

It contains the time zone in which the change documents were written. If it’s not set UTC applies.

If it contains a time zone, this zone is used as the time zone in which the change documents were saved.

If the change documents were saved in CET, the parameter must be set to CET.



</td>
</tr>
<tr>
<td>

 



</td>
<td>

it\_changenr



</td>
<td>

Range table for change document number. Change document numbers were created internally as part of key of change documents. The key of change document is represented by Object name, Object ID of the application object and a change number. During creation of change documents using the write method of class `<name space>CL_<change document object name>_CHDO`

Change documents numbers were received by export paramter `CHANGENUMBER`.



</td>
</tr>
</table>

<a name="loioc34f02daa1824f96a9a9e2cb2017d80f__table_uy5_tzv_2jb"/>Export Parameter


<table>
<tr>
<th>

Parameter Name



</th>
<th>

Field Name



</th>
<th>

Value Help



</th>
</tr>
<tr>
<td>



</td>
<td>

OBJECTCLAS



</td>
<td>

Name of Change Document Object



</td>
</tr>
<tr>
<td>



</td>
<td>

OBJECTID



</td>
<td>

Object ID of application object



</td>
</tr>
<tr>
<td>



</td>
<td>

OBJECTID\_DB



</td>
<td>

Object value



</td>
</tr>
<tr>
<td>



</td>
<td>

CHANGENR



</td>
<td>

Change Number of Document



</td>
</tr>
<tr>
<td>



</td>
<td>

OBJECTTXT



</td>
<td>

Object Description



</td>
</tr>
<tr>
<td>



</td>
<td>

USERNAME



</td>
<td>

Username of the person responsible in change document



</td>
</tr>
<tr>
<td>



</td>
<td>

USERNAME\_DB



</td>
<td>

Username of the person responsible in change document



</td>
</tr>
<tr>
<td>



</td>
<td>

UDATE



</td>
<td>

Creation date of the change document



</td>
</tr>
<tr>
<td>



</td>
<td>

UDATE\_DB



</td>
<td>

Creation date of the change document



</td>
</tr>
<tr>
<td>



</td>
<td>

UTIME



</td>
<td>

Time changed



</td>
</tr>
<tr>
<td>



</td>
<td>

UTIME\_DB



</td>
<td>

Time changed



</td>
</tr>
<tr>
<td>



</td>
<td>

TCODE



</td>
<td>

Transaction in which a change was made



</td>
</tr>
<tr>
<td>



</td>
<td>

APPLNAME



</td>
<td>

Application Object



</td>
</tr>
<tr>
<td>



</td>
<td>

APPLTYPE



</td>
<td>

Application Type



</td>
</tr>
<tr>
<td>



</td>
<td>

TABNAME



</td>
<td>

Change document creation: Table name



</td>
</tr>
<tr>
<td>



</td>
<td>

TABNAME\_DB



</td>
<td>

Change document creation: Table name



</td>
</tr>
<tr>
<td>



</td>
<td>

TABKEY



</td>
<td>

Key of Changed Table Line



</td>
</tr>
<tr>
<td>



</td>
<td>

TABKEY\_DB



</td>
<td>

Key of Changed Table Line



</td>
</tr>
<tr>
<td>



</td>
<td>

KEYLEN



</td>
<td>

Table key length



</td>
</tr>
<tr>
<td>



</td>
<td>

CHNGIND



</td>
<td>

Type of Change



</td>
</tr>
<tr>
<td>



</td>
<td>

FNAME



</td>
<td>

Field Name



</td>
</tr>
<tr>
<td>



</td>
<td>

FNAME\_DB



</td>
<td>

Field Name



</td>
</tr>
<tr>
<td>



</td>
<td>

FTEXT



</td>
<td>

Explanatory Short Text



</td>
</tr>
<tr>
<td>



</td>
<td>

TEXTART



</td>
<td>

Create change document: Text type



</td>
</tr>
<tr>
<td>



</td>
<td>

SPRACHE



</td>
<td>

Language Key



</td>
</tr>
<tr>
<td>



</td>
<td>

TEXT\_CASE



</td>
<td>

Text change flag \('X'\)



</td>
</tr>
<tr>
<td>



</td>
<td>

OUTLEN



</td>
<td>

Output length of the old and new value



</td>
</tr>
<tr>
<td>



</td>
<td>

F\_OLD



</td>
<td>

Old contents of changed field



</td>
</tr>
<tr>
<td>



</td>
<td>

F\_NEW



</td>
<td>

New contents of changed field



</td>
</tr>
<tr>
<td>



</td>
<td>

F\_NEW\_DB



</td>
<td>

New contents of changed field



</td>
</tr>
<tr>
<td>



</td>
<td>

VALUE\_OLD



</td>
<td>

Old Extended Value \(Long\)



</td>
</tr>
<tr>
<td>



</td>
<td>

VALUE\_OLD\_DB



</td>
<td>

Old Extended Value \(Long\)



</td>
</tr>
<tr>
<td>



</td>
<td>

VALUE\_NEW



</td>
<td>

New Extended Value \(Long\)



</td>
</tr>
<tr>
<td>



</td>
<td>

VALUE\_NEW\_DB



</td>
<td>

New Extended Value \(Long\)



</td>
</tr>
<tr>
<td>



</td>
<td>

VALUE\_RAWSTR\_OLD



</td>
<td>

Old Change Document Value for RAWSTRING Variable



</td>
</tr>
<tr>
<td>



</td>
<td>

VALUE\_RAWSTR\_OLD\_DB



</td>
<td>

Old Change Document Value for RAWSTRING Variable



</td>
</tr>
<tr>
<td>



</td>
<td>

VALUE\_RAWSTR\_NEW



</td>
<td>

New Change Document Value for RAWSTRING Variable



</td>
</tr>
<tr>
<td>



</td>
<td>

VALUE\_RAWSTR\_NEW\_DB



</td>
<td>

New Change Document Value for RAWSTRING Variable



</td>
</tr>
<tr>
<td>



</td>
<td>

VALUE\_SHSTR\_OLD



</td>
<td>

Old Extended Value \(Short\)



</td>
</tr>
<tr>
<td>



</td>
<td>

VALUE\_SHSTR\_OLD\_DB



</td>
<td>

Old Extended Value \(Short\)



</td>
</tr>
<tr>
<td>



</td>
<td>

VALUE\_SHSTR\_NEW



</td>
<td>

New Extended Value \(Short\)



</td>
</tr>
<tr>
<td>



</td>
<td>

VALUE\_SHSTR\_NEW\_DB



</td>
<td>

New Extended Value \(Short\)



</td>
</tr>
<tr>
<td>



</td>
<td>

KEYGUID



</td>
<td>

KEYGUID for Link to CDPOS\_UID



</td>
</tr>
<tr>
<td>



</td>
<td>

TABKEY254



</td>
<td>

Key of Modified Table Row



</td>
</tr>
<tr>
<td>



</td>
<td>

TABKEY254\_DB



</td>
<td>

Key of Modified Table Row



</td>
</tr>
<tr>
<td>



</td>
<td>

EXT\_KEYLEN



</td>
<td>

Table key length



</td>
</tr>
<tr>
<td>



</td>
<td>

KEYGUID\_STR



</td>
<td>

KEYGUID for Link to CDPOS\_STR



</td>
</tr>
<tr>
<td>



</td>
<td>

VERSION



</td>
<td>

3-Byte field



</td>
</tr>
</table>

> ### Sample Code:  
> Read all change documents for object class `ZCHDO_TEST`
> 
> ```lang-abap
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

