<!-- loio061e055dd3b040e290cc0c70f84d5188 -->

# Maintaining the Translation of a Unit of Measurement

Use method `MAINTAIN_TRANSLATION` to maintain the translation of a unit of measurement for a particular language.

> ### Caution:  
> Changing the initial set of configurations has implications. Before proceeding with any change, familiarize yourself with the warnings in [Units of Measurement](units-of-measurement-8961c2c.md).



<a name="loio061e055dd3b040e290cc0c70f84d5188__section_zyl_brq_fdc"/>

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
<tr>
<td valign="top">

COMMERCIAL

</td>
<td valign="top">

Commercial/external measurement unit format

</td>
</tr>
<tr>
<td valign="top">

TECHNICAL

</td>
<td valign="top">

Technical measurement unit format

</td>
</tr>
<tr>
<td valign="top">

TEXT

</td>
<td valign="top">

Description of a unit of measurement \(optional\)

</td>
</tr>
<tr>
<td valign="top">

LONG\_TEXT

</td>
<td valign="top">

Long description of a unit of measurement \(optional\)

</td>
</tr>
</table>



<a name="loio061e055dd3b040e290cc0c70f84d5188__section_tst_brq_fdc"/>

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
> CLASS zcl_uom_maintain_transl_test DEFINITION
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
> CLASS zcl_uom_maintain_transl_test IMPLEMENTATION.
> 
>   METHOD if_oo_adt_classrun~main.
> 
>       DATA(lo_uom) = cl_uom_maintenance=>get_instance( ).
> 
>       TRY.
>           lo_uom->maintain_translation( EXPORTING language   = 'F'
>                                                   unit_int   = 'ZYX'
>                                                   commercial = 'zyx'
>                                                   technical  = 'zyx'
>                                                   text       = 'FR transl'
>                                                   long_text  = 'FR transl'
>                                         IMPORTING error = DATA(lv_error) ).
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

