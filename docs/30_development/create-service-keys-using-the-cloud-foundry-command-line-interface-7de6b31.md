<!-- loio7de6b314b62748b9b59df5fc09dbe8fb -->

# Create Service Keys Using the Cloud Foundry Command Line Interface

Use the Cloud Foundry Command Line Interface to create a service key.



<a name="loio7de6b314b62748b9b59df5fc09dbe8fb__prereq_e2l_pld_wbb"/>

## Prerequisites

-   Download and install the cf CLI and log on to Cloud Foundry. For more information, see [Download and Install the Cloud Foundry Command Line Interface](../50_administration_and_ops/download-and-install-the-cloud-foundry-command-line-interface-4ef907a.md) and [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](../50_administration_and_ops/log-on-to-the-cloud-foundry-environment-using-the-cloud-foundry-command-line-interface-7a37d66.md).

-   Create a service instance. For more information, see [Create Service Instances Using the Cloud Foundry Command Line Interface](create-service-instances-using-the-cloud-foundry-command-line-interface-a872531.md).




## Procedure

1.  Run the following command to create a service key:

    ```
    cf create-service-key SERVICE_INSTANCE SERVICE_KEY [-c PARAMETERS_AS_JSON]
    ```

    Specify the following parameters:

    -   `SERVICE_INSTANCE`: Name of the service instance.

    -   `SERVICE_KEY`: Name for the service key.

    -   `-c`: \(Optional\) Provide service-specific configuration parameters either in a valid JSON object in-line or in a parameters file. This file reference can be an absolute or relative path to a file.





<a name="loio7de6b314b62748b9b59df5fc09dbe8fb__result_alz_3md_wbb"/>

## Results

Local clients, apps in other spaces, or entities outside your deployment can now access your service instance with this key.

**Related Information**  


[Creating Service Instances](creating-service-instances-8221b74.md "Use the SAP BTP cockpit or the Cloud Foundry Command Line Interface to create service instances:")

[Binding Service Instances to Applications](binding-service-instances-to-applications-e98280a.md "Use the SAP BTP cockpit or the Cloud Foundry Command Line Interface to bind service instances to applications:")

[About Services](about-services-d1d0fc8.md "In the Cloud Foundry environment, you usually enable services by creating a service instance using either the SAP BTP cockpit or the Cloud Foundry command line interface (cf CLI), and binding that instance to your application.")

