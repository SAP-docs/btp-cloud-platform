<!-- loio3a3f0e1eca5f4962bc7ff436424cc048 -->

# Business Users

**User accounts** enable users to log on to SAP BTP, access subaccounts, and to use services according to the permissions granted to them. In this context, it's important to understand the difference between the two types of users that we refer to: business users and platform users.

**Business users** use the applications that are deployed to SAP BTP. For example, the end users of SaaS apps or services, such as SAP Workflow service or SAP Cloud Integration, or end users of your custom applications are business users.

In the Cloud Foundry environment, application developers \([platform users](platform-users-9e5e635.md)\) create and deploy application-based security artifacts for business users. Administrators use these artifacts to assign roles, build role collections, and then assign those role collections to business users or user groups. The assignment of role collections enables administrators to control the permissions that the users have in the deployed applications.

For business users, there's a [default identity provider](default-identity-provider-d6a8db7.md). We expect that you have your own user base. We recommend that you configure the SAP Cloud Identity Services service as the identity provider and connect SAP Cloud Identity Services to your own corporate identity provider.

**Related Information**  


[Platform Users](platform-users-9e5e635.md "User accounts enable users to log on to SAP BTP, access subaccounts, and to use services according to the permissions granted to them. In this context, it's important to understand the difference between the two types of users that we refer to: Platform users and business users.")

[Establish Trust and Federation Between SAP Authorization and Trust Management Service and SAP Cloud Identity Services](establish-trust-and-federation-between-sap-authorization-and-trust-management-service-a-161f8f0.md "Use your SAP Cloud Identity Services tenant as an identity provider or a proxy to your own identity provider hosting your business users. This method avoids the upload and download of SAML meta data by using Open ID Connect (OIDC) to establish trust.")

[Manually Establish Trust and Federation Between SAP Authorization and Trust Management Service and SAP Cloud Identity Services](manually-establish-trust-and-federation-between-sap-authorization-and-trust-management-7c6aa87.md#loio7c6aa87459764b179aeccadccd4f91f3 "Use your SAP Cloud Identity Services tenant as an identity provider or a proxy to your own identity provider hosting your business users. Exchange SAML metadata to establish trust with the SAP Cloud Identity Services tenant and then register your subaccount with the tenant. To complete federation, maintain the federation attributes of the user groups.")

[Establish Trust and Federation with UAA Using Any SAML Identity Provider](establish-trust-and-federation-with-uaa-using-any-saml-identity-provider-2ce3938.md#loio2ce3938c66d94479848bff3090999027 "To establish trust, configure the trust configuration of the SAML 2.0 identity provider in your subaccount using the SAP BTP cockpit. Next, register your subaccount in User Account and Authentication service using the administration console of your SAML 2.0 identity provider. To complete federation, maintain the federation attributes of the SAML 2.0 user groups. This makes sure that you can assign authorizations to user groups.")

[Using Multiple Identity Providers from the Same Subaccount](using-multiple-identity-providers-from-the-same-subaccount-b8c0aac.md "You need to use multiple identity providers for different groups of business users. You want to guide business users to the right identity provider for logon.")

