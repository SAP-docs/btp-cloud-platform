<!-- loioee732d69e7c94586819efe0e165a9566 -->

# Implementing a Protection Against Unauthorized Write Activities

To protect a service, such as the example of bonus calculation from unauthorized creations, updates, or deletions, enhance the behavior implementation of the service in ABAP Development Tools \(ADT\). The implementation is required by what has been defined as authorization control in the behavior definition.



## Context

Among the methods of the behavior implementation, you add methods that check the authorizations for creation and for update and delete.

For more information about authorization control, see [Authorization Control](https://help.sap.com/viewer/923180ddb98240829d935862025004d6/Cloud/en-US/375a8124b22948688ac1c55297868d06.html) in the documentation for the ABAP RESTful Application Programming Model.



<a name="loioee732d69e7c94586819efe0e165a9566__steps_lcv_pjj_xlb"/>

## Procedure

1.  In the *Source Code Library* folder of your package, under *Classes*, choose the behavior implementation of your service.

2.  In the `PRIVATE SECTION` in the handler class of the behavior implementation, define the method for authorization checks for update and deletion:

    > ### Sample Code:  
    > ```lang-abap
    >   METHODS get_instance_authorizations FOR INSTANCE AUTHORIZATION
    >     IMPORTING it_entity_keys REQUEST requested_authorizations FOR <behavior definition or its alias> RESULT result.
    > ```

    In the bonus calculation example, this method definition can look as follows:

    > ### Sample Code:  
    > ```lang-abap
    >   METHODS get_instance_authorizations FOR INSTANCE AUTHORIZATION
    >     IMPORTING keys REQUEST requested_authorizations FOR calculation RESULT result.
    > ```

3.  In the `PRIVATE SECTION` in the handler class of the behavior implementation, also define the method for authorization checks for creation:

    > ### Sample Code:  
    > ```lang-abap
    >   METHODS get_global_authorizations FOR GLOBAL AUTHORIZATION
    >     IMPORTING REQUEST requested_authorizations FOR <behavior definition or its alias> RESULT result.
    > ```

    In the bonus calculation example, this method definition can look as follows:

    > ### Sample Code:  
    > ```lang-abap
    >   METHODS get_global_authorizations FOR GLOBAL AUTHORIZATION
    >     IMPORTING REQUEST requested_authorizations FOR calculation RESULT result.
    > ```

4.  Add a method implementation that checks the authorizations for updates and deletions.

    In the bonus calculation example, this method can look like this:

    > ### Sample Code:  
    > ```lang-abap
    >   METHOD get_instance_authorizations.
    > 
    > *     As import table contains only keys, we need to get complete bonus calculation data for bonus variant value
    >     READ ENTITIES OF z_i_bonus_calculation IN LOCAL MODE
    >              ENTITY calculation
    >               ALL FIELDS
    >                  WITH CORRESPONDING #( it_bonus_calc_keys )
    >              RESULT DATA(lt_bonus_calcs).
    > 
    > *     fill result list with authorizations per bonus calculation
    >     LOOP AT lt_bonus_calcs INTO DATA(ls_bonus_calc).
    > 
    > *       check update authorization for bonus calculation incl. bonus variant dependency
    >       AUTHORITY-CHECK OBJECT 'ZBNSCLC_AO' ID 'ACTVT' FIELD '02' ID 'ZBNS_VARNT' FIELD ls_bonus_calc-bonusvariant.
    > *       set variable for update authorization
    >       DATA(lv_update_allowed) = COND #( WHEN sy-subrc = 0 THEN if_abap_behv=>auth-allowed ELSE if_abap_behv=>auth-unauthorized ).
    > 
    > *       check delete authorization for bonus calculation incl. bonus variant dependency
    >       AUTHORITY-CHECK OBJECT 'ZBNSCLC_AO' ID 'ACTVT' FIELD '06' ID 'ZBNS_VARNT' FIELD ls_bonus_calc-bonusvariant.
    > *       set variable for delete authorization
    >       DATA(lv_delete_allowed) = COND #( WHEN sy-subrc = 0 THEN if_abap_behv=>auth-allowed ELSE if_abap_behv=>auth-unauthorized ).
    > 
    > *       fill result list
    >       APPEND VALUE #( id = ls_bonus_calc-id %update = lv_update_allowed %delete = lv_delete_allowed ) TO result.
    >     ENDLOOP.
    > 
    >   ENDMETHOD.
    > 
    > ```

5.  Add a method that checks the authorizations for creation.

    In the bonus calculation example, such a method could look like this:

    > ### Sample Code:  
    > ```lang-abap
    >   METHOD get_global_authorizations.
    >   
    >     IF requested_authorizations-%create EQ if_abap_behv=>mk-on.
    > *     check create authorization
    >       AUTHORITY-CHECK OBJECT 'ZBNSCLC_AO' ID 'ACTVT' FIELD '01'.
    >       result-%create = COND #( WHEN sy-subrc = 0 THEN
    >       if_abap_behv=>auth-allowed ELSE
    >       if_abap_behv=>auth-unauthorized ).
    >     ENDIF.
    > 
    >   ENDMETHOD.
    > ```




<a name="loioee732d69e7c94586819efe0e165a9566__result_pyz_scp_nlb"/>

## Results

The implemented methods provide the desired protection from unauthorized uses:

-   With the implementation of the method `get_instance_authorizations`, an unauthorized business user gets an error message when trying to update or delete a business object instance \(in the example, a bonus calculation\) via service call.

-   With the implementation of the method `get_global_authorizations`, an unauthorized business user gets an error message when trying to save the creation of a new business object instance.

-   Unauthorized business users can't use the *Delete* button in the list view on the service UI. In addition, the *Edit* and *Delete* buttons are hidden in the detail view on the service UI for a business object instance.


Now, the service is secured against unauthorized operations. As a next step, you must make sure that business users who need to use service get the corresponding authorizations.

