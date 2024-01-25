<!-- loio71e6a8e44d45412ebd221b119d90c233 -->

# Service Consumption Model as SOAP Consumer

A Service Consumption Model is the main requirement for consuming a web service in the ABAP environment. To learn how to create a Service Consumption Model with ABAP development tools for Eclipse \(ADT\), see [Creating Service Consumption Model](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/creating-service-consumption-model?version=sap_btp).

> ### Recommendation:  
> We recommend creating a Service Consumption Model in an empty package. Dependent enterprise service objects are reused between different Service Consumption Models in the same package.

For the consumption type web service, you need to upload the WSDL of the service you want to consume. See [Generating Proxies for Remote Web Service](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/generating-proxies-for-remote-web-service?version=sap_btp). Upon successful activation, all the dependent objects are created and displayed in the ADT project explorer, such as:

-   The enterprise service
-   Corresponding dictionary objects
-   The generated ABAP class

For any operation of the web service, a code snippet is displayed in ADT that indicates how to call the service via the corresponding method of the generated class. It is instantiated using a destination object that refers to a communication arrangement and scenario.

An enhanced WSDL document has been introduced that describes how schema/WSDL entities are mapped to ABAP. In the WSDL, any schema element is enhanced by ABAP properties such as ABAP name and type. You can change all these ABAP properties by editing the enhanced WSDL and reactivating the Service Consumption Model. To learn more about the enhanced WSDL, see [Enhanced WSDL Document](enhanced-wsdl-document-3a893d9.md).

> ### Note:  
> The Service Consumption Model is initially saved in an inactive state. Therefore, not all dependent objects are immediately visible in the project explorer. Upon activation, all dependent objects are created according to the enhanced WSDL. They are then visible in the project explorer.

