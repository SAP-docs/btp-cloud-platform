<!-- loio11855583e3834fc9ab44fc3cbf54091e -->

# Simulating Consumption



## Prerequisites

-   The *Enterprise Event Enablement ‒ Configure Channel Bindings* app is visible.

    If the *Enterprise Event Enablement ‒ Configure Channel Bindings* app is not visible, add the *Enterprise Event Enablement* business catalog to the `SAP_BR_ADMINISTRATOR` role using the *Maintain Business Roles* app. The change in your role becomes effective after you have logged out and logged in again. For more information about adding catalogs to business roles, refer to [Maintain Business Roles](maintain-business-roles-8980ad0.md).

-   You have an inbound topic binding with status *Ok* in your *Inbound Topics* table.




## Context

To allow you to test your consumer implementation, you can use the *Simulate Consumption* action. Then a dummy event of a given *Topic Consumer* will be sent to its consumer implementation.



## Procedure

1.  Log on to the SAP Fiori launchpad in the SAP S/4HANA Cloud system.

2.  In the *Communication Management* app, select the *Enterprise Event Enablement ‒ Configure Channel Binding* app.

3.  Choose a channel name \(created in [Creating Communication Arrangements](creating-communication-arrangements-78ababb.md)\).

4.  Select an *Inbound Topic*.

    If you have no *Inbound Topic* with *Status: Ok*, refer to [Configuring Inbound Event Topic Bindings](configuring-inbound-event-topic-bindings-b62727d.md)

5.  Select the radio button of the *Topic Consumer* you want to simulate consumption with.

6.  Choose *Simulate Consumption*.




## Results

In case of a wildcard in the topic, the wildcard is resolved and events for all resolved topics are created. The dummy events are sent to the corresponding consumer implementation. Then the simulated event is retrieved from the internal event queue and the status is checked. A short message is raised, informing the user on the success or failure of the simulation.

