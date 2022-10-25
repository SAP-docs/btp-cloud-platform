<!-- loioefc372130faf412198a0f2990d97782b -->

# Defining an Authorization Object

As in the scenario for granting access based on activities, you define an authorization object. However, for this scenario, you also add the authorization field `ZBNS_VARN` for the bonus variant.



<a name="loioefc372130faf412198a0f2990d97782b__steps_vhr_ptj_vlb"/>

## Procedure

Follow the procedure in the ABAP development guide: [Defining an Authorization Object](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/6135edd0bf75427fa932875a6e3b0378.html).

 > ### Tip:  
> In our example, in the newly created authorization object, under *Authorization Fields*, you need the following:
> 
> -   The predefined *Activity \(ACTVT\)* authorization field to define the permitted activities for the business users of your business service: *01 Add or Create*, *02 Change*, *03 Display*, and *06 Delete* as standard activities as well as *93 Calculate* for the business object-specific activity *Calculate Bonus*. If you click on an empty row and choose [ENTER\], the list of available values is shown.
> 
> -   The newly created authorization field `ZBNS_VARN` for the bonus variant

 