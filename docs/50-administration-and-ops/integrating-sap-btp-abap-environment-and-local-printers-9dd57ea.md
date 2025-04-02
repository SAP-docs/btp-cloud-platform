<!-- loio9dd57ea515324746aa21f03dbd6ef56f -->

# Integrating SAP BTP ABAP environment and Local Printers

To set up the integration between SAP BTP ABAP environment and local printers, you can use two communication scenarios, `SAP_COM_0466` and `SAP_COM_0467`.

Both communication scenarios are designed to connect third-party output management systems \(OMS\). OMS provide you with more refined printing functionalities. With `SAP_COM_0466`, the OMS use polling to check for the availability of new items to print. The communication scenario only has inbound communication. The *SAP Cloud Print Manager for Pull Integration* is supported by this communication scenario.

With `SAP_COM_0467`, the SAP BTP ABAP environment system sends a notification to the OMS if new items are available to print. Therefore, the communication scenario has in- and outbound communication. This communication scenario doesn't support the use of the *SAP Cloud Print Manager for Pull Integration*.

Item retrieval and status update is the same for both methods. The only difference is the determination of new items to print.

Please check the documentation of your OMS first to see which method is supported before creating a communication arrangement of any type. An example of an implementation of these communication scenarios is Microsoft Universal Print. See [this blog](https://community.sap.com/t5/technology-blogs-by-members/it-has-never-been-easier-to-print-from-sap-with-microsoft-universal-print/ba-p/13672206) for more details.

**Related Information**  


[SAP\_COM\_0466](sap-com-0466-524c13a.md "This document describes the configuration steps that have to be carried out by customers to set up the integration between SAP BTP ABAP environment and local printers using SAP_COM_0466.")

[SAP\_COM\_0A86](sap-com-0a86-3a7d4d7.md "This document describes the print queue administrator integration. It provides the configuration steps that have to be carried out by customers to create and delete print queues using SAP_COM_0A86.")

[SAP\_COM\_0467](sap-com-0467-523eb80.md "This document describes the configuration steps that have to be carried out by customers to set up the integration between SAP BTP ABAP environment and local printers using SAP_COM_0467.")

[Maintain Print Queues](maintain-print-queues-9dd6f64.md "")

[Printing](../30-development/printing-754b6cd.md "Find out how to create a print queue item API.")

