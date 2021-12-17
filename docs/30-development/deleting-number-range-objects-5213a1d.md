<!-- loio5213a1d09ac14e7d85153ecbf264a106 -->

# Deleting Number Range Objects

Use method `DELETE` to delete number range objects.

<a name="loio5213a1d09ac14e7d85153ecbf264a106__table_os3_mvy_fjb"/>Import Parameters


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

OBJECT



</td>
<td valign="top">

 



</td>
<td valign="top">

Number Range Object



</td>
</tr>
<tr>
<td valign="top">

CORRNR



</td>
<td valign="top">

 



</td>
<td valign="top">

Correction number for transport



</td>
</tr>
</table>

> ### Sample Code:  
> ```
> 
> …
> lv_object = 'Z_TEST_03'.
> lv_corrnr = 'SIDK123456'.
> …
>   cl_numberrange_objects=>delete(
>     EXPORTING
>       object = lv_object
>       corrnr = lv_corrnr
>         ).
> …
> 
> ```

