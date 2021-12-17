<!-- loio798cf04e151f4b4f91eaa1bde8f65856 -->

# Reading a Change Document Object Definition

Use method `IF_CHDO_OBJECT_TOOLS_REL~READ_OBJECT` to read a change document object definition.

The name of the object is assigned using the import parameter `IV_OBJECT`. The information is returned using the export parameter `ET_OBJECT_INFO`.

<a name="loio798cf04e151f4b4f91eaa1bde8f65856__table_tlz_gwv_2jb"/>Import Parameter


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
</table>

<a name="loio798cf04e151f4b4f91eaa1bde8f65856__table_hcr_lwv_2jb"/>Export Parameters


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

ET\_OBJECT\_INFO



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

ET\_OBJECT\_INFO



</td>
<td valign="top">

Name of the change document object



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

ET\_OBJECT\_INFO



</td>
<td valign="top">

Generation information counter for field gen\_type



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

ET\_OBJECT\_INFO



</td>
<td valign="top">

Generation information type technical name \(DEFINITION, GENERATION, CLASS\)



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

ET\_OBJECT\_INFO



</td>
<td valign="top">

Generation information type text \(Definition, Generate, Class details\)



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

ET\_OBJECT\_INFO



</td>
<td valign="top">

Line counter for field name



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

ET\_OBJECT\_INFO



</td>
<td valign="top">

Information long text



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

ET\_OBJECT\_INFO



</td>
<td valign="top">

Information technical name



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

ET\_OBJECT\_INFO



</td>
<td valign="top">

Value of the change document object



</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

OBJECTCLASS



</td>
<td valign="top">

Name of the change document object



</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

GNR



</td>
<td valign="top">

Generation information counter for field gen\_type



</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

GEN\_TYPE



</td>
<td valign="top">

Generation information type technical name \(DEFINITION, GENERATION, CLASS\)



</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

GROUP



</td>
<td valign="top">

Generation information type text \(Definition, Generate, Class details\)



</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

ZNR



</td>
<td valign="top">

Line counter



</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

INFOTEXT



</td>
<td valign="top">

Information long text



</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

OBJ\_TYPE



</td>
<td valign="top">

Information technical name



</td>
</tr>
<tr>
<td valign="top">



</td>
<td valign="top">

NAME



</td>
<td valign="top">

Information value \(e.g. table name, package, user name, class name\)



</td>
</tr>
</table>

> ### Sample Code:  
> ```lang-abap
> 
> CLASS zcl_chdo_read_object DEFINITION
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
> CLASS zcl_chdo_read_object IMPLEMENTATION.
>   METHOD if_oo_adt_classrun~main.
>     DATA: pt_object_info TYPE if_chdo_object_tools_rel=>tty_object_info.
>     data: lr_err                TYPE REF TO cx_chdo_generation_error.
>       TRY.
>       cl_chdo_object_tools_rel=>if_chdo_object_tools_rel~read_object(
>         EXPORTING
>           iv_object      = 'ZCHDO_TEST'     " change document object name
>         IMPORTING
>           et_object_info = pt_object_info   " change document object details
>       ).
>       CATCH cx_chdo_generation_error INTO lr_err.
>         out->write( |Exception occurred: { lr_err->get_text( ) }| ).
>     ENDTRY.
>   ENDMETHOD.
> ENDCLASS.
> 
> ```

