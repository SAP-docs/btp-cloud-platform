<!-- loiodd0076e454e74034bd862d867e153bd5 -->

# Creating Intervals of Number Range Objects

Use the `CREATE` method to create number range intervals.

<a name="loiodd0076e454e74034bd862d867e153bd5__table_sgd_22f_gjb"/>Import Parameters


<table>
<tr>
<th>

Parameter Name



</th>
<th>

Field Name



</th>
<th>

Value Help



</th>
</tr>
<tr>
<td>

INTERVAL



</td>
<td>

 



</td>
<td>

Interval Table



</td>
</tr>
<tr>
<td>

 



</td>
<td>

SUBOBJECT



</td>
<td>

Number Range Object Sub-object Value



</td>
</tr>
<tr>
<td>

 



</td>
<td>

NRRANGENR



</td>
<td>

Number Range Number



</td>
</tr>
<tr>
<td>

 



</td>
<td>

TOYEAR



</td>
<td>

To Fiscal Year



</td>
</tr>
<tr>
<td>

 



</td>
<td>

FROMNUMBER



</td>
<td>

From Number



</td>
</tr>
<tr>
<td>

 



</td>
<td>

TONUMBER



</td>
<td>

To Number



</td>
</tr>
<tr>
<td>

 



</td>
<td>

NRLEVEL



</td>
<td>

Number Range Level



</td>
</tr>
<tr>
<td>

 



</td>
<td>

EXTERNIND



</td>
<td>

Internal \(' '\) or external \('X'\) number range flag



</td>
</tr>
<tr>
<td>

 



</td>
<td>

PROCIND



</td>
<td>

Processing flag \(I=Insert, D=Delete, U=Update,' '=no changes\)



</td>
</tr>
<tr>
<td>

OBJECT



</td>
<td>

 



</td>
<td>

Number Range Object



</td>
</tr>
<tr>
<td>

SUBOBJECT



</td>
<td>

 



</td>
<td>

Sub-object



</td>
</tr>
</table>

<a name="loiodd0076e454e74034bd862d867e153bd5__table_utn_x2f_gjb"/>Export Parameters


<table>
<tr>
<th>

Parameter Name



</th>
<th>

Field Name



</th>
<th>

Value Help



</th>
</tr>
<tr>
<td>

ERROR



</td>
<td>

 



</td>
<td>

Flag showing that an error occurred during testing



</td>
</tr>
<tr>
<td>

ERROR\_INF



</td>
<td>

 



</td>
<td>

Error Information



</td>
</tr>
<tr>
<td>

 



</td>
<td>

MSGNR



</td>
<td>

Message Number



</td>
</tr>
<tr>
<td>

 



</td>
<td>

TABLENAME



</td>
<td>

Parameter Name



</td>
</tr>
<tr>
<td>

 



</td>
<td>

FIELDNAME



</td>
<td>

Field Name



</td>
</tr>
<tr>
<td>

 



</td>
<td>

TABIX



</td>
<td>

Index of Row with Error



</td>
</tr>
<tr>
<td>

ERROR\_IV



</td>
<td>

 



</td>
<td>

Intervals with errors



</td>
</tr>
<tr>
<td>

 



</td>
<td>

SUBOBJECT



</td>
<td>

Number range object subobject value



</td>
</tr>
<tr>
<td>

 



</td>
<td>

NRRANGENR



</td>
<td>

Number range number



</td>
</tr>
<tr>
<td>

 



</td>
<td>

TOYEAR



</td>
<td>

To fiscal year



</td>
</tr>
<tr>
<td>

 



</td>
<td>

FROMNUMBER



</td>
<td>

From number



</td>
</tr>
<tr>
<td>

 



</td>
<td>

TONUMBER



</td>
<td>

To number



</td>
</tr>
<tr>
<td>

 



</td>
<td>

NRLEVEL



</td>
<td>

Number range level



</td>
</tr>
<tr>
<td>

 



</td>
<td>

EXTERNIND



</td>
<td>

Internal \(' '\) or external \('X'\) number range flag



</td>
</tr>
<tr>
<td>

 



</td>
<td>

PROCIND



</td>
<td>

Processing flag \(I=Insert, D=Delete, U=Update,' '=no changes\)



</td>
</tr>
<tr>
<td>

WARNING



</td>
<td>

 



</td>
<td>

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

