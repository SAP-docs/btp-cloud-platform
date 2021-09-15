<!-- loiob4f5ab1001f847c8a129d717ef5e9356 -->

# Determining the Conversion Factors

Use method `UNIT_PARAMETERS_GET` to determine the data conversion factors of a unit.



<a name="loiob4f5ab1001f847c8a129d717ef5e9356__section_nnt_k4m_rlb"/>

## Import Parameters

<a name="loiob4f5ab1001f847c8a129d717ef5e9356__table_utf_j4m_rlb"/>


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

Unit of measurement



</td>
</tr>
</table>



<a name="loiob4f5ab1001f847c8a129d717ef5e9356__section_bjl_fpm_rlb"/>

## Export Parameters

<a name="loiob4f5ab1001f847c8a129d717ef5e9356__table_nbs_gpm_rlb"/>


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

DECIMALS 



</td>
<td>

Number of decimal places for rounding



</td>
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

NUMERATOR



</td>
<td>

Numerator for conversion to SI unit



</td>
</tr>
<tr>
<td>

DENOMINATOR



</td>
<td>

Denominator for conversion to SI unit



</td>
</tr>
<tr>
<td>

EXPONENT



</td>
<td>

Base ten exponent for conversion to SI unit



</td>
</tr>
<tr>
<td>

ADD\_CONST



</td>
<td>

Additive constant for conversion to SI unit



</td>
</tr>
<tr>
<td>

DECAN



</td>
<td>

Number of decimal places for number display



</td>
</tr>
<tr>
<td>

FAMUNIT



</td>
<td>

Unit of measurement family



</td>
</tr>
</table>



<a name="loiob4f5ab1001f847c8a129d717ef5e9356__section_zvl_cqm_rlb"/>

## Exceptions

<a name="loiob4f5ab1001f847c8a129d717ef5e9356__table_jwv_dqm_rlb"/>


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

UNIT\_NOT\_FOUND



</td>
<td>

Unit of measurement is not maintained



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
>     data: lo_unit     type ref to cl_uom_conversion,
>           decimal     type cl_uom_conversion=>ty_andec,
>           dimension   type cl_uom_conversion=>ty_dimid,
>           numerator   type cl_uom_conversion=>ty_dzaehl,
>           denominator type cl_uom_conversion=>ty_nennr.
> 
> 
>    lo_unit = cl_uom_conversion=>create( ).
> 
>    lo_unit->unit_parameters_get(
>      EXPORTING
>        unit           = 'G'
>      IMPORTING
>        decimals       = decimal
>        dimension      = dimension
>        numerator      = numerator
>        denominator    = denominator
> 
>      EXCEPTIONS
>        unit_not_found = 1
>        others         = 2
>     ).
>     IF SY-SUBRC = 0.
>       out->write( dimension ).
>       out->write( decimal ).
>       out->write( numerator ).
>       out->write( denominator ).
>    ENDIF.
> 
>   ENDMETHOD.
> 
>  ENDCLASS.
> 
> ```

