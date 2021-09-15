<!-- loio5213a1d09ac14e7d85153ecbf264a106 -->

# Deleting Number Range Objects

Use method `DELETE` to delete number range objects.

<a name="loio5213a1d09ac14e7d85153ecbf264a106__table_os3_mvy_fjb"/>Import Parameters


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

OBJECT



</td>
<td>

 



</td>
<td>

Number Range Object



</td>
</tr>
<tr>
<td>

CORRNR



</td>
<td>

 



</td>
<td>

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

