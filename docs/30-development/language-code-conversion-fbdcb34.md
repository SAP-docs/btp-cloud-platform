<!-- loiofbdcb348e43d46f0bbc4aa11af281f81 -->

# Language Code Conversion

Learn how to use the methods `LANGUAGE_CODE_EXT_TO_INT` and `LANGUAGE_CODE_INT_TO_EXT` to convert SAP language codes.



## LANGUAGE\_CODE\_EXT\_TO\_INT

Use method `LANGUAGE_CODE_EXT_TO_INT` to convert an external language into an SAP language.



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

ISO language code

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

SAP language code

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
> CLASS zcl_conversion_ext_int_test IMPLEMENTATION.
> 
>   METHOD if_oo_adt_classrun~main.
> 
>     TRY.
>         DATA(lo_conv) = cl_conversion_ext_int=>get_instance( ).
>       CATCH cx_conversion_ext_int.
>     ENDTRY.
> 
>     "Conversion of languages codes ISO to SAP
>     TRY.
>         lo_conv->language_code_ext_to_int(
>           EXPORTING
>             iso_code = 'EN'
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



## LANGUAGE\_CODE\_INT\_TO\_EXT

Use method `LANGUAGE_CODE_INT_TO_EXT` to convert an SAP language into an external language.



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

SAP language code

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

ISO language code

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
>     "Conversion of languages codes SAP to ISO
>     TRY.
>         lo_conv->language_code_int_to_ext(
>           EXPORTING
>             sap_code = 'E'
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
> 
> ```

