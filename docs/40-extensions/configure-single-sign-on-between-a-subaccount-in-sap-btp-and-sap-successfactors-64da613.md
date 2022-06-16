<!-- loio64da613776814c3f8d899686dee558ca -->

# Configure Single Sign-On Between a Subaccount in SAP BTP and SAP SuccessFactors

Use this procedure to configure the single sign-on \(SSO\) between SAP BTP and the SAP SuccessFactors system.



<a name="loio64da613776814c3f8d899686dee558ca__prereq_e4k_nsx_ylb"/>

## Prerequisites

You have the *UI and Role Administrator* role assigned to your user. See [Security Administration: Managing Authentication and Authorization](../50-administration-and-ops/security-administration-managing-authentication-and-authorization-1ff47b2.md).



## Context

The authentication to SAP SuccessFactors applications is restricted to the authorized users. The identification of a user is verified by the identity provider, as specified by SAML 2.0. The Identity Authentication service stores a list of all users that are allowed to access the SAP SuccessFactors system along with their credentials. The integration between the SAP SuccessFactors and the identity provider is based on a trust configuration. When a user attempts to access SAP SuccessFactors for the first time, the system redirects the user to the identity provider for identification. From then on, the user session is kept active, and the user is no longer prompted for credentials when trying to use the SAP SuccessFactors application. This is called single sign-on \(SSO\).

To ensure the required security for accessing the applications, you need to configure the single sign-on between the subaccount in SAP BTP and the SAP SuccessFactors system using a SAML identity provider. The single sign-on requires both solutions to be configured as trusted SAML service providers for the identity provider, and at the same time, the identity provider to be configured as trusted identity provider for the two solutions.

If you have an account in the Cloud Foundry environment, you need to set up the single sign-on \(SSO\) according to this environment.



## Procedure

1.  [Configure SAP SuccessFactors as a Trusted Identity Provider in SAP BTP](configure-sap-successfactors-as-a-trusted-identity-provider-in-sap-btp-80a3fd1.md).

2.  [Register the Assertion Consumer Service of the Subaccount in SAP BTP in SAP SuccessFactors](register-the-assertion-consumer-service-of-the-subaccount-in-sap-btp-in-sap-successfactor-de3a1b3.md).

3.  [Register the Assertion Consumer Service for Every Extension Application in SAP SuccessFactors](register-the-assertion-consumer-service-for-every-extension-application-in-sap-successfac-ebc8341.md).


