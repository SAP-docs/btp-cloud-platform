<!-- loio8b6723b265d54c13866fbade4a7a087b -->

# Set Up SOAP Communication

Developers can consume SOAP-based web services for outbound communication from the ABAP environment.



<a name="loio8b6723b265d54c13866fbade4a7a087b__section_f33_btv_tyb"/>

## Overview

To consume SOAP-based web services, you must create a Service Consumption Model \(SRVC\). For the SRVC, you need to provide the WSDL of the service you want to consume via the local file system.



<a name="loio8b6723b265d54c13866fbade4a7a087b__section_mzr_21s_flb"/>

## Feature Scope

SOAP-based web services cover the following features:

-   Synchronous and asynchronous outbound web service communication
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
-   The creation of a Service Consumption Model in ADT is similar to the creation of a service consumer from an external WSDL within the web service wizard in SAP GUI.
-   The enhanced WSDL document is like the design time WSDL in the Proxy Editor in SAP GUI enhanced by ABAP properties.
-   The enhanced WSDL document replaces the function to change ABAP types in the Proxy Editor in SAP GUI.



<a name="loio8b6723b265d54c13866fbade4a7a087b__section_o5l_lnf_mtb"/>

## Related Links

-   [Enable SOAP Communication in Your ABAP Code](enable-soap-communication-in-your-abap-code-6ab460e.md)
-   [Tutorial: Consume SOAP-Based Web Services with SAP BTP ABAP Environment](https://developers.sap.com/tutorials/abap-environment-soap-web-services.html)

