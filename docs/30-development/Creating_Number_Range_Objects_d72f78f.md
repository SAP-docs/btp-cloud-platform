<!-- loiod72f78f5dc7a4c859a9407e99026b330 -->

# Creating Number Range Objects

Use method `CREATE` to create number range objects.

When creating a number range object, the following naming-rules apply:

-   For customer objects, the name must start with a ‘Z’ or a ‘Y’.

-   The maximum length of a number range object is 10 characters.


<a name="loiod72f78f5dc7a4c859a9407e99026b330__table_hw1_gry_fjb"/>Import Parameters


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

Name Range Object.



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

Flag, whether number range object is to- year relevant.



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

Selecting the flag prevents the intervals from automatically starting from the beginning at the upper limit.



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

 



</td>
<td>

DEVCLASS



</td>
<td>

Development class of the object.



</td>
</tr>
<tr>
<td>

OBJ\_TEXT



</td>
<td>

CORRNR



</td>
<td>

Correction number for transport.



</td>
</tr>
<tr>
<td>

 



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

<a name="loiod72f78f5dc7a4c859a9407e99026b330__table_skr_yty_fjb"/>Export Parameters


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

ERRORS



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

MSGID



</td>
<td>

Message class \(NR\)



</td>
</tr>
<tr>
<td>

 



</td>
<td>

MSGTYPE



</td>
<td>

Message type



</td>
</tr>
<tr>
<td>

 



</td>
<td>

MSGNUMBER



</td>
<td>

Message number



</td>
</tr>
<tr>
<td>

 



</td>
<td>

MSGVAR1



</td>
<td>

Variable to message



</td>
</tr>
<tr>
<td>

 



</td>
<td>

MSGVAR2



</td>
<td>

Variable to message



</td>
</tr>
<tr>
<td>

 



</td>
<td>

MSGVAR3



</td>
<td>

Variable to message



</td>
</tr>
<tr>
<td>

 



</td>
<td>

MSGVAR4



</td>
<td>

Variable to message



</td>
</tr>
<tr>
<td>

 



</td>
<td>

TABLENAME



</td>
<td>

Table



</td>
</tr>
<tr>
<td>

 



</td>
<td>

FIELDNAME



</td>
<td>

Field



</td>
</tr>
<tr>
<td>

 



</td>
<td>

CRITCHANGE



</td>
<td>

Critical change



</td>
</tr>
<tr>
<td>

RETURNCODE



</td>
<td>

 



</td>
<td>

Space: no error

E: error

W: warning



</td>
</tr>
</table>

> ### Sample Code:  
> ```
> 
> CLASS zcl_nr_object_create DEFINITION
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
> CLASS zcl_nr_object_create IMPLEMENTATION.
>   METHOD if_oo_adt_classrun~main.
> 
>   DATA: 
>     lv_object   TYPE cl_numberrange_objects=>nr_attributes-object,
>     lv_devclass TYPE cl_numberrange_objects=>nr_attributes-devclass,
>     lv_corrnr   TYPE cl_numberrange_objects=>nr_attributes-corrnr.
> 
>     lv_object   = 'Z_TEST_03'.
>     lv_devclass = 'Z_SNUM'.
>     lv_corrnr   = 'SIDK123456'.
> 
>     TRY.
>     cl_numberrange_objects=>create(
>       EXPORTING
>         attributes = VALUE #( object     = lv_object
>                               domlen     = 'CHAR8'
>                               percentage = 5
>                               buffer     = abap_true
>                               noivbuffer = 10
>                               devclass   = lv_devclass
>                               corrnr     = lv_corrnr )
>         obj_text   = VALUE #( object     = lv_object
>                               langu      = 'E'
>                               txt        = 'Create object'
>                               txtshort   = 'Test create' )
>       IMPORTING
>         errors     = DATA(lt_errors)
>         returncode = DATA(lv_returncode)
>         ).
>       CATCH.
>         …
>     ENDTRY.
>     …
>   ENDMETHOD.
> ENDCLASS. 
> 
> ```

