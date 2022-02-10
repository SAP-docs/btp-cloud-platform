<!-- loio302f2a33833a45a98ac531cc328d14e8 -->

# Delete Service Instances Using the Cloud Foundry Command Line Interface

You can use the Cloud Foundry Command Line Interface \(cf CLI\) to delete service instances.



<a name="loio302f2a33833a45a98ac531cc328d14e8__prereq_mts_jwl_qbb"/>

## Prerequisites

-   Download and install the cf CLI and log on to Cloud Foundry.

    For more information, see [Download and Install the Cloud Foundry Command Line Interface](../50-administration-and-ops/download-and-install-the-cloud-foundry-command-line-interface-4ef907a.md) and [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](../50-administration-and-ops/log-on-to-the-cloud-foundry-environment-using-the-cloud-foundry-command-line-interface-7a37d66.md).




## Procedure

1.  Open a command line and log in.

    ```
    cf l -a <API endpoint>
    ```

2.  \(Optional\) List all services and bound apps in your org:

    ```
    cf services
    ```

3.  Unbind the service from any application.

    ```
    cf unbind-service APP_NAME SERVICE_INSTANCE
    ```

4.  \(Optional\) List all service keys for your service instance.

    ```
    cf service-keys SERVICE_INSTANCE
    ```

5.  Delete any service key from the service instance.

    ```
    cf delete-service-key SERVICE_INSTANCE SERVICE_KEY
    ```

6.  Run the following command to delete a service instance:

    ```
    cf delete-service SERVICE_INSTANCE
    ```

    Specify the following parameters:

    -   `SERVICE_INSTANCE`: The name of your service instance.

    -   `APP_NAME`: The name of an application your service instance is connected to.

    -   `SERVICE_KEY`: The name of the service key of your service instance.



**Related Information**  


[About Services](about-services-d1d0fc8.md "In the Cloud Foundry environment, you usually enable services by creating a service instance using either the SAP BTP cockpit or the Cloud Foundry command line interface (cf CLI), and binding that instance to your application.")

[Deleting Service Instances](deleting-service-instances-aa0d25a.md "Use the SAP BTP cockpit or the Cloud Foundry Command Line Interface to delete service instances:")

