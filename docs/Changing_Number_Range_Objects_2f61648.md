<!-- loio2f6164804db943438222c579b898e67e -->

# Changing Number Range Objects

Use method `CHANGE` to update number range objects.

Import and export parameters are the same as in the `CREATE` method.

> ### Sample Code:  
> ```
> 
> …
>     lv_object   = 'Z_TEST_03'.
>     lv_devclass = 'Z_SNUM'.
>     lv_corrnr   = 'SIDK123456'.
> …
>   cl_numberrange_objects=>update(
>     EXPORTING
>       attributes = VALUE #( object     = lv_object
>                             domlen     = 'CHAR8'
>                             percentage = 9
>                             buffer     = 'S'
>                             noivbuffer = 12
>                             devclass   = lv_devclass
>                             corrnr     = lv_corrnr )
>       obj_text   = VALUE #( object     = lv_object
>                             langu      = 'E'
>                             txt        = 'Update object'
>                             txtshort   = 'Test update' )
>     IMPORTING
>       errors     = DATA(lt_errors)
>       returncode = DATA(lv_returncode)
>         ).   
>     …
> 
> ```

