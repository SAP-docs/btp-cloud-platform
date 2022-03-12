<!-- loiob69324cf22bf44e6ae4439b1d25476ae -->

# Reading a Dimension

Use method `READ` to read a dimension.



<a name="loiob69324cf22bf44e6ae4439b1d25476ae__section_u5d_g4v_plb"/>

## Import Parameters

<a name="loiob69324cf22bf44e6ae4439b1d25476ae__table_y4d_h4v_plb"/>


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
</table>



<a name="loiob69324cf22bf44e6ae4439b1d25476ae__section_hyl_cdv_plb"/>

## Export Parameters

<a name="loiob69324cf22bf44e6ae4439b1d25476ae__table_gxj_fdv_plb"/>


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
</table>

> ### Note:  
> Class exception `CX_UOM_ERROR` is raised if no dimension is found.

> ### Sample Code:  
> ```abap
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
>     DATA: lo_dim TYPE REF TO cl_uom_dim_maintenance, 
>           ls_dim type cl_uom_dim_maintenance=>ty_dim_ts. 
>  
>     "Get instance 
>     cl_uom_dim_maintenance=>get_instance( 
>     RECEIVING 
>       ro_dimension = lo_dim ). 
>  
>     try. 
>         lo_dim->read( exporting  dimid  = 'AAAADL' 
>                      importing   dim_st = ls_dim 
>                            ). 
>       catch cx_uom_error. 
>     endtry. 
>  
>     out->write( ls_dim-DIMID ). 
>     out->write( ls_dim-txdim ). 
>  
>   ENDMETHOD. 
>  
> ENDCLASS.
> 
> ```

