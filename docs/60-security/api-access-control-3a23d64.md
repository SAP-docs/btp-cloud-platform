<!-- loio3a23d64d74574a18a551d13fe11b94b1 -->

# API Access Control

The Cloud Foundry environment extends SAP BTP. It provides platform security functions such as business system authentication, authorization management, and other security functions to enable business systems to access the applications \(for example, Java or Node.js\) in the runtime container. Business systems use APIs to access the runtime container.

A business system uses APIs to directly access the resources in the runtime container.

The following diagram shows the architecture with the components that are responsible for business system authentication, authorization management, and security.

![](images/API_Access_Diagram_e9d66bf.png)

The User Account and Authentication \(UAA\) component is the central infrastructure component of the runtime platform for authentication and authorization management. The users can be stored in the following identity providers:

-   SAP Cloud Identity Services

-   Any identity provider


Business system use APIs to directly access the resources in the runtime container. The UAA acts as an OAuth authorization server and issues an appropriate access token. It enables the business system to directly access an application in the runtime container. Runtime containers act as OAuth resource servers, using the container security API of the relevant container \(for example, Java\) to validate the token issued by the OAuth authorization server.

**Related Information**  


[Protecting Your Application](../30-development/protecting-your-application-7c5c565.md "Developers create authorization information for business users in their environment; this information is deployed in an application and made available to administrators who complete the authorization setup and assign the authorizations to business users.")

[Tutorials for the SAP Authorization and Trust Management Service](../30-development/tutorials-for-the-sap-authorization-and-trust-management-service-902ae80.md "Follow the tutorials below to get familiar with the SAP Authorization and Trust Management service in the Cloud Foundry environment of SAP BTP.")

