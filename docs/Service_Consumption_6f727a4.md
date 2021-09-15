<!-- loio6f727a40201547c79d9d7abf3baff344 -->

# Service Consumption

Connecting an ABAP environment system to SAP Analytics Cloud \(SAC\) using the InA service is only possible via direct connection \(Live Data Connection\) using communication scenario SAP\_COM\_0065. To find out more about direct connection, see [Live Data Connections to SAP S/4HANA](https://help.sap.com/viewer/00f68c2e08b941f081002fd3691d86a7/latest/en-US/d2a1edf7cda74315a2c5052de8a3a4eb.html).

To use the communication scenario, you need to create a communication system and a communication arrangement using the Fiori launchpad of the ABAP Environment system.

Please note:

-   Only one communication arrangement can be created per communication scenario.

-   Since the direct connection uses CORS, please verify your end-users' web browser configuration and access. Your end users' web browser has to be configured to:

    -   allow pop-up windows from the SAP Analytics Cloud domain: \[\*.\]sapbusinessobjects.cloud.

    -   allow third-party cookies from the SAP S/4HANA server's domain. For example, in Internet Explorer 11, go to *Internet Options* \> *Security* \> *Trusted Sites*, add your domain name, then select *Enable Protected Mode*.


**Related Information**  


[Connect the ABAP Environment System to SAP Analytics Cloud](Connect_the_ABAP_Environment_System_to_SAP_Analytics_Cloud_a102853.md "Connect your ABAP environment system to SAP Analytics Cloud (SAC) using communication scenario SAP_COM_0065. Here's how:")

