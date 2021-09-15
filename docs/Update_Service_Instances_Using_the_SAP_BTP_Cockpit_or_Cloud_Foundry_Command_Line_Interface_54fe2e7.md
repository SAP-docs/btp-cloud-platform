<!-- loio54fe2e7250924b12916897727ea78d29 -->

# Update Service Instances Using the SAP BTP Cockpit or Cloud Foundry Command Line Interface

> ### Note:  
> We have redesigned SAP BTP cockpit screens to view and manage service instances.
> 
> For more information about the procedure to update service instances using the cockpit, see [Updating Service Instances](https://help.sap.com/viewer/09cc82baadc542a688176dce601398de/Cloud/en-US/002ae850a32244af85c8405fbcd7d9ab.html).
> 
> To learn how to update service instances using the Cloud Foundry Command Line Interface, continue reading this document.

Use Cloud Foundry Command Line Interface to update service instances:



<a name="loio54fe2e7250924b12916897727ea78d29__prereq_mts_jwl_qbb"/>

## Prerequisites

-   Download and install the cf CLI and log on to Cloud Foundry.

    For more information, see [Download and Install the Cloud Foundry Command Line Interface](Download_and_Install_the_Cloud_Foundry_Command_Line_Interface_4ef907a.md) and [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](Log_On_to_the_Cloud_Foundry_Environment_Using_the_Cloud_Foundry_Command_Line_Interface_7a37d66.md).




## Context

You are using a service instance, for which you want to change the plan or the service-specific configuration.



<a name="loio54fe2e7250924b12916897727ea78d29__steps_c2g_tmq_rgb"/>

## Procedure

1.  \(Optional\) Open a command line and enter the following string to list all services in your space:

    ```
    cf services
    ```

2.  \(Optional\) Enter the following string to list the details of your service:

    ```
    cf service SERVICE_INSTANCE
    ```

3.  Run the following command to update your service instance:

    ```
    cf update-service SERVICE_INSTANCE [-p NEW_PLAN] [-c PARAMETERS_AS_JSON] [-t TAGS]
    ```

    Specify the following parameters:

    -   `SERVICE_INSTANCE`: The name of your service instance as shown when executing `cf services`.


