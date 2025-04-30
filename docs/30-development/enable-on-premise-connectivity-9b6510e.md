<!-- loio9b6510edf4d844a28f022b3db41f3202 -->

# Enable On-Premise Connectivity

Create an HTTP and an RFC destination to enable communication from the ABAP environment to your on-premise systems.



<a name="loio9b6510edf4d844a28f022b3db41f3202__section_b5c_rl3_43b"/>

## Prerequisites

-   You have installed Cloud Connector version 2.12.3 or higher, see [Cloud Connector: Installation](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/57ae3d62f63440f7952e57bfcef948d3.html).

-   You have done the initial configuration for the Cloud Connector, see[Cloud Connector: Initial Configuration](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/db9170a7d97610148537d5a84bf79ba2.html).

-   If you want to use principal propagation as authentication type, the Cloud Connector must be configured to support this authentication type. See [Cloud Connector: Configuring Principal Propagation](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/c84d4d0b12d34890b334998185f49e88.html).

    Also, make sure that no communication arrangement to the deprecated communication scenario `SAP_COM_0200` exists.

-   If you use more than one Cloud Connector in your subaccount, you have assigned a location ID to each of these Cloud Connectors. See [Managing Subaccounts](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/f16df12fab9f4fe1b8a4122f0fd54b6e.html).



<a name="loio9b6510edf4d844a28f022b3db41f3202__section_p43_dm3_43b"/>

## Procedure

To enable on-premise connectivity, you must use the Cloud Connector in your communication system:

-   [Creating a Communication System for Outbound HTTP](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/create-communication-system-for-outbound-http?version=sap_btp)
-   [Creating a Communication System for Outbound RFC](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/create-communication-system-for-outbound-rfc?version=sap_btp)

**Related Information**  


[Outbound Communication](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/outbound-communication-48d3624d9f7d47d7ab712d110cb02d77?version=sap_btp)

[Communication System](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/communication-system?version=sap_btp)

