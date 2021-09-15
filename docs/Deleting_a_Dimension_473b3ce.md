<!-- loio473b3cef24484784bd9df78b31c64990 -->

# Deleting a Dimension

Use method `DELETE` to delete a dimension. For customer dimensions, the name of the dimension ID must start with a ‘Z’ to allow for deletion.



<a name="loio473b3cef24484784bd9df78b31c64990__section_u5d_g4v_plb"/>

## Import Parameters

<a name="loio473b3cef24484784bd9df78b31c64990__table_y4d_h4v_plb"/>


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



<a name="loio473b3cef24484784bd9df78b31c64990__section_fkc_ddv_plb"/>

## Export Parameters

<a name="loio473b3cef24484784bd9df78b31c64990__table_ztj_m2v_plb"/>


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
> CLASS zcl_uom_dimension_delete_test DEFINITION 
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
> CLASS zcl_uom_dimension_delete_test IMPLEMENTATION. 
>   METHOD if_oo_adt_classrun~main. 
>  
>     DATA: lo_dim TYPE REF TO cl_uom_dim_maintenance. 
>  
>     cl_uom_dim_maintenance=>get_instance( 
>     RECEIVING 
>       ro_dimension = lo_dim ). 
>  
>     TRY. 
>         lo_dim->delete( EXPORTING dimid =  'ZNEWDI' 
>                         IMPORTING error = DATA(error) 
>                        ). 
>       CATCH cx_uom_error INTO DATA(lo_error). 
>         out->write( |Exception raised| ). 
>         out->write( lo_error->get_text( ) ). 
>     ENDTRY. 
>   ENDMETHOD. 
> ENDCLASS.
> 
> ```

