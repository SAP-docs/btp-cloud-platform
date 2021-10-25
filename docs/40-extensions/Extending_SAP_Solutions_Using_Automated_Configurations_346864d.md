<!-- loio346864df64f24011b49abee07bbd79af -->

# Extending SAP Solutions Using Automated Configurations

The extension capabilities of SAP Business Technology Platform \(SAP BTP\) enables developers to implement loosely coupled extension applications securely, thus implementing additional workflows or modules on top of the existing SAP cloud solution they already have.



<a name="loio346864df64f24011b49abee07bbd79af__section_ptj_pmf_nhb"/>

## Overview

With the automated configuration you have the following key benefits:

-   A way of extending standard SAP solutions without disrupting their performance and core processes

-   Frameworks that offer simplified, standardized, and unified extensibility and configuration for SAP solutions

-   A central repository for solutions' APIs, events, credentials, and other data, thereby ensuring easy access to services while creating your extensions




<a name="loio346864df64f24011b49abee07bbd79af__section_tsg_vmf_nhb"/>

## Process Flow

You can use the extension capabilities of SAP BTP to implement additional workflows or modules on top of your existing SAP solutions. You can extend one or more SAP solutions grouped together in a common business case. The following SAP system types are supported:

-   SAP S/4HANA Cloud

-   SAP Marketing Cloud

-   SAP SuccessFactors

-   SAP Commerce Cloud

-   SAP Cloud for Customer

-   SAP Field Service Management


To enable the integration, you need to:

1.  Connect the corresponding SAP system with the global account.

    During the pairing process you create an integration token which is then used by the SAP system administrator to configure the integration on the SAP system side. See [Registering an SAP System](Registering_an_SAP_System_2ffdaff.md).

2.  Make the SAP system accessible in the subaccounts in which you want to build your extension applications.

    To do so, you create a formation containing one or more different systems assigned to a common subaccount. See [Assigning SAP Systems to a Formation](Assigning_SAP_Systems_to_a_Formation_68b04fa.md).

    For the systems of type SAP Commerce Cloud, SAP Cloud for Customer, and SAP Field Service Management, you can continue with developing your extension application.

    For systems of type SAP S/4HANA Cloud, SAP Marketing Cloud, and SAP SuccessFactors, configure the entitlements and assign the corresponding quota and service plans to the subaccounts where the extension applications will reside. The service plans define the access to the corresponding SAP solution APIs.

3.  For systems of type SAP S/4HANA Cloud, SAP Marketing Cloud, and SAP SuccessFactors, configure the communication flow for the extension application.

    To be able to consume the SAP S/4HANA Cloud, SAP Marketing Cloud, and SAP SuccessFactors APIs, you need to create a service instance for the corresponding SAP solution system. During the creation of the service instance, you configure the communication flow between the subaccount and the corresponding SAP solution. An HTTP destination which contains the binding properties for establishing the connection is automatically generated.

    After you have created the service instance, you have two options to configure the extension application's connectivity to the corresponding SAP solution:

    -   Consume the HTTP destination

    -   Bind the service instance to the extension application



**Related Information**  


[Extending SAP S/4HANA Cloud in the Cloud Foundry and Kyma Environment](Extending_SAP_S4HANA_Cloud_in_the_Cloud_Foundry_and_Kyma_Environment_40b9e6c.md "Extend SAP S/4HANA Cloud with extension applications running on the cloud platform using automated integration configuration.")

[Extending SAP SuccessFactors in the Cloud Foundry and Kyma Environment](Extending_SAP_SuccessFactors_in_the_Cloud_Foundry_and_Kyma_Environment_9e33934.md "Use SAP BTP to extend SAP SuccessFactors with extension applications running on the cloud platform.")

[Extending SAP Customer Experience Products in the Kyma Environment](Extending_SAP_Customer_Experience_Products_in_the_Kyma_Environment_83df31a.md "You can configure the integration between SAP BTP and SAP Customer Experience automatically to extend SAP Customer Experience products with applications running on the cloud platform.")

