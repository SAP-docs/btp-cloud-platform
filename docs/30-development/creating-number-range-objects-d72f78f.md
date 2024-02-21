<!-- loiod72f78f5dc7a4c859a9407e99026b330 -->

# Creating Number Range Objects

Use method `CREATE` to create number range objects.

When creating a number range object, the following naming-rules apply:

-   For customer objects, the name must start with a ‘Z’ or a ‘Y’.

-   The maximum length of a number range object is 10 characters.


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

Name Range Object.

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

Flag, whether number range object is to- year relevant.

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

Selecting the flag prevents the intervals from automatically starting from the beginning at the upper limit.

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

 

</td>
<td valign="top">

DEVCLASS

</td>
<td valign="top">

Development class of the object.

</td>
</tr>
<tr>
<td valign="top">

OBJ\_TEXT

</td>
<td valign="top">

CORRNR

</td>
<td valign="top">

Correction number for transport.

</td>
</tr>
<tr>
<td valign="top">

 

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

ERRORS

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

MSGID

</td>
<td valign="top">

Message class \(NR\)

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

MSGTYPE

</td>
<td valign="top">

Message type

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

MSGNUMBER

</td>
<td valign="top">

Message number

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

MSGVAR1

</td>
<td valign="top">

Variable to message

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

MSGVAR2

</td>
<td valign="top">

Variable to message

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

MSGVAR3

</td>
<td valign="top">

Variable to message

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

MSGVAR4

</td>
<td valign="top">

Variable to message

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

TABLENAME

</td>
<td valign="top">

Table

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

FIELDNAME

</td>
<td valign="top">

Field

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

CRITCHANGE

</td>
<td valign="top">

Critical change

</td>
</tr>
<tr>
<td valign="top">

RETURNCODE

</td>
<td valign="top">

 

</td>
<td valign="top">

Space: no error

E: error

W: warning

</td>
</tr>
</table>

> ### Sample Code:  
> ```abap
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

