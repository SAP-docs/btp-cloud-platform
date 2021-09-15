<!-- loio61920789e1a247258c2fcf4b0697621e -->

# Integrating the ABAP Environment with SAP Document Management Service

You can integrate the ABAP environment of SAP Business Technology Platform with SAP Document Management Service to establish a communication scenario.



<a name="loio61920789e1a247258c2fcf4b0697621e__prereq_hwv_vvj_jpb"/>

## Prerequisites

-   You've subscribed to the service Document Management Service, Integration Option and created an instance in Cloud Foundry environment. See [Initial Setup for Document Management Service, Integration Option](https://help.sap.com/viewer/f6e70dd4bffa4b65965b43feed4c9429/Cloud/en-US/bc0f1ec7d5374b968e0b0de6db470c94.html).

-   The global administrator of your SAP BTP account has added the service plan for Document Management Service, Repository Option to your subaccount via entitlements. See [Configure Entitlements for Subaccounts](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/5ba357b4fa1e4de4b9fcc4ae771609da.html).

-   You've onboarded Document Management provided storage capability. See [Connect to Document Management Service, Repository Option Using API](https://help.sap.com/viewer/f6e70dd4bffa4b65965b43feed4c9429/Cloud/en-US/d30200e0993a457888db2786d4bb5cd9.html).

-   You've created and copied the service key in the same subaccount of Cloud Foundry environment where Document Management, integration option instance is created. For more information about creating service key, see [Create Service Keys Using the Cockpit](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/cdf4f200db3e4c248fa67401937b2f78.html).

-   You've the *Administrator* role \(role template `ID SAP_BR_ADMINISTRATOR`\). See [Maintain Business Roles](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/8980ad05330b4585ab96a8e09cef4688.html).



## Context

SAP Document Management Service helps companies with managing records or attachments that are linked to business objects or a specific business context.

For each tenant of SAP BTP ABAP environment, a service instance of SAP Document Management Service in Cloud Foundry environment has to be created.

You can build and edit communication arrangements that your organization has set up with a communication partner using the *Communication Arrangement* application. The system provides communication scenarios for inbound and outbound communication that you can use to create communication arrangements. Inbound communication describes how a communication partner receives business documents, while outbound communication describes how a communication partner sends business documents to a communication partner. The communication scenario specifies the authorizations, inbound and outbound services, and supported authentication methods that are necessary for the communication.

-   **[Create a Communication Arrangement](Create_a_Communication_Arrangement_b7a87fd.md "Create a communication arrangement in the ABAP environment.")**  
Create a communication arrangement in the ABAP environment.
-   **[Sample Code](Sample_Code_76b08e1.md "This topic contains a set of sample codes that can be used to create various classes in
		an ABAP environment.")**  
This topic contains a set of sample codes that can be used to create various classes in an ABAP environment.

