<!-- loiob4f5ab1001f847c8a129d717ef5e9356 -->

# Determining the Conversion Factors

Use method `UNIT_PARAMETERS_GET` to determine the data conversion factors of a unit.



<a name="loiob4f5ab1001f847c8a129d717ef5e9356__section_nnt_k4m_rlb"/>

## Import Parameters

<a name="loiob4f5ab1001f847c8a129d717ef5e9356__table_utf_j4m_rlb"/>


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

Unit of measurement



</td>
</tr>
</table>



<a name="loiob4f5ab1001f847c8a129d717ef5e9356__section_bjl_fpm_rlb"/>

## Export Parameters

<a name="loiob4f5ab1001f847c8a129d717ef5e9356__table_nbs_gpm_rlb"/>


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

DECIMALS 



</td>
<td valign="top">

Number of decimal places for rounding



</td>
</tr>
<tr>
<td valign="top">

DIMENSION



</td>
<td valign="top">

Dimension key



</td>
</tr>
<tr>
<td valign="top">

NUMERATOR



</td>
<td valign="top">

Numerator for conversion to SI unit



</td>
</tr>
<tr>
<td valign="top">

DENOMINATOR



</td>
<td valign="top">

Denominator for conversion to SI unit



</td>
</tr>
<tr>
<td valign="top">

EXPONENT



</td>
<td valign="top">

Base ten exponent for conversion to SI unit



</td>
</tr>
<tr>
<td valign="top">

ADD\_CONST



</td>
<td valign="top">

Additive constant for conversion to SI unit



</td>
</tr>
<tr>
<td valign="top">

DECAN



</td>
<td valign="top">

Number of decimal places for number display



</td>
</tr>
<tr>
<td valign="top">

FAMUNIT



</td>
<td valign="top">

Unit of measurement family



</td>
</tr>
</table>



<a name="loiob4f5ab1001f847c8a129d717ef5e9356__section_zvl_cqm_rlb"/>

## Exceptions

<a name="loiob4f5ab1001f847c8a129d717ef5e9356__table_jwv_dqm_rlb"/>


<table>
<tr>
<th valign="top">

Exception Name



</th>
<th valign="top">

Value Help



</th>
</tr>
<tr>
<td valign="top">

UNIT\_NOT\_FOUND



</td>
<td valign="top">

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

