<!-- loio4609de1fb41c466caf393b91316e084a -->

# Checking Channel Binding

This topic describes how to check the channel binding for the enterprise event enablement.



## Prerequisites

-   You've set up a communication arrangement for`SAP_COM_0092` or `SAP_COM_0492` as described in [Communication Management](communication-management-659855d.md).

-   You've created an event consumption model and a communication scenario as described in [Event Consumption](event-consumption-a2c4285.md).




## Context

Inbound topic bindings are automatically created during generation and configuration of an event consumption model by assigning the communication system of your event consumption model to the corresponding communication arrangement. Maintaining inbound topic bindings can only be done through changes of the communication system of your event consumption model.

Follow the steps below to view the inbound topic bindings.



## Procedure

1.  Log on to the SAP Fiori launchpad in the ABAP environment system.

2.  In the *Communication Management* app, select the *Enterprise Event Enablement ‒ Configure Channel Binding* app.

3.  Select the *Channel* name of the corresponding communication arrangement to which the communication system of your event consumption model has been assigned to in [Creating a Communication Arrangement for the Communication Scenario bound to an Event Consumption Model](creating-a-communication-arrangement-for-the-communication-scenario-bound-to-an-event-con-461955b.md).

    In the *Inbound Topic Bindings* tab under *Inbound Topics*, the event topics of the event consumption model are displayed. The topics you see here correspond to the event types you've selected during the creation of the event consumption model. Since these are created automatically, the *Maintained by* field has the value *Communication Management*.

4.  Maintain the subscriptions in the *Subscriptions* tab as described in [Queue Subscriptions](queue-subscriptions-d39f689.md).

    Here you can add all subscription addresses of the respective event exchange infrastructure queues from which you want to consume events.

    If a subscription to a queue of the respective event exchange infrastructure service instance is maintained and acknowledged, all events on this queue are consumed by the ABAP environment. Only if the event topics are maintained under *Inbound Topics*, the incoming events are handed over to the consumer extension class of the corresponding event consumption model. If the event topic isn't maintained, the event is consumed without any further processing.


