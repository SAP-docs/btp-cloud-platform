<!-- loioa735641b4c944953a3aedc887b2f250c -->

# Create a Service Instance to Consume the SAP S/4HANA Cloud APIs

To enable the integration of your extension applications with the SAP S/4HANA Cloud system you have registered in the SAP BTP global account, and to configure the communication flow, you create a service instance of the SAP S/4HANA Cloud Extensibility service.



<a name="loioa735641b4c944953a3aedc887b2f250c__prereq_q5t_m4c_1jb"/>

## Prerequisites

For a communication flow with SAML Bearer Assertion authentication, you must:

-   Configure Single-Sign On \(SSO\). See [Single Sign-On Configuration](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/8d3c376e573946258dad098b54fba480.html).

-   Protect your application. See [Configure Application Authentication](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/0926369928ce4e89ac22c847e4a51662.html).




## Context

In both Cloud Foundry and Kyma environments, you consume services by creating a service instance. Service instances are created using a specific service plan.

To allow applications running on SAP BTP to consume SAP S/4HANA Cloud APIs, you need to create a service instance of the SAP S/4HANA Cloud Extensibility service using the *api-access* service plan.

> ### Note:  
> These service plans have been deprecated:
> 
> -   *sap\_com\_0109*
> 
> -   *sap\_com\_0009*
> 
> -   *sap\_com\_0008*
> 
> 
> However, you can still enable these communication scenarios using the *api-access* service plan:
> 
> -   *Sales Order Integration \(SAP\_COM\_0109\)*: allows you to integrate your extension applications with sales order processing in SAP S/4HANA Cloud. For more information, see [https://api.sap.com/api/API\_SALES\_ORDER\_SRV/overview](https://api.sap.com/api/API_SALES_ORDER_SRV/overview).
> 
> -   *Product Integration \(SAP\_COM\_0009\)*: enables you to replicate product master data from client system to SAP S/4HANA system. For more information, see [https://api.sap.com/api/PRODUCTMDMBULKREPLICATEREQUEST/overview](https://api.sap.com/api/PRODUCTMDMBULKREPLICATEREQUEST/overview).
> 
> -   *Business Partner, Customer and Supplier Integration \(SAP\_COM\_0008\)*: allows you to consume the Business Partner API which enables you to create, read, update, and delete master data related to Business Partners, Suppliers, and Customers in an SAP S/4HANA system. For more information, see [https://api.sap.com/api/API\_BUSINESS\_PARTNER/overview](https://api.sap.com/api/API_BUSINESS_PARTNER/overview).
> 
> 
> For a sample JSON for these communication scenarios, see [Communication Arrangement JSON/YAML File - Properties](communication-arrangement-json-yaml-file-properties-553a4c6.md).

The *api-access* service plan define the access to the corresponding SAP S/4HANA Cloud APIs. It supports both predefined and custom communication scenarios for consuming the SAP S/4HANA Cloud APIs and integrating your extension applications. See:

-   [Supported Service Plans for SAP S/4HANA Cloud](supported-service-plans-for-sap-s-4hana-cloud-925c00a.md)

-   [Custom Communication Scenarios](https://help.sap.com/viewer/0f69f8fb28ac4bf48d2b57b9637e81fa/latest/en-US/41b6543c04864dc298123c3ef5efd7a3.html?q=communication%20scenario)


You create the service instance in your subaccount with the respective environment enabled. When creating the service instance, you configure the connectivity by specifying the required configurations in a JSON format. The following authentication scenarios are supported for the communication flow between the extension application and SAP S/4HANA Cloud:

-   Basic Authentication \(inbound and outbound connections\)

-   OAuth 2.0 Client Credentials \(outbound connections\)

-   OAuth 2.0 SAML Bearer Assertion \(inbound connections\)

    To communicate with SAP S/4HANA Cloud the extension application can use Principal Propagation which is done using OAuth 2.0 SAML Bearer Assertion flows. Principal Propagation means you forward the identity of the logged-in cloud users when accessing or updating data in the SAP S/4HANA Cloud system.

    This is useful in scenarios where you need to have restricted data access based on the logged-in user from your extension. Or, you want to ensure only users with the right permissions are able to update the system via extensions deployed in SAP BTP.

    To use this authentication scenario, you first need to configure single-sign on \(SSO\) with the Identity Authentication service and protect your application. See [Single Sign-On Configuration](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/8d3c376e573946258dad098b54fba480.html).

-   Client Certificate Authentication \(inbound and outbound connections\)

-   OAuth2mTLS \(outbound connections\)


Depending on whether you are using Cloud Foundry or Kyma environment, you have to follow different steps to create an SAP S/4HANA Cloud Extensibility service instance:

-   [Create an SAP S/4HANA Cloud Extensibility Service Instance in the Cloud Foundry Environment](create-an-sap-s-4hana-cloud-extensibility-service-instance-in-the-cloud-foundry-environme-d866cf6.md)

-   [Create an SAP S/4HANA Cloud Extensibility Service Instance in the Kyma Environment](create-an-sap-s-4hana-cloud-extensibility-service-instance-in-the-kyma-environment-32bd423.md)


**Related Information**  


[Communication Arrangement JSON/YAML File - Properties](communication-arrangement-json-yaml-file-properties-553a4c6.md "Learn how to construct a JSON or YAML file for the SAP S/4HANA Cloud APIs, including parameters such as system name, communication arrangement, authentication type, communication system, outbound services, and additional properties. It also provides guidelines and rules for each property.")

