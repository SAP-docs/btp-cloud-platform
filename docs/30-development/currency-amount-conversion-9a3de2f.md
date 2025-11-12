<!-- loio9a3de2fc04d5407a90d8a7e5d2037871 -->

# Currency Amount Conversion

Learn how to use the methods `CURRENCY_AMOUNT_EXT_TO_INT` and `CURRENCY_AMOUNT_INT_TO_EXT` to convert SAP currency amounts.



## Context

In an SAP system, a currency amount field only makes sense in connection with a currency because this is the only way to correctly set the decimal point in the amounts. Therefore, each currency amount field must be assigned to a currency field. For example, two Yen are stored as 0.02 in the database in a field of data type `CURR`.

All SAP currency data types have two decimal places, despite some currencies having three decimal places.



## CURRENCY\_AMOUNT\_EXT\_TO\_INT

Use method `CURRENCY_AMOUNT_EXT_TO_INT` to convert an external currency amount into an SAP currency amount.



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

`CURRENCY` 

</td>
<td valign="top">

ISO currency code

</td>
</tr>
<tr>
<td valign="top">

`BAPI_AMOUNT` 

</td>
<td valign="top">

External currency amount

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

`SAP_AMOUNT` 

</td>
<td valign="top">

SAP currency amount

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
>     "Conversion of currency amounts ISO to SAP
>     DATA lv_amount TYPE bapicurr_d.
>     lv_amount = CONV #( '20' ).
>     TRY.
>         lo_conv->currency_amount_ext_to_int(
>           EXPORTING
>             currency = 'JPY'
>             bapi_amount = lv_amount
>           IMPORTING
>             sap_amount = DATA(lv_sap_amount)
>         ).
>         out->write( |Result: { lv_sap_amount } | ).
>       CATCH cx_conversion_ext_int INTO DATA(lo_error).
>         out->write( lo_error->get_text( ) ).
>     ENDTRY.
> 
>   ENDMETHOD.
> ENDCLASS.
> 
> 
> ```



## CURRENCY\_AMOUNT\_INT\_TO\_EXT

Use method `CURRENCY_AMOUNT_INT_TO_EXT` to convert an SAP currency amount into an external currency amount.



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

`CURRENCY` 

</td>
<td valign="top">

ISO currency code

</td>
</tr>
<tr>
<td valign="top">

`SAP_AMOUNT` 

</td>
<td valign="top">

SAP currency amount

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

`BAPI_AMOUNT` 

</td>
<td valign="top">

External currency amount

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
>     "Conversion of currency amounts SAP to ISO
>     DATA lv_amount TYPE bapicurr_d.
>     lv_amount = CONV #( '0.2000' ).
>     TRY.
>         lo_conv->currency_amount_int_to_ext(
>           EXPORTING
>             currency = 'JPY'
>             sap_amount = lv_amount
>           IMPORTING
>             bapi_amount = DATA(lv_iso_amount)
>         ).
>         out->write( |Result: { lv_iso_amount } | ).
>       CATCH cx_conversion_ext_int INTO DATA(lo_error).
>         out->write( lo_error->get_text( ) ).
>     ENDTRY.
> 
>   ENDMETHOD.
> ENDCLASS.
> 
> 
> ```

