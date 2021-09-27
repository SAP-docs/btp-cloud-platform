<!-- loiod60c7fb9468b48c995c2a323c88fe11f -->

# Providing Access Based on Field Values for Business Users

You can enable access to a service in such a way that it's dependent on the field values of a business object. As a result, business users can view or change only business object instances where the field values match their authorizations.



<a name="loiod60c7fb9468b48c995c2a323c88fe11f__section_a4r_qmg_pmb"/>

## Overview

![](images/Access_Based_on_Field_Values_819a9fa.png)

The central concept in this scenario is the restriction field: In a restriction field, you can expose an existing authorization field as a restrictable field in a business role. You first create an authorization object and implement an access control and authority checks in the behavior implementation to protect your service from unauthorized use. Then you create an IAM app and a business catalog to make it available to administrators, who want to include the service \(or, rather, the corresponding business catalog\) into a business role. With the restriction field, you as a developer, can define which authorization fields should be available for the administrator during business role maintenance. Administrators can then decide which values of the restriction fields are relevant for some business roles. In the example of the bonus calculation service, administrators can create business roles to restrict the access for bonus calculations to selected bonus variants only.



<a name="loiod60c7fb9468b48c995c2a323c88fe11f__section_npc_zzm_5mb"/>

## Process

To create access protection and provide authorizations, you perform the following steps:



### Protecting the Service from Unauthorized Use

As a developer, you perform the following steps in ABAP Development Tools \(ADT\):

1.  Create an authorization field. For example, create an authorization field `ZBNS_VARN` for the bonus variant.

2.  Create an authorization object with the standard authorization field `ACTVT` and other authorization fields if needed, for example, bonus variant.

3.  Implement an access control as a read protection for the service.

4.  Model authority checks in the behavior definition of the service.

5.  Implement authority checks in the behavior implementation of the service to allow create, update, and delete activities only to users who have the authorizations of the authorization object.


As a result, no user can access the service to display bonus calculations or create, update, or delete bonus calculations anymore.



### Developing Authorizations for the Service

As a developer, you perform the following steps in ADT:

1.  Add the required authorization objects to the list of default authorization values.

2.  Create an IAM app and assign the service binding to it.

3.  For each authorization field that you want to expose and consider in a business role, create a corresponding restriction field.

4.  Assign the restriction fields to a restriction type.

5.  Create a business catalog and assign the IAM app to it. Add the restriction types to the business catalog.

6.  Optional: Create a business role template and assign the catalog to it.


Now, administrators can start granting access to business users. Development is finished and testing can start.



### Granting Authorizations to Business Users

As an administrator in the ABAP environment, you can now grant authorizations to business users for this service:

1.  Create business roles and assign them to business users.

    For each business role, set the access category *Write* to restricted. Select the values for which you want to authorize the users. For example, create a business role with the authorization to create, update, and delete only bonus calculations that are based on specific bonus variants.


As a result, business users with the business role assigned can access the service to display bonus calculations or create, update, or delete bonus calculations again.

-   **[Protecting the Service \(Developer\)](Protecting_the_Service_(Developer)_00bb671.md "With creating authorization fields and an authorization object for your service and with the implementation of a protection against
		unauthorized read and creation, you can implement a protection of your service against unauthorized use on field level.")**  
With creating authorization fields and an authorization object for your service and with the implementation of a protection against unauthorized read and creation, you can implement a protection of your service against unauthorized use on field level.
-   **[Developing Authorizations \(Developer\)](Developing_Authorizations_(Developer)_3cb5b19.md "After you’ve protected your service against unauthorized use, you create the objects that are needed for granting authorizations to
		business users to use your service.")**  
After you’ve protected your service against unauthorized use, you create the objects that are needed for granting authorizations to business users to use your service.
-   **[Granting Authorizations to Business Users \(Administrator\)](Granting_Authorizations_to_Business_Users_(Administrator)_6d3776e.md "As an administrator, create business roles to grant authorizations to business users.")**  
As an administrator, create business roles to grant authorizations to business users.

