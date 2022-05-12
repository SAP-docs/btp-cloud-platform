<!-- copy13ddb57e77684d84be7c21872912b7b9 -->

# Defining Permitted Activities in an Authorization Object

To define the permitted activities for a service, create an authorization object with the standard authorization field *Activity* \(`ACTVT`\) for the permitted activities.



## Procedure

1.  Follow the procedure in the ABAP development guide: [Defining an Authorization Object](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/6135edd0bf75427fa932875a6e3b0378.html).

    > ### Tip:  
    > In our example, in the newly created authorization object, under *Authorization Fields*, you only need the predefined *Activity* authorization field to define the permitted activities for the business users of your service. In our example, these activities would be *01 Add or Create*, *02 Change*, *03 Display*, and *06 Delete*. If you click on an empty row and choose [ENTER\], the list of available values is shown.




<a name="copy13ddb57e77684d84be7c21872912b7b9__result_ask_l2j_vlb"/>

## Results

In the following, the newly created authorization object for the bonus calculation example is called `ZBNSCLC_AO`.

