<!-- loio296cd5945fd84d7d91061b2b2bcacb93 -->

# Bind Service Instances to Applications Using the Cloud Foundry Command Line Interface

You can bind service instances to applications using the Cloud Foundry Command Line Interface \(cf CLI\).



<a name="loio296cd5945fd84d7d91061b2b2bcacb93__prereq_wqc_ksm_qbb"/>

## Prerequisites

-   Download and install the cf CLI and log on to Cloud Foundry. For more information, see [Download and Install the Cloud Foundry Command Line Interface](../50_administration_and_ops/download-and-install-the-cloud-foundry-command-line-interface-4ef907a.md) and [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](../50_administration_and_ops/log-on-to-the-cloud-foundry-environment-using-the-cloud-foundry-command-line-interface-7a37d66.md).

-   Deploy an application in the same space in which you plan to create the service instance. For more information, see [Deploy Business Applications in the Cloud Foundry Environment](deploy-business-applications-in-the-cloud-foundry-environment-4946ea5.md).

-   Create a service instance. For more information, see [Create Service Instances Using the Cloud Foundry Command Line Interface](create-service-instances-using-the-cloud-foundry-command-line-interface-a872531.md).




## Procedure

1.  Open a command line and enter the following string:

    ```
    cf bind-service APP-NAME SERVICE_INSTANCE [-c PARAMETERS_AS_JSON]
    ```

    Specify the following parameters:

    -   `APP_NAME`: Name of the application.

    -   `SERVICE_INSTANCE`: Name of the service instance.

    -   `-c`: \(Optional\) Provide service-specific configuration parameters either in a valid JSON object in-line or in a parameters file. This file reference can be an absolute or relative path to a file.



**Related Information**  


[Creating Service Instances](creating-service-instances-8221b74.md "Use the SAP BTP cockpit or the Cloud Foundry Command Line Interface to create service instances:")

[Creating Service Keys](creating-service-keys-4514a14.md "You can use service keys to generate credentials to communicate directly with a service instance. Once you configure them for your service, local clients, apps in other spaces, or entities outside your deployment can access your service with these keys.")

[About Services](about-services-d1d0fc8.md "In the Cloud Foundry environment, you usually enable services by creating a service instance using either the SAP BTP cockpit or the Cloud Foundry command line interface (cf CLI), and binding that instance to your application.")

