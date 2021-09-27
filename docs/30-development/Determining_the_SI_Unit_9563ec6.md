<!-- loio9563ec60a6804dc68410a861dc605927 -->

# Determining the SI Unit

Use method `SI_UNIT_GET` to determine the SI unit.



<a name="loio9563ec60a6804dc68410a861dc605927__section_mmp_djm_rlb"/>

## Import Parameters

<a name="loio9563ec60a6804dc68410a861dc605927__table_fwm_jjm_rlb"/>


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

DIMENSION



</td>
<td>

Dimension key



</td>
</tr>
<tr>
<td>

UNIT



</td>
<td>

Unit of measurement



</td>
</tr>
</table>



<a name="loio9563ec60a6804dc68410a861dc605927__section_en3_njm_rlb"/>

## Export Parameters

<a name="loio9563ec60a6804dc68410a861dc605927__table_opj_4jm_rlb"/>


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

SI\_UNIT



</td>
<td>

Base unit/SI unit of a dimension



</td>
</tr>
</table>



<a name="loio9563ec60a6804dc68410a861dc605927__section_enf_sjm_rlb"/>

## Exceptions

<a name="loio9563ec60a6804dc68410a861dc605927__table_rnv_sjm_rlb"/>


<table>
<tr>
<th>

Exception Name



</th>
<th>

Value Help



</th>
</tr>
<tr>
<td>

DIMENSION\_NOT\_FOUND



</td>
<td>

Dimension is not defined



</td>
</tr>
<tr>
<td>

UNIT\_NOT\_FOUND



</td>
<td>

Unit of measurement is not maintained



</td>
</tr>
<tr>
<td>

SI\_UNIT\_NOT\_FOUND



</td>
<td>

SI unit is not defined



</td>
</tr>
</table>

> ### Sample Code:  
> ```lang-abap
> CLASS zcl_uom_conversion DEFINITION
>   PUBLIC
>   FINAL
>   CREATE PUBLIC .
> 
>   PUBLIC SECTION.
>      INTERFACES if_oo_adt_classrun.
>   PROTECTED SECTION.
>   PRIVATE SECTION.
> ENDCLASS.
> 
> CLASS zcl_uom_conversion IMPLEMENTATION.
> 
>   METHOD if_oo_adt_classrun~main.
> 
>    data: lo_unit type ref to cl_uom_conversion,
>          si_unit type cl_uom_conversion=>ty_msehi.
> 
>    lo_unit = cl_uom_conversion=>create( ).
> 
>    lo_unit->si_unit_get(
>      EXPORTING
>        dimension           = 'MASS'
>        unit                = 'G'
>      IMPORTING
>        si_unit             = si_unit
>      EXCEPTIONS
>        dimension_not_found = 1
>        unit_not_found      = 2
>        si_unit_not_found   = 3
>        others              = 4
>    ).
>    IF SY-SUBRC = 0.
>       out->write( si_unit ).
>    ENDIF.
> 
>   ENDMETHOD.
> 
> ENDCLASS.
> ```

