<!-- loio231e276a27d042bab7f6517dde2df019 -->

# Exception Handling

Learn how to handle the exception `CX_APJ_RT_CONTENT` of the method `EXECUTE`.

The method `EXECUTE` has the exception `CX_APJ_RT_CONTENT` in its signature. You can raise an exception of this type and specify a message text \(see code snippet\) . The application job framework handles exceptions of type `CX_APJ_RT_CONTENT` and creates a separate log for the application job. The log contains the message text, and information about the source position where the exception was raised. The application job gets the status *Failed*.

> ### Sample Code:  
> ```abap
> " the following coding simulates the application logic that causes a system exception
> " (in this case: division by zero)
> 
> DATA a TYPE i.
> DATA b TYPE i.
> DATA c TYPE i.
> 
> TRY.
> 
>    a = 1.
>    b = 0.
>    c = a / b.
> 
>    CATCH cx_root INTO DATA(exc).
> 
> " Precondition for the following statement:
> " message class Z_APJ must exist, message 001 must exist in this message class with one variable part
>         
>    RAISE EXCEPTION TYPE cx_apj_rt_content MESSAGE ID 'Z_APJ' NUMBER 001 WITH exc->get_text(  ).
> 
> ENDTRY.
> ```

The application job framework doesn't handle any other exception apart from `CX_APJ_RT_CONTENT`. Any other exception which is not handled within the `EXECUTE` method itself will lead to a runtime error. The log will then contain the name of the runtime error, and further details of the runtime error have to be checked in the *ABAP Runtime Errors* app.

