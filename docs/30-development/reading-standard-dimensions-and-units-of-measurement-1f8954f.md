<!-- loio1f8954f82b654475bff37519964df00a -->

# Reading Standard Dimensions and Units of Measurement

Use the `GET_DIMENSIONS` method to read the standard dimensions for a unit of measurement, and the `GET_UNITS` method to read the standard units of measurement.

These methods perform the following actions based on the parameters listed below:

-   Language filter \(`IV_LANGUAGE`\):

    If the `IV_LANGUAGE` filter is set, the API retrieves all standard dimensions/all standard units of measurement based on the specified language.

-   Dimension filter \(`IV_DIM`\) and unit filter \(`IV_UNIT`\):

    If these filters are set, the API retrieves the standard dimensions or, respectively, standard units of measurement for the specified dimension/unit across all languages available in the standard units of measurement.

-   Both language and dimension or unit filters \(`IV_LANGUAGE` and `IV_DIM` or `IV_UNIT`\):

    If both these filters are set, the API retrieves the standard dimension/standard unit of measurement based on both the specified language **and** dimension or unit filters.

-   No parameters provided:

    If no parameters are set, the API retrieves all standard dimensions and units of measurement.




<a name="loio1f8954f82b654475bff37519964df00a__section_fh2_ckk_k2c"/>

## Import Parameters

****


<table>
<tr>
<th valign="top">

Parameters

</th>
<th valign="top">

Value Help

</th>
</tr>
<tr>
<td valign="top">

IV\_LANGUAGE



</td>
<td valign="top">

Specific language to filter

</td>
</tr>
<tr>
<td valign="top">

IV\_DIM

IV\_UNIT

</td>
<td valign="top">

Specific dimension or unit to filter

</td>
</tr>
</table>



<a name="loio1f8954f82b654475bff37519964df00a__section_l2v_ckk_k2c"/>

## Returning Parameters

****


<table>
<tr>
<th valign="top">

Parameter Name

</th>
<th valign="top">

Field Name

</th>
<th valign="top">

Value Help

</th>
</tr>
<tr>
<td valign="top">

RT\_DIMENSIONS

RT\_UNITS

</td>
<td valign="top">

IF\_UOM\_CONTENT\_HANDLER=\>TT\_DIM\_TS

IF\_UOM\_CONTENT\_HANDLER=\>tt\_uom\_content\_ts

</td>
<td valign="top">

Table type for the read dimension or units of measurement

See also the *Export Parameters* section in [Reading a Dimension](reading-a-dimension-b69324c.md) and [Reading a Unit of Measurement](reading-a-unit-of-measurement-7e003ad.md).

</td>
</tr>
</table>

> ### Note:  
> Class exception `CX_UOM_ERROR` is raised if no unit is found.

> ### Sample Code:  
> ```abap
> 
> CLASS zcl_read_std_uom DEFINITION
>   PUBLIC
>   FINAL
>   CREATE PUBLIC .
> 
>   PUBLIC SECTION.
> 
>     INTERFACES if_oo_adt_classrun .
>   PROTECTED SECTION.
>   PRIVATE SECTION.
> ENDCLASS.
> 
> CLASS zcl_read_std_uom IMPLEMENTATION.
> 
>   METHOD if_oo_adt_classrun~main.
>     CONSTANTS pieces TYPE msehi VALUE 'ST' ##NO_TEXT.
>     CONSTANTS dimensionless TYPE dimid VALUE 'AAAADL' ##NO_TEXT.
> 
>     DATA(lo_uom) = cl_uom_content_handler=>get_instance( ).
>     TRY.
> 
>         DATA(lt_standard_uom_content) = lo_uom->get_units(
>             iv_unit     = pieces
>             iv_language = sy-langu
>         ).
>         out->write( lt_standard_uom_content ).
> 
>         DATA(lt_standard_dim_content) = lo_uom->get_dimensions(
>             iv_dim      = dimensionless
>             iv_language = sy-langu
>         ).
>         out->write( lt_standard_dim_content ).
> 
>       CATCH cx_uom_error INTO DATA(error).
>         out->write( error->get_text( ) ).
>         out->write( |Error occurred while fetching standard content| ).
>     ENDTRY.
>   ENDMETHOD.
> ENDCLASS.
> 
> 
> ```

