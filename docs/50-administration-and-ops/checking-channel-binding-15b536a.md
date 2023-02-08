<!-- loio15b536a25998491c870f6821a1147ea2 -->

# Checking Channel Binding

This topic describes how to check the channel binding for the enterprise event enablement.



## Prerequisites

-   You've set up a communication arrangement for `SAP_COM_0092` as described in [Communication Management](communication-management-56cf82e.md).

-   You've created an *Event Consumption Model* and a *Communication Scenario* as described in [Event Consumption](event-consumption-a2c4285.md).




## Context

Inbound topic bindings are automatically created during generation and configuration of an *Event Consumption Model* by assigning the communication system of your *Event Consumption Model* to the corresponding `SAP_COM_0092` communication arrangement. Maintaining inbound topic bindings can only be done through changes of the communication system of your *Event Consumption Model*.

Follow the steps below to view the inbound topic bindings.



## Procedure

1.  Log on to the SAP Fiori launchpad in the SAP S/4HANA Cloud system.

2.  In the *Communication Management* app, select the *Enterprise Event Enablement ‒ Configure Channel Binding* app.

3.  Select the *Channel* name of the corresponding `SAP_COM_0092` communication arrangement to which the communication system of your *Event Consumption Model* has been assigned to in [Creating a Communication Arrangement for the Communication Scenario bound to an Event Consumption Model](creating-a-communication-arrangement-for-the-communication-scenario-bound-to-an-event-c-711286a.md).

    In the *Inbound Topic Bindings* tab under *Inbound Topics*, the event topics of the *Event Consumption Model* are displayed. The topics you see here correspond to the event types you've selected during the creation of the event consumption model. Since these are created automatically, the *Maintained by* field has the value *Communication Management*.

4.  Maintain the subscriptions in the *Subscriptions* tab as described in [Queue Subscriptions](queue-subscriptions-e859a14.md).

    Here you can add all subscription addresses of the *Event Mesh* queues from which you want to consume events.

    If a subscription to a queue of the SAP Event Mesh service instance is maintained and acknowledged, all events on this queue are consumed by SAP S/4HANA Cloud. Only if the event topics are maintained under *Inbound Topics*, the incoming events are handed over to the consumer extension class of the corresponding *Event Consumption Model*. If the event topic isn't maintained, the event is consumed without any further processing.


