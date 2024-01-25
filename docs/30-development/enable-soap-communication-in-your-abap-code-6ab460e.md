<!-- loio6ab460e1a59e4890b8faa3fcc35f3343 -->

# Enable SOAP Communication in Your ABAP Code



<a name="loio6ab460e1a59e4890b8faa3fcc35f3343__section_ls1_qty_gzb"/>

## Feature Scope

SOAP-based web services cover the following features:

-   Synchronous and asynchronous outbound web service communication
-   Self-contained WSDL \(single file with no import or include statements\)
-   gCTS Support \(not relevant for Developer Extensibility, see [Developer Extensibility](https://help.sap.com/docs/PRODUCT_ID/6aa39f1ac05441e5a23f484f31e477e7/e1059ff581854a699f15734049f14293.html?state=PRODUCTION&version=latest&locale=en-US)\)
-   Web service protocols, e.g. to add custom XML elements to the SOAP request header, add the Application Interface Key, or enable EOIO processing. For more information, see [SOAP Protocols](soap-protocols-8846682.md).

To enable SOAP communication, there are three different approaches:

-   Communication arrangement

    -   Provides APIs for receiver determination based on arbitrary properties \(see [Define Specific Properties for Communication Scenarios](define-specific-properties-for-communication-scenarios-fae8f0f.md) \).
    -   Local configuration via communication management UIs or central configuration in SAP BTP cockpit via SAP BTP destination service reference in the communication system \(not relevant for Developer Extensibility, see [Developer Extensibility](https://help.sap.com/docs/SAP_S4HANA_CLOUD/6aa39f1ac05441e5a23f484f31e477e7/e1059ff581854a699f15734049f14293.html?locale=en-US&state=PRODUCTION&version=LATEST)\). For more information, see [Communication Systems](../50-administration-and-ops/communication-systems-15663c1.md).
    -   Requires the development of communication scenario artifacts.

-   Destination service \(not relevant for Developer Extensibility, see [Developer Extensibility](https://help.sap.com/docs/SAP_S4HANA_CLOUD/6aa39f1ac05441e5a23f484f31e477e7/e1059ff581854a699f15734049f14293.html?locale=en-US&state=PRODUCTION&version=LATEST)\).

    -   Provides APIs to fetch connection information for a given destination name from the SAP BTP destination service. No additional development artifacts required.
    -   Central configuration in SAP BTP cockpit.

-   URL approach: By using a plain URL and setter methods to provide the needed configuration directly in the coding.

All of the listed approaches above require a Service Consumption Model. For more information, see [Service Consumption Model as SOAP Consumer](service-consumption-model-as-soap-consumer-71e6a8e.md).

