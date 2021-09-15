<!-- loio4083add554614debb3766af36604cc80 -->

# Simple Conversion Between Two Units

Use method `UNIT_CONVERSION_SIMPLE` to convert values from one measurement unit to another and round the result to the number of decimal places maintained in the measurement unit table `T006`, if necessary. Depending on the parameter `ROUND_SIGN`, the rounding is up \(***'+'***\), down \(***'-'***\), commercial \(***'X'***'\), or no rounding \(SPACE\).

> ### Note:  
> Make sure that both units are maintained in the measurement unit table and have the same dimension.



<a name="loio4083add554614debb3766af36604cc80__section_qjw_n2m_rlb"/>

## Import Parameters

<a name="loio4083add554614debb3766af36604cc80__table_xvd_p2m_rlb"/>


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

INPUT



</td>
<td>

Input value



</td>
</tr>
<tr>
<td>

NO\_TYPE\_CHECK



</td>
<td>

Conversion factor type check

***'X'***: No check

***Space***: Type check



</td>
</tr>
<tr>
<td>

ROUND\_SIGN



</td>
<td>

Rounding flag

***'+'***: Up

***'-'***: Down

***'X'***: Commercial



</td>
</tr>
<tr>
<td>

UNIT\_IN



</td>
<td>

Unit of input value



</td>
</tr>
</table>



<a name="loio4083add554614debb3766af36604cc80__section_am5_vfm_rlb"/>

## Export Parameters

<a name="loio4083add554614debb3766af36604cc80__table_tvy_wfm_rlb"/>


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

ADD\_CONST



</td>
<td>

Additive constant for conversion



</td>
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

DENOMINATOR



</td>
<td>

Denominator for conversion



</td>
</tr>
<tr>
<td>

NUMERATOR



</td>
<td>

Numerator for conversion



</td>
</tr>
<tr>
<td>

OUTPUT



</td>
<td>

Output value



</td>
</tr>
</table>



<a name="loio4083add554614debb3766af36604cc80__section_fkh_ggm_rlb"/>

## Exceptions

<a name="loio4083add554614debb3766af36604cc80__table_fcj_hgm_rlb"/>


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

CONVERSION\_NOT\_FOUND



</td>
<td>

Conversion factor could not be determined



</td>
</tr>
<tr>
<td>

DIVISION\_BY\_ZERO



</td>
<td>

Division by zero caught



</td>
</tr>
<tr>
<td>

INPUT\_INVALID



</td>
<td>

Input value is not a number



</td>
</tr>
<tr>
<td>

OUTPUT\_INVALID



</td>
<td>

Output parameter is not a number



</td>
</tr>
<tr>
<td>

OVERFLOW



</td>
<td>

Field overflow



</td>
</tr>
<tr>
<td>

TYPE\_INVALID



</td>
<td>

Output parameter is not a number



</td>
</tr>
<tr>
<td>

UNITS\_MISSING



</td>
<td>

No units specified



</td>
</tr>
<tr>
<td>

UNIT\_IN\_NOT\_FOUND



</td>
<td>

UNIT\_IN is not maintained



</td>
</tr>
<tr>
<td>

UNIT\_OUT\_NOT\_FOUND



</td>
<td>

UNIT\_OUT is not maintained



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
>          input  type p decimals 8,
>          result type p decimals 8.
> 
>     input = '1.98678923'.
>     lo_unit = cl_uom_conversion=>create( ).
> 
>     lo_unit->unit_conversion_simple( exporting input      = input
>                                                round_sign = 'X'
>                                                unit_in    = 'KG'
>                                                unit_out   = 'G'
>                                      importing
>                                                output = result
>                                        exceptions
>                                          conversion_not_found = 01
>                                          division_by_zero     = 02
>                                          input_invalid        = 03
>                                          output_invalid       = 04
>                                          overflow             = 05
>                                          units_missing        = 06
>                                          unit_in_not_found    = 07
>                                          unit_out_not_found   = 08 ).
>     IF SY-SUBRC = 0.
>        out->write( result ).
>     ENDIF.
> 
>   ENDMETHOD.
> ```

