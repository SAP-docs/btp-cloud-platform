<!-- loiod626599e40814b29ad40b860f2d2e7be -->

# Conversion of Units of Measurement

Learn how to use the methods `UNIT_OF_MEASURE_EXT_TO_INT` and `UNIT_OF_MEASURE_INT_TO_EXT` to convert SAP units of measurement.



## UNIT\_OF\_MEASURE\_EXT\_TO\_INT

Use method `UNIT_OF_MEASURE_EXT_TO_INT` to convert an external unit of measurement into an SAP unit of measurement.



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

ISO code unit of measurement

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

SAP code unit of measurement

</td>
</tr>
<tr>
<td valign="top">

`UNIQUE` 

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
>     "Conversion of units of measurements ISO to SAP
>     TRY.
>         lo_conv->unit_of_measure_ext_to_int(
>           EXPORTING
>             iso_code = 'MTR'
>           IMPORTING
>             sap_code = DATA(lv_sap_code)
>         ).
>         out->write( |Result: { lv_sap_code } | ).
>       CATCH cx_conversion_ext_int INTO DATA(lo_error).
>         out->write( lo_error->get_text( ) ).
>     ENDTRY.
> 
>   ENDMETHOD.
> ENDCLASS.
> 
> ```



## UNIT\_OF\_MEASURE\_INT\_TO\_EXT

Use method `UNIT_OF_MEASURE_INT_TO_EXT` to convert an SAP unit of measurement into an external unit of measurement.



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

SAP code unit of measurement

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

ISO code unit of measurement

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
>     "Conversion of units of measurements SAP to ISO
>     TRY.
>         lo_conv->unit_of_measure_int_to_ext(
>           EXPORTING
>             sap_code = 'KM'
>           IMPORTING
>             iso_code = DATA(lv_iso_code)
>         ).
>         out->write( |Result: { lv_iso_code } | ).
>       CATCH cx_conversion_ext_int INTO DATA(lo_error).
>         out->write( lo_error->get_text( ) ).
>     ENDTRY.
> 
>   ENDMETHOD.
> ENDCLASS.
> 
> ```

