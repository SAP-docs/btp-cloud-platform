<!-- loio24513517eb7d44fd8363f81a6d2c9068 -->

# Changing a Unit of Measurement

Use method `UPDATE` to change a unit of measurement. For customer units, the name of the internal unit must start with a ‘Z’ for any changes.



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
>   CREATE PUBLIC . 
>  
>   PUBLIC SECTION. 
>     INTERFACES if_oo_adt_classrun. 
>   PROTECTED SECTION. 
>   PRIVATE SECTION. 
> ENDCLASS. 
>  
> CLASS zcl_uom_unit_update_test IMPLEMENTATION. 
>   METHOD if_oo_adt_classrun~main. 
>  
>     DATA: lo_uom  TYPE REF TO cl_uom_maintenance, 
>           ls_unit TYPE cl_uom_maintenance=>ty_uom_upd_ts. 
>  
>     cl_uom_maintenance=>get_instance( 
>   RECEIVING 
>     ro_uom = lo_uom ). 
>  
>     ls_unit-commercial = 'ZYA'. 
>     ls_unit-technical  = 'ZYA'. 
>     ls_unit-denominator = '1'. 
>     ls_unit-numerator = '1'. 
>     ls_unit-dec_disp = '5'. 
>     ls_unit-long_text = 'Update Unit'. 
>     ls_unit-text = 'Upd Unit'. 
>  
>     TRY. 
>         lo_uom->update( EXPORTING unit = 'ZYX' 
>                                   unit_upd_ts = ls_unit 
>                         IMPORTING 
>                              error       = DATA(error) 
>                          ). 
>       CATCH cx_uom_error INTO DATA(lo_error). 
>         out->write( |Exception raised| ). 
>         out->write( lo_error->get_text( ) ). 
>     ENDTRY. 
>  
>   ENDMETHOD. 
> ENDCLASS.
> 
> ```

