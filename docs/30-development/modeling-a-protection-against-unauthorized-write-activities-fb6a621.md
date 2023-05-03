<!-- loiofb6a6213fced4fe8af8466e25fa73035 -->

# Modeling a Protection Against Unauthorized Write Activities

To protect your service from activities such as create, update or delete by unauthorized business users, you can use the authorization controls that are available for services based on managed business objects.



<a name="loiofb6a6213fced4fe8af8466e25fa73035__context_wbn_z1n_plb"/>

## Context

In the example used here, the service is based on a managed business object *Bonus Calculation*. The use of a managed business object allows you to benefit from the global and instance-based authorizations for managed business objects, which are part of the ABAP RESTful Application Programming model. For more information about authorization control, see [Authorization Control](https://help.sap.com/viewer/923180ddb98240829d935862025004d6/Cloud/en-US/375a8124b22948688ac1c55297868d06.html) in the documentation for the ABAP RESTful Application Programming Model.



<a name="loiofb6a6213fced4fe8af8466e25fa73035__steps_ij2_gbp_nnb"/>

## Procedure

1.  In ABAP Development Tools, call up the behavior definition of your service.

2.  In the behavior definition, define authorization controls for your service.

    In the bonus calculation example, they can look as follows:

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

    With the line `authorization master ( instance, global )`, an authorization check for the standard operations `create`, `update`, and `delete` and for non-standard operations, for example, `calculate bonus`, is defined. You must implement the authorization check using methods with addition `FOR GLOBAL AUTHORIZATION` \(for `create`\) and `FOR INSTANCE AUTHORIZATION` \(for `update`, `delete`\) in the behavior implementation.

    The sample code also contains the definition of your own authorization context. The own authorization context documents all authorization objects that are used by the business object implementation. In the bonus calculation example used in this documentation, this is the authorization object `ZBNSCLC_AO` because it's checked in the RAP authorization control and the CDS access control. The own authorization context can also be used to prefill authorization defaults.


