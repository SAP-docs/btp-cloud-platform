<!-- loioa30fb84f8b974acb9218c4c6c6e6c587 -->

# Deleting a Change Document Object

Use method `IF_CHDO_OBJECT_TOOLS_REL~DELETE_OBJECT` to delete change document objects. The name of the object is assigned using the import parameter `IV_OBJECT`.

Furthermore, the import parameter `IV_DEL_CL_WHEN_USED` determines, if the class of the change document object should be deleted \(if value passed is `ABAP_TRUE`\) or not \(value `ABAP_FALSE`\) when it is still being used. The changes made to the class are saved in the transport request \(`IV_CORRNR`\).

The export parameter `ET_ERRORS` is used to return all deletion messages \(messages from message class `CD`\).

The object will be deleted if no exception and no error messages of kind ‘E-‘ were raised.

<a name="loioa30fb84f8b974acb9218c4c6c6e6c587__table_vz2_bvv_2jb"/>Import Parameters


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

Change document object name



</td>
</tr>
<tr>
<td valign="top">

IV\_CORRNR



</td>
<td valign="top">

 



</td>
<td valign="top">

Transport request where deletion should be logged



</td>
</tr>
<tr>
<td valign="top">

IV\_DEL\_CL\_WHEN\_USED



</td>
<td valign="top">

 



</td>
<td valign="top">

Delete generated class "CL\_<change document object name\>\_CHDO" even if it is currently used.



</td>
</tr>
</table>

<a name="loioa30fb84f8b974acb9218c4c6c6e6c587__table_uz2_3vv_2jb"/>Export Parameters


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
</table>

> ### Sample Code:  
> ```abap
> 
> CLASS zcl_chdo_delete_object DEFINITION
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
> CLASS zcl_chdo_delete_object IMPLEMENTATION.
>   METHOD if_oo_adt_classrun~main.
>     data: ls_error              TYPE abap_bool,
>           lr_err                TYPE REF TO cx_chdo_generation_error,
>           lt_errors_err         TYPE LINE OF if_chdo_object_tools_rel=>ty_tr_error_tab,
>           rt_errors             TYPE if_chdo_object_tools_rel=>ty_tr_error_tab.
>     TRY.
>       cl_chdo_object_tools_rel=>if_chdo_object_tools_rel~delete_object(
>         EXPORTING
>           iv_object           = 'ZCHDO_TEST'    " change document object name
>           iv_corrnr           = '<transport_request>'   " transport request number
>           iv_del_cl_when_used = 'X'             " delete class even when it is used
>         IMPORTING
>           et_errors           = rt_errors       " messages from deletion
>       ).
>       CATCH cx_chdo_generation_error into lr_err.
>         out->write( |Exception occurred: { lr_err->get_text( ) }| ).
>         ls_error ='X'.
>     ENDTRY.
>     IF ls_error IS INITIAL.
>       READ TABLE rt_errors WITH KEY kind = 'E-'
>                                INTO lt_errors_err.
>       IF sy-subrc IS INITIAL.
>         out->write( |Exception occurred: { lt_errors_err-text } | ).
>       ELSE.
>         out->write( |Change document object deleted | ).
>       ENDIF.
>     ENDIF.
>   ENDMETHOD.
> ENDCLASS.
> 
> ```

