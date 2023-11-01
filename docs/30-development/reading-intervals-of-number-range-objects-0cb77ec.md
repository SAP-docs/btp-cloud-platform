<!-- loio0cb77ec7fba84084a416688de830dd71 -->

# Reading Intervals of Number Range Objects

Use the `READ` method to get the properties of number range intervals.

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

NR\_RANGE\_NR1

</td>
<td valign="top">

 

</td>
<td valign="top">

Interval Number \(internal interval\)

</td>
</tr>
<tr>
<td valign="top">

NR\_RANGE\_NR2

</td>
<td valign="top">

 

</td>
<td valign="top">

Interval Number \(external interval\)

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

