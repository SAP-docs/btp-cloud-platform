<!-- copy653833f2615544cc9c85c65adca627b9 -->

# Communication Management

Learn more about the basic principles of communication management when integrating your system or solution with other systems to enable data exchange in your ABAP environment.

![](../30-development/images/ABAP_Environment_Communication_Management_Overview_38d2057.png) 

 <a name="copy0ea48d6604ad4f369a61d019d096a9fe"/>

<!-- copy0ea48d6604ad4f369a61d019d096a9fe -->

## Communication Scenario

A communication scenario, which is created in the development system using ABAP Development Tools and transported to other systems, is a design time description of how two communication partners communicate with each other. It consists of inbound and/or outbound services as well as supported authentication methods.

It provides technical information, such as the used inbound and outbound services and their service type, for example OData or SOAP, and the number of allowed communication arrangement instances. If the scenario exposes inbound services, it specifies the authorizations that are required to execute the services.

The following types of communication scenarios are available:

-   **Managed by SAP**, where SAP provides a ready-to-use communication scenario and you create and maintain a communication arrangement.
-   **Managed by customer**, where you develop a communication scenario and create and maintain a communication arrangement.

**Related Information**  


[Display Communication Scenarios](display-communication-scenarios-baa798b.md "You can use this app to get an overview of available communication scenarios.")

[Overview of Communication Scenarios Managed by SAP](overview-of-communication-scenarios-managed-by-sap-2d16f49.md "Find a quick overview of all the communication scenarios in the ABAP environment.")

[Developing External Service Consumption \(Outbound Communication\)](../30-development/developing-external-service-consumption-outbound-communication-f871712.md "Get more information about consuming external services.")

[Developing APIs for Inbound Communication](../30-development/developing-apis-for-inbound-communication-94ebfa0.md "Learn more about developing APIs for inbound communication.")

 <a name="copy8973afa24520400f945acf8612b10aa5"/>

<!-- copy8973afa24520400f945acf8612b10aa5 -->

## Communication System

A communication system is a specification of a system that represents a communication partner and the technical information required for the communication, such as the host name, port, users for inbound or outbound communication, certificates, etc.

If the communication system represents an on-premise system that is protected by a firewall, the system can be connected by assigning a cloud connector.

Instead of maintaining the credentials for outbound communication in the communication system itself, the communication system can also refer to a destination from the destination service. This can be a destination on subaccount level, or a destination from a destination service instance.

An administrator user in the ABAP environment has to create the communication system in the [Communication Systems](communication-systems-15663c1.md) app in SAP Fiori launchpad. Note that the communication system is not transported between ABAP systems but created locally. The communication partner can vary for each system.

 <a name="copy05da40ab27cf47a1a63d48d9e63b9c30"/>

<!-- copy05da40ab27cf47a1a63d48d9e63b9c30 -->

## Communication User

A communication user is a specific type of technical user that is assigned to a communication system. The user can be assigned a password or X.509 certificate.

A communication user is added as a user for inbound communication to communication systems.

An administrator user in the ABAP environment creates the communication user in the [Maintain Communication Users](maintain-communication-users-eef80dd.md) app in SAP Fiori launchpad. Note that the communication user is not transported between systems but created locally. The technical users and their credentials can vary for each system.

 <a name="copy9f7862b64d424e558630462ef4b17f59"/>

<!-- copy9f7862b64d424e558630462ef4b17f59 -->

## Communication Arrangement

A communication arrangement is a runtime description of a specific communication scenario. It describes which communication partners communicate with each other in the scenario, and how they communicate.

To describe this runtime behavior, you have to create an arrangement for a scenario, assign the communication system and communication users, and select the authentication method that shall be used.

If the communication scenario exposes inbound services, the communication user is granted the authorizations that have been specified for the communication scenario.

An administrator user in the ABAP environment creates the communication arrangement in the [Communication Arrangements](communication-arrangements-1decd8b.md) app in SAP Fiori launchpad. Note that it is not transported between systems but created locally. For certain SAP-managed scenarios that integrate an SAP BTP service, you can also create a communication arrangement from a service key of the service instance that you would like to connect.

For inbound-only scenarios, you can create a communication arrangement by creating a corresponding service key for the ABAP environment service instance.

**Related Information**  


[Maintain a Communication Arrangement for Inbound Communication](https://developers.sap.com/tutorials/abap-environment-communication-arrangement.html)

 <a name="copy3f8a0aed508c4940a71aaaf18e037095"/>

<!-- copy3f8a0aed508c4940a71aaaf18e037095 -->

## Destination Service

Using the SAP destination service, you can retrieve and store technical information about the target resource \(destination\) that you want to connect with your application to a remote service or a system.

The destination service allows you to read and manage the address of a remote service and the user authentication information for the connection on subaccount and service instance level.

**Related Information**  


[Destination Service](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/daca64dacc6148fcb5c70ed86082ef91.html#loiodaca64dacc6148fcb5c70ed86082ef91__services)

[Create a Destination](../30-development/create-a-destination-3fa7934.md "If your business application uses external services, you have to set up a destination for outbound communication either in your subaccount, which is recommended, or in your space.")

 <a name="copydfe2a7d9df774e1d874dd0d9d1db8a41"/>

<!-- copydfe2a7d9df774e1d874dd0d9d1db8a41 -->

## Destination

A destination is stored in the SAP destinations service and contains the connection details for the communication partner.

You can use a destination to:

-   Connect your application to the Internet \(via HTTP, RFC, or WebSocket RFC\) or to an on-premise system \(via HTTP or RFC\)

-   Send and retrieve emails by configuring a mail destination


> ### Note:  
> You can create a destination for a destination service on instance level or subaccount level.
> 
> A destination can be referenced in a communication system. To refer a destination from a destination service instance, a communication arrangement for SAP-managed scenario `SAP_COM_0276` needs to be maintained to enable communication with the destination service instance. See [Create a Destination](../30-development/create-a-destination-3fa7934.md). In this case, the destination name and the service instance name need to be maintained in the communication system.

**Related Information**  


[Managing Destinations](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/84e45e071c7646c88027fffc6a7bb787.html)

 <a name="copyf33e0590b65c484a93110ed252d43738"/>

<!-- copyf33e0590b65c484a93110ed252d43738 -->

## Cloud Connector

The Cloud Connector serves as a link between cloud applications and on-premise systems.

In the Cloud Connector, the subaccount of the ABAP system is connected so that the Cloud Connector can be used within a communication system or destination in the subaccount.

It provides an easy setup with a clear configuration of the systems that are exposed to SAP BTP.

**Related Information**  


[Cloud Connector](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e6c7616abb5710148cfcf3e75d96d596.html#loioe6c7616abb5710148cfcf3e75d96d596__context)

[Integrating On-Premise Systems](../30-development/integrating-on-premise-systems-c95327f.md "Set up the Cloud Connector to enable communication from the ABAP environment to your on-premise systems using Remote Function Calls (RFC) and HTTP calls.")

