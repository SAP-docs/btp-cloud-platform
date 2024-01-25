<!-- loio5b5da393ab0b485e88970ec56a440f6e -->

# Event Metadata



## Prerequisites

-   You have established a connection through the configuration of the communication arrangement in the previous steps. For more information, refer to [Communication Arrangements](communication-arrangements-ee55a6a.md).

-   The *Enterprise Event Enablement ‒ Configure Channel Bindings* app is visible.

    If the *Enterprise Event Enablement ‒ Configure Channel Bindings* app is not visible, add the *Enterprise Event Enablement* business catalog to the `SAP_BR_ADMINISTRATOR` role using the *Maintain Business Roles* app. The change in your role becomes effective after you have logged out and logged in again.




## Context

The enterprise event enablement is applying the CloudEvents specification \([https://cloudevents.io](https://cloudevents.io)\) for the runtime representation of an event. CloudEvents is a specification for describing event data in common formats to ensure interoperability across services, platforms, and systems.

You can find all released SAP events on the SAP Business Accelerator Hub \([https://api.sap.com](https://api.sap.com)\). The SAP Business Accelerator Hub is the central catalog of SAP and selected partner APIs to search, discover, test, and consume these APIs to build extensions or integrations using the SAP Business Technology Platform.

The enterprise event enablement applies the AsyncAPI specification to describe a catalog of events.

> ### Note:  
> You can find the corresponding AsyncAPI event catalogs for released events in the *Event Resources* section of the individual released events on the SAP Business Accelerator Hub. This specification is required for example to create an event consumption model.



## Procedure

1.  Log on to the SAP Fiori launchpad in the ABAP environment system.

2.  In the *Communication Management* app, select the *Enterprise Event Enablement ‒ Configure Channel Binding* app.

3.  Choose a channel name \(created in [Creating Communication Arrangements](creating-communication-arrangements-705564a.md)\).

4.  Select *Event Metadata*.




## Next Steps

In the *Event Metadata* tab, you can view the metadata for the event types selected on the *Outbound Topic Bindings* tab for event publishing. This metadata contains the definition of the structure of all event types, which you have selected for publishing from the ABAP environment system. The metadata is represented as an AsyncAPI catalog of events and can contain released SAP events as well as customer events. You can also use the AsyncAPI representation for creating your event consumption model.

**Related Information**  


[CloudEvents Context Attributes](cloudevents-context-attributes-4f5467b.md "Events published through the enterprise event enablement are compliant with the CloudEvents specification. Context attributes contained in events are listed in this topic.")

[Creating an Event Consumption Model](https://help.sap.com/docs/SAP_S4HANA_CLOUD/25cf71e63940453397a32dc2b7676947/ea3dbc187ccd4c16aa9d0a11af1efd47.html)

