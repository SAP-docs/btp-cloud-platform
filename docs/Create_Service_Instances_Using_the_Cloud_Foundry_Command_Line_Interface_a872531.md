<!-- loioa872531845d6416b8fa07a8b84875d7e -->

# Create Service Instances Using the Cloud Foundry Command Line Interface

You can use the Cloud Foundry Command Line Interface \(cf CLI\) to create service instances.



<a name="loioa872531845d6416b8fa07a8b84875d7e__prereq_mts_jwl_qbb"/>

## Prerequisites

-   Download and install the cf CLI and log on to Cloud Foundry.

    For more information, see [Download and Install the Cloud Foundry Command Line Interface](Download_and_Install_the_Cloud_Foundry_Command_Line_Interface_4ef907a.md) and [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](Log_On_to_the_Cloud_Foundry_Environment_Using_the_Cloud_Foundry_Command_Line_Interface_7a37d66.md).

-   If you are working in an enterprise account, you need to add quotas to the services you purchased in your subaccount before they appear in the service marketplace. Otherwise, only default free-of-charge services are listed. Quotas are automatically assigned to the resources available in trial accounts.

    For more information, see [Configure Entitlements and Quotas for Subaccounts](Configure_Entitlements_and_Quotas_for_Subaccounts_5ba357b.md).




## Procedure

1.  \(Optional\) Open a command line and enter the following string to list all services and service plans that are available in your org:

    ```
    cf marketplace
    ```

2.  Run the following command to create a service instance:

    ```
    cf create-service SERVICE PLAN SERVICE_INSTANCE
    ```

    Specify the following parameters:

    -   `SERVICE`: The name of the service you want to create an instance of.

    -   `PLAN`: The name of the service plan you want to use.

    -   `SERVICE_INSTANCE`: The new name for your service instance. Use only alphanumeric characters, hyphens, and underscores.


**Related Information**  


[Binding Service Instances to Applications](Binding_Service_Instances_to_Applications_e98280a.md "Use the SAP BTP cockpit or the Cloud Foundry Command Line Interface to bind service instances to applications:")

[Creating User-Provided Service Instances](Creating_User-Provided_Service_Instances_a44355e.md "User-provided service instances enable you to use services that are not available in the marketplace with your applications running in the Cloud Foundry environment.")

[About Services](About_Services_d1d0fc8.md "In the Cloud Foundry environment, you usually enable services by creating a service instance using either the SAP BTP cockpit or the Cloud Foundry command line interface (cf CLI), and binding that instance to your application.")

