<!-- loioe8542d805f5e430fba469c8ebe8e76f4 -->

# Declaring System APIs and Events as Dependencies for Business Scenarios



## Context

For certain formation types, systems of type *Other System Type*, *CAP Application*, or *SAP Integration Suite* that are part of the *System Landscape* page may need to describe their runtime dependencies so other systems can comply with these dependencies to be able to interact with these systems in a common scenario.

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

    Integration dependencies are exposed as available event subscriptions in SAP Event Broker. This template helps you write simplified integration dependencies that identify the types of events a subscribing application wants to consume. Here's an example. Let's say SAP SuccessFactors publishes a set of events. You want to receive a subset of those events. You can use the *Simplified Business Eventing Template* to identify the event types that SAP Event Broker makes available to your subscribing system.


