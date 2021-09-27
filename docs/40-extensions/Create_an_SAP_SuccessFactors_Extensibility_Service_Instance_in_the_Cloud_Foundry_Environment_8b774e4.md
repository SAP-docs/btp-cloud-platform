<!-- loio8b774e4ca8be46a4830a021f727667ed -->

# Create an SAP SuccessFactors Extensibility Service Instance in the Cloud Foundry Environment

To enable the integration of your extension applications with the SAP SuccessFactors system you have registered in the global account in SAP BTP, you first need to create a service instance of the corresponding service.



<a name="loio8b774e4ca8be46a4830a021f727667ed__context_yfs_2sz_mmb"/>

## Context

In the Cloud Foundry environment, you consume services by creating a service instance. Service instances are created using a specific service plan. The services are offered in the Service Marketplace, from which you can create service instances to provision the reserved resources.

To allow applications running on SAP BTP to consume SAP SuccessFactors HXM Suite OData APIs, you need to create a service instance of the SAP SuccessFactors Extensibility service using the *api-access* service plan.

You create the service instance in a space of your subaccount. When creating the service instance, you configure the authentication type for the communication by specifying the required configurations in a JSON format. SAP BTP supports the following authentication scenarios for SAP SuccessFactors:

-   OData access with OAuth 2.0 SAML bearer assertion

    To use this authentication type, you must protect your application. See [Authentication for Applications](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/09f5bd3f346b4ee08b5ca084128e2e81.html).

-   OData access with OAuth 2.0 SAML bearer assertion with technical user


During the creation of the service instance, a destination on a subaccount level with the same name as the service instance name is automatically created in this subaccount. It contains all instance binding properties which are sufficient to establish connection to the SAP SuccessFactors system.

> ### Note:  
> Make sure that you don't already have a destination with the same name as the service instance. If you do, you will not be able to create the service instance.



<a name="loio8b774e4ca8be46a4830a021f727667ed__steps_zfs_2sz_mmb"/>

## Procedure

1.  In the SAP BTP cockpit, navigate to the subaccount in which you want to create a service instance.

2.  In the navigation area, choose *Services* \> *Service Marketplace*.

    All services available to you appear.

3.  To enable the integration with an SAP SuccessFactors system that you have registered in SAP BTP global account, choose *SAP SuccessFactors Extensibility*.

4.  In the *SAP SuccessFactors Extensibility* page, choose *Create Instance*.

5.  In the *New Instance* wizard:

    1.  In the *Service* dropdown list, ensure you have selected the *SAP SuccessFactors Extensibility* service.

    2.  In the *Service Plan* dropdown list select the *api-access* service plan.

    3.  A message ending with a link appears bellow the *Service Plan* field. Click on the link to finish the procedure. You are redirected to another page.

    4.  Choose *New Instance*.

6.  In the *Create Instance* wizard:

    1.  In the *Plan* dropdown list select the *api-access* service plan, and then in the *System Name* dropdown list select the SAP SuccessFactors system that you have registered. Choose *Next*.

    2.  To define the authentication type for the access to the SAP SuccessFactors HXM Suite API, specify a JSON file or specify parameters in the JSON format. Choose *Next*.

        For more information about the structure of the JSON file, see [Authentication Type JSON File](Authentication_Type_JSON_File_543fbd6.md).

    3.  \(Optional\) If you have already deployed an application that you want to bind to the new service instance, choose it from the list. For more information about why you may need to bind an application to the service instance, see the **Next Steps** section in this document. Choose *Next*.

    4.  Enter a name for your instance and choose *Finish*.




<a name="loio8b774e4ca8be46a4830a021f727667ed__result_hyq_ck3_1jb"/>

## Results

After you have created the service instance:

-   The newly created instance appears in the list of instances in the *Instance* panel.

-   An HTTP destination on a subaccount level with the same name as the service instance name is automatically generated in this subaccount.


Alternatively, you can use the Cloud Foundry Command Line Interface \(cf CLI\) to create the service instance using the technical name of the SAP SuccessFactors Extensibilty service which is ***sap-successfactors-extensibility***.

For more information, see [Create Service Instances Using the Cloud Foundry Command Line Interface](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/a872531845d6416b8fa07a8b84875d7e.html).

> ### Note:  
> You can use the cf CLI to troubleshoot if the creation of the service instance fails. To do that, use this command in the cf CLI:
> 
> ```
> cf service <service_instance_name>
> ```



<a name="loio8b774e4ca8be46a4830a021f727667ed__postreq_adx_zn4_lhb"/>

## Next Steps

After creating the *SAP SuccessFactors Extensibility* service instance, you have the following options for configuring the connectivity for your extension application:

-   Bind the instance to an application, and it will be assigned an access URL and credentials to the corresponding API. For more information about binding applications to service instances, see [Binding Service Instances to Applications](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/e98280a71f17413088f8a10838a1e4cc.html?q=binding%20applications).

-   Consume the automatically generated destination.

    To consume the destination, you use the Destination service. You can either consume the Destination service directly, or configure the application router to consume it.

    > ### Note:  
    > The name of the destination is the same as the name of the service instance you have created.

    -   For more information about consuming the destination service using the application router, see [Application Routes and Destinations](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/3cc788ebc00e40a091505c6b3fa485e7.html).

    -   For more information about consuming the destination service directly, see [Consuming the Destination Service \(Cloud Foundry Environment\)](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/7e306250e08340f89d6c103e28840f30.html).

