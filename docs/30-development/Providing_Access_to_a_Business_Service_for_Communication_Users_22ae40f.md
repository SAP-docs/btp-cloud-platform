<!-- loio22ae40f62252495baa7968e484824db2 -->

# Providing Access to a Business Service for Communication Users

Instead of accessing a business service using a business user, it is also possible to access a business service using a communication user. In this case, as a developer, you create a communication scenario.

Communication users are relevant in scenarios where you work with an API business service \(inbound or outbound\) from or into the ABAP environment.

The main difference to providing access to a business user is that, as a developer, you do not create an IAM app and a business catalog but a communication scenario. Authorizations are maintained in the communication scenario. Administrators cannot restrict the authorizations defined in the communication scenario later on when they create communication arrangements based on the communication scenario. Therefore, you as a developer decide which authorizations are granted for the communication user by the administrator.



<a name="loio22ae40f62252495baa7968e484824db2__section_xsp_l1x_3pb"/>

## Overview of Development Activities

You can provide access the following ways:

-   Unrestricted access
-   Access based on activties from an authorization object

-   **[Granting \(Unrestricted\) Access for Communication Users](Granting_(Unrestricted)_Access_for_Communication_Users_3cd6f05.md "In this scenario, you get information about how to grant unrestricted access for communication users with a few steps.")**  
In this scenario, you get information about how to grant unrestricted access for communication users with a few steps.
-   **[Granting Access Based on Activities for Communication Users](Granting_Access_Based_on_Activities_for_Communication_Users_bc9c2c9.md "In this scenario, you grant access depending on what the communication user should be allowed to do, for example, read or write access. ")**  
In this scenario, you grant access depending on what the communication user should be allowed to do, for example, read or write access.

