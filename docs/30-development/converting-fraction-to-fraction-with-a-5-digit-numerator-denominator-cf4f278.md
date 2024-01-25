<!-- loiocf4f278f8ddc414989517cd125cd2de9 -->

# Converting Fraction to Fraction with a 5-Digit Numerator/Denominator

Use method `CONVERT_TO_FRACT5` to convert a fraction to a fraction with a maximum of 5-digit numerators/denominators.

If the numerator or denominator contain more than 5 digits, the result will be an approximation as close as possible.



<a name="loiocf4f278f8ddc414989517cd125cd2de9__section_csh_j3c_kzb"/>

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

NOMIN

</td>
<td valign="top">

Nominator input

</td>
</tr>
<tr>
<td valign="top">

DENOMIN

</td>
<td valign="top">

Denominator input

</td>
</tr>
</table>



<a name="loiocf4f278f8ddc414989517cd125cd2de9__section_xrb_k3c_kzb"/>

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

NOMOUT

</td>
<td valign="top">

Nominator output \(5-digit max.\)

</td>
</tr>
<tr>
<td valign="top">

DENOMOUT

</td>
<td valign="top">

Denominator output \(5-digit max.\)

</td>
</tr>
</table>



<a name="loiocf4f278f8ddc414989517cd125cd2de9__section_emp_ljc_kzb"/>

## Exceptions

****


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

CONVERSION\_OVERFLOW

</td>
<td valign="top">

Unit of measurement is not maintained.

</td>
</tr>
</table>

> ### Sample Code:  
> ```abap
> CLASS zcl_uom_convert_to_fract5 DEFINITION
>   PUBLIC
>   FINAL
>   CREATE PUBLIC.
>   PUBLIC SECTION.
>     INTERFACES if_oo_adt_classrun.
>   PROTECTED SECTION.
>   PRIVATE SECTION.
> ENDCLASS.
>  
> 
>  
> CLASS zcl_convert_to_fract5 IMPLEMENTATION.
>   METHOD if_oo_adt_classrun~main.
>     DATA: lv_nomin   TYPE f VALUE 999998,
>           lv_denomin TYPE f VALUE 999999.
>           
>     DATA(lo_unit) = cl_uom_conversion=>create( ).
>     TRY.
>         lo_unit->convert_to_fract5(
>           EXPORTING
>             nomin    = lv_nomin
>             denomin  = lv_denomin
>           IMPORTING
>             nomout   = DATA(lv_nomout)
>             denomout = DATA(lv_denomout) ).
>         
>       CATCH cx_uom_error INTO DATA(lo_error).
>         out->write( |Exception raised| ).
>         out->write( lo_error->get_text( ) ).
>     ENDTRY.
>     out->write( lv_nomout ).
>     out->write( lv_denomout ).
>   ENDMETHOD.
> ENDCLASS.
> 
> ```

