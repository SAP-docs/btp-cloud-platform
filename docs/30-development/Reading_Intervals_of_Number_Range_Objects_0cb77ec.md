<!-- loio0cb77ec7fba84084a416688de830dd71 -->

# Reading Intervals of Number Range Objects

Use the `READ` method to get the properties of number range intervals.

<a name="loio0cb77ec7fba84084a416688de830dd71__table_tgb_tgf_gjb"/>Import Parameters


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

NR\_RANGE\_NR1



</td>
<td>

 



</td>
<td>

Interval Number \(internal interval\)



</td>
</tr>
<tr>
<td>

NR\_RANGE\_NR2



</td>
<td>

 



</td>
<td>

Interval Number \(external interval\)



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

> ### Sample Code:  
> ```
> 
> …
>   lv_object = 'Z_TEST_03'.
> …
>   CALL METHOD cl_numberrange_intervals=>read
>        EXPORTING
>          object       = lv_object
>          nr_range_nr1 = ' '
>          nr_range_nr2 = ' '
>          subobject    = ' '
>        IMPORTING
>          interval     = lt_interval.
> …
> 
> ```

