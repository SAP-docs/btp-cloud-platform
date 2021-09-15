<!-- loioa30fb84f8b974acb9218c4c6c6e6c587 -->

# Deleting a Change Document Object

Use method `IF_CHDO_OBJECT_TOOLS_REL~DELETE_OBJECT` to delete change document objects. The name of the object is assigned using the import parameter `IV_OBJECT`.

Furthermore, the import parameter `IV_DEL_CL_WHEN_USED` determines, if the class of the change document object should be deleted \(if value passed is `ABAP_TRUE`\) or not \(value `ABAP_FALSE`\) when it is still being used. The changes made to the class are saved in the transport request \(`IV_CORRNR`\).

The export parameter `ET_ERRORS` is used to return all deletion messages \(messages from message class `CD`\).

The object will be deleted if no exception and no error messages of kind ‘E-‘ were raised.

<a name="loioa30fb84f8b974acb9218c4c6c6e6c587__table_vz2_bvv_2jb"/>Import Parameters


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

IV\_OBJECT



</td>
<td>

 



</td>
<td>

Change document object name



</td>
</tr>
<tr>
<td>

IV\_CORRNR



</td>
<td>

 



</td>
<td>

Transport request where deletion should be logged



</td>
</tr>
<tr>
<td>

IV\_DEL\_CL\_WHEN\_USED



</td>
<td>

 



</td>
<td>

Delete generated class "CL\_<change document object name\>\_CHDO" even if it is currently used.



</td>
</tr>
</table>

<a name="loioa30fb84f8b974acb9218c4c6c6e6c587__table_uz2_3vv_2jb"/>Export Parameters


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

ET\_ERRORS



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

kind



</td>
<td>

Message type \(emtpy means information message, ‚E-‚ means error\)



</td>
</tr>
<tr>
<td>

 



</td>
<td>

msgid



</td>
<td>

Message class \(CD\)



</td>
</tr>
<tr>
<td>

 



</td>
<td>

msgnr



</td>
<td>

Message ID



</td>
</tr>
<tr>
<td>

 



</td>
<td>

v1



</td>
<td>

Variable to message



</td>
</tr>
<tr>
<td>

 



</td>
<td>

v2



</td>
<td>

Variable to message



</td>
</tr>
<tr>
<td>

 



</td>
<td>

v3



</td>
<td>

Variable to message



</td>
</tr>
<tr>
<td>

 



</td>
<td>

v4



</td>
<td>

Variable to message



</td>
</tr>
<tr>
<td>

 



</td>
<td>

text



</td>
<td>

Short text of the message



</td>
</tr>
</table>

> ### Sample Code:  
> ```lang-abap
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

