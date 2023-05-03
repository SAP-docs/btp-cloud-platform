<!-- loio22ae40f62252495baa7968e484824db2 -->

# Providing Access to a Business Service for Communication Users

For a newly created business service, you must define how communication users can access it and which activities are allowed.

Instead of accessing a business service using a business user, it is also possible to access a business service using a communication user. Communication users are relevant in scenarios where you work with an API business service \(inbound or outbound\) from or into the ABAP environment.

For communication users, you must provide access to a newly created service because access isn’t automatically available. However, on instance level, all activities are allowed as long as you don't protect your business service. Therefore, you must develop identity and access management artifacts.

The main difference to providing access to a business user is that, as a developer, you do not create an IAM app and a business catalog but a communication scenario. Authorizations are maintained in the communication scenario. Administrators cannot restrict the authorizations defined in the communication scenario later on when they create communication arrangements based on the communication scenario. Therefore, you as a developer decide which authorizations are granted for the communication user by the administrator.



<a name="loio22ae40f62252495baa7968e484824db2__section_xsp_l1x_3pb"/>

## Overview of Development Options

You can provide access the following ways:

-   Unrestricted access
-   Access based on activties from an authorization object

