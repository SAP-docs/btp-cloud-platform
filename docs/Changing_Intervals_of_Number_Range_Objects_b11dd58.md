<!-- loiob11dd584e5a046a4b69d3792497efabb -->

# Changing Intervals of Number Range Objects

Use the `UPDATE` method to change number range intervals.

Import and export parameters are the same as in the `CREATE` method.

> ### Sample Code:  
> ```
> 
> …
>     lv_object = 'Z_TEST_03'.
> *   intervals
>     ls_interval-nrrangenr  = '01'.
>     ls_interval-fromnumber = '00000002'.
>     ls_interval-tonumber   = '19999998'.
>     ls_interval-procind    = 'U'.
>     APPEND ls_interval TO lt_interval.
>     ls_interval-nrrangenr  = '02'.
>     ls_interval-fromnumber = '20000002'.
>     ls_interval-tonumber   = '29999997'.
>     APPEND ls_interval TO lt_interval.
> …
>  CALL METHOD cl_numberrange_intervals=>update
>       EXPORTING
>         interval  = lt_interval
>         object    = lv_object
>         subobject = ' '
>       IMPORTING
>         error     = DATA(lv_error)
>         error_inf = DATA(ls_error)
>         error_iv  = DATA(lt_error_iv)
>         warning   = DATA(lv_warning)
> …
> 
> ```

