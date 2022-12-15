<!-- loioc33599391557415896921ace44f2ba73 -->

# Providing Write Access Using Privileged Mode

Use the keyword `PRIVILEGED` to provide write access using privileged mode.



## Context

After open bonus calculations have been retrieved, the bonus calculation action `calculatebonus` is triggered in the *Bonus Calculation* business object with privileged access. By using the keyword `PRIVILEGED` after the behavior definition`z_i_bonus_calculation`, you enable privileged mode. As a result, the bonus calculation is executed without further authorization checks in the RAP authorization control.



## Procedure

In the example used in this documentation, you can use the following code:

 > ### Sample Code:  
> ```
> MODIFY ENTITIES OF z_i_bonus_calculation
>         PRIVILEGED
>         ENTITY calculation
>         EXECUTE calculatebonus FROM CORRESPONDING  #( lt_bonus_calculation )
>         RESULT DATA(result)
>         REPORTED DATA(reported)
>         FAILED DATA(failed).
> 
> ```

 