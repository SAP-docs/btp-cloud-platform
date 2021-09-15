<!-- loiod3c73f11f6a14ba68c3083e026e05e7e -->

# Create User-Provided Service Instances Using the Cloud Foundry Command Line Interface

Use the Cloud Foundry Command Line Interface to make a user-provided service instance available to Cloud Foundry applications.



<a name="loiod3c73f11f6a14ba68c3083e026e05e7e__prereq_w1y_5cg_xbb"/>

## Prerequisites

-   Download and install the cf CLI and log on to Cloud Foundry. For more information, see [Download and Install the Cloud Foundry Command Line Interface](Download_and_Install_the_Cloud_Foundry_Command_Line_Interface_4ef907a.md) and [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](Log_On_to_the_Cloud_Foundry_Environment_Using_the_Cloud_Foundry_Command_Line_Interface_7a37d66.md).

-   Obtain a URL, port, user name, and password for communicating with a service that is not available in the marketplace.




<a name="loiod3c73f11f6a14ba68c3083e026e05e7e__context_eyd_42g_xbb"/>

## Context

For more informaton on user-provided service instances, see [https://docs.cloudfoundry.org/devguide/services/user-provided.html](https://docs.cloudfoundry.org/devguide/services/user-provided.html).



## Procedure

1.  Open a command line and enter the following string to create a user-provided service instance:

    ```
    cf create-user-provided-service SERVICE_INSTANCE [-p CREDENTIALS]
    ```

    Specify the following parameters:

    -   `SERVICE_INSTANCE`: The new name for your service instance.

    -   `CREDENTIALS`: Credentials as JSON




<a name="loiod3c73f11f6a14ba68c3083e026e05e7e__postreq_oly_52g_xbb"/>

## Next Steps

To bind your application to the user-provided service instance, follow the steps described in [Bind Service Instances to Applications Using the Cloud Foundry Command Line Interface](Bind_Service_Instances_to_Applications_Using_the_Cloud_Foundry_Command_Line_Interface_296cd59.md).

**Related Information**  


[Creating Service Instances](Creating_Service_Instances_8221b74.md "Use the SAP BTP cockpit or the Cloud Foundry Command Line Interface to create service instances:")

[Creating Service Keys](Creating_Service_Keys_4514a14.md "You can use service keys to generate credentials to communicate directly with a service instance. Once you configure them for your service, local clients, apps in other spaces, or entities outside your deployment can access your service with these keys.")

[About Services](About_Services_d1d0fc8.md "In the Cloud Foundry environment, you usually enable services by creating a service instance using either the SAP BTP cockpit or the Cloud Foundry command line interface (cf CLI), and binding that instance to your application.")

