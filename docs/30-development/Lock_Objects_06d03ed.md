<!-- loio06d03eda843643b7a64acfb67edf521b -->

# Lock Objects

When you activate a lock object in the ABAP Dictionary, the system automatically creates function modules for setting locks \(`ENQUEUE_<lock object name>`\) and releasing locks \(`DEQUEUE_<lock object name>`\).



<a name="loio06d03eda843643b7a64acfb67edf521b__section_fzv_5v1_zmb"/>

## Using Lock Objects

Since the direct usage of these function modules is not permitted, the function module calls are wrapped in a generic API to set and release locks.

-   Use class `CL_ABAP_LOCK_OBJECT_FACTORY` to do the following:
    -   Create a lock object instance using method `GET_INSTANCE`

    -   Release all locks of the current LUW using method `DEQUEUE_ALL`

-   Use the created lock object instance to do the following:

    -   Set a lock using method `ENQUEUE`

    -   Release a lock using method `DEQUEUE`


For more information, see the ABAP Doc comments of class `CL_ABAP_LOCK_OBJECT_FACTORY` and interface`IF_ABAP_LOCK_OBJECT`. The interface`IF_ABAP_LOCK_OBJECT` also contains constants to be used for parameterization of lock methods.

> ### Sample Code:  
> ```lang-abap
> data lv_value type <type of lock object parameter 1>.
> lv_value = <value for lock parameter 1>.
> data(lr_lock_object) =  cl_abap_lock_object_factory=>get_instance( 
>     exporting iv_name = <name of lock object> ).
> 
> try.
>     lr_lock_object->enqueue( 
>        it_parameter =  value #( ( name = <name of lock parameter 1> value =  ref #( lv_value ) ) )
>        it_table_mode = value #( ( table_name = <table name> mode = if_abap_lock_object=>cs_mode-<constant for lock mode>) ) ).
> 
>   catch cx_abap_lock_failure into data(lr_exc).
> 	<exception handling code>
> endtry.
> 
> <application code>
> 
> 
> try.
>     lr_lock_object->dequeue( ).
> 
>   catch cx_abap_lock_failure into lr_exc.
> 	<exception handling code>
> endtry.
> 
> ```

