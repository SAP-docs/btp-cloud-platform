<!-- loioc9b48a1983ab4c8db00bd3bd8f63632c -->

# Getting Numbers from an Interval

The `CL_NUMBERRANGE_RUNTIME` class provides methods for getting numbers from an interval at runtime.



<a name="loioc9b48a1983ab4c8db00bd3bd8f63632c__section_byp_xhf_gjb"/>

## Checking Numbers for External Intervals

Use the `NUMBER_CHECK` method to check whether a number is within an external interval.

<a name="loioc9b48a1983ab4c8db00bd3bd8f63632c__table_r2b_p3f_gjb"/>Import Parameters


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

NR\_RANGE\_NR



</td>
<td valign="top">

 



</td>
<td valign="top">

Interval number



</td>
</tr>
<tr>
<td valign="top">

NUMBER



</td>
<td valign="top">

 



</td>
<td valign="top">

Number to be checked



</td>
</tr>
<tr>
<td valign="top">

NUMERIC\_CHECK



</td>
<td valign="top">

 



</td>
<td valign="top">

Numeric check \(for numeric intervals only\)



</td>
</tr>
<tr>
<td valign="top">

OBJECT



</td>
<td valign="top">

 



</td>
<td valign="top">

Number range object



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
<tr>
<td valign="top">

TOYEAR



</td>
<td valign="top">

 



</td>
<td valign="top">

To fiscal year



</td>
</tr>
<tr>
<td valign="top">

NUMBER\_ALPHA



</td>
<td valign="top">

 



</td>
<td valign="top">

Obsolete. Please use parameter NUMBER



</td>
</tr>
<tr>
<td valign="top">

LENGTH\_CHECK



</td>
<td valign="top">

 



</td>
<td valign="top">

Check of number length



</td>
</tr>
</table>

<a name="loioc9b48a1983ab4c8db00bd3bd8f63632c__table_pbb_x3f_gjb"/>Export Parameter


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

RETURNCODE



</td>
<td valign="top">

 



</td>
<td valign="top">

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

IGNORE\_BUFFER



</td>
<td valign="top">

 



</td>
<td valign="top">

Ignore Buffer



</td>
</tr>
<tr>
<td valign="top">

NR\_RANGE\_NR



</td>
<td valign="top">

 



</td>
<td valign="top">

Interval Number



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

QUANTITY



</td>
<td valign="top">

 



</td>
<td valign="top">

Number of Numbers in Buffer



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
<tr>
<td valign="top">

TOYEAR



</td>
<td valign="top">

 



</td>
<td valign="top">

To Fiscal Year



</td>
</tr>
</table>

<a name="loioc9b48a1983ab4c8db00bd3bd8f63632c__table_d11_ljf_gjb"/>External Parameters


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

NUMBER



</td>
<td valign="top">

 



</td>
<td valign="top">

Returned number



</td>
</tr>
<tr>
<td valign="top">

RETURNCODE



</td>
<td valign="top">

 



</td>
<td valign="top">

Return code



</td>
</tr>
<tr>
<td valign="top">

RETURNED\_QUANTITY



</td>
<td valign="top">

 



</td>
<td valign="top">

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

