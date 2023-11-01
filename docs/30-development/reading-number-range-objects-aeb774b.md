<!-- loioaeb774b1efe84d6d8c67f9299f001364 -->

# Reading Number Range Objects

Use the `READ` method to read the attributes of a number range object.

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

LANGUAGE

</td>
<td valign="top">

 

</td>
<td valign="top">

Language for the object texts

</td>
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

ATTRIBUTES

</td>
<td valign="top">

 

</td>
<td valign="top">

Number Range Object Definition.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

OBJECT

</td>
<td valign="top">

Number Range Object.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

DTELSOBJ

</td>
<td valign="top">

Data element for sub-object.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

YEARIND

</td>
<td valign="top">

Flag, whether number range object is to-year relevant.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

DOMLEN

</td>
<td valign="top">

Domain, which determines the length of the numbers.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

PERCENTAGE

</td>
<td valign="top">

Percentage of numbers remaining in an interval after having identified in which number assignment a warning is given.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

CODE

</td>
<td valign="top">

Transaction code to call interval maintenance \(obsolete for ABAP CP\).

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

BUFFER

</td>
<td valign="top">

Buffering type for number assignment.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

NOIVBUFFER

</td>
<td valign="top">

Number of numbers in the buffer.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

NRSWAP

</td>
<td valign="top">

Selecting the flag prevents intervals from automatically starting from the beginning at the upper limit.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

NRCHECKASCII

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

INTERVAL\_EXISTS

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

OBJ\_TEXT

</td>
<td valign="top">

 

</td>
<td valign="top">

Texts for objects for change document object creation.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

LANGU

</td>
<td valign="top">

Language.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

TXT

</td>
<td valign="top">

Description of object, long text.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

TXTSHORT

</td>
<td valign="top">

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

