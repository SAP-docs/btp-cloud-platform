<!-- loio15b536a25998491c870f6821a1147ea2 -->

# Configure Channel Binding App



## Context

Configure the subscriptions to consume events from the *SAP Event Mesh* service instance.



## Procedure

1.  Open the *Enterprise Event Enablement - Configure Channel Binding* app.

2.  Select the channel name of the corresponding `SAP_COM_0092` communication arrangement to which the communication system of your `Event Consumption Model` has been assigned to in [Create a Communication Arrangement for the Communication Scenario bound to an Event Consumption Model](create-a-communication-arrangement-for-the-communication-scenario-bound-to-an-event-consu-711286a.md).

    > ### Note:  
    > In the *Inbound Topic Bindings* tab under *Inbound Topics*, the event topics of the `Event Consumption Model` are displayed. The topics you see here correspond to the event types you've selected during the creation of the Event Consumption Model. Since these are maintained indirectly by assigning the communication system of your `Event Consumption Model` to the corresponding `SAP_COM_0092` communication arrangement. These bindings cannot be maintained manually, but only through changes of the communication system of your `Event Consumption Model`.That's why the *Maintained by* field has the value *Communication Management*.

3.  Maintain the Subscriptions in the *Subscription* tab as described in [Queue Subscriptions](queue-subscriptions-e859a14.md). Here you can add all subscription addresses of the *Event Mesh* queues from which you want to consume events.

    If a subscription to a queue of the*SAP Event Mesh* service instance instance is maintained and acknowledged, all events on this queue are consumed by SAP S4/HANA Cloud. Only if the event topics are maintained under *Inbound Topics*, the incoming events are handed over to the consumer extension class of the corresponding `Event Consumption Model`. If the event topic isn't maintained, the event is consumed without any further processing.


