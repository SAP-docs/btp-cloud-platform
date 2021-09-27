<!-- loio8b6723b265d54c13866fbade4a7a087b -->

# Generate a Proxy to Consume SOAP-Based Web Services

Consuming synchronous SOAP-based web services for outbound communication from the ABAP environment.



<a name="loio8b6723b265d54c13866fbade4a7a087b__section_ns2_mfr_hlb"/>

## Overview

A service consumption model is the main requirement for consuming a web service in the ABAP environment. To learn how to create a service consumption model with ABAP Development Tools \(ADT\), see [Creating Service Consumption Model](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/96132822b3554016b653d3601bb9ff1a.html).

For the consumption type web service, other than for example OData, you need to provide the WSDL of the service you want to consume via the local file system. See [Generating Proxies for Remote Web Service](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/3b9c145adad147058177cec27cef1f44.html). Upon successful activation, all the dependent objects, such as the enterprise service, corresponding dictionary objects, and the generated ABAP class, are created and displayed in the ADT project explorer.

For any operation of the web service, a code snippet is displayed in ADT that indicates how to call the service via the respective method of the generated class. It is instantiated via a destination object containing information such as the endpoint URL and authentication method. You can either create such a destination object in your code or retrieve it from a destination service.

> ### Recommendation:  
> We recommend retrieving your destination object from a destination service if a destination service is available for your system. See [SOAP Communication via Destination Service](SOAP_Communication_via_Destination_Service_72bb6b5.md).

The metadata of your service consumption model display the so-called enhanced Web Services Description Language \(WSDL\). It describes how schema/WSDL entities are mapped to ABAP, and are enhanced by their ABAP names and types in particular. You can change all of these ABAP properties by editing the enhanced WSDL and re-activating the service consumption model. To learn more about the enhanced WSDL, see [Enhanced Web Services Description Language \(WSDL\)](Enhanced_Web_Services_Description_Language_(WSDL)_3a893d9.md).



<a name="loio8b6723b265d54c13866fbade4a7a087b__section_mzr_21s_flb"/>

## Feature Scope

-   Synchronous outbound web service communication
-   Self-contained WSDLs \(no import statements\)
-   Destination configuration options for the following authentication methods:
    -   No authentication
    -   Basic authentication
    -   ClientCertificateAuthentication
-   gCTS support
-   Support for proxy type ***Internet*** and ***OnPremise***



<a name="loio8b6723b265d54c13866fbade4a7a087b__section_lwk_jjr_hlb"/>

## What You Need to Know



> ### Recommendation:  
> We recommend creating a service consumption model in an empty package. Dependent enterprise service objects are reused between different service consumption models in the same package.

> ### Note:  
> You can view dictionary objects and the generated ABAP class in the project explorer for an inactive service consumption model, but you can only create them upon activation of the service consumption model.



<a name="loio8b6723b265d54c13866fbade4a7a087b__section_dly_cbs_flb"/>

## Comparison Between On Premise and Cloud

-   The service consumption model takes over the role of the service consumer
-   The creation of a service consumption model in ADT is very similar to the creation of a service consumer from an external WSDL within the web service wizard in SAP GUI
-   The idea of persisted logical ports shifted towards a transient concept. The corresponding data, such as the endpoint URL and authentication method, now reside in a destination, that can be retrieved from a destination service
-   The enhanced WSDL is similar to the Design Time WSDL in the Proxy Editor in SAP GUI enhanced by ABAP properties
-   The enhanced WSDL replaces the Proxy Editor in SAP GUI

-   **[Enhanced Web Services Description Language \(WSDL\)](Enhanced_Web_Services_Description_Language_(WSDL)_3a893d9.md "The enhanced Web Services Description Language (WSDL) is a WSDL enriched by ABAP
		information that are relevant for design time.")**  
The enhanced Web Services Description Language \(WSDL\) is a WSDL enriched by ABAP information that are relevant for design time.

**Related Information**  


[Creating Service Consumption Model](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/96132822b3554016b653d3601bb9ff1a.html)

[SOAP Communication via Destination Service](SOAP_Communication_via_Destination_Service_72bb6b5.md "Create a SOAP destination and enable SOAP communication from the ABAP environment.")

[Enhanced Web Services Description Language \(WSDL\)](Enhanced_Web_Services_Description_Language_(WSDL)_3a893d9.md "The enhanced Web Services Description Language (WSDL) is a WSDL enriched by ABAP information that are relevant for design time.")

[Tutorial: Consume SOAP-Based Web Services with SAP BTP ABAP Environment](https://developers.sap.com/tutorials/abap-environment-soap-web-services.html)

