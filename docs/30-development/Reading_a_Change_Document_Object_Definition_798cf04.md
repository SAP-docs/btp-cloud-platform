<!-- loio798cf04e151f4b4f91eaa1bde8f65856 -->

# Reading a Change Document Object Definition

Use method `IF_CHDO_OBJECT_TOOLS_REL~READ_OBJECT` to read a change document object definition.

The name of the object is assigned using the import parameter `IV_OBJECT`. The information is returned using the export parameter `ET_OBJECT_INFO`.

<a name="loio798cf04e151f4b4f91eaa1bde8f65856__table_tlz_gwv_2jb"/>Import Parameter


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
</table>

<a name="loio798cf04e151f4b4f91eaa1bde8f65856__table_hcr_lwv_2jb"/>Export Parameters


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

ET\_OBJECT\_INFO



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

ET\_OBJECT\_INFO



</td>
<td>

Name of the change document object



</td>
</tr>
<tr>
<td>

 



</td>
<td>

ET\_OBJECT\_INFO



</td>
<td>

Generation information counter for field gen\_type



</td>
</tr>
<tr>
<td>

 



</td>
<td>

ET\_OBJECT\_INFO



</td>
<td>

Generation information type technical name \(DEFINITION, GENERATION, CLASS\)



</td>
</tr>
<tr>
<td>

 



</td>
<td>

ET\_OBJECT\_INFO



</td>
<td>

Generation information type text \(Definition, Generate, Class details\)



</td>
</tr>
<tr>
<td>

 



</td>
<td>

ET\_OBJECT\_INFO



</td>
<td>

Line counter for field name



</td>
</tr>
<tr>
<td>

 



</td>
<td>

ET\_OBJECT\_INFO



</td>
<td>

Information long text



</td>
</tr>
<tr>
<td>

 



</td>
<td>

ET\_OBJECT\_INFO



</td>
<td>

Information technical name



</td>
</tr>
<tr>
<td>

 



</td>
<td>

ET\_OBJECT\_INFO



</td>
<td>

Value of the change document object



</td>
</tr>
<tr>
<td>



</td>
<td>

OBJECTCLASS



</td>
<td>

Name of the change document object



</td>
</tr>
<tr>
<td>



</td>
<td>

GNR



</td>
<td>

Generation information counter for field gen\_type



</td>
</tr>
<tr>
<td>



</td>
<td>

GEN\_TYPE



</td>
<td>

Generation information type technical name \(DEFINITION, GENERATION, CLASS\)



</td>
</tr>
<tr>
<td>



</td>
<td>

GROUP



</td>
<td>

Generation information type text \(Definition, Generate, Class details\)



</td>
</tr>
<tr>
<td>



</td>
<td>

ZNR



</td>
<td>

Line counter



</td>
</tr>
<tr>
<td>



</td>
<td>

INFOTEXT



</td>
<td>

Information long text



</td>
</tr>
<tr>
<td>



</td>
<td>

OBJ\_TYPE



</td>
<td>

Information technical name



</td>
</tr>
<tr>
<td>



</td>
<td>

NAME



</td>
<td>

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

