<!-- loiob91768df40da4b4ab83fd12f8cdd013f -->

# Creating a Dimension

Use method `CREATE` to create a new dimension. For customer dimensions, the name of the dimension ID must start with a ‘Z’.



<a name="loiob91768df40da4b4ab83fd12f8cdd013f__section_hyl_cdv_plb"/>

## Import Parameters

<a name="loiob91768df40da4b4ab83fd12f8cdd013f__table_gxj_fdv_plb"/>


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

DIM\_CRE\_TS



</td>
<td valign="top">

 



</td>
<td valign="top">

Structure for creating a dimension



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



<a name="loiob91768df40da4b4ab83fd12f8cdd013f__section_fkc_ddv_plb"/>

## Export Parameters

<a name="loiob91768df40da4b4ab83fd12f8cdd013f__table_ztj_m2v_plb"/>


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

ERROR



</td>
<td valign="top">

***Space***: No error

***‘X’***: Save error



</td>
</tr>
</table>

> ### Note:  
> Class exception `CX_UOM_ERROR` is raised to check the integrity of the data import parameters.

> ### Sample Code:  
> ```abap
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

