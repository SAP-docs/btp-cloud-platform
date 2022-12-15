<!-- loio92a6c4843f0345b9861326ae5ce59819 -->

# Providing Read Access Using Privileged Mode

Use the keyword `WITH PRIVILEGED ACCESS` to provide read access using privileged mode.



## Context

For the bonus calculation job in the example used in this documentation, all valid bonus calculations with empty bonus amount are retrieved for calculation in the job. By using the keyword `WITH PRIVILEGED ACCESS` after the entity `z_i_bonus_calculation`, the CDS access controls with checks for authorization objects defined in authorization context `NoCheckWhenPrivileged` are disabled. As a result, unfiltered access to the `z_i_bonus_calculation` entity is possible.



## Procedure

In the example used in this documentation, you can use the following code for selecting bonus calculations:

 > ### Sample Code:  
> ```
> SELECT * FROM z_i_bonus_calculation
>         WITH PRIVILEGED ACCESS
>         WHERE z_i_bonus_calculation~validityenddate >= @sy-datum
>         AND z_i_bonus_calculation~bonusamount_v = 0
>         INTO TABLE @DATA(lt_bonus_calculation).
> 
> ```

 