<!-- loio051e4983667a4b519aad8c853db0266b -->

# Deleting the Translation of a Dimension

Use method `DELETE_TRANSLATION` to delete translation of a dimension for a particular language.

> ### Caution:  
> Changing the initial set of configurations has implications. Before proceeding with any change, familiarize yourself with the warnings in [Units of Measurement](units-of-measurement-8961c2c.md).



<a name="loio051e4983667a4b519aad8c853db0266b__section_tnc_phq_fdc"/>

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

LANGUAGE



</td>
<td valign="top">

Language key

</td>
</tr>
<tr>
<td valign="top">

DIMID

</td>
<td valign="top">

Dimension key

</td>
</tr>
</table>



<a name="loio051e4983667a4b519aad8c853db0266b__section_ihl_phq_fdc"/>

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

ERROR

</td>
<td valign="top">

`Space`: No error

`‘X’`: Save error

</td>
</tr>
</table>

> ### Note:  
> Class exception `CX_UOM_ERROR` is raised to check the integrity of the data import parameters.

> ### Sample Code:  
> ```abap
> 
> CLASS zcl_dim_delete_transl_test DEFINITION
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
> CLASS zcl_dim_maintain_transl_test IMPLEMENTATION.
> 
>   METHOD if_oo_adt_classrun~main.
> 
>      DATA(lo_dim) = cl_uom_dim_maintenance=>get_instance( ).
> TRY.
>         lo_dim->delete_translation( EXPORTING dimid    = 'ZNEWDI'
>                                               language = 'F'
>                                        IMPORTING
>                                              error = DATA(lv_error) ).
>      CATCH cx_uom_error INTO DATA(lo_error).
>         out->write( |Exception raised| ).
>         out->write( lo_error->get_text( ) ).
>      ENDTRY.
>      IF lv_error = abap_true.
>         out->write( |Error occurred while updating the data in the database| ).
>      ENDIF.
> 
>   ENDMETHOD.
> ENDCLASS.
> 
> ```

