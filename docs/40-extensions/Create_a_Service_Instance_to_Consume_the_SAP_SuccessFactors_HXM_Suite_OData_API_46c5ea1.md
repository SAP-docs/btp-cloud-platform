<!-- loio46c5ea17eff94bc6949857e588797273 -->

# Create a Service Instance to Consume the SAP SuccessFactors HXM Suite OData API

To enable the integration of your extension applications with the SAP SuccessFactors system you have registered in the global account in SAP BTP, you first need to create a service instance of the corresponding service.



## Context

In both Cloud Foundry and Kyma environment, you consume services by creating a service instance. Service instances are created using a specific service plan.

To allow applications running on SAP BTP to consume SAP SuccessFactors HXM Suite OData APIs, you need to create a service instance of the SAP SuccessFactors Extensibility service using the *api-access* service plan.

You create the service instance in your subaccount with the respective environment enabled. When creating the service instance, you configure the authentication type for the communication by specifying the required configurations in a JSON format. SAP BTP supports the following authentication scenarios for SAP SuccessFactors:

-   OData access with OAuth 2.0 SAML bearer assertion

    To use this authentication type, you must protect your application. See [Authentication for Applications](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/09f5bd3f346b4ee08b5ca084128e2e81.html).

-   OData access with OAuth 2.0 SAML bearer assertion with technical user


The process for creating a service instance depends on the environment you are using:

-   For Cloud Foundry environment, see [Create an SAP SuccessFactors Extensibility Service Instance in the Cloud Foundry Environment](Create_an_SAP_SuccessFactors_Extensibility_Service_Instance_in_the_Cloud_Foundry_Environment_8b774e4.md).

-   For Kyma environment, see [Create an SAP SuccessFactors Extensibility Service Instance in the Kyma Environment](Create_an_SAP_SuccessFactors_Extensibility_Service_Instance_in_the_Kyma_Environment_f371f81.md).


-   **[Create an SAP SuccessFactors Extensibility Service Instance in the Cloud Foundry Environment](Create_an_SAP_SuccessFactors_Extensibility_Service_Instance_in_the_Cloud_Foundry_Environment_8b774e4.md "To enable the integration of your extension applications with the SAP SuccessFactors
		system you have registered in the global account in SAP BTP, you first need to
		create a service instance of the corresponding service. ")**  
To enable the integration of your extension applications with the SAP SuccessFactors system you have registered in the global account in SAP BTP, you first need to create a service instance of the corresponding service.
-   **[Create an SAP SuccessFactors Extensibility Service Instance in the Kyma Environment](Create_an_SAP_SuccessFactors_Extensibility_Service_Instance_in_the_Kyma_Environment_f371f81.md "")**  

-   **[Authentication Type JSON File](Authentication_Type_JSON_File_543fbd6.md "Use the authentication type JSON descriptor to define the authentication type for the
		inbound connectivity to the SAP SuccessFactors HXM Suite OData API.")**  
Use the authentication type JSON descriptor to define the authentication type for the inbound connectivity to the SAP SuccessFactors HXM Suite OData API.

