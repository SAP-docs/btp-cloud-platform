<!-- loiob750ee36051b4f7fb2cc3dfabeeebd81 -->

# Integrating the ABAP Environment with SAP S/4HANA Cloud

You can integrate the SAP BTP, ABAP environment with an SAP S/4HANA Cloud Public Edition system. ​This allows ABAP developers to implement outbound service calls from the ABAP environment to the SAP S/4HANA Cloud Public Edition system.



<a name="loiob750ee36051b4f7fb2cc3dfabeeebd81__section_q1n_5xt_s2b"/>

## Context

Developers in SAP BTP, ABAP environment would like to access data from business services in SAP S/4HANA Cloud Public Edition as part of their applications.

This documentation provides you with a high-level description of how to integrate the two systems and how to implement service calls from SAP BTP, ABAP environment to SAP S/4HANA Cloud Public Edition. This is complemented by a tutorial group that provides a detailed, step-by-step description based on an example.



<a name="loiob750ee36051b4f7fb2cc3dfabeeebd81__section_arf_pn3_v2b"/>

## Overview of Implementation Activities

To set up remote connectivity it is necessary to perform some steps in both involved systems, as the connection must be enabled by both communication partners.

In the scenario that we are considering, an SAP S/4HANA Cloud Public Edition service is called from SAP BTP, ABAP environment. In other words, SAP S/4HANA Cloud Public Edition is the *inbound* communication partner, while SAP BTP, ABAP environment is the *outbound* communication partner.

Following, you can find an overview of necessary steps, grouped by the executing persona.



### Developer in SAP BTP, ABAP environment

-   *Create a communication scenario*

    As a developer you create an outbound service that represents the service of an SAP S/4HANA Cloud Public Edition system. You add this outbound service to a communication scenario and maintain the supported authentication method.

-   *Create a service consumption model*

    As a developer you can use the metadata of a given service to create a service consumption model. Although not strictly necessary, this greatly simplifies the consumption of the remote service from your ABAP code.

-   *Implement the application*

    The actual service call itself needs to be implemented. This can be part of a frontend application, API service, application job, console application, etc. The communication artifacts and the service consumption model are reused to create compact and understandable code.




### Administrator in SAP S/4HANA Cloud Public Edition

-   *Expose the service*

    As administrator you need to make the required service available for remote access. To do so, you create a communication arrangement for a scenario containing the API as an inbound service. Along with the arrangement, you define a communication system and an inbound communication user that shall be used to establish the connection.




### *Configure the outbound communication*

As administrator you create a communication arrangement based on the scenario implemented by the developer. The arrangement is tied to a communication system that identifies the SAP S/4HANA Cloud Public Edition system as the target host.

Tutorial group [Integrate the SAP BTP, ABAP environment with SAP S/4HANA Cloud, public edition](https://developers.sap.com/group.sap-btp-abap-s4hana-integrate.html) shows how to consume the business partner OData API service in SAP S/4HANA Cloud Public Edition from a console application in SAP BTP, ABAP environment using basic authentication \(communication user\) and OAuth 2.0 SAML Bearer Assertion \(propagation of business user\).

