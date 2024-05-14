<!-- loio0faea48bdc4640cb90fc1fa4c491b71e -->

# Integrating Enterprise Event Enablement

Get an overview of integrating the enterprise event enablement framework into your SAP BTP, ABAP environment system.



The enterprise event enablement framework enables the exchange of events across different platforms for seamless event-driven communication. To successfully exchange events between the respective event exchange infrastructure and an ABAP environment system, an upright connection is required. This connection is maintained by the enterprise event enablement framework during the creation of the corresponding *Communication Management* artifacts like *Communication Arrangements* and *Communication Systems*.



You can publish events triggered from ABAP environment applications through [RAP Business Events](https://help.sap.com/docs/abap-cloud/abap-rap/business-events?version=sap_btp) and consume events delivered through the respective event exchange infrastructure from external applications.

The respective event exchange infrastructure service provided on the SAP Business Technology Platform is the message broker as a service, which provides real-time messaging capabilities. All events are exposed in a standard way with a well-defined hierarchy and metadata so they can easily be consumed on different platforms.



## Prerequisites

The following prerequisites must be met to integrate the enterprise event enablement:

-   You have a subaccount in the SAP BTP. Refer to [Getting Started](https://help.sap.com/docs/btp/sap-business-technology-platform/btp-getting-started).

-   You have created a service instance for SAP Event Mesh or SAP Advanced Mesh Service Plan.
-   The key user must have the business role `SAP_BR_ADMINISTRATOR` \(Administrator\) that contains the business catalog `SAP_CORE_BC_COM` \(Communication Management\).


