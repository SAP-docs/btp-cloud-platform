<!-- loioa151c7524a0c445eb2c6dbbbc7666b71 -->

# Defining an Authorization Field

As in the scenario for granting access based on activities, you define an authorization object. However, for this scenario, you first define authorization fields to fine-tune access on field level.



## Context

In the following, we assume that the bonus calculation service has a bonus variant field of type domain. You create an authorization field based on this data element.



## Procedure

1.  Create an authorization field `ZBNS_VARN` for the bonus variant by following the procedure in the ABAP development guide: [Defining Authorization Fields](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/cd2bb3a279454b1eab7d28c371740a5c.html).

2.  In the *Data Element* field, enter the data element for the bonus variant.

3.  In the *Check Table* field, enter the SQL view name that you have created as a check table for all possible bonus variants \(see [Creating a Check Table for Authorization Fields](Creating_a_Check_Table_for_Authorization_Fields_e7cfd14.md)\).

    > ### Note:  
    > You can use the *Search Help* button to simulate the field help as it's shown to the administrator during the business role maintenance.


