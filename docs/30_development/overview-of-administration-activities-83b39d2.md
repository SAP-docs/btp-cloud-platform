<!-- loio83b39d21b4694bd88d07ad9564d41f6e -->

# Overview of Administration Activities

Get an overview of the example used in this documentation and what kind of administration activities you need to expect and why.



<a name="loio83b39d21b4694bd88d07ad9564d41f6e__section_arf_pn3_v2b"/>

## Example Scenario Used in This Documentation

In the example scenario used in this documentation, developers want to make an outbound service call from the ABAP environment to SAP S/4HANA Cloud, using an SAP S/4HANA service to create a business partner.

When an outbound service call in ABAP environment is implemented, there are two authentication methods that can be used to authenticate at the S4/HANA cloud system:

-   User ID and password \(basic authentication\)

-   OAuth 2.0


In this example scenario, OAuth 2.0 authentication will be used.



<a name="loio83b39d21b4694bd88d07ad9564d41f6e__section_pjp_4rn_v2b"/>

## Overview of Administration Activities

   
  
<a name="loio83b39d21b4694bd88d07ad9564d41f6e__fig_u4q_3z4_v2b"/>Administration Activities for Establishing Trust Between SAP S/4HANA Cloud and Cloud Foundry \(Developer Activities Grayed Out\)

 ![](images/SAP_BTP_and_SAP_S_4HANA_Cloud_Integration_8449d3b.png "Administration Activities for Establishing Trust Between SAP S/4HANA Cloud and Cloud Foundry (Developer Activities Grayed
					Out)") 

For the OAuth 2.0 authentication, the main task for you as administrator is to establish a trust relationship between the communication partners \(that is, ABAP environment and SAP S/4HANA Cloud\). You establish this trust relationship by creating a communication system in SAP S/4HANA Cloud and configuring the trusted OAuth 2.0 identity provider as part of this communication system. To make sure that a developer can expose a business service, you need to create a communication arrangement, which is based on this communication system and a communication scenario.

Communication arrangements help you to configure the electronic data exchange between the system and a communication partner. The system provides communication scenarios for inbound and outbound communication that you can use to create communication arrangements. Predefined communication scenarios are available for different use cases, including the communication scenario *Business Partner, Customer and Supplier Integration* \(`SAP_COM_0008`\), which is used as relevant communication scenario for the example in this documentation.



<a name="loio83b39d21b4694bd88d07ad9564d41f6e__section_fxw_bl4_v2b"/>

## More Information

For more information about how to use the communication management apps in SAP S4/HANA systems to integrate with other systems see [Communication Management](https://help.sap.com/viewer/f544846954f24b9183eddadcc41bdc3b/latest/en-US/2e84a10c430645a88bdbfaaa23ac9ff7.html).

For more information about available services in SAP S/4HANA Cloud that can be consumed by external systems, search for services on the SAP API Business Hub at [http://api.sap.com](http://api.sap.com) or follow this [direct link](https://api.sap.com/package/SAPS4HANACloud?section=Artifacts).

For more information about how to consume services offered as part of SAP S/4HANA Cloud or other SAP products, see [API Management](https://help.sap.com/viewer/66d066d903c2473f81ec33acfe2ccdb4/Cloud/en-US/adcbc07b031b4ac285b22867a1216306.html).

After you have completed the integration of the ABAP environment with SAP S/4HANA Cloud, developers can start implementing their services. For more information about the next steps of the developers and additional resources, see [Implementing an Outbound Service Call to SAP S/4HANA Cloud](implementing-an-outbound-service-call-to-sap-s-4hana-cloud-a4e21bd.md).

