<!-- loio9a82de715db141ad8593244ffde35402 -->

# Create an Exception

One item category, which can be written into an application log, is an *Exception*. An exception is raised by the application using ABAP command ***RAISE EXCEPTION*** and can be caught by ABAP command ***CATCH***.

To define an application log exception, you can set the following attributes:

-   Severity, such as 'Error', 'Warning', 'Information'. Possible values of the severity are defined as constants in interface`IF_BALI_CONSTANTS`.

-   Reference to the exception object

-   Detail Level of the item: If the application displays the items of the application log, the detail level can be used to define at which level of detail the item shall be displayed.


To add an exception to an application log, an instance of interface `IF_BALI_EXCEPTION_SETTER` is required. To create this instance, method `CREATE` of class `CL_BALI_EXCEPTION_SETTER` can be used. It allows to set the severity and the reference to the exception object.

If you want to set or change the attributes of the exception, you can use interface `IF_BALI_EXCEPTION_SETTER`. It contains the following methods:

-   SET\_EXCEPTION: Changes the reference to the exception object and the severity.

-   SET\_DETAIL\_LEVEL: Sets the detail level.


> ### Sample Code:  
> ```
> 
> ...
>  DATA: i TYPE i.
>  TRY.
>      i = 1 / 0.
>    CATCH cx_sy_zerodivide INTO DATA(l_exception_ref).
>  ENDTRY.
> 
>  DATA(l_ref) = cl_bali_exception_setter=>create( severity = if_bali_constants=>c_severity_error
>                                                  exception = l_exception_ref ).
>  l_ref->set_detail_level( detail_level = '2' ).
> ...
> ```

