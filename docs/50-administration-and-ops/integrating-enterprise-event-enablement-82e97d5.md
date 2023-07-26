<!-- loio82e97d5329044732af1efd996bfdc2ab -->

# Integrating Enterprise Event Enablement

Get an overview of integrating the enterprise event enablement framework into your SAP S/4HANA Cloud system.



The enterprise event enablement framework enables the exchange of events across different platforms for seamless event-driven communication. To successfully exchange events between the SAP Event Mesh and an ABAP environment system, an upright connection is required. This connection is maintained by the enterprise event enablement framework during the creation of the corresponding *Communication Management* artifacts like *Communication Arrangements* and *Communication Systems*.



You can publish events triggered from ABAP environment applications through [RAP Business Events](https://help.sap.com/docs/BTP/923180ddb98240829d935862025004d6/0b925bc556d4491aad395b21ec2566ff.html) and consume events delivered through the SAP Event Mesh service from external applications. The SAP Event Mesh service provided on the SAP Business Technology Platform is the message broker as a service, which provides real-time messaging capabilities. All events are exposed in a standard way with a well-defined hierarchy and metadata so they can easily be consumed on different platforms.



## Prerequisites

The following prerequisites must be met to integrate the enterprise event enablement:

-   You have a subaccount in SAP BTP, Cloud Foundry environment. Refer to [Getting Started with a Trial Account in the Cloud Foundry Environment](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/e50ab7b423f04a8db301d7678946626e.html).

-   You have created a service instance for SAP Event Mesh. If you haven't created a service instance before, refer to [Creating an Enterprise Messaging Service Instance](https://help.sap.com/viewer/bf82e6b26456494cbdd197057c09979f/Cloud/en-US/d0483a9e38434f23a4579d6fcc72654b.html).

-   The key user must have the business role `SAP_BR_ADMINISTRATOR` \(Administrator\) that contains the business catalog `SAP_CORE_BC_COM` \(Communication Management\).


