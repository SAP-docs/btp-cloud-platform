<!-- loiod866cf6d012e450d9643356d031067eb -->

# Create an SAP S/4HANA Cloud Extensibility Service Instance in the Cloud Foundry Environment



<a name="loiod866cf6d012e450d9643356d031067eb__prereq_fms_2dv_5lb"/>

## Prerequisites

-   Before creating an SAP S/4HANA Cloud Extensibility service instance in the Cloud Foundry environment, see [Create a Service Instance to Consume the SAP S/4HANA Cloud APIs](create-a-service-instance-to-consume-the-sap-s-4hana-cloud-apis-a735641.md).

-   Have enabled Cloud Foundry environment for your subaccount. See [Enable Environment or Create Environment Instance](../50-administration-and-ops/enable-environment-or-create-environment-instance-78c14b6.md).

-   Have registered an SAP S/4HANA Cloud system. See[Register an SAP S/4HANA Cloud System in a Global Account in SAP BTP](register-an-sap-s-4hana-cloud-system-in-a-global-account-in-sap-btp-28171b6.md).

-   Have configured the entitlements to the SAP S/4HANA Cloud Extensibility service. See [Configure the Entitlements for the SAP S/4HANA Cloud Extensibility Service](configure-the-entitlements-for-the-sap-s-4hana-cloud-extensibility-service-65ad330.md).




<a name="loiod866cf6d012e450d9643356d031067eb__context_b4x_ncv_5lb"/>

## Context

To consume the SAP S/4HANA Cloud APIs \(inbound connection\) or consume APIs exposed by the extension application from SAP S/4HANA Cloud \(outbound connection\), you create an SAP S/4HANA Cloud Extensibility service instance. When creating the service instance, you configure the communication arrangement and the authentication type for the connection.

For communication arrangements with inbound connections, a destination on a subaccount level with the same name as the service instance name is automatically created in this subaccount. It contains all instance binding properties which are sufficient to establish connection to the SAP S/4HANA Cloud system.

> ### Note:  
> Make sure that you don't already have a destination with the same name as the service instance. If you do, you will not be able to create the service instance.

> ### Note:  
> Multitenant applications, that this subaccount is subscribed to, can access the destination and connect to the SAP S/4HANA Cloud system without binding to the created service instance.
> 
> See [Developing Multitenant Business Applications in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/5e8a2b74e4f2442b8257c850ed912f48.html).



<a name="loiod866cf6d012e450d9643356d031067eb__steps_c4x_ncv_5lb"/>

## Procedure

1.  In the SAP BTP cockpit, navigate to the subaccount in which you want to create a service instance.

2.  In the navigation area, choose *Services* \> *Service Marketplace*.

    All services available to you appear.

3.  To enable the integration with an SAP S/4HANA Cloud system that you have registered in SAP BTP global account, choose *SAP S/4HANA Cloud Extensibility*.

4.  In the *SAP S/4HANA Cloud Extensibility* page, choose *Create*.

5.  In the *New Instance or Subscription* wizard:

    1.  In the *Service* dropdown list, ensure you have selected the *SAP S/4HANA Cloud Extensibility* service.

    2.  In the *Plan* dropdown list, select the *api-access* service plan.

    3.  In the *Runtime Environment* dropdown list, select *Cloud Foundry*.

    4.  In the *Space* dropdown list, select your space. If you haven't create a space yet, you can do it at this point.

    5.  In the *System Name* dropdown list, select the SAP S/4HANA Cloud system you have registered.

    6.  In the *Instance Name* field, enter a name for your instance. Choose *Next*.

    7.  To define the communication arrangement and the authentication type for the API access, specify a JSON file or specify parameters in the JSON format. If you decide to define the communication arrangement and the authentication type later on, you have to delete this service instance and create it again. Choose *Next*.

        For more information about the structure of the JSON file, see [Communication Arrangement JSON/YAML File - Properties](communication-arrangement-json-yaml-file-properties-553a4c6.md).

    8.  Choose *Create*.


    After you have created the service instance:

    -   The newly created instance appears in the list of instances in the *Instance and Subscriptions* page.

    -   An HTTP destination on a subaccount level with the same name as the service instance name is automatically generated in this subaccount.


    Alternatively, you can use the Cloud Foundry Command Line Interface \(cf CLI\) to create the service instance using the technical name of the SAP S/4HANA Cloud Extensibility service which is ***s4-hana-cloud***.

    For more information, see [Create Service Instances Using the Cloud Foundry Command Line Interface](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/a872531845d6416b8fa07a8b84875d7e.html).

    > ### Note:  
    > You can use the cf CLI to troubleshoot if the creation of the service instance fails. To do that, use this command in the cf CLI:
    > 
    > ```
    > cf service <service_instance_name>
    > ```




<a name="loiod866cf6d012e450d9643356d031067eb__postreq_adx_zn4_lhb"/>

## Next Steps

After you have created the service instance:

-   The newly created instance appears in the list of instances in the *Instance and Subscriptions* page.

-   An HTTP destination on a subaccount level with the same name as the service instance name is automatically generated in this subaccount.


Alternatively, you can use the Cloud Foundry Command Line Interface \(cf CLI\) to create the service instance using the technical name of the SAP S/4HANA Cloud Extensibility service which is ***s4-hana-cloud***.

For more information, see [Create Service Instances Using the Cloud Foundry Command Line Interface](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/a872531845d6416b8fa07a8b84875d7e.html).

> ### Note:  
> You can use the cf CLI to troubleshoot if the creation of the service instance fails. To do that, use this command in the cf CLI:
> 
> ```
> cf service <service_instance_name>
> ```

After creating the *SAP S/4HANA Cloud Extensibility* service instance, you have the following options for configuring the connectivity for your extension application:

-   Bind the instance to an application, and it will be assigned an access URL and credentials to the corresponding API. For more information about binding applications to service instances, see [Binding Service Instances to Applications](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/e98280a71f17413088f8a10838a1e4cc.html?q=binding%20applications) in the SAP BTP documentation.

-   Consume the automatically generated destination.

    To consume the destination, you use the destination service. You can either consume the Destination service directly, or configure the application router to consume it.

    > ### Note:  
    > The name of the destination is the same as the name of the service instance you have created.

    -   For more information about consuming the destination service using the application router, see [Application Routes and Destinations](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/3cc788ebc00e40a091505c6b3fa485e7.html).

    -   For more information about consuming the destination service directly, see [Consuming the Destination Service \(Cloud Foundry Environment\)](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/7e306250e08340f89d6c103e28840f30.html).



