<!-- loio8b6723b265d54c13866fbade4a7a087b -->

# Set Up SOAP Communication

Developers can consume synchronous SOAP-based Web services for outbound communication from the ABAP environment.



<a name="loio8b6723b265d54c13866fbade4a7a087b__section_ns2_mfr_hlb"/>

## Overview

A Service Consumption Model is the main requirement for consuming a Web service in the ABAP environment. To learn how to create a Service Consumption Model with ABAP Development Tools \(ADT\), see [Creating Service Consumption Model](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/96132822b3554016b653d3601bb9ff1a.html).

> ### Recommendation:  
> We recommend creating a Service Consumption Model in an empty package. Dependent enterprise service objects are reused between different Service Consumption Models in the same package.

For the consumption type Web service, you need to provide the WSDL of the service you want to consume via the local file system. See [Generating Proxies for Remote Web Service](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/3b9c145adad147058177cec27cef1f44.html). Upon successful activation, all the dependent objects are created and displayed in the ADT project explorer, such as:

-   The enterprise service
-   Corresponding dictionary objects
-   The generated ABAP class

For any operation of the Web service, a code snippet is displayed in ADT that indicates how to call the service via the corresponding method of the generated class. It is instantiated using a destination object that contains information such as the endpoint URL and authentication method. To learn how to create a SOAP destination object, see [Enable SOAP Communication in Your ABAP Code](enable-soap-communication-in-your-abap-code-6ab460e.md).

An enhanced WSDL document has been introduced that describes how schema/WSDL entities are mapped to ABAP. In the WSDL, any schema element is enhanced by ABAP properties such as ABAP name and type. You can change all these ABAP properties by editing the enhanced WSDL and reactivating the Service Consumption Model. To learn more about the enhanced WSDL, see [Enhanced WSDL Document](enhanced-wsdl-document-3a893d9.md).

> ### Note:  
> The Service Consumption Model is initially saved in an inactive state. Therefore, not all dependent objects are immediately visible in the project explorer. Upon activation, all dependent objects are created according to the enhanced WSDL. They are then visible in the project explorer.



<a name="loio8b6723b265d54c13866fbade4a7a087b__section_mzr_21s_flb"/>

## Feature Scope

SOAP-based Web services cover the following features:

-   Synchronous outbound Web service communication
-   Self-contained WSDL \(single file with no import or include statements\)
-   gCTS Support \(not relevant for Developer Extensibility, see [Developer Extensibility](https://help.sap.com/viewer/6aa39f1ac05441e5a23f484f31e477e7/latest/en-US/e1059ff581854a699f15734049f14293.html)\)
-   Web services SOAP header protocol to add custom XML elements to the SOAP request header, see [Add Custom SOAP Header Elements](add-custom-soap-header-elements-3dadfa9.md)

To enable SOAP communication, there are three different approaches:

-   Communication arrangement
-   Destination service \(not relevant for Developer Extensibility, see [Developer Extensibility](https://help.sap.com/viewer/6aa39f1ac05441e5a23f484f31e477e7/latest/en-US/e1059ff581854a699f15734049f14293.html)\)
-   URL \(recommended for test purposes only\)

See [Enable SOAP Communication in Your ABAP Code](enable-soap-communication-in-your-abap-code-6ab460e.md) for more Information.

The following authentication methods are supported.

**Internet**:

-   Basic Authentication
-   Client Certificate Authentication
-   OAuth 2.0 Client Credentials Grant \(not for static configuration\)

**On-Premise**:

-   Basic Authentication
-   Client Certificate Authentication
-   Principal Propagation \(not for static configuration in communication management and in code\)



<a name="loio8b6723b265d54c13866fbade4a7a087b__section_dly_cbs_flb"/>

## Comparison Between On-Premise and Cloud

-   The Service Consumption Model takes on the role of the service consumer.
-   The creation of a Service Consumption Model in ADT is similar to the creation of a service consumer from an external WSDL within the Web service wizard in SAP GUI.
-   The enhanced WSDL document is like the design time WSDL in the Proxy Editor in SAP GUI enhanced by ABAP properties.
-   The enhanced WSDL document replaces the function to change ABAP types in the Proxy Editor in SAP GUI.

**Related Information**  


[Enable SOAP Communication in Your ABAP Code](enable-soap-communication-in-your-abap-code-6ab460e.md "SOAP-based Web service outbound communication within the ABAP environment is enabled by using SOAP destination objects.")

