<!-- loio99dcde1a72ed4e7fb0959ead46a7fbf5 -->

# Implementing the Business Logic



The following development steps require a user with the development role.

Create a class which implements the two interfaces:

-   **IF\_APJ\_DT\_EXEC\_OBJECT**
-   **IF\_APJ\_RT\_EXEC\_OBJECT**

This class is considered the main class per application job. This class needs to be part of a customer-defined software component \(not ZLOCAL\) in order to be able to transport the class into subsequent systems.

The first interface, IF\_APJ\_DT\_EXEC\_OBJECT, contains design-time related methods. Method **GET\_PARAMETERS\( \)** is called by the application jobs framework to get all supported selection parameters.

The method GET\_PARAMETERS\( \) returns two internal tables:

-   The content of the table **ET\_PARAMETER\_DEF** determines the parameter section for the job catalog entry, which will refer to this main class.
-   The content of the table **ET\_PARAMETER\_VAL** determines the default values for these parameters in the job template, which will refer to the job catalog entry mentioned above.


The second interface, IF\_APJ\_RT\_EXEC\_OBJECT, contains runtime related methods. Method **EXECUTE\(\)** is called by the application jobs framework if a scheduled job will actually be executed. It receives an internal table as parameter. This table is of the same type as the table ET\_PARAMETER\_VAL of method GET\_PARAMETERS\(\). The method EXECUTE\(\) simply receives the parameters and values, which were stored in the template and which were originally delivered by the method GET\_PARAMETERS\(\).

Please refer to the example code for an application jobs main class. Literals are used instead of language-dependent texts in order to simplify the example.

> ### Sample Code:  
> ```abap
> CLASS zcl_test_apj_simple DEFINITION
>   PUBLIC
>   FINAL
>   CREATE PUBLIC .
> 
>   PUBLIC SECTION.
>     INTERFACES if_apj_dt_exec_object.
>     INTERFACES if_apj_rt_exec_object.
>   PROTECTED SECTION.
>   PRIVATE SECTION.
> ENDCLASS.
> 
> 
> CLASS zcl_test_apj_simple IMPLEMENTATION.
> 
>   METHOD if_apj_dt_exec_object~get_parameters.
> 
>     " Return the supported selection parameters here
>     et_parameter_def = VALUE #(
>       ( selname = 'S_ID'    kind = if_apj_dt_exec_object=>select_option datatype = 'C' length = 10 param_text = 'My ID'                                      changeable_ind = abap_true )
>       ( selname = 'P_DESCR' kind = if_apj_dt_exec_object=>parameter     datatype = 'C' length = 80 param_text = 'My Description'   lowercase_ind = abap_true changeable_ind = abap_true )
>       ( selname = 'P_COUNT' kind = if_apj_dt_exec_object=>parameter     datatype = 'I' length = 10 param_text = 'My Count'                                   changeable_ind = abap_true )
>       ( selname = 'P_SIMUL' kind = if_apj_dt_exec_object=>parameter     datatype = 'C' length =  1 param_text = 'My Simulate Only' checkbox_ind = abap_true  changeable_ind = abap_true )
>     ).
> 
>     " Return the default parameters values here
>     et_parameter_val = VALUE #(
>       ( selname = 'S_ID'    kind = if_apj_dt_exec_object=>select_option sign = 'I' option = 'EQ' low = '4711' )
>       ( selname = 'P_DESCR' kind = if_apj_dt_exec_object=>parameter     sign = 'I' option = 'EQ' low = 'My Default Description' )
>       ( selname = 'P_COUNT' kind = if_apj_dt_exec_object=>parameter     sign = 'I' option = 'EQ' low = '200' )
>       ( selname = 'P_SIMUL' kind = if_apj_dt_exec_object=>parameter     sign = 'I' option = 'EQ' low = abap_true )
>     ).
> 
>   ENDMETHOD.
> 
>   METHOD if_apj_rt_exec_object~execute.
> 
>     TYPES ty_id TYPE c LENGTH 10.
> 
>     DATA s_id    TYPE RANGE OF ty_id.
>     DATA p_descr TYPE c LENGTH 80.
>     DATA p_count TYPE i.
>     DATA p_simul TYPE abap_boolean.
> 
>     " Getting the actual parameter values
>     LOOP AT it_parameters INTO DATA(ls_parameter).
>       CASE ls_parameter-selname.
>         WHEN 'S_ID'.
>           APPEND VALUE #( sign   = ls_parameter-sign
>                           option = ls_parameter-option
>                           low    = ls_parameter-low
>                           high   = ls_parameter-high ) TO s_id.
>         WHEN 'P_DESCR'. p_descr = ls_parameter-low.
>         WHEN 'P_COUNT'. p_count = ls_parameter-low.
>         WHEN 'P_SIMUL'. p_simul = ls_parameter-low.
>       ENDCASE.
>     ENDLOOP.
> 
>     " Implement the job execution
> 
>   ENDMETHOD.
> 
> ENDCLASS.
> 
> ```

**Related Information**  


[Creating the Job Catalog Entry](creating-the-job-catalog-entry-1cff59e.md "")

[Defining the Job Template](defining-the-job-template-1f04ad2.md "")

[Setting up the Authorizations](setting-up-the-authorizations-bb559a5.md "Some further activities in ADT and in the administrator’s launchpad are necessary to be able to schedule the job template in the Fiori app Application Jobs.")



