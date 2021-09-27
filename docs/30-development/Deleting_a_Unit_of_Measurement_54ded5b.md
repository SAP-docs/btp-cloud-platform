<!-- loio54ded5bdf2284bed955a19981f5b310f -->

# Deleting a Unit of Measurement

Use method `DELETE` to delete a unit of measurement. For customer units, the name of the internal unit must start with a ‘Z’ to allow for deletion.



<a name="loio54ded5bdf2284bed955a19981f5b310f__section_cdm_ccl_rlb"/>

## Import Parameters

<a name="loio54ded5bdf2284bed955a19981f5b310f__table_twy_xbl_rlb"/>


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

UNIT



</td>
<td>

Internal unit of measurement



</td>
</tr>
</table>



<a name="loio54ded5bdf2284bed955a19981f5b310f__section_fkc_ddv_plb"/>

## Export Parameters

<a name="loio54ded5bdf2284bed955a19981f5b310f__table_ztj_m2v_plb"/>


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
> CLASS zcl_uom_unit_delete_test DEFINITION 
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
> CLASS zcl_uom_unit_delete_test IMPLEMENTATION. 
>  
>   METHOD if_oo_adt_classrun~main. 
>  
>     DATA: lo_uom  TYPE REF TO cl_uom_maintenance. 
>  
>     cl_uom_maintenance=>get_instance( 
>     RECEIVING 
>       ro_uom = lo_uom ). 
>  
>     TRY. 
>         lo_uom->delete( EXPORTING unit = 'ZYX' 
>                         IMPORTING error = DATA(error) 
>                        ). 
>       CATCH cx_uom_error INTO DATA(lo_error). 
>         out->write( | Exception raised | ). 
>         out->write( lo_error->get_text( ) ). 
>     ENDTRY. 
>  
>   ENDMETHOD. 
>  
> ENDCLASS.
> 
> ```

