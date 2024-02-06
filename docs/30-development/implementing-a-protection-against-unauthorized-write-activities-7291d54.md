<!-- copy7291d547186544549cb8ad9ade0204a9 -->

# Implementing a Protection Against Unauthorized Write Activities

To protect a service such as the example of bonus calculation against unauthorized bonus creations, updates, or deletions, enhance the behavior implementation of the service in ABAP development tools \(ADT\). The implementation is required by what has been defined in the behavior definition.



<a name="copy7291d547186544549cb8ad9ade0204a9__context_ibt_d3n_plb"/>

## Context

Among the methods of the behavior implementation, you add methods that check the authorizations for creation and for update and delete.



## Procedure

1.  In the *Source Code Library* folder of your package, under *Classes*, choose the behavior implementation of your service.

2.  In the `PRIVATE SECTION` in the handler class of the behavior implementation, define the methods for authorization checks for creation, update, and deletion.

    > ### Sample Code:  
    > ```abap
    >   METHODS get_global_authorizations FOR GLOBAL AUTHORIZATION
    >     IMPORTING REQUEST requested_authorizations FOR <behavior definition or its alias> RESULT result.
    > 
    > ```

    In the bonus calculation example, these method definitions could be the following:

    > ### Sample Code:  
    > ```abap
    >   METHODS get_global_authorizations FOR GLOBAL AUTHORIZATION
    >     IMPORTING REQUEST requested_authorizations FOR calculation RESULT result.
    > 
    > ```

3.  Add a method implementation that checks the authorizations for creations, updates, and deletions.

    > ### Note:  
    > For more information about authorization control, see the documentation for the [ABAP RESTful Application Programming Model](https://help.sap.com/docs/abap-cloud/abap-rap/abap-restful-application-programming-model?locale=en-US).

    In the bonus calculation example, this method could be the following:

    > ### Sample Code:  
    > ```abap
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
    >     IF requested_authorizations-%update EQ if_abap_behv=>mk-on.
    > *     check update authorization
    >       AUTHORITY-CHECK OBJECT 'ZBNSCLC_AO' ID 'ACTVT' FIELD '02'.
    >       result-%update = COND #( WHEN sy-subrc = 0 THEN
    >       if_abap_behv=>auth-allowed ELSE
    >       if_abap_behv=>auth-unauthorized ).
    >     ENDIF.
    > 
    >     IF requested_authorizations-%delete EQ if_abap_behv=>mk-on.
    > *     check delete authorization
    >       AUTHORITY-CHECK OBJECT 'ZBNSCLC_AO' ID 'ACTVT' FIELD '06'.
    >       result-%delete = COND #( WHEN sy-subrc = 0 THEN
    >       if_abap_behv=>auth-allowed ELSE
    >       if_abap_behv=>auth-unauthorized ).
    >     ENDIF.
    > 
    >   ENDMETHOD.
    > ```




<a name="copy7291d547186544549cb8ad9ade0204a9__result_pyz_scp_nlb"/>

## Results

The implemented methods provide the desired protection from unauthorized uses:

-   With the implementation of the method defined with the addition `FOR GLOBAL AUTHORIZATION`, an unauthorized business user gets an error message when trying to create a business object instance \(in the example, a bonus calculation\) or when trying to update or delete it via service call.

-   Unauthorized business users can't use the *Delete* button in the list view on the service UI. In addition, the *Edit* and *Delete* buttons are hidden in the detail view on the service UI for a business object instance.


Now, the service is secured against unauthorized operations. As a next step, you must make sure that business users who need to use the service get the corresponding authorizations.

