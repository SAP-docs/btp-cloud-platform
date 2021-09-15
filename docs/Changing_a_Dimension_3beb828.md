<!-- loio3beb828bea9d451e90ced55e03b2727f -->

# Changing a Dimension

Use method `UPDATE` to change an existing dimension. For customer dimensions, the name of the dimension ID must start with a ‘Z’ for any changes.



<a name="loio3beb828bea9d451e90ced55e03b2727f__section_hyl_cdv_plb"/>

## Import Parameters

<a name="loio3beb828bea9d451e90ced55e03b2727f__table_gxj_fdv_plb"/>


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

DIMID



</td>
<td>

 



</td>
<td>

Dimension key



</td>
</tr>
<tr>
<td>

DIM\_UPD\_TS



</td>
<td>

 



</td>
<td>

Structure for updating a dimension



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



<a name="loio3beb828bea9d451e90ced55e03b2727f__section_fkc_ddv_plb"/>

## Export Parameters

<a name="loio3beb828bea9d451e90ced55e03b2727f__table_ztj_m2v_plb"/>


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

ERROR



</td>
<td>

***Space***: No error

***‘X’***: Save error



</td>
</tr>
</table>

> ### Note:  
> Class exception `CX_UOM_ERROR` is raised to check the integrity of the data import parameters.

> ### Sample Code:  
> ```lang-abap
> CLASS zcl_uom_dimension_update_test DEFINITION 
>   PUBLIC 
>   FINAL 
>   CREATE PUBLIC . 
> 
>   PUBLIC SECTION. 
>     INTERFACES if_oo_adt_classrun. 
> 
>   PROTECTED SECTION. 
>   PRIVATE SECTION. 
> ENDCLASS. 
> 
> CLASS zcl_uom_dimension_update_test IMPLEMENTATION. 
>   METHOD if_oo_adt_classrun~main. 
> 
>     DATA: lo_dim TYPE REF TO cl_uom_dim_maintenance, 
>           ls_dim TYPE cl_uom_dim_maintenance=>ty_dim_upd_ts. 
> 
>     "Get instance 
>     cl_uom_dim_maintenance=>get_instance( 
>     RECEIVING 
>       ro_dimension = lo_dim ). 
> 
>     ls_dim-txdim = 'Update Dimension'. 
>     ls_dim-mass  = 88. 
>     ls_dim-length = 88. 
> 
>     TRY. 
>         lo_dim->update( EXPORTING dimid = 'ZNEWDI' 
>                                   dim_upd_ts = ls_dim 
>                     IMPORTING 
>                          error = DATA(error) 
>                    ). 
>       CATCH cx_uom_error INTO DATA(lo_error). 
>         out->write( |Exception raised| ). 
>         out->write( lo_error->get_text( ) ). 
>     ENDTRY. 
> 
>   ENDMETHOD. 
> 
> ENDCLASS.
> ```

