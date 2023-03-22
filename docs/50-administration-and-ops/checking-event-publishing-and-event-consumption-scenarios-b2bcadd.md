<!-- loiob2bcadd964b0437e9a8d8b25f9763cf5 -->

# Checking Event Publishing and Event Consumption Scenarios

This topic describes how to check the channel bindings for the enterprise event enablement.



## Context

Configure the integration with the Event Mesh kernel service instance.



## Procedure

1.  Log on to the SAP Fiori launchpad in the SAP S/4HANA Cloud system.

2.  In the *Communication Management* app, select the *Enterprise Event Enablement ‒ Configure Channel Binding* app.

3.  Select the *Channel* name of the corresponding `SAP_COM_0892` communication arrangement.

    In the overview page, you can see the inbound and outbound bindings for the selected channel.

    > ### Note:  
    > The inbound and outbound bindings can only be maintained using the configuration reconciliation. That's why the *Maintained by* field in the *Inbound Topic Bindings* section has the value *SAP BTP*. The configuration reconciliation is triggered through the end user in the SAP Event Mesh 2.0 UI at activation of the event flow.


