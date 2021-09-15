<!-- loiob91768df40da4b4ab83fd12f8cdd013f -->

# Creating a Dimension

Use method `CREATE` to create a new dimension. For customer dimensions, the name of the dimension ID must start with a ‘Z’.



<a name="loiob91768df40da4b4ab83fd12f8cdd013f__section_hyl_cdv_plb"/>

## Import Parameters

<a name="loiob91768df40da4b4ab83fd12f8cdd013f__table_gxj_fdv_plb"/>


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

DIM\_CRE\_TS



</td>
<td>

 



</td>
<td>

Structure for creating a dimension



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



<a name="loiob91768df40da4b4ab83fd12f8cdd013f__section_fkc_ddv_plb"/>

## Export Parameters

<a name="loiob91768df40da4b4ab83fd12f8cdd013f__table_ztj_m2v_plb"/>


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
> CLASS zcl_uom_dimension_create_test DEFINITION 
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
> CLASS zcl_uom_dimension_create_test IMPLEMENTATION. 
> 
>   METHOD if_oo_adt_classrun~main. 
> 
>     DATA: lo_dim TYPE REF TO cl_uom_dim_maintenance, 
>           ls_dim TYPE cl_uom_dim_maintenance=>ty_dim_cre_ts. 
> 
>     "Get instance 
>     cl_uom_dim_maintenance=>get_instance( 
>     RECEIVING 
>       ro_dimension = lo_dim ). 
> 
>     ls_dim-dimid = 'ZNEWDI'. 
>     ls_dim-txdim = 'New Dimension'. 
>     ls_dim-mass  = 89. 
> 
>     TRY. 
>         lo_dim->create( EXPORTING dim_cre_ts = ls_dim 
>                     IMPORTING 
>                          error = DATA(error) 
>                    ). 
>       CATCH cx_uom_error INTO DATA(lo_error). 
>         out->write( |Exception raised| ). 
>         out->write( lo_error->get_text( ) ). 
> 
>     ENDTRY. 
>   ENDMETHOD. 
> 
> ENDCLASS.
> ```

