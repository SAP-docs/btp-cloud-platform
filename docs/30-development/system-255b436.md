<!-- loio255b436361674688a304efda8ccffe4b -->

# System

With the XCO system module, you can easily request information about the current system.



<a name="loio255b436361674688a304efda8ccffe4b__section_gbk_dgg_4vb"/>

## Namespaces

You can get a handle for a given namespace via the API `XCO_CP_SYSTEM=>NAMESPACE`. Once obtained, you can use a namespace handle to find out whether the given namespace exists in the system and, if so, whether it's changeable:

> ### Sample Code:  
> ```abap
> " LO_NAMESPACE is a handle that can be used to request information
> " about namespace /ABC/.
> DATA(lo_namespace) = xco_cp_system=>namespace->for( '/ABC/' ).
>  
> " LV_NAMESPACE is an ABAP_BOOL value indicating whether the namespace
> " represented by LO_NAMESPACE exists or not.
> DATA(lv_namespace_exists) = lo_namespace->exists( ).
>  
> " LV_NAMESPACE_IS_CHANGEABLE is an ABAP_BOOL value indicating whether the
> " namespace represented by LO_NAMESPACE is changeable or not. Note that,
> " before invoking this method, it should be ensured that the namespace exists
> " as otherwise a runtime exception will be raised.
> DATA(lv_namespace_is_changeable) = lo_namespace->is_changeable( ).
> ```

