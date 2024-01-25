<!-- loio0bc1e5fd5c89424fa0dbad617b4c5e63 -->

# Design Time API

You can use the *Application Log Design Time API* if you want to create, change, or delete an application log object or subobject during the development process of an application.

For information on how to create an application log object in ADT, see [Working with Application Log Objects](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/working-with-application-log-objects?version=sap_btp).

The *Application Log Design Time API* provides the following design time operations:

-   Create a new application log object, optionally with subobjects

-   Delete an application log object and all of its subobjects

-   Add a new subobject to an existing application log object

-   Delete a subobject from an application log object

-   Read an application log object and all of its subobjects




<a name="loio0bc1e5fd5c89424fa0dbad617b4c5e63__section_ovl_n3s_wlb"/>

## Create a New Application Log Object, Optionally with Subobjects

Once you have created an instance of the `CL_BALI_OBJECT_HANDLER` API class using method`CREATE_OBJECT`, a new application log object is created.

> ### Sample Code:  
> ```
> 
> DATA(lo_log_object) = cl_bali_object_handler=>get_instance( ).
> TRY.
>     lo_log_object->create_object( EXPORTING iv_object = 'MYOBJECT'
>                                             iv_object_text = 'My Application Log Object'
>                                             iv_package = 'MYPACKAGE'
>                                             iv_transport_request = 'MYTRANSPORT' ).
>   CATCH cx_bali_objects INTO DATA(lx_exception).
>     WRITE lx_exception->get_text( ).
> ENDTRY.
> ```

In case the new application log object has subobjects, you can create these too, using the `CREATE_OBJECT` method.

> ### Sample Code:  
> ```
> 
> DATA: ls_subobject TYPE LINE OF if_bali_object_handler=>ty_tab_subobject,
>       lt_subobject TYPE if_bali_object_handler=>ty_tab_subobject.
> 
> ls_subobject-subobject = 'MYSUBOBJECT'.
> ls_subobject-subobject_text = 'My Application Log Sub-Object'.
> APPEND ls_subobject TO lt_subobject.
> DATA(lo_log_object) = cl_bali_object_handler=>get_instance( ).
> TRY.
>     lo_log_object->create_object( EXPORTING iv_object = 'MYOBJECT'
>                                             iv_object_text = 'My Application Log Object'
>                                             it_subobjects = lt_subobject
>                                             iv_package = 'MYPACKAGE'
>                                             iv_transport_request = 'MYTRANSPORT' ).
>   CATCH cx_bali_objects INTO DATA(lx_exception).
>     WRITE lx_exception->get_text( ).
> ENDTRY.
> ```



<a name="loio0bc1e5fd5c89424fa0dbad617b4c5e63__section_bxr_2js_wlb"/>

## Delete an Application Log Object and all of its Subobjects

Use method `DELETE_OBJECT` to delete an application log object and all of its subobjects.

> ### Sample Code:  
> ```
> 
> DATA(lo_log_object) = cl_bali_object_handler=>get_instance( ).
> TRY.
>     lo_log_object->delete_object( EXPORTING iv_object = 'MYOBJECT'
>                                             iv_transport_request = 'MYTRANSPORT' ).
>   CATCH cx_bali_objects INTO DATA(lx_exception).
>     WRITE lx_exception->get_text( ).
> ENDTRY.
> ```



<a name="loio0bc1e5fd5c89424fa0dbad617b4c5e63__section_ncv_mjs_wlb"/>

## Add a New Subobject to an Existing Application Log Object

Use method `ADD_SUBOBJECT` if you want to add a new subobject to an existing application log object.

> ### Sample Code:  
> ```
> 
> DATA(lo_log_object) = cl_bali_object_handler=>get_instance( ).
> TRY.
>     lo_log_object->add_subobject( EXPORTING iv_object = 'MYOBJECT'
>                                             iv_subobject = 'MYSUBOBJECT'
>                                             iv_subobject_text = 'My Application Log Sub-Object'
>                                             iv_transport_request = 'MYTRANSPORT' ).
>   CATCH cx_bali_objects INTO DATA(lx_exception).
>     WRITE lx_exception->get_text( ).
> ENDTRY.
> ```



<a name="loio0bc1e5fd5c89424fa0dbad617b4c5e63__section_wmt_tjs_wlb"/>

## Delete a Subobject from an Application Log Object

You can delete a subobject using method `DELETE_SUBOBJECT`.

> ### Sample Code:  
> ```
> 
> DATA(lo_log_object) = cl_bali_object_handler=>get_instance( ).
> TRY.
>     lo_log_object->delete_subobject( EXPORTING iv_object = 'MYOBJECT'
>                                                iv_subobject = 'MYSUBOBJECT'
>                                                iv_transport_request = 'MYTRANSPORT' ).
>   CATCH cx_bali_objects INTO DATA(lx_exception).
>     WRITE lx_exception->get_text( ).
> ENDTRY.
> ```



<a name="loio0bc1e5fd5c89424fa0dbad617b4c5e63__section_ap2_zjs_wlb"/>

## Read an Application Log Object and all of its Subobjects

Use method `READ_OBJECT` to read an application log object with its subobjects.

> ### Sample Code:  
> ```
> 
> DATA(lo_log_object) = cl_bali_object_handler=>get_instance( ).
> TRY.
>     lo_log_object->read_object( EXPORTING iv_object = 'MYOBJECT'
>                                 IMPORTING et_subobjects = DATA(lt_subobjects)
>                                           ev_object_text = DATA(lv_object_text) ).
>   CATCH cx_bali_objects INTO DATA(lx_exception).
>     WRITE lx_exception->get_text( ).
> ENDTRY.
> ```

