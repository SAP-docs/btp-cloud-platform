<!-- loioa151c7524a0c445eb2c6dbbbc7666b71 -->

# Defining an Authorization Field

As in the scenario for granting access based on activities, you define an authorization object. However, for this scenario, you first define authorization fields to fine-tune access on field level.



## Context

In the following, we assume that the bonus calculation service has a bonus variant field of type domain. You create an authorization field based on this data element.



## Procedure

1.  To create an authorization field `ZBNS_VARN` for the bonus variant, following the procedure for defining authorization fields in the [user guide for ABAP development tools](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide) \(ADT\).

2.  In the *Data Element* field, enter the data element for the bonus variant.

3.  In the *Check Table* field, enter the SQL view name that you have created as a check table for all possible bonus variants \(see [Creating a Check Table for Authorization Fields](creating-a-check-table-for-authorization-fields-e7cfd14.md)\).

    > ### Note:  
    > You can use the *Search Help* button to simulate the field help as it's shown to the administrator during the business role maintenance.


