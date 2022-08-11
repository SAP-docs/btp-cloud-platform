<!-- loio38b5744273324b60b782948afce5241a -->

# Configure Event Consumer

In this topic, you can find information about how to enable the event consumption for an `Event Consumption Model` you've defined using the `ABAP Development Tools` and how to set up the corresponding communication arrangement . For more information about how to define an `Event Consumption Model`, see [Creating an Event Consumption Model](https://help.sap.com/docs/SAP_S4HANA_CLOUD/25cf71e63940453397a32dc2b7676947/ea3dbc187ccd4c16aa9d0a11af1efd47.html).



<a name="loio38b5744273324b60b782948afce5241a__section_dsc_tyy_xtb"/>

## Prerequisites

-   You've set up a communication arrangement for *SAP\_COM\_0092* as described in [Communication Management](communication-management-56cf82e.md).

-   You've created an `Event Consumption Model` and a `Communication Scenario` as described in [Creating an Event Consumption Model](https://help.sap.com/docs/SAP_S4HANA_CLOUD/25cf71e63940453397a32dc2b7676947/ea3dbc187ccd4c16aa9d0a11af1efd47.html).

The communication arrangement `SAP_COM_0092` defines the connection from SAP S4/HANA Cloud to the SAP Event Mesh instance. Via this communication arrangement, ABAP environment receives events from the event queue and transfers the events to the `Event Consumption Model` which then processes the event. The event is processed according to the logic implemented in the `handle_event method` of the `Consumer Extension Class`



<a name="loio38b5744273324b60b782948afce5241a__section_uqj_f1z_xtb"/>

## Procedure

The following steps are required to configure the event consumer:

