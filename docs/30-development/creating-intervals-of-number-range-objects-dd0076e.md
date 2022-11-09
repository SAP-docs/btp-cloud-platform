<!-- loiodd0076e454e74034bd862d867e153bd5 -->

# Creating Intervals of Number Range Objects

Use the `CREATE` method to create number range intervals.

**Import Parameters**


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

INTERVAL



</td>
<td valign="top">

 



</td>
<td valign="top">

Interval Table



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

SUBOBJECT



</td>
<td valign="top">

Number Range Object Sub-object Value



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

NRRANGENR



</td>
<td valign="top">

Number Range Number



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

TOYEAR



</td>
<td valign="top">

To Fiscal Year



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

FROMNUMBER



</td>
<td valign="top">

From Number



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

TONUMBER



</td>
<td valign="top">

To Number



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

NRLEVEL



</td>
<td valign="top">

Number Range Level



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

EXTERNIND



</td>
<td valign="top">

Internal \(' '\) or external \('X'\) number range flag



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

PROCIND



</td>
<td valign="top">

Processing flag \(I=Insert, D=Delete, U=Update,' '=no changes\)



</td>
</tr>
<tr>
<td valign="top">

OBJECT



</td>
<td valign="top">

 



</td>
<td valign="top">

Number Range Object



</td>
</tr>
<tr>
<td valign="top">

SUBOBJECT



</td>
<td valign="top">

 



</td>
<td valign="top">

Sub-object



</td>
</tr>
</table>

**Export Parameters**


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

ERROR



</td>
<td valign="top">

 



</td>
<td valign="top">

Flag showing that an error occurred during testing



</td>
</tr>
<tr>
<td valign="top">

ERROR\_INF



</td>
<td valign="top">

 



</td>
<td valign="top">

Error Information



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

MSGNR



</td>
<td valign="top">

Message Number



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

TABLENAME



</td>
<td valign="top">

Parameter Name



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

FIELDNAME



</td>
<td valign="top">

Field Name



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

TABIX



</td>
<td valign="top">

Index of Row with Error



</td>
</tr>
<tr>
<td valign="top">

ERROR\_IV



</td>
<td valign="top">

 



</td>
<td valign="top">

Intervals with errors



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

SUBOBJECT



</td>
<td valign="top">

Number range object subobject value



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

NRRANGENR



</td>
<td valign="top">

Number range number



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

TOYEAR



</td>
<td valign="top">

To fiscal year



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

FROMNUMBER



</td>
<td valign="top">

From number



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

TONUMBER



</td>
<td valign="top">

To number



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

NRLEVEL



</td>
<td valign="top">

Number range level



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

EXTERNIND



</td>
<td valign="top">

Internal \(' '\) or external \('X'\) number range flag



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

PROCIND



</td>
<td valign="top">

Processing flag \(I=Insert, D=Delete, U=Update,' '=no changes\)



</td>
</tr>
<tr>
<td valign="top">

WARNING



</td>
<td valign="top">

 



</td>
<td valign="top">

Flag: Warning after check?



</td>
</tr>
</table>

> ### Sample Code:  
> ```
> 
> …
> CLASS zcl_nr_test_intervals_create DEFINITION
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
> CLASS zcl_nr_test_intervals_create IMPLEMENTATION.
> 
> METHOD if_oo_adt_classrun~main.
> DATA: lv_object   TYPE cl_numberrange_objects=>nr_attributes-object,
>       lt_interval TYPE cl_numberrange_intervals=>nr_interval,
>       ls_interval TYPE cl_numberrange_intervals=>nr_nriv_line.
> 
>     lv_object = 'Z_TEST_03'.
> 
> *   intervals
>     ls_interval-nrrangenr  = '01'.
>     ls_interval-fromnumber = '00000001'.
>     ls_interval-tonumber   = '19999999'.
>     ls_interval-procind    = 'I'.
>     APPEND ls_interval TO lt_interval.
> 
>     ls_interval-nrrangenr  = '02'.
>     ls_interval-fromnumber = '20000000'.
>     ls_interval-tonumber   = '29999999'.
>     APPEND ls_interval TO lt_interval.
> 
> *   create intervals
>     TRY.
> 
>         out->write( |Create Intervals for Object: { lv_object } | ).
> 
>         CALL METHOD cl_numberrange_intervals=>create
>           EXPORTING
>             interval  = lt_interval
>             object    = lv_object
>             subobject = ' '
>           IMPORTING
>             error     = DATA(lv_error)
>             error_inf = DATA(ls_error)
>             error_iv  = DATA(lt_error_iv)
>             warning   = DATA(lv_warning).
> 
>        ENDTRY.
> 
>   ENDMETHOD.
> ENDCLASS.    
> …
> 
> ```

