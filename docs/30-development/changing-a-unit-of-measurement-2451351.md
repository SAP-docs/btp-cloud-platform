<!-- loio24513517eb7d44fd8363f81a6d2c9068 -->

# Changing a Unit of Measurement

Use method `UPDATE` to change a unit of measurement.

> ### Caution:  
> Changing the initial set of configurations has implications. Before proceeding with any change, familiarize yourself with the warnings in [Units of Measurement](units-of-measurement-8961c2c.md).



<a name="loio24513517eb7d44fd8363f81a6d2c9068__section_ykb_qxy_qlb"/>

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

UNIT

</td>
<td valign="top">

 

</td>
<td valign="top">

Internal unit of measurement

</td>
</tr>
<tr>
<td valign="top">

UNIT\_UPD\_TS

</td>
<td valign="top">

 

</td>
<td valign="top">

Structure for updating a unit of measurement

> ### Caution:  
> Be aware that all the fields belonging to the structure will be updated.



</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

COMMERCIAL

</td>
<td valign="top">

Commercial/external measurement unit format

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

TECHNICAL

</td>
<td valign="top">

Technical measurement unit format

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

DEC\_ROUND

</td>
<td valign="top">

Number of decimal places to which this measurement unit should be rounded for conversion

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

NUMERATOR

</td>
<td valign="top">

Numerator for conversion to SI unit

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

DENOMINATOR

</td>
<td valign="top">

Denominator for conversion into SI unit

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

EXPONENT

</td>
<td valign="top">

Base ten exponent for conversion to SI unit

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

CONSTANT

</td>
<td valign="top">

Additive constant for conversion to SI unit

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

DEC\_DISP

</td>
<td valign="top">

Number of decimal places with which this measurement unit is displayed

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

ISOCODE

</td>
<td valign="top">

ISO code for measurement units. An ISO code can be assigned to several internal measurement units of a dimension.

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

PRIMARY

</td>
<td valign="top">

Unit of measure flagged as a primary unit for an ISO code

`Space`: Not primary

`‘X’`: Set as primary

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

TEXT

</td>
<td valign="top">

Description of a unit of measurement

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

LONG\_TEXT

</td>
<td valign="top">

Long description of a unit of measurement

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

ISCOMMERCIAL

</td>
<td valign="top">

Flag for commercial measurement units

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

ISVALUEBASE

</td>
<td valign="top">

Value-based commitment indicator

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

ISGRPBYFAM

</td>
<td valign="top">

Measurement units grouped by family

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

TEMPERATURE

</td>
<td valign="top">

Temperature value

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

TEMPERATUREUNIT

</td>
<td valign="top">

Temperature unit

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

PRESSURE

</td>
<td valign="top">

Pressure value

</td>
</tr>
<tr>
<td valign="top">

 

</td>
<td valign="top">

PRESSUREUNIT

</td>
<td valign="top">

Pressure unit

</td>
</tr>
</table>



<a name="loio24513517eb7d44fd8363f81a6d2c9068__section_fkc_ddv_plb"/>

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
> CLASS zcl_uom_unit_update_test DEFINITION 
>   PUBLIC 
>   FINAL 
>   CREATE PUBLIC. 
>  
>   PUBLIC SECTION. 
>     INTERFACES if_oo_adt_classrun. 
>   PROTECTED SECTION. 
>   PRIVATE SECTION. 
> ENDCLASS. 
>  
> CLASS zcl_uom_unit_update_test IMPLEMENTATION. 
>   METHOD if_oo_adt_classrun~main. 
>     DATA(lo_uom) = cl_uom_maintenance=>get_instance( ).
> 
> TRY.
> lo_uom->read( EXPORTING  unit       = 'ZYX'
>               IMPORTING unit_st = DATA(ls_unit) ).
> 
> DATA(ls_upd_unit) = VALUE cl_uom_maintenance=>ty_uom_upd_ts(
>                     BASE CORRESPONDING #( ls_unit )
>                                          commercial   = 'ZYA'
>                                          technical    = 'ZYA'
>                                          denominator  = '1'
>                                          numerator    = '1'
>                                          dec_disp     = '5'
>                                          long_text    = 'Updates Unit'
>                                          text         = 'Upd Unit' ).
> 
> lo_uom->update( EXPORTING unit        = 'ZYX'
>                           unit_upd_ts = ls_upd_unit
>                 IMPORTING error 	 = DATA(lv_error) ).    
> 
>       CATCH cx_uom_error INTO DATA(lo_error).
>         out->write( |Exception raised| ).
>         out->write( lo_error->get_text( ) ).
>     ENDTRY.
>     IF lv_error = abap_true.
>       out->write( |Error occurred while updating the data in the database| ).
>     ENDIF.
>   ENDMETHOD. 
> ENDCLASS.
> 
> ```

