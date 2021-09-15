<!-- loio832caf00f5914c1a9bf8b0575c2904f3 -->

# Deleting Intervals of Number Range Objects

Use the `DELETE` method to delete number range intervals.

Import and export parameters are the same as in the `CREATE` method.

> ### Sample Code:  
> ```
> 
> …
>     lv_object = 'Z_TEST_03'
> *   intervals
>     ls_interval-nrrangenr  = '01'.
>     ls_interval-fromnumber = '00000001'.
>     ls_interval-tonumber   = '19999999'.
>     ls_interval-procind    = 'D'.
>     APPEND ls_interval TO lt_interval.
>     ls_interval-nrrangenr  = '02'.
>     ls_interval-fromnumber = '20000000'.
>     ls_interval-tonumber   = '29999999'.
>     APPEND ls_interval TO lt_interval.
>  …
>   CALL METHOD cl_numberrange_intervals=>delete
>        EXPORTING
>          interval  = lt_interval
>          object    = lv_object
>          subobject = ' '
>        IMPORTING
>          error     = DATA(lv_error)
>          error_inf = DATA(ls_error)
>          error_iv  = DATA(lt_error_iv)
>          warning   = DATA(lv_warning).
> …
> 
> ```

