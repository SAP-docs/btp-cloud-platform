<!-- loio64da613776814c3f8d899686dee558ca -->

# Single Sign-On Between a Subaccount in SAP BTP and SAP SuccessFactors

Use this procedure to configure the single sign-on \(SSO\) between SAP BTP and the SAP SuccessFactors system.

When a user attempts to access SAP SuccessFactors for the first time, the system redirects the user to the identity provider for authentication. From then on, the user session is kept active, and the user is no longer prompted for credentials when trying to use the SAP SuccessFactors application. This is called single sign-on \(SSO\).



## Using Identity Authentication

You can use Identity Authentication to set up the single sign-on \(SSO\) between SAP SuccessFactors and SAP BTP. Identity Authentication provides you with controlled cloud-based access to business processes, applications, and data. It simplifies your user experience through authentication mechanisms, single sign-on, on-premise integration, and convenient self-service options. We recommend using Identity Authentication as a central point to integrate SAP applications for a seamless single sign-on experience.

-   Authentication: All SAP cloud applications can offer their users the same authentication mechanisms​, as well as strong authentication with configurable multi-factor \(MFA\) enforcement; easy separation mechanism for multiple user stores and flexible configuration where to validate user's credentials.

-   Single Sign-On: Identity Authentication offers central SSO endpoint for all SAP cloud applications and pre-configured or semi-automated trust configuration​.

-   Integrating SAP applications: Identity Authentication offers common identity for users, as well as a unified way for user management and security token service for protection of ​system-to-system communication. Data across applications can be correlated​.


See [SAP SuccessFactors Integration Scenario](https://help.sap.com/docs/cloud-identity/system-integration-guide/sap-successfactors-integration-scenario?version=Cloud).



## Using SAP SuccessFactors as a Trusted Identity Provider



### Prerequisites

You have the *UI and Role Administrator* role assigned to your user. See [Security Administration: Managing Authentication and Authorization](../50-administration-and-ops/security-administration-managing-authentication-and-authorization-1ff47b2.md).



### Context

The authentication to SAP SuccessFactors applications is restricted to the authorized users. The identification of a user is verified by the identity provider, as specified by SAML 2.0. The identity provider stores a list of all users that are allowed to access the SAP SuccessFactors system along with their credentials. The integration between the SAP SuccessFactors and the identity provider is based on a trust configuration.

To ensure the required security for accessing the applications, you need to configure the single sign-on between the subaccount in SAP BTP and the SAP SuccessFactors system using a SAML identity provider. The single sign-on requires both solutions to be configured as trusted SAML service providers for the identity provider, and at the same time, the identity provider to be configured as trusted identity provider for the two solutions.

Use a subaccount in SAP BTP with the SAP BTP, Cloud Foundry runtime enabled and follow these steps to set up the single sign-on \(SSO\):

1.  [Configure SAP SuccessFactors as a Trusted Identity Provider in SAP BTP](configure-sap-successfactors-as-a-trusted-identity-provider-in-sap-btp-80a3fd1.md)
2.  [Configure the Subaccount as a Trusted Service Provider in SAP SuccessFactors](configure-the-subaccount-as-a-trusted-service-provider-in-sap-successfactors-9efe2a1.md)

