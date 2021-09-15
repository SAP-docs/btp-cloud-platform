<!-- loioaeb774b1efe84d6d8c67f9299f001364 -->

# Reading Number Range Objects

Use the `READ` method to read the attributes of a number range object.

<a name="loioaeb774b1efe84d6d8c67f9299f001364__table_j2z_rwy_fjb"/>Import Parameters


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

LANGUAGE



</td>
<td>

 



</td>
<td>

Language for the object texts



</td>
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
</table>

<a name="loioaeb774b1efe84d6d8c67f9299f001364__table_onc_zwy_fjb"/>Export Parameters


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

ATTRIBUTES



</td>
<td>

 



</td>
<td>

Number Range Object Definition.



</td>
</tr>
<tr>
<td>

 



</td>
<td>

OBJECT



</td>
<td>

Number Range Object.



</td>
</tr>
<tr>
<td>

 



</td>
<td>

DTELSOBJ



</td>
<td>

Data element for sub-object.



</td>
</tr>
<tr>
<td>

 



</td>
<td>

YEARIND



</td>
<td>

Flag, whether number range object is to-year relevant.



</td>
</tr>
<tr>
<td>

 



</td>
<td>

DOMLEN



</td>
<td>

Domain, which determines the length of the numbers.



</td>
</tr>
<tr>
<td>

 



</td>
<td>

PERCENTAGE



</td>
<td>

Percentage of numbers remaining in an interval after having identified in which number assignment a warning is given.



</td>
</tr>
<tr>
<td>

 



</td>
<td>

CODE



</td>
<td>

Transaction code to call interval maintenance \(obsolete for ABAP CP\).



</td>
</tr>
<tr>
<td>

 



</td>
<td>

BUFFER



</td>
<td>

Buffering type for number assignment.



</td>
</tr>
<tr>
<td>

 



</td>
<td>

NOIVBUFFER



</td>
<td>

Number of numbers in the buffer.



</td>
</tr>
<tr>
<td>

 



</td>
<td>

NRSWAP



</td>
<td>

Selecting the flag prevents intervals from automatically starting from the beginning at the upper limit.



</td>
</tr>
<tr>
<td>

 



</td>
<td>

NRCHECKASCII



</td>
<td>

 



</td>
</tr>
<tr>
<td>

INTERVAL\_EXISTS



</td>
<td>

 



</td>
<td>

 



</td>
</tr>
<tr>
<td>

OBJ\_TEXT



</td>
<td>

 



</td>
<td>

Texts for objects for change document object creation.



</td>
</tr>
<tr>
<td>

 



</td>
<td>

LANGU



</td>
<td>

Language.



</td>
</tr>
<tr>
<td>

 



</td>
<td>

TXT



</td>
<td>

Description of object, long text.



</td>
</tr>
<tr>
<td>

 



</td>
<td>

TXTSHORT



</td>
<td>

Description of object, short text.



</td>
</tr>
</table>

> ### Sample Code:  
> ```
> 
> …
>  lv_object = 'Z_TEST_03'
> …
> cl_numberrange_objects=>read(
>           EXPORTING
>             language        = sy-langu
>             object          = lv_object
>           IMPORTING
>             attributes      = DATA(ls_attributes)
>             interval_exists = DATA(lv_interval_exists)
>             obj_text        = DATA(obj_text)
>         ).
> …
> 
> ```

