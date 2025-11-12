<!-- loioe423991759ea4bb9b4a8e275447fb874 -->

# Currency Code Conversion

Learn how to use the methods `CURRENCY_CODE_EXT_TO_INT` and `CURRENCY_CODE_INT_TO_EXT` to convert SAP currency codes.



## CURRENCY\_CODE\_EXT\_TO\_INT

Use method `CURRENCY_CODE_EXT_TO_INT` to convert an external currency into an SAP currency.



### Import Parameters

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

`ISO_CODE` 

</td>
<td valign="top">

ISO currency code

</td>
</tr>
</table>



### Export Parameters

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

`SAP_CODE` 

</td>
<td valign="top">

SAP currency code

</td>
</tr>
<tr>
<td valign="top">

`IS_UNIQUE` 

</td>
<td valign="top">

`ABAP_FALSE` if an ISO code is assigned to any SAP codes

</td>
</tr>
</table>

> ### Note:  
> Class exception `CX_CONVERSION_EXT_INT` is raised to check the integrity of the data import parameters.

> ### Sample Code:  
> ```abap
> CLASS zcl_conversion_ext_int_test DEFINITION
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
> 
> CLASS zcl_conversion_ext_int_test IMPLEMENTATION.
> 
>   METHOD if_oo_adt_classrun~main.
> 
>     TRY.
>         DATA(lo_conv) = cl_conversion_ext_int=>get_instance( ).
>       CATCH cx_conversion_ext_int.
>     ENDTRY.
> 
>     "Conversion of currency codes ISO to SAP
>     TRY.
>         lo_conv->currency_code_ext_to_int(
>           EXPORTING
>             iso_code = 'USD'
>           IMPORTING
>             sap_code = DATA(lv_sap_code)
>             is_unique = DATA(lv_unique)
>         ).
>         out->write( |Result: { lv_sap_code } is unique { lv_unique }| ).
>       CATCH cx_conversion_ext_int INTO DATA(lo_error).
>         out->write( lo_error->get_text( ) ).
>     ENDTRY.
> 
>   ENDMETHOD.
> ENDCLASS.
> 
> ```



## CURRENCY\_CODE\_INT\_TO\_EXT

Use method `CURRENCY_CODE_INT_TO_EXT` to convert an SAP currency into an external currency.



### Import Parameters

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

`SAP_CODE` 

</td>
<td valign="top">

SAP currency code

</td>
</tr>
</table>



### Export Parameters

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

`ISO_CODE` 

</td>
<td valign="top">

ISO currency code

</td>
</tr>
<tr>
<td valign="top">

`IS_UNIQUE` 

</td>
<td valign="top">

`ABAP_FALSE` if an ISO code is assigned to any SAP codes

</td>
</tr>
</table>

> ### Note:  
> Class exception `CX_CONVERSION_EXT_INT` is raised to check the integrity of the data import parameters.

> ### Sample Code:  
> ```abap
> CLASS zcl_conversion_ext_int_test DEFINITION
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
> CLASS zcl_conversion_ext_int_test IMPLEMENTATION.
> 
>   METHOD if_oo_adt_classrun~main.
> 
>     TRY.
>         DATA(lo_conv) = cl_conversion_ext_int=>get_instance( ).
>       CATCH cx_conversion_ext_int.
>     ENDTRY.
> 
>     "Conversion of currency codes SAP to ISO
>     TRY.
>         lo_conv->currency_code_int_to_ext(
>           EXPORTING
>             sap_code = 'USD'
>           IMPORTING
>             iso_code = DATA(lv_iso_code)
>         ).
>         out->write( |Result: { lv_iso_code }| ).
>       CATCH cx_conversion_ext_int INTO DATA(lo_error).
>         out->write( lo_error->get_text( ) ).
>     ENDTRY.
> 
>   ENDMETHOD.
> ENDCLASS.
> 
> 
> ```

