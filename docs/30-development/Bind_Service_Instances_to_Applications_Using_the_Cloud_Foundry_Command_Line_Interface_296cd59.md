<!-- loio296cd5945fd84d7d91061b2b2bcacb93 -->

# Bind Service Instances to Applications Using the Cloud Foundry Command Line Interface

You can bind service instances to applications using the Cloud Foundry Command Line Interface \(cf CLI\).



<a name="loio296cd5945fd84d7d91061b2b2bcacb93__prereq_wqc_ksm_qbb"/>

## Prerequisites

-   Download and install the cf CLI and log on to Cloud Foundry. For more information, see [Download and Install the Cloud Foundry Command Line Interface](../50-administration-and-ops/Download_and_Install_the_Cloud_Foundry_Command_Line_Interface_4ef907a.md) and [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](../50-administration-and-ops/Log_On_to_the_Cloud_Foundry_Environment_Using_the_Cloud_Foundry_Command_Line_Interface_7a37d66.md).

-   Deploy an application in the same space in which you plan to create the service instance. For more information, see [Deploy Business Applications in the Cloud Foundry Environment](Deploy_Business_Applications_in_the_Cloud_Foundry_Environment_4946ea5.md).

-   Create a service instance. For more information, see [Create Service Instances Using the Cloud Foundry Command Line Interface](Create_Service_Instances_Using_the_Cloud_Foundry_Command_Line_Interface_a872531.md).




## Procedure

1.  Open a command line and enter the following string:

    ```
    cf bind-service APP-NAME SERVICE_INSTANCE {-c PARAMETERS_AS_JSON}
    ```

    Specify the following parameters:

    -   `APP_NAME`: Name of the application.

    -   `SERVICE_INSTANCE`: Name of the service instance.

    -   `-c`: \(Optional\) Provide service-specific configuration parameters in a valid JSON object.



**Related Information**  


[Creating Service Instances](Creating_Service_Instances_8221b74.md "Use the SAP BTP cockpit or the Cloud Foundry Command Line Interface to create service instances:")

[Creating Service Keys](Creating_Service_Keys_4514a14.md "You can use service keys to generate credentials to communicate directly with a service instance. Once you configure them for your service, local clients, apps in other spaces, or entities outside your deployment can access your service with these keys.")

[About Services](About_Services_d1d0fc8.md "In the Cloud Foundry environment, you usually enable services by creating a service instance using either the SAP BTP cockpit or the Cloud Foundry command line interface (cf CLI), and binding that instance to your application.")

