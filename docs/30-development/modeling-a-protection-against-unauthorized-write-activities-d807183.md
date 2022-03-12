<!-- loiod807183367a34038bbc11218c71ef339 -->

# Modeling a Protection Against Unauthorized Write Activities

To protect your service from activities such as create, update or delete by unauthorized business users, you can use the authorization controls that are available for services based on managed business objects.



<a name="loiod807183367a34038bbc11218c71ef339__context_wbn_z1n_plb"/>

## Context

In the example used here, the service is based on a managed business object *Bonus Calculation*. The use of a managed business object allows you to benefit from the global authorization for managed business objects, which is part of the ABAP RESTful Application Programming model. For more information about authorization control, see [Authorization Control](https://help.sap.com/viewer/923180ddb98240829d935862025004d6/Cloud/en-US/375a8124b22948688ac1c55297868d06.html) in the documentation for the ABAP RESTful Application Programming Model.



## Procedure

1.  In ABAP Development Tools, call up the behavior definition of your service.

2.  In the behavior definition, define authorization controls for your service.

    In the bonus calculation example, they can look as follows:

    > ### Sample Code:  
    > ```abap
    > managed;
    > 
    > define behavior for z_i_bonus_calculation alias calculation
    > implementation in class zbp_bonus_calculation unique
    > persistent table zbonusclc
    > lock master
    > 
    > // Identity and Access Management:
    > // Enable RAP managed authorization check at create, update, and delete
    > // -> requires implementation of a method with addition "FOR GLOBAL AUTHORIZATION"
    > authorization master ( global )
    > 
    > ```

    With the line `authorization master ( global )`, an authorization check for the standard operations create, update, and delete is defined, which you must implement using a method with addition `FOR GLOBAL AUTHORIZATION` in the behavior implementation.


