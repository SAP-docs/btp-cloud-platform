<!-- loio9984a29f721e4981ad6a0b0b0cb6b868 -->

# Manage Environment Variables

You can use the SAP BTP cockpit to view system-provided and create user-provided variables. The Cloud Foundry environment uses these variables to communicate with the applications deployed in it.



<a name="loio9984a29f721e4981ad6a0b0b0cb6b868__section_f1g_f3f_32c"/>

## Environment Variables

In the Cloud Foundry environment, there are two types of environment variables:

-   System-provided

    The system-provided variables are provided by the Cloud Foundry environment.

    They are split into `VCAP_APPLICATION` and `VCAP_SERVICES`:

    -   `VCAP_APPLICATION` contain the attributes of your deployed application.

    -   `VCAP_SERVICES` contain information about the service instances bound to your application, if any.


-   User-provided

    You can create your own custom environment variables as key-value pairs. For more information, see [Create User-Provided Variables](manage-environment-variables-9984a29.md#loio9984a29f721e4981ad6a0b0b0cb6b868__section_wgl_w3f_32c).




<a name="loio9984a29f721e4981ad6a0b0b0cb6b868__section_y4c_svs_32c"/>

## Environment Variable Groups

There are two types of environment variable groups:

-   Running

    All variables available to your application at runtime.

-   Staging

    All variables available to your application at the time of staging.




<a name="loio9984a29f721e4981ad6a0b0b0cb6b868__section_s3r_v3f_32c"/>

## View System-Provided Variables and Environment Variable Groups



### Prerequisites

-   You must have at least one application deployed in your Cloud Foundry space.

-   You have the Space Developer or Space Supporter role.




### Procedure

1.  In the SAP BTP cockpit, navigate to the *Applications* page in your Cloud Foundry space.

2.  Choose the application whose environment variables you want to view.

3.  Choose *Environment Variables*.




<a name="loio9984a29f721e4981ad6a0b0b0cb6b868__section_wgl_w3f_32c"/>

## Create User-Provided Variables



### Prerequisites

-   You must have at least one application deployed in your Cloud Foundry space.

-   You have the Space Developer or Space Supporter role.




### Procedure

1.  In the SAP BTP cockpit, navigate to the *Applications* page in your Cloud Foundry space.

2.  Choose the application for which you want to create a user-provided variable.

3.  Choose *User-Provided Variables*.

4.  Choose *Create Variable*.

5.  Provide a *Key* and a *Value*.

    These values are case-sensitive.

6.  Choose *Create*.


**Related Information**  


[https://docs.cloudfoundry.org/devguide/deploy-apps/environment-variable.html](https://docs.cloudfoundry.org/devguide/deploy-apps/environment-variable.html)

