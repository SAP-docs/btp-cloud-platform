<!-- loio63cb1c060276481a99e2316e4bf9214e -->

# Creating a Change Document Object



When creating a change document object, the following naming-rules apply:

-   For customer objects, start the name with a ‘Z’ or a ‘Y’. For more information, see SAP Note 16466.

-   If a name space is requested, use an object starting with namespace as object name.

-   Keep in mind that the change document object name including the name space has a maximum length of 15 characters. That means that if the name space has 10 characters, only 5 characters are left for the change document object name.


**Process**

Use method `IF_CHDO_OBJECT_TOOLS_REL~CREATE_AND_GENERATE_OBJECT` to create and generate change document objects.

The name of the object is assigned using the import parameter `IV_OBJECT`. Object details and generation information are passed using the internal tables `IT_CD_OBJECT_DEF` \(the object definition\), `IT_CDOBJECT_TEXT` \(object texts\) and`IS_CD_OBJECT_GEN` \(generation information\).

Once generated, the class `(<name space>CL_<change document object name>_CHDO)` with methods `WRITE` and `IF_CHDO_ENHANCEMENTS~AUTHORITY_CHECK` are created. `IV_CL_OVERWRITE` can be used to specify whether an existing class with the specified name can be overwritten or not. If a class already exists and can’t be overwritten, no changes will be made. Changes are saved in the transport request \(`IV_CORRNR`\).

Method `AUTHORITY_CHECK` of interface `'IF_CHDO_ENHANCEMENTS'` must be implemented later on in order to enable an authorization check for reading change documents.

The export parameter `ET_ERRORS` is used to return all generation messages \(messages from message class `CD`\). Any syntax errors in the generated class are provided using `ET_SYNT_ERROR` \(with long text if applicable \(`ET_SYNT_ERROR_LONG`\)\).

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

IV\_OBJECT

</td>
<td valign="top">

 

</td>
<td valign="top">

Name of change document object

</td>
</tr>
<tr>
<td valign="top">

IT\_CD\_OBJECT\_DEF

</td>
<td valign="top">

 

</td>
<td valign="top">

Change document object definition

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

TABNAME

</td>
<td valign="top">

Name of the table as defined in the dictionary

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

MULTCASE

</td>
<td valign="top">

If more than one record for a particular table is to be documented during a single `CREATE/UPDATE/DELETE` operation, the value `MULTCASE` should be `‘ABAP_TRUE’` or `‘X’`\(multiple case\). If no value is provided a single record can be documented and passed in a work area \(single case\).

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

DOCUDEL

</td>
<td valign="top">

DOCUDEL = SPACE

The deletion of a table entry will be documented in one change document item using the table key to identify the table entry deleted. The field FNAME will be filled with `‘KEY’`.

DOCUDEL = ‘X’

Each change document relevant field value of the table entry will be documented individually in its own change document item.

The change indicator is ‘E’ instead of ‘D’.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

DOCUINS

</td>
<td valign="top">

DOCUINS = SPACE

The insert of a table entry will be documented in one change document item using the table key to identify the inserted table entry. The field FNAME will be filled with ‘KEY’.

DOCUINS = ‘X’

Each change document relevant field value of the table entry will be documented individually in its own change document item.

The change indicator is ‘J’ instead of ‘I’.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

REFNAME

</td>
<td valign="top">

If fields of table `TABNAME` reference unit or currency field values from another table, the name of that table must be passed here to document its values as well. Only one reference table can be used for table TABNAME.

In single case, the referenced entry from table `REFNAME` is passed as two additional work areas \(old, new\). In multiple case, the import tables \(old, new\) are enhanced to include the referenced structure of table `REFNAME`.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

DOCUD\_IF

</td>
<td valign="top">

If you want to document the value of a field even though it is initial when data is deleted, mark this field. If it is not marked, log entries will only be written if the field values are not initial when they are deleted.

Be aware that a lot of additional change documents may be written, if you choose this option. Only mark this flag if it is required.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

DOCUI\_IF

</td>
<td valign="top">

If you want to document the value of a field even though it is initial when data is inserted, mark this field. If it is not marked, log entries will only be written if the field values are not initial when they are inserted.

Be aware that a lot of additional change documents may be written, if you choose this option. Only mark this flag, if it is required.

</td>
</tr>
<tr>
<td valign="top">

IT\_CD\_OBJECT\_TEXT

</td>
<td valign="top">

 

</td>
<td valign="top">

Object texts for change document object

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

LANG\_KEY

</td>
<td valign="top">

Language key of the text

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

OBJECT\_TEXT

</td>
<td valign="top">

Descriptive short text for the change document object

</td>
</tr>
<tr>
<td valign="top">

IS\_CD\_OBJECT\_GEN

</td>
<td valign="top">

 

</td>
<td valign="top">

Change document object generation information

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

AUTHOR

</td>
<td valign="top">

User who performs the generation

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

UPDNAME

</td>
<td valign="top">

User who performs the change

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

CHANGE\_DATE

</td>
<td valign="top">

Date of change

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

CHANGE\_TIME

</td>
<td valign="top">

Time of change

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

TEXTCASE

</td>
<td valign="top">

Special Text Handling flag

Select this field to log long text changes. The old and new status of long texts is not logged. Only the fact that they have been changed is noted.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

DEVCLASS

</td>
<td valign="top">

Change document object package

</td>
</tr>
<tr>
<td valign="top">

IV\_CL\_OVERWRITE

</td>
<td valign="top">

 

</td>
<td valign="top">

Whether generated class should overwrite an already existing class. Value ‘X’ means an existing class will be overwritten.

</td>
</tr>
<tr>
<td valign="top">

IV\_CORRNR

</td>
<td valign="top">

 

</td>
<td valign="top">

Transport request where changes should be logged

</td>
</tr>
</table>

**Export Parameters**


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

ET\_ERRORS

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

kind

</td>
<td valign="top">

Message type \(emtpy means information message, ‚E-‚ means error\)

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

msgid

</td>
<td valign="top">

Message class \(CD\)

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

msgnr

</td>
<td valign="top">

Message ID

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

v1

</td>
<td valign="top">

Variable to message

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

v2

</td>
<td valign="top">

Variable to message

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

v3

</td>
<td valign="top">

Variable to message

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

v4

</td>
<td valign="top">

Variable to message

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

text

</td>
<td valign="top">

Short text of the message

</td>
</tr>
<tr>
<td valign="top">

ET\_SYNT\_ERRORS

</td>
<td valign="top">

 

</td>
<td valign="top">

Syntax errors raised during generation of class. Check syntax of generated class directly.

</td>
</tr>
<tr>
<td valign="top">

ET\_SYNT\_ERROR\_LONG

</td>
<td valign="top">

 

</td>
<td valign="top">

Syntax errors raised during generation of class. Check syntax of generated class directly.

</td>
</tr>
</table>

> ### Sample Code:  
> ```abap
> 
> CLASS zcl_chdo_test DEFINITION
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
> 
> 
> CLASS zcl_chdo_test IMPLEMENTATION.
>   METHOD if_oo_adt_classrun~main.
>     DATA:
>       ls_error       TYPE abap_bool,
>       rt_errors      TYPE if_chdo_object_tools_rel=>ty_tr_error_tab,
>       lt_errors_err  TYPE LINE OF if_chdo_object_tools_rel=>ty_tr_error_tab,
>       p_it_tcdob     TYPE if_chdo_object_tools_rel=>ty_tcdobdef_tab,
>       p_it_tcdobt    TYPE if_chdo_object_tools_rel=>ty_tcdobtext_tab,
>       p_it_tcdrp     TYPE if_chdo_object_tools_rel=>ty_tcdgen,
>       lt_tcdobt      TYPE if_chdo_object_tools_rel=>ty_tcdobt_tabtyp,
>       ls_tcdob       TYPE LINE OF if_chdo_object_tools_rel=>ty_tcdobdef_tab,
>       ls_tcdobt      TYPE LINE OF if_chdo_object_tools_rel=>ty_tcdobtext_tab.
>     data: lr_err                TYPE REF TO cx_chdo_generation_error.
>     ls_tcdob-tabname = 'ZCHDO'.
>     ls_tcdob-multcase = ' '.
>     ls_tcdob-docudel = ' '.
>     ls_tcdob-docuins = ' '.
>     ls_tcdob-docud_if = ' '.
> 
>     APPEND ls_tcdob TO p_it_tcdob.
> 
>     ls_tcdobt-lang_key = 'D'.
>     ls_tcdobt-object_text = 'Single Case'.
> 
>     APPEND ls_tcdobt TO p_it_tcdobt.
> 
>     p_it_tcdrp-author = 'X11'.
>     p_it_tcdrp-textcase = 'X'.
>     p_it_tcdrp-devclass = '<development class>'.
> 
>     CLEAR: rt_errors, lr_err.
>     TRY.
>       cl_chdo_object_tools_rel=>if_chdo_object_tools_rel~create_and_generate_object(
>         EXPORTING
>           iv_object          = 'ZCHDO_TEST' " change document object name
>           it_cd_object_def   = p_it_tcdob   " change document object definition
>           it_cd_object_text  = p_it_tcdobt  " change document object text
>           is_cd_object_gen   = p_it_tcdrp   " change document object generation info
>           iv_cl_overwrite    = 'X'          " class overwrite flag
>           iv_corrnr          = '<transport_request>' " transport request number
>         IMPORTING
>           et_errors          = rt_errors    " generation message table
> *          et_synt_errors     =
> *          et_synt_error_long =
>       ).
>       CATCH cx_chdo_generation_error into lr_err.
>         out->write( |Exception occurred: { lr_err->get_text( ) }| ).
>         ls_error = 'X'.
>     ENDTRY.
>       IF ls_error IS INITIAL.
>         READ TABLE rt_errors WITH KEY kind = 'E-'
>                                  INTO lt_errors_err.
>         IF sy-subrc IS INITIAL.
>           out->write( |Exception occurred: { lt_errors_err-text } | ).
>         ELSE.
>           out->write( |Change document object created and generated | ).
>         ENDIF.
>       ENDIF.
>   ENDMETHOD.
> ENDCLASS.
> 
> ```

