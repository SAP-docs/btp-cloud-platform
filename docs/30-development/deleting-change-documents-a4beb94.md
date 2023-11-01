<!-- loioa4beb9453c084561bfd154a21d91cece -->

# Deleting Change Documents

Use class `CL_CHDO_DELETE_TOOLS` to delete change documents.

First use `GET_INSTANCE` method to create an instance for the interface `IF_CHDO_DELETE_TOOLS`.


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

RO\_INSTANCE

</td>
<td valign="top">

 

</td>
<td valign="top">

Return parameter for instance creation

</td>
</tr>
</table>

Method `IF_CHDO_DELETE_TOOLS~CHANGEDOCUMENT_DELETE` deletes the change documents for one change document object. You can restrict the selection by various parameters \(such as date, change number or time\).

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

I\_OBJECTCLASS

</td>
<td valign="top">

 

</td>
<td valign="top">

Name of change document object

</td>
</tr>
<tr>
<td valign="top">

I\_OBJECTID

</td>
<td valign="top">

 

</td>
<td valign="top">

Parameter of application objects IDs

</td>
</tr>
<tr>
<td valign="top">

I\_UP\_TO\_DATE

</td>
<td valign="top">

 

</td>
<td valign="top">

Date by which the change documents are to be deleted

All change documents until the specified date are deleted.

</td>
</tr>
<tr>
<td valign="top">

I\_CHANGENUMBER

</td>
<td valign="top">

 

</td>
<td valign="top">

Change Number of Document

If only one specific change document number is to be deleted, it can be transferred here.

</td>
</tr>
<tr>
<td valign="top">

I\_WITH\_COMMIT

</td>
<td valign="top">

 

</td>
<td valign="top">

Flag whether there should be a `COMMIT WORK` in the method.

The flag determines whether a `COMMIT WORK` should be called in the method. This can be necessary when a lot is to be deleted. In this case the delete operations are divided up to avoid Rollback segment overflow. The division is by clusters, so that no inconsistencies occur in the case of cancellation.

</td>
</tr>
<tr>
<td valign="top">

COMMIT\_COUNTER

</td>
<td valign="top">

 

</td>
<td valign="top">

The parameter is only effective when a `COMMIT WORK` should be performed in the method \(see parameter `I_WITH_COMMIT`\).

In the method, as many object change documents are read as are passed in `COMMIT_COUNTER`. These change documents are then deleted, and `COMMIT WORK` called. This procedure is repeated until there are no more change documents for the object before the until date.

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

E\_NUMBER\_OF\_DELETED\_HEADERS

</td>
<td valign="top">

 

</td>
<td valign="top">

Number of deleted change document headers

This parameter contains the number of deleted change document headers

</td>
</tr>
<tr>
<td valign="top">

E\_NUMBER\_OF\_DELETED\_POSITIONS

</td>
<td valign="top">

 

</td>
<td valign="top">

Number of deleted change document items

This parameter contains the number of deleted change document items.

</td>
</tr>
<tr>
<td valign="top">

E\_NUMBER\_OF\_DELETED\_UIDS

</td>
<td valign="top">

 

</td>
<td valign="top">

Number of deleted change document item GUIDs

</td>
</tr>
<tr>
<td valign="top">

E\_NUMBER\_OF\_DELETED\_STRINGS

</td>
<td valign="top">

 

</td>
<td valign="top">

Number of deleted change document item STRINGs

This parameter contains the number of deleted change document items with STRINGs.

</td>
</tr>
</table>

> ### Sample Code:  
> ```abap
> 
> DATA lv_objectclass   TYPE if_chdo_object_tools_rel=>ty_cdobjectcl VALUE 'ZTEST_CO'.
>     DATA lv_objectid  TYPE cl_chdo_write_tools=>ty_cdobjectv VALUE '9990001'.
>     DATA lv_changenr  TYPE cl_chdo_write_tools=>ty_cdchangenr VALUE '0000000001'.
>     DATA lr_err TYPE REF TO cx_chdo_delete_error.
> 
>           ).
> 
>     TRY.
> 
>       DATA(lo_instance) = cl_chdo_delete_tools=>get_instance( ).
> 
>       lo_instance->if_chdo_delete_tools~changedocument_delete(
>         EXPORTING
>           i_objectclass                 = lv_objectclass
>           it_objectid                   = lv_objectid
>           i_changenumber                = lv_changenr
>           i_with_commit                 = abap_true
>         IMPORTING
>           e_number_of_deleted_headers   = DATA(ls_headers)
>           e_number_of_deleted_positions = DATA(ls_positions)
>           e_number_of_deleted_uids      = DATA(ls_uids)
>           e_number_of_deleted_strings   = DATA(ls_strings)
>       ).
>       CATCH cx_chdo_delete_error INTO lr_err.
> *	error handling for deletion
>     ENDTRY.
> 
> ```

