<!-- loio51c167750d024d84aaaca699320f6cf8 -->

# Introduction to Identity and Access Management on SAP BTP

Identity and Access Management \(IAM\) is a fundamental capability of SAP Business Technology Platform that controls how you access applications and the platform itself. IAM ensures that the right users have access to the right systems with the appropriate authorizations.

When you work with SAP BTP, understanding Identity and Access Management is essential for securing your landscape and managing user access effectively. The IAM process for users begins in the system of origin where user records are created, continues with granting authorizations to those records, and ensures secure authentication when you access SAP BTP.



## Cloud Identity Services: Your Central IAM Component

Cloud Identity Services play a central role in the IAM reference architecture for SAP software. By establishing these services as a core IAM component, SAP ensures that SAP cloud applications offer a consistent set of integration capabilities for identity lifecycle management and single sign-on. You can also continue using your existing third-party or legacy components, such as a central user store.

Cloud Identity Services are the default integration component for SAP cloud solutions, including SAP BTP. You can use them to protect access to the platform itself and to applications running on SAP BTP. As an SAP BTP customer, you're entitled to at least two tenants of Cloud Identity Services, one for testing and one for production. We recommend using these tenants instead of the default identity provider. If you're using an SAP BTP trial account, you receive one trial tenant.



## The Four Components of Cloud Identity Services

Cloud Identity Services consist of four key components that work together to provide comprehensive identity and access management.



### Identity Authentication

Identity Authentication provides central capabilities for authentication and single sign-on \(SSO\). It offers convenient user self-services such as registration and password resetting for employees and partners. Security features include protecting access to applications, defining risk-based authentication rules, using two-factor authentication, and delegating authentication to other identity providers.

Some key capabilities:

-   Secure authentication for browser-based applications

-   SSO and single logout functionality from anywhere on any device

-   Strong authentication with configurable multi-factor authentication enforcement

-   Risk-based authentication applied to applications, user group assignments, and IP address ranges

-   Support for SAP and third-party applications

-   Password policies at the service-provider application level

-   Customizable look and feel, including company branding

-   User self-services, including registration and password resetting

-   Delegated authentication through integration with corporate identity providers and on-premises user stores

-   Identity federation with corporate identity providers and applications based on SAML 2.0 and OpenID Connect




### Identity Provisioning

Identity Provisioning is a cloud service for managing identity lifecycle processes. It automates these processes and helps you provision identities and related authorization assignments to various cloud and on-premises business applications.

Some key capabilities:

-   Rapid scenario extensions using optimized connectors for provisioning users and groups among multiple supported SAP and non-SAP cloud and on-premises systems

-   Connectors for source, target, or proxy systems in your provisioning scenario, including connectors for SAP BTP global accounts, directories, subaccounts, for the Cloud Foundry and ABAP environments

-   Flexible data transformations, where you can customize connectors using either the graphical editor or the JSON editor

-   Automatic delivery of default provisioning systems for specific SAP cloud solutions

-   Real-time provisioning with dedicated source systems

-   Consumability either directly through built-in APIs or from the user interface, which is integrated into the administration console in Cloud Identity Services

-   SCIM-compliant integration with identity management solutions

-   Support for cloud and on-premises user stores as sources, relying on dedicated integration with local identity stores

-   Comprehensive job scheduling for provisioning processes




### Identity Directory

Identity Directory is the persistency layer inside Cloud Identity Services. This component facilitates identity lifecycle flows and enables important features, such as a central user store for newer SAP BTP applications, which helps you avoid replicating users to every single application.

Identity Directory acts as the central point of truth regarding users of SAP cloud solutions. Users are typically replicated into Identity Directory from your company's user source and central point of truth, either an HR system or a corporate identity management solution.

Some key capabilities:

-   SCIM 2.0 REST API for management of users, groups, and custom schemas

-   Accessibility from the Cloud Identity Services admin console or through its SCIM 2.0 REST API or Identity Provisioning services

-   Custom schema creation

-   Generation of global user IDs

-   Integration with the Authorization Management service and various SAP solutions that rely on user persistence in Identity Directory




### Authorization Management

Authorization Management Service \(AMS\) enables you as an Cloud Identity Services administrator to customize authorization policies of cloud applications and assign them to users.

Application developers declare the detailed authorization model of their application. They group related authorizations into predefined authorization policies \(base policies\), which serve as a foundation for you to design custom policies.

Some key capabilities:

-   Authorization design and assignment in the same user interface

-   Powerful instance-based authorizations \(through configuration of restrictions in the authorization policies\)

-   Easy maintenance of restrictions through value help based on application data

-   Client libraries for Java, Node.js, and Go

-   Tight integration into the Cloud Application Programming model \(CAP\), which supports fully declarative authorization enforcement in typical use cases




## Using Cloud Identity Services with SAP BTP

Cloud Identity Services are the default integration component for SAP cloud solutions and for SAP BTP. You can use them to protect access to the platform, the SAP BTP cockpit itself, or the applications running on top of the platform. For more information about Cloud Identity Services, refer to the [Cloud Identity Services](https://help.sap.com/docs/cloud-identity-services) documentation or explore the [learning journey](https://learning.sap.com/courses/operating-sap-business-technology-platform).

