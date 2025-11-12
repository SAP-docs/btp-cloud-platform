<!-- loio545ebc6586d746c89c69508a18180810 -->

# Resetting Content to Standard Units of Measurement

You can reset content to standard units of measurement either with or without a transport request.



## Reset Without Transport Request

Use method `RESET_TO_STD_ LOCALLY` to reset the units, dimensions, and ISO codes to the standard units of measurement delivered by SAP. The changes are saved locally.

> ### Note:  
> Class exception `CX_UOM_ERROR` is raised if the reset fails.

> ### Caution:  
> Make sure you read and understand the risks and warnings described in [Retrieving and Resetting Standard Units of Measurement](retrieving-and-resetting-standard-units-of-measurement-5225632.md).

> ### Sample Code:  
> ```abap
> CLASS zcl_reset_to_std_locally DEFINITION
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
> CLASS zcl_reset_to_std_locally IMPLEMENTATION.
>   METHOD if_oo_adt_classrun~main.
>     DATA(lo_uom_reset_tool) = cl_uom_content_handler=>get_instance( ).
>         TRY.
>            lo_uom_reset_tool->reset_to_std_locally( ).
> 
>       CATCH cx_uom_error INTO DATA(error).
>         out->write( error->get_text( ) ).
>         out->write( |Error occurred while resetting to standard content| ).
>     ENDTRY.
>  
>   ENDMETHOD.
> ENDCLASS.
> 
> ```



## Reset Using a Transport Request

Use method `RESET_TO_STD_USING_TRANSPORT` to reset units, dimensions, and ISO codes to the standard units of measurement delivered by SAP. The changes are transported.

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

`IV_TRANSPORT` 

</td>
<td valign="top">

Transport Request

</td>
</tr>
</table>

> ### Note:  
> Class exception `CX_UOM_ERROR` is raised if the reset fails.

> ### Caution:  
> All changes and standard units, dimensions, and ISO codes will be included in the customizing transport. Make sure you read and understand the risks and warnings described in [Retrieving and Resetting Standard Units of Measurement](retrieving-and-resetting-standard-units-of-measurement-5225632.md).

> ### Sample Code:  
> ```abap
> CLASS zcl_reset_to_std_transport DEFINITION
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
> CLASS zcl_reset_to_std_transport IMPLEMENTATION.
>   METHOD if_oo_adt_classrun~main.
>     DATA(lo_uom_reset_tool) = cl_uom_content_handler=>get_instance( ).
>         TRY.
>            lo_uom_reset_tool->reset_to_std_using_transport( iv_transport =  'transport_request' ).
> 
>       CATCH cx_uom_error INTO DATA(error).
>         out->write( error->get_text( ) ).
>         out->write( |Error occurred while resetting to standard content| ).
>     ENDTRY.
> 
>   ENDMETHOD.
> ENDCLASS.
> 
> ```

