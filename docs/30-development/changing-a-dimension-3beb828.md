<!-- loio3beb828bea9d451e90ced55e03b2727f -->

# Changing a Dimension

Use method `UPDATE` to change an existing dimension.

> ### Caution:  
> Changing the initial set of configurations has implications. Before proceeding with any change, familiarize yourself with the warnings in [Units of Measurement](units-of-measurement-8961c2c.md).



<a name="loio3beb828bea9d451e90ced55e03b2727f__section_hyl_cdv_plb"/>

## Import Parameters

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

DIMID

</td>
<td valign="top">

 

</td>
<td valign="top">

Dimension key

</td>
</tr>
<tr>
<td valign="top">

DIM\_UPD\_TS

</td>
<td valign="top">

 

</td>
<td valign="top">

Structure for updating a dimension

> ### Caution:  
> Be aware that all the fields belonging to the structure will be updated.



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
</table>



<a name="loio3beb828bea9d451e90ced55e03b2727f__section_fkc_ddv_plb"/>

## Export Parameters

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

ERROR

</td>
<td valign="top">

`Space`: No error

`‘X’`: Save error

</td>
</tr>
</table>

> ### Note:  
> Class exception `CX_UOM_ERROR` is raised to check the integrity of the data import parameters.

> ### Sample Code:  
> ```abap
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
>    DATA(lo_dim) = cl_uom_dim_maintenance=>get_instance( ).
> 
> 
>    TRY.
>         lo_dim->read( EXPORTING dimid    = 'ZNEWDI'
>               IMPORTING dim_st = DATA(ls_dim) ).
> 
>    DATA(ls_upd_dim) = VALUE cl_uom_dim_maintenance=>ty_dim_upd_ts(
>                       BASE CORRESPONDING #( ls_dim )
>                                             txdim = 'Update Dimension'
>                                             mass  = 88
>                                             length = 89 ).
> 
>     lo_dim->update( EXPORTING dimid      = 'ZNEWDI'
>                               dim_upd_ts = ls_upd_dim
>                     IMPORTING error      = DATA(lv_error) ).
> 
> 
>    CATCH cx_uom_error INTO DATA(lo_error).
>       out->write( |Exception raised| ).
>       out->write( lo_error->get_text( ) ).
>    ENDTRY.
>    IF lv_error = abap_true.
>      out->write( |Error occurred while updating the data in the database| ).
>    ENDIF.
>   ENDMETHOD. 
> ENDCLASS.
> 
> ```

