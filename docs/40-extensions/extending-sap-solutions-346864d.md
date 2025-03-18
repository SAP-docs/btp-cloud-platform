<!-- loio346864df64f24011b49abee07bbd79af -->

# Extending SAP Solutions

The extension capabilities of SAP Business Technology Platform \(SAP BTP\) enables developers to implement loosely coupled extension applications securely, thus implementing additional workflows or modules on top of the existing SAP cloud solution they already have.



<a name="loio346864df64f24011b49abee07bbd79af__section_ptj_pmf_nhb"/>

## Overview

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

With the automated configuration you have the following key benefits:

-   A way of extending standard SAP solutions without disrupting their performance and core processes

-   Frameworks that offer simplified, standardized, and unified extensibility and configuration for SAP solutions

-   A central repository for solutions' APIs, events, credentials, and other data, thereby ensuring easy access to services while creating your extensions


You can also use dedicated formations that help you integrate automaticatically the SAP solution you want to extend with runtimes and tools you might need. See:

-   [Setting Up System Landscape for Kyma](setting-up-system-landscape-for-kyma-9154051.md)
-   [Setting Up System Landscape for SAP Build](setting-up-system-landscape-for-sap-build-6424311.md)
-   [Setting Up System Landscape for SAP Integration Suite](setting-up-system-landscape-for-sap-integration-suite-a14c276.md)
-   [Setting Up System Landscape for SAP Business Application Studio](setting-up-system-landscape-for-sap-business-application-studio-272ca23.md)



<a name="loio346864df64f24011b49abee07bbd79af__section_tsg_vmf_nhb"/>

## Process Flow

You can use the extension capabilities of SAP BTP to implement additional workflows or modules on top of your existing SAP solutions. You can extend one or more SAP solutions grouped together in a common business case.

To enable the integration, you need to:

1.  Connect the corresponding SAP system with the global account.

    -   For systems of type SAP S/4HANA Cloud, SAP Marketing Cloud, SAP SuccessFactors and SAP systems from the SAP Customer Experience portfolio, during the pairing process you create an registration token which is then used by the SAP system administrator to configure the registration on the SAP system side. See [Registering and Deregistering Systems](registering-and-deregistering-systems-2ffdaff.md).

    -   For systems of type different than SAP S/4HANA Cloud, SAP Marketing Cloud, SAP SuccessFactors and SAP systems from the SAP Customer Experience portfolio, the SAP system is already registered when it's part of the *Systems* page. However, in the *Status* column, there is no status shown. See [Registering and Deregistering Systems](registering-and-deregistering-systems-2ffdaff.md).

    -   For third-party systems, the system is already registered when it's part of the *Systems* page. However, in the *Status* column, there is no status shown. See [Register a Third-Party System](register-a-third-party-system-5481d59.md).


    > ### Note:  
    > You cannot migrate the registered SAP systems between global accounts.
    > 
    > If you want to start using another global account, you will have to register your SAP systems again.

2.  Optional: Group SAP systems so that they can be extended in a business scenario at one go.

    To do so, you create a formation containing one or more different systems assigned to a common subaccount. See [Automating Integrations Using Formations](automating-integrations-using-formations-68b04fa.md).

3.  Make the SAP system accessible in the subaccounts in which you want to build your extension applications.

    For systems of type SAP S/4HANA Cloud, SAP Marketing Cloud, and SAP SuccessFactors, configure the entitlements and assign the corresponding quota and service plans to the subaccounts where the extension applications will reside. The service plans define the access to the corresponding SAP solution APIs. See:

    -   [Configure the Entitlements for the SAP S/4HANA Cloud Extensibility Service](configure-the-entitlements-for-the-sap-s-4hana-cloud-extensibility-service-65ad330.md)

    -   [Configure the Entitlements for the SAP SuccessFactors Extensibility Service](configure-the-entitlements-for-the-sap-successfactors-extensibility-service-b01e625.md)


    For the systems of type different than SAP S/4HANA Cloud, SAP Marketing Cloud, and SAP SuccessFactors, you can continue with developing your extension application.

4.  For systems of type SAP S/4HANA Cloud, SAP Marketing Cloud, and SAP SuccessFactors, configure the communication flow for the extension application.

    To be able to consume the SAP S/4HANA Cloud, SAP Marketing Cloud, and SAP SuccessFactors APIs, you need to create a service instance for the corresponding SAP solution system. During the creation of the service instance, you configure the communication flow between the subaccount and the corresponding SAP solution. An HTTP destination which contains the binding properties for establishing the connection is automatically generated.

    After you have created the service instance, you have two options to configure the extension application's connectivity to the corresponding SAP solution:

    -   Consume the HTTP destination

    -   Bind the service instance to the extension application



**Related Information**  


[Extending SAP S/4HANA Cloud in the Cloud Foundry and Kyma Environment](extending-sap-s-4hana-cloud-in-the-cloud-foundry-and-kyma-environment-40b9e6c.md "Extend SAP S/4HANA Cloud with extension applications running on SAP BTP using automated integration configuration.")

[Extending SAP SuccessFactors in the Cloud Foundry and Kyma Environment](extending-sap-successfactors-in-the-cloud-foundry-and-kyma-environment-9e33934.md "Use SAP BTP to extend SAP SuccessFactors with extension applications running on the cloud platform.")

[Extending SAP Customer Experience Products in the Kyma Environment](extending-sap-customer-experience-products-in-the-kyma-environment-83df31a.md "You can configure the integration between SAP BTP and SAP Customer Experience automatically to extend SAP Customer Experience products with applications running on the cloud platform.")

[Extending SAP Marketing Cloud in the Cloud Foundry and Kyma Environment](extending-sap-marketing-cloud-in-the-cloud-foundry-and-kyma-environment-18bb3d9.md "")

