<!-- copy18bb590e16fd41068f08ea2d7d015b0d -->

# Modeling a Protection Against Unauthorized Write Activities

To protect your service from activities such as create, update or delete by unauthorized users, you can use the authorization controls that are available for services based on managed business objects.



<a name="copy18bb590e16fd41068f08ea2d7d015b0d__context_wbn_z1n_plb"/>

## Context

In the example used here, the service is based on a managed business object *Bonus Calculation*. The use of a managed business object allows you to benefit from the global authorization for managed business objects, which is part of the ABAP RESTful Application Programming model. For more information about authorization control, see the documentation for the [ABAP RESTful Application Programming Model](https://help.sap.com/docs/abap-cloud/abap-rap/abap-restful-application-programming-model?locale=en-US).



## Procedure

1.  In ABAP development tools, call up the behavior definition of your service.

2.  In the behavior definition, define authorization controls for your service.

    In the bonus calculation example, they can be as follows:

    > ### Sample Code:  
    > ```abap
    > managed;
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
    > 
    > ```

    With the line `authorization master ( global )`, an authorization check for the standard operations `create`, `update`, and `delete` and for non-standard operations, for example, `calculate bonus`, is defined. You must implement the authorization check using a method with addition `FOR GLOBAL AUTHORIZATION` in the behavior implementation.

    The sample code also contains the definition of your own authorization context. The own authorization context documents all authorization objects that are used by the business object implementation. In the bonus calculation example used in this documentation, this is the authorization object `ZBNSCLC_AO` because it's checked in the authorization control. The own authorization context is also used to prefill authorization defaults.


