<!-- loio088c6780c2b340ff81f1868cd640fb9a -->

# Reading Classes and Interfaces from a Remote Destination

Besides the default and local origin, the Read APIs for both classes and interfaces offer the option to read the content of classes and interfaces from remote systems. Currently, only reading from On-Premise systems is supported. Reading from SAP Public Cloud systems is not yet available. Remote systems are identified via an`IF_RFC_DEST` for which objects can be obtained via `CL_RFC_DESTINATION_PROVIDER`. Origins for classes and interfaces are obtained via `XCO_CP_ABAP_OBJECTS=>ORIGIN` which provides a common basis for both classes and interfaces. To obtain a remote origin, the following code can be used:

> ### Sample Code:  
> ```abap
> TRY.
>     DATA(lo_rfc_destination) = cl_rfc_destination_provider=>create_by_comm_arrangement( 'MY_COMM_ARRANGEMENT' ).
>   CATCH cx_rfc_dest_provider_error INTO DATA(lx_rfc_dest_provider_error).
>     " Handle exception.
> ENDTRY.
>  
> DATA(lo_remote_origin) = xco_cp_abap_objects=>origin->remote( lo_rfc_destination ).
> ```

> ### Note:  
> **Authorization requirements for remote reading**
> 
> Note that the user used for the system identified by the RFC destination needs to have the following authorizations in order to support the remote reading of classes and interfaces:
> 
> -   S\_RFC with RFC\_TYPE = Function module, RFC\_NAME = `SEO_CLASS_TYPEINFO_GET_RFC`, `SEO_INTERFACE_TYPEINFO_GET_RFC` and ACTVT = Execute
> 
> 
> or alternatively for the complete function group, meaning
> 
> -   S\_RFC with RFC\_TYPE = Function group, RFC\_NAME = SEO\_REMOTE and ACTVT = Execute

Once the origin has been obtained, it can be used for any of the exposed GET\_\* methods as part of the Read APIs for classes and interfaces. The code sample below illustrates how the public methods of the active version of a class can be read out for a remote destination:

> ### Sample Code:  
> ```abap
> 
> DATA(lt_public_methods) = xco_cp_abap=>class( 'MY_REMOTE_CLASS' )->definition->section-public->components->method->all->get(
>   io_version = xco_cp_abap_objects=>version->active
>   io_origin  = lo_remote_origin
> ).
>  
> LOOP AT lt_public_methods INTO DATA(lo_public_method).
>   " The name of the public method.
>   DATA(lv_public_method_name) = lo_public_method->name.
>  
>   " The short description of the method.
>   DATA(lv_short_description) = ls_public_method-short_description.
>  
>   " The indicator whether the method is ABSTRACT.
>   DATA(lv_abstract_indicator) = ls_public_method-abstract_indicator.
>  
>   " The indicator whether the method is FINAL.
>   DATA(lv_final_indicator) = ls_public_method-final_indicator.
>  
>   " The indicator whether the method is a REDEFINITION.
>   DATA(lv_redefinition_indicator) = ls_public_method-redefinition_indicator.
>  
>   " A structure containing the AMDP attributes of the method (definition).
>   DATA(ls_amdp) = ls_public_method-amdp.
> ENDLOOP.
> ```

Similarly, using the same LO\_REMOTE\_ORIGIN as in the example above, we can read the constants of the inactive version of a remote interface:

> ### Sample Code:  
> ```abap
> DATA(lt_constants) = xco_cp_abap=>interface( 'MY_REMOTE_INTERFACE' )->components->constant->all->get(
>   io_version = xco_cp_abap_objects=>version->inactive
>   io_origin  = lo_remote_origin
> ).
>  
> LOOP AT lt_constants INTO DATA(lo_constant).
>   " The name of the constant.
>   DATA(lv_constant_name) = lo_constant->name.
>  
>   DATA(ls_constant) = lo_constant->content( xco_cp_abap_objects=>version->inactive )->get( lo_remote_origin ).
>  
>   " The typing method of the constant.
>   DATA(lo_typing_method) = ls_constant-typing_method.
>  
>   " The typing definition of the constant.
>   DATA(lo_typing_definition) = ls_constant-typing_definition.
>  
>   " The value of the constant
>   DATA(lv_value) = ls_constant-value.
> ENDLOOP.
> ```

