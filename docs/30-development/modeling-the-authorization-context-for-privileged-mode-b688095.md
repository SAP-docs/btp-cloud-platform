<!-- loiob688095178884a07b2db1b9bceff4cb9 -->

# Modeling the Authorization Context for Privileged Mode

To enable privileged mode, you need another authorization context named `NoCheckWhenPrivileged`.



## Context

Let's assume that you want to enable privileged mode for the bonus calculation object that's used as an example in this documentation. First, you define an authorization context called `NoCheckWhenPrivileged` in the behavior definition. This authorization context is needed in addition to the `own authorization` context of the business object that you've already defined in the behavior definition. Then, you enable privileged mode for the business object by disabling `NoCheckWhenPrivileged` using the clause `with privileged mode disabling NoCheckWhenPrivileged`. As a result, authorization objects in the context `NoCheckWhenPrivileged` aren't checked during privileged access.



## Procedure

In the behavior definition, add the following code, for example:

 > ### Sample Code:  
> ```
> managed;
> 
> define authorization context NoCheckWhenPrivileged
> {
>   'ZBNSCLC_AO';
> }
> 
> with privileged mode disabling NoCheckWhenPrivileged;
> define own authorization context
> {
>   'ZBNSCLC_AO';
> }
> 
> define behavior for z_i_bonus_calculation alias calculation
> implementation in class zbp_bonus_calculation unique
> persistent table zbonusclc
> lock master
> 
> // Identity and Access Management:
> // Enable RAP managed authorization check at create, update, and delete
> // -> requires implementation of two methods, one with the addition "FOR INSTANCE AUTHORIZATION"
> //  and one with the addition "FOR GLOBAL AUTHORIZATION"
> 
> authorization master ( instance, global )
> ```

 