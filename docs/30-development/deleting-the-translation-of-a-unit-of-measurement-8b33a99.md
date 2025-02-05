<!-- loio8b33a99ea83448ea9f3c345068ebc15e -->

# Deleting the Translation of a Unit of Measurement

Use method `DELETE_TRANSLATION` to delete translation of a unit of measurement for a particular language.

> ### Caution:  
> Changing the initial set of configurations has implications. Before proceeding with any change, familiarize yourself with the warnings in [Units of Measurement](units-of-measurement-8961c2c.md).



<a name="loio8b33a99ea83448ea9f3c345068ebc15e__section_fcn_rsq_fdc"/>

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

UNIT\_INT

</td>
<td valign="top">

Internal unit of measurement

</td>
</tr>
</table>



<a name="loio8b33a99ea83448ea9f3c345068ebc15e__section_rsh_rsq_fdc"/>

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
> CLASS zcl_uom_delete_transl_test DEFINITION
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
> CLASS zcl_uom_delete_transl_test IMPLEMENTATION.
> 
>   METHOD if_oo_adt_classrun~main.
> 
>       DATA(lo_uom) = cl_uom_maintenance=>get_instance( ).
> 
>       TRY.
>           lo_uom->delete_translation( EXPORTING language   = 'F'
>                                                 unit_int   = 'ZYX'
>                                       IMPORTING error = DATA(lv_error) ).
>           CATCH cx_uom_error INTO DATA(lo_error).
>              out->write( | Exception raised | ).
>              out->write( lo_error->get_text( ) ).
>        ENDTRY.
>        IF lv_error = abap_true.
>           out->write( |Error occurred while saving the data in the database| ).
>        ENDIF.
>   ENDMETHOD.
> ENDCLASS.
> 
> ```

