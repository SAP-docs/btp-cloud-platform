<!-- loiob69324cf22bf44e6ae4439b1d25476ae -->

# Reading a Dimension

Use method `READ` to read a dimension.



<a name="loiob69324cf22bf44e6ae4439b1d25476ae__section_u5d_g4v_plb"/>

## Import Parameters

<a name="loiob69324cf22bf44e6ae4439b1d25476ae__table_y4d_h4v_plb"/>


<table>
<tr>
<th>

Parameter Name



</th>
<th>

Value Help



</th>
</tr>
<tr>
<td>

DIMID



</td>
<td>

Dimension key



</td>
</tr>
</table>



<a name="loiob69324cf22bf44e6ae4439b1d25476ae__section_hyl_cdv_plb"/>

## Export Parameters

<a name="loiob69324cf22bf44e6ae4439b1d25476ae__table_gxj_fdv_plb"/>


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

DIM\_ST



</td>
<td>

 



</td>
<td>

Structure for reading a dimension



</td>
</tr>
<tr>
<td>

 



</td>
<td>

DIMID



</td>
<td>

Dimension key



</td>
</tr>
<tr>
<td>

 



</td>
<td>

TXDIM



</td>
<td>

Description of the dimension key



</td>
</tr>
<tr>
<td>

 



</td>
<td>

SI\_UNIT



</td>
<td>

Base unit of a dimension



</td>
</tr>
<tr>
<td>

 



</td>
<td>

SI\_TXT



</td>
<td>

Description of the base unit



</td>
</tr>
<tr>
<td>

 



</td>
<td>

LENGTH



</td>
<td>

Length exponent of the dimension



</td>
</tr>
<tr>
<td>

 



</td>
<td>

MASS



</td>
<td>

Mass exponent of the dimension



</td>
</tr>
<tr>
<td>

 



</td>
<td>

TIME



</td>
<td>

Time exponent of the dimension



</td>
</tr>
<tr>
<td>

 



</td>
<td>

CURRENT



</td>
<td>

Electric current exponent of the dimension



</td>
</tr>
<tr>
<td>

 



</td>
<td>

TEMPERATURE



</td>
<td>

Temperature exponent of the dimension



</td>
</tr>
<tr>
<td>

 



</td>
<td>

MOLE\_QTY



</td>
<td>

Mole quantity exponent of the dimension



</td>
</tr>
<tr>
<td>

 



</td>
<td>

LUMINOSITY



</td>
<td>

Light exponent of the dimension



</td>
</tr>
</table>

> ### Note:  
> Class exception `CX_UOM_ERROR` is raised if no dimension is found.

> ### Sample Code:  
> ```lang-abap
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

