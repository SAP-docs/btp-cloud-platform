<!-- loioc9b48a1983ab4c8db00bd3bd8f63632c -->

# Getting Numbers from an Interval

The `CL_NUMBERRANGE_INTERVALS` class provides methods for getting numbers from an interval at runtime.



<a name="loioc9b48a1983ab4c8db00bd3bd8f63632c__section_byp_xhf_gjb"/>

## Checking Numbers for External Intervals

Use the `NUMBER_CHECK` method to check whether a number is within an external interval.

<a name="loioc9b48a1983ab4c8db00bd3bd8f63632c__table_r2b_p3f_gjb"/>Import Parameters


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

NR\_RANGE\_NR



</td>
<td>

 



</td>
<td>

Interval number



</td>
</tr>
<tr>
<td>

NUMBER



</td>
<td>

 



</td>
<td>

Number to be checked



</td>
</tr>
<tr>
<td>

NUMERIC\_CHECK



</td>
<td>

 



</td>
<td>

Numeric check \(for numeric intervals only\)



</td>
</tr>
<tr>
<td>

OBJECT



</td>
<td>

 



</td>
<td>

Number range object



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
<tr>
<td>

TOYEAR



</td>
<td>

 



</td>
<td>

To fiscal year



</td>
</tr>
</table>

<a name="loioc9b48a1983ab4c8db00bd3bd8f63632c__table_pbb_x3f_gjb"/>Export Parameter


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

RETURNCODE



</td>
<td>

 



</td>
<td>

Return code



</td>
</tr>
</table>



<a name="loioc9b48a1983ab4c8db00bd3bd8f63632c__section_ddq_z3f_gjb"/>

## Getting Numbers for Internal Intervals

Use the `NUMBER_GET` method to determine the next number of a number range interval.

<a name="loioc9b48a1983ab4c8db00bd3bd8f63632c__table_hns_fjf_gjb"/>Import Parameters


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

IGNORE\_BUFFER



</td>
<td>

 



</td>
<td>

Ignore Buffer



</td>
</tr>
<tr>
<td>

NR\_RANGE\_NR



</td>
<td>

 



</td>
<td>

Interval Number



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

QUANTITY



</td>
<td>

 



</td>
<td>

Number of Numbers in Buffer



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
<tr>
<td>

TOYEAR



</td>
<td>

 



</td>
<td>

To Fiscal Year



</td>
</tr>
</table>

<a name="loioc9b48a1983ab4c8db00bd3bd8f63632c__table_d11_ljf_gjb"/>External Parameters


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

NUMBER



</td>
<td>

 



</td>
<td>

Returned number



</td>
</tr>
<tr>
<td>

RETURNCODE



</td>
<td>

 



</td>
<td>

Return code



</td>
</tr>
<tr>
<td>

RETURNED\_QUANTITY



</td>
<td>

 



</td>
<td>

Number of returned numbers



</td>
</tr>
</table>

> ### Sample Code:  
> ```
> 
> …
>   lv_object = 'Z_TEST_03'.
> …
>   CALL METHOD cl_numberrange_runtime=>number_get
>        EXPORTING
>          nr_range_nr = '01'
>          object      = lv_object
>        IMPORTING
>          number      = DATA(lv_number)
>          returncode  = DATA(lv_rcode).
> …
> 
> ```

