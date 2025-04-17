<!-- loio74d5b1a9ec654bf59871631eba0491d6 -->

# Scoping Space and Page Templates

The scoping of space and page templates refers to the process of defining the visibility or accessibility of these objects.

Space and page templates are not visible in the [Manage Launchpad Spaces](https://help.sap.com/docs/btp/user-interface-configurations/manage-launchpad-spaces?version=Cloud) and [Manage Launchpad Pages](https://help.sap.com/docs/btp/user-interface-configurations/manage-launchpad-pages?version=Cloud) apps in the development system by default. Meaning, they cannot be assigned or used within a business role. The space and page templates need to be scoped.

To use the space and page templates in the development system you must implement your own scoping using the scoping API \(Application Programming Interface\) `DL APS BC SCOPE CHANGE API`. It's recommended to use a console application to set the space and page template in scope.

> ### Note:  
> Please be aware that the API in the following example is not available for SAP trial accounts.

> ### Sample Code:  
> ```
> 
>     CONSTANTS obj_name_page  TYPE c LENGTH 40 VALUE 'PAGE_NAME' ##NO_TEXT.
>     CONSTANTS obj_name_space TYPE c LENGTH 40 VALUE 'SPACE_NAME' ##NO_TEXT.
> 
>     DATA(lo_scope_api) = cl_aps_bc_scope_change_api=>create_instance( ).
> 
>     lo_scope_api->scope(
>       EXPORTING it_object_scope  = VALUE #(
>           pgmid       = if_aps_bc_scope_change_api=>gc_tadir_pgmid-R3TR
>           scope_state = if_aps_bc_scope_change_api=>gc_scope_state-ON
>           ( object = if_aps_bc_scope_change_api=>gc_tadir_object-UIST obj_name = obj_name_space )
>           ( object = if_aps_bc_scope_change_api=>gc_tadir_object-UIPG obj_name = obj_name_page ) )
>                 iv_simulate      = abap_false
>                 iv_force         = abap_false
>       IMPORTING et_object_result = DATA(lt_results)
>                 et_message       = DATA(lt_messages) ).
> 
>     LOOP AT lt_results INTO DATA(ls_result).
>        ...
>     ENDLOOP.
> 
> ```

In non-development systems, space and page templates are scoped automatically during import into the system.

**Related Information**  


[Scoping Framework](https://help.sap.com/docs/btp/sap-business-technology-platform/scoping-framework?version=Cloud)

