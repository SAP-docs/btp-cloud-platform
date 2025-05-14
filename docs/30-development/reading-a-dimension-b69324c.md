<!-- loiob69324cf22bf44e6ae4439b1d25476ae -->

# Reading a Dimension

Use method `READ` to read a dimension.



<a name="loiob69324cf22bf44e6ae4439b1d25476ae__section_u5d_g4v_plb"/>

## Import Parameters

****


<table>
<tr>
<th valign="top">

Parameter Name

</th>
<th valign="top">

Value Help

</th>
</tr>
<tr>
<td valign="top">

DIMID

</td>
<td valign="top">

Dimension key

</td>
</tr>
<tr>
<td valign="top">

LANGUAGE

</td>
<td valign="top">

Language key \(optional\)

> ### Note:  
> If no language key is provided, the default logon language is used.



</td>
</tr>
</table>



<a name="loiob69324cf22bf44e6ae4439b1d25476ae__section_hyl_cdv_plb"/>

## Export Parameters

****


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

DIM\_ST

</td>
<td valign="top">

 

</td>
<td valign="top">

Structure for reading a dimension

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

DIMID

</td>
<td valign="top">

Dimension key

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

TXDIM

</td>
<td valign="top">

Description of the dimension key

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

SI\_UNIT

</td>
<td valign="top">

Base unit of a dimension

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

SI\_TXT

</td>
<td valign="top">

Description of the base unit

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

LENGTH

</td>
<td valign="top">

Length exponent of the dimension

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

MASS

</td>
<td valign="top">

Mass exponent of the dimension

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

TIME

</td>
<td valign="top">

Time exponent of the dimension

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

CURRENT

</td>
<td valign="top">

Electric current exponent of the dimension

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

TEMPERATURE

</td>
<td valign="top">

Temperature exponent of the dimension

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

MOLE\_QTY

</td>
<td valign="top">

Mole quantity exponent of the dimension

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

LUMINOSITY

</td>
<td valign="top">

Light exponent of the dimension

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

HASUNITSWITHTEMPERATURESPEC

</td>
<td valign="top">

Indicates whether the dimension has units with a temperature specification

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

HASUNITSWITHPRESSURESPEC

</td>
<td valign="top">

Indicates whether the dimension has units with a pressure specification

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

LANGUAGE

</td>
<td valign="top">

Language key

</td>
</tr>
</table>

> ### Note:  
> Class exception `CX_UOM_ERROR` is raised if no dimension is found.

> ### Sample Code:  
> ```abap
> 
> CLASS zcl_uom_dimension_read_test DEFINITION 
>   PUBLIC 
>   FINAL 
>   CREATE PUBLIC . 
>  
>   PUBLIC SECTION. 
>     INTERFACES if_oo_adt_classrun. 
>   PROTECTED SECTION. 
>   PRIVATE SECTION. 
> ENDCLASS. 
>  
> CLASS zcl_uom_dimension_read_test IMPLEMENTATION. 
>  
>   METHOD if_oo_adt_classrun~main. 
>  
>     DATA(lo_dim) = cl_uom_dim_maintenance=>get_instance( ).
>  
>     TRY. 
>         lo_dim->read( EXPORTING  dimid  = 'AAAADL'
>                                  language = 'E'   
>                       IMPORTING  dim_st = DATA(ls_dim) ). 
>       CATCH cx_uom_error. 
>     ENDTRY. 
>  
>     out->write( ls_dim-DIMID ). 
>     out->write( ls_dim-txdim ). 
>  
>   ENDMETHOD. 
>  
> ENDCLASS.
> ```

