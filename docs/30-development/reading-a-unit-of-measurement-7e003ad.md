<!-- loio7e003ad72c6e494cbc9a9aa2b1db4950 -->

# Reading a Unit of Measurement

Use method `READ` to read a unit of measurement.



<a name="loio7e003ad72c6e494cbc9a9aa2b1db4950__section_cdm_ccl_rlb"/>

## Import Parameters

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

UNIT



</td>
<td valign="top">

Internal unit of measurement



</td>
</tr>
</table>



<a name="loio7e003ad72c6e494cbc9a9aa2b1db4950__section_ykb_qxy_qlb"/>

## Export Parameters

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

UNIT\_ST



</td>
<td valign="top">

 



</td>
<td valign="top">

Structure for reading a unit of measurement



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

UNIT



</td>
<td valign="top">

Internal unit of measurement



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

***Space***: Not primary

***‘X’***: Set as primary



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

> ### Note:  
> Class exception `CX_UOM_ERROR` is raised if no unit is found.

> ### Sample Code:  
> ```abap
> CLASS zcl_uom_unit_read_test DEFINITION 
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
>  
>  
> CLASS zcl_uom_unit_read_test IMPLEMENTATION. 
>   METHOD if_oo_adt_classrun~main. 
>  
>     DATA: lo_uom  TYPE REF TO cl_uom_maintenance, 
>           ls_unit TYPE cl_uom_maintenance=>ty_uom_ts. 
>  
>     cl_uom_maintenance=>get_instance( 
>      RECEIVING 
>        ro_uom = lo_uom ). 
>  
>     TRY. 
>         "Unit found 
>         lo_uom->read( EXPORTING unit = 'ST' 
>                       IMPORTING unit_st = ls_unit 
>                            ). 
>       CATCH cx_uom_error. 
>     ENDTRY. 
>     out->write( ls_unit-unit ). 
>     out->write( ls_unit-commercial ). 
>     out->write( ls_unit-technical ). 
>     out->write( ls_unit-dimid ). 
>  
>   ENDMETHOD. 
> ENDCLASS.
> 
> ```

