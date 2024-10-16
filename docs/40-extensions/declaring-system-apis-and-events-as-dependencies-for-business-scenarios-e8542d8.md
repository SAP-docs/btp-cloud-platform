<!-- loioe8542d805f5e430fba469c8ebe8e76f4 -->

# Declaring System APIs and Events as Dependencies for Business Scenarios



## Context

For certain formation types, systems of type *Other System Type*, *SAP BTP Application*, or *SAP Integration Suite* that are part of the *System Landscape* page may need to describe their runtime dependencies so other systems can comply with these dependencies to be able to interact with these systems in a common scenario.

The integration dependency includes a list of requirements, which point out which API and event resources are involved. Each requirement describes one aspect and can be used to express alternatives using OR conditions for achieving the same outcome.

To add the necessary API and event resources to an integration dependency, systems use the Open Resource Discovery standard. The Open Resource Discovery standard is about adding missing or common high-level information and standardizing the discovery aspects. See [Why ORD](https://sap.github.io/open-resource-discovery/details/articles/why-ord).

Every integration dependency has the following properties:

-   Name: a human-readable name that does not exceed 255 characters. For example, `Integration Dependency to realize Customer Order data product`.

-   Description: a plain text that does not exceed 255 characters. For example, `SAP S/4HANA Cloud, our next generation cloud ERP suite designed for in-memory computing.`

-   Version: the version is assigned automatically when adding a new integration dependency.

    > ### Note:  
    > If you add a new integration dependency using the same name as an existing integration dependency, the version of the new integration dependency will be automatically increased. Then, in the given system, there will be two integration dependencies with the same name and different versions.


Depending on your use case, there are different templates that help you set up the necessary integration dependency:

-   Blank template

    You write integration dependencies from scratch inluding the aspects that contain a set of APIs and/or events of a system that define the dependencies other systems need to comply with to be able to be part of an integration scenario together.

-   Simplified Business Eventing template

    Integration dependencies are exposed as available event subscriptions in SAP Cloud Application Event Hub. This template helps you write simplified integration dependencies that identify the types of events a subscribing application wants to consume. Here's an example. Let's say SAP SuccessFactors publishes a set of events. You want to receive a subset of those events. You can use the *Simplified Business Eventing Template* to identify the event types that SAP Cloud Application Event Hub makes available to your subscribing system.


<a name="loio030b4c59ae6f4c19aa50274a4999e68f"/>

<!-- loio030b4c59ae6f4c19aa50274a4999e68f -->

## Add an Integration Dependency Using a Blank Template



<a name="loio030b4c59ae6f4c19aa50274a4999e68f__prereq_cnw_xw5_cbc"/>

## Prerequisites

You have a system of type *Other System Type* or *SAP BTP Application* listed in the *Systems* page of your global account in SAP BTP. See [Registering a Third-Party System](registering-a-third-party-system-5481d59.md).



## Context

Integration dependencies contain aspects. An aspect contains a set of APIs and/or events of a system that define the dependencies other systems need to comply with to be able to be part of an integration scenario together.



<a name="loio030b4c59ae6f4c19aa50274a4999e68f__steps_p3z_g1w_vzb"/>

## Procedure

1.  In the cockpit, navigate to your global account, and then choose *System Landscape* \> *Systems* .

2.  On the *Systems* page, select a system of type *Other System Type* to which you want to add an integration dependency and open its system details.

3.  In the *Integration Dependencies* tab, choose *Add*.

4.  Select *Blank Template* to write an integration dependency from scratch.

5.  Define a name and a description for the new integration dependency. Choose *Next Step*.

    > ### Note:  
    > The version is assigned automatically when adding a new integration dependency. If you add a new integration dependency using the same name as an existing integration dependency, the version of the new integration dependency will be automatically increased.

6.  Define a name and a description for the first aspect and add more if necessary. Choose *Next Step*.

7.  Add at least one API or event to each aspect and choose *Review*.

8.  Check if all the aspects are configured properly and choose *Add*.

    > ### Note:  
    > Once you add an integration dependency to a system, you can no longer edit it and add or delete aspects, APIs or events. You can only delete an integration dependency.


<a name="loiob7c9275992bb4e4cbef41d804d6e70e8"/>

<!-- loiob7c9275992bb4e4cbef41d804d6e70e8 -->

## Add an Integration Dependency Using a Simplified Business Eventing Template



<a name="loiob7c9275992bb4e4cbef41d804d6e70e8__prereq_k3v_l1d_bbc"/>

## Prerequisites

-   An SAP Cloud system is registered in the *Systems* page in SAP BTP cockpit and has a catalog of events that it plans to publish. Refer to the product documentation for the publishing system for more details. For example, an SAP SuccessFactors system can be configured to publish events. See [SAP Cloud Application Event Hub Service Guide: Integration Use Cases](https://help.sap.com/docs/event-broker/event-broker-service-guide/integration-use-cases?version=Cloud).

    The SAP system you plan to use as the subscriber is registered in the *Systems* page. If you want to use SAP Integration Suite integration flows to consume events from SAP Cloud Application Event Hub, then the tenant with the integration flow must be registered in the *Systems* page. See [Integration Example using SAP Integration Suite](https://help.sap.com/docs/event-broker/event-broker-service-guide/integration-example-using-sap-integration-suite-iflows?version=Cloud).

-   Your subscribing system is listed in the *Systems* page of your global account in SAP BTP.

    For example, you have a system of type *SAP Integration Suite* listed in the *Systems* page. It appears as auto-discovered.




## Context

You can subscribe to events with extension applications. For example, you use SAP SuccessFactors to publish events and an Integration Suite tenant to consume them. The SAP SuccessFactors system is publishing these events and you add the event types that you want this system to receive using the *Simplified Business Eventing Template* of the integration dependencies. Integration dependencies are exposed as available event subscriptions in SAP Cloud Application Event Hub. The *Simplified Business Eventing Template* helps you write simplified integration dependencies specifying only event-specific information.



## Procedure

1.  In the cockpit, navigate to your global account, and then choose *System Landscape* \> *Systems*.

2.  On the *Systems* page, select a system of type *Integration Suite* to which you want to add an integration dependency and open its system details.

3.  In the *Integration Dependencies* tab, choose *Add*.

4.  Select *Simplified Business Eventing Template* to identify the system that is publishing events and add the event types that you want to receive. Integration dependencies are exposed as available event subscriptions in SAP Cloud Application Event Hub.

5.  Define a name and a description for the new integration dependency.

    > ### Note:  
    > The version is assigned automatically when adding a new integration dependency. If you add a new integration dependency using the same name as an existing integration dependency, the version of the new integration dependency will be automatically increased.

6.  In the *Publishing System Namespace* field, provide the system namespace of the system that is publishing events. You can find the system namespace in the *System Details* of the system.

    The system namespace has to follow these rules:

    -   Use only lowercase ASCII letters \(a-z\) and digits \(0-9\)

    -   Include at least one character

    -   Use the dot \(.\) only to separate fragments

    -   Include only two fragments separated by a dot

        Example: sap.foo


7.  In the *Event Type* field, list the event types published by the system that you want to make available to your subscribing system. 

    You can write or paste the event types separated by comma, semicolon or new row. Preferably, each event type should be on a new row. You have a counter giving the number of event types that are already filled in.

8.  Choose *Next Step*.

9.  Check if all the event types are configured properly and choose *Add*.

    > ### Note:  
    > Once you add an integration dependency to a system, you can no longer edit it and add or delete event types. You can only delete the integration dependency itself.


