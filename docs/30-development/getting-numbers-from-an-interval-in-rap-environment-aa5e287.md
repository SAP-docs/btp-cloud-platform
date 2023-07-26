<!-- loioaa5e287bc8214c079922680f6688a55c -->

# Getting Numbers from an Interval in RAP environment

The CL\_NUMBERRANGE\_BUFFER class provides methods for getting numbers from an interval at runtime. Each method is called based on the buffer type setting of the object. In case the method caller calls a method, which doesn’t coincide with the buffer type of the object, an exception CX\_NUMBER\_RANGES will be raised.



<a name="loioaa5e287bc8214c079922680f6688a55c__section_nkk_sj1_wxb"/>

## Getting Numbers for Internal Intervals

Based on the buffering settings of the object, you can call a specific API method.



### Getting Numbers for the Object with main Memory Buffering

Use the NUMBER\_GET\_MAIN\_MEMORY method to determine the next number of a number range interval.

**Import Parameters**


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

IV\_OBJECT



</td>
<td valign="top">

Number Range Object



</td>
</tr>
<tr>
<td valign="top">

IV\_SUBOBJECT



</td>
<td valign="top">

Sub-object



</td>
</tr>
<tr>
<td valign="top">

IV\_INTERVAL



</td>
<td valign="top">

Interval Number



</td>
</tr>
<tr>
<td valign="top">

IV\_QUANTITY



</td>
<td valign="top">

Number of Numbers in Buffer



</td>
</tr>
<tr>
<td valign="top">

IV\_TOYEAR



</td>
<td valign="top">

To Fiscal Year



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

Value Help



</th>
</tr>
<tr>
<td valign="top">

EV\_NUMBER



</td>
<td valign="top">

Returned Number



</td>
</tr>
<tr>
<td valign="top">

EV\_RETURNCODE



</td>
<td valign="top">

Return Code



</td>
</tr>
<tr>
<td valign="top">

EV\_RETURNED\_QUANTITY



</td>
<td valign="top">

Number of Returned Numbers



</td>
</tr>
</table>

> ### Sample Code:  
> ```
> lv_object = 'ZIG_NR5'.
> lv_interval = '01'.
> lv_quantity = 10.
> TRY.
> DATA(lo_get_number) = cl_numberrange_buffer=>get_instance( ).
> lo_get_number->if_numberrange_buffer~number_get_main_memory( EXPORTING 
> iv_object    = lv_object                                                                  iv_subobject = lv_subobject
>                                                iv_interval  = lv_interval
>                                                      iv_quantity  = lv_quantity
>                                              iv_toyear    = lv_year
>                                                   IMPORTING 
> ev_number    = lv_number
>                                              ev_returned_quantity = lv_returned_qunatity).
> CATCH cx_number_ranges INTO DATA(lr_error).
> ENDTRY.
> 
> ```



### Getting Numbers for the object with parallel buffering

Use NUMBER\_GET\_PARALLEL method to determine the next number of a number range interval.

**Import Parameters**


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

IV\_OBJECT



</td>
<td valign="top">

Number Range Object



</td>
</tr>
<tr>
<td valign="top">

IV\_SUBOBJECT



</td>
<td valign="top">

Sub-object



</td>
</tr>
<tr>
<td valign="top">

IV\_INTERVAL



</td>
<td valign="top">

Interval Number



</td>
</tr>
<tr>
<td valign="top">

IV\_QUANTITY



</td>
<td valign="top">

Number of Numbers in Buffer



</td>
</tr>
<tr>
<td valign="top">

IV\_TOYEAR



</td>
<td valign="top">

To Fiscal Year



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

Value Help



</th>
</tr>
<tr>
<td valign="top">

EV\_NUMBER



</td>
<td valign="top">

Returned Number



</td>
</tr>
<tr>
<td valign="top">

EV\_RETURNCODE



</td>
<td valign="top">

Return Code



</td>
</tr>
</table>

> ### Sample Code:  
> ```
> lv_object = 'ZIG_NR2'.
> lv_interval = '01'.
> TRY.
> DATA(lo_get_number) = cl_numberrange_buffer=>get_instance( ).
> lo_get_number->if_numberrange_buffer~number_get_parallel( EXPORTING 
> iv_object    = lv_object
>                                                            iv_interval  = lv_interval
>                                                            iv_subobject = lv_subobject
>                                                            iv_toyear    = lv_year
>                                                            IMPORTING 
> ev_number    = iv_number ).
>   CATCH cx_number_ranges INTO DATA(lr_error).
> ENDTRY.
>  
> 
> ```



### Getting Numbers for the Object without Buffering

Use the NUMBER\_GET\_NO\_BUFFER method to determine the next number of a number range interval.

**Export Parameters**


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

EV\_NUMBER



</td>
<td valign="top">

Returned Number



</td>
</tr>
<tr>
<td valign="top">

EV\_RETURNCODE



</td>
<td valign="top">

Return Code



</td>
</tr>
<tr>
<td valign="top">

EV\_RETURNED\_QUANTITY



</td>
<td valign="top">

Number of Returned Numbers



</td>
</tr>
</table>

> ### Sample Code:  
> ```
> lv_object = 'ZIG_NR9'.
> lv_interval = '01'.
> lv_quantity = 10.
> TRY.
>   DATA(lo_get_number) = cl_numberrange_buffer=>get_instance( ).
> lo_get_number->if_numberrange_buffer~number_get_no_buffer( EXPORTING 
> iv_object            = lv_object
>                                                      iv_subobject         = lv_subobject
>                                                      iv_interval          = lv_interval
>                                                      iv_toyear            = lv_year
>                                                      iv_quantity          = lv_quantity
>                                                      iv_ignore_buffer     = abap_true
>               IMPORTING 
>  ev_number            = lv_number
>          ev_returned_quantity = lv_returned_qunatity). 
> CATCH cx_number_ranges INTO DATA(lr_error).
> ENDTRY.
> 
> ```

