<!-- loio6ab460e1a59e4890b8faa3fcc35f3343 -->

# Enable SOAP Communication in Your ABAP Code

SOAP-based web service outbound communication within the ABAP environment is enabled by using SOAP destination objects.



<a name="loio6ab460e1a59e4890b8faa3fcc35f3343__section_tbk_413_zkb"/>

## Context

A SOAP destination is used to instantiate the web service consumer proxy in the coding. You have the following options to create a SOAP destination object:

-   Communication arrangement approach: By specifying a destination based on a communication arrangement. See [Communication Arrangement](communication-management-5b8ff39.md#loio201de48e2f57404e9222181b019eff14).
-   Destination service approach: By using a destination that is maintained in a destination service that resides in the Cloud Foundry environment \(not relevant for Developer Extensibility, see [Developer Extensibility](https://help.sap.com/viewer/6aa39f1ac05441e5a23f484f31e477e7/latest/en-US/e1059ff581854a699f15734049f14293.html)\).
-   URL approach: By using a plain URL and setter methods to provide the needed configuration directly in the coding.

All of the listed approaches above require an existing consumption model.

> ### Note:  
> In on-premise systems, SOAP services are configured by logical ports, which are maintained in transaction `SOAMANAGER`. In the ABAP environment, the concept of logical ports has been replaced by the concept of SOAP destination objects.

A Service Consumption Model is the main requirement for consuming a web service in the ABAP environment. To learn how to create a Service Consumption Model with ABAP Development Tools \(ADT\), see [Creating Service Consumption Model](https://help.sap.com/docs/BTP/5371047f1273405bb46725a417f95433/96132822b3554016b653d3601bb9ff1a.html?version=Cloud&q=creating%20service%20consumption).

> ### Recommendation:  
> We recommend creating a Service Consumption Model in an empty package. Dependent enterprise service objects are reused between different Service Consumption Models in the same package.

For the consumption type web service, you need to provide the WSDL of the service you want to consume via the local file system. See [Generating Proxies for Remote Web Service](https://help.sap.com/docs/btp/sap-abap-development-user-guide/generating-proxies-for-remote-web-service?version=Cloud). Upon successful activation, all the dependent objects are created and displayed in the ADT project explorer, such as:

-   The enterprise service
-   Corresponding dictionary objects
-   The generated ABAP class

For any operation of the web service, a code snippet is displayed in ADT that indicates how to call the service via the corresponding method of the generated class. It is instantiated using a destination object that contains information such as the endpoint URL and authentication method. To learn how to create a SOAP destination object, see [Enable SOAP Communication in Your ABAP Code](enable-soap-communication-in-your-abap-code-6ab460e.md).

An enhanced WSDL document has been introduced that describes how schema/WSDL entities are mapped to ABAP. In the WSDL, any schema element is enhanced by ABAP properties such as ABAP name and type. You can change all these ABAP properties by editing the enhanced WSDL and reactivating the Service Consumption Model. To learn more about the enhanced WSDL, see [Enhanced WSDL Document](enhanced-wsdl-document-3a893d9.md).

> ### Note:  
> The Service Consumption Model is initially saved in an inactive state. Therefore, not all dependent objects are immediately visible in the project explorer. Upon activation, all dependent objects are created according to the enhanced WSDL. They are then visible in the project explorer.

**Related Information**  


[SOAP Communication via Communication Arrangements](soap-communication-via-communication-arrangements-2133e15.md "")

[SOAP Communication via Destination Service \(Deprecated\)](soap-communication-via-destination-service-deprecated-72bb6b5.md)

[SOAP Communication via URL](soap-communication-via-url-7e22ed9.md)

