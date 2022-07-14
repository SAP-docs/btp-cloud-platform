<!-- loio3a3f0e1eca5f4962bc7ff436424cc048 -->

# Business Users

**User accounts** enable users to log on to SAP BTP and access subaccounts and use services according to the permissions given to them. In this context, it's important to understand the difference between the 2 types of users that we refer to: **Business users** and **[platform users](platform-users-9e5e635.md)**.

**Business users** use the applications that are deployed to SAP BTP. For example, the end users of SaaS apps or services, such as SAP Workflow service or SAP Cloud Integration, or end users of your custom applications are business users.

In the Cloud Foundry environment, application developers \([platform users](platform-users-9e5e635.md)\) create and deploy application-based security artifacts for business users. Administrators use these artifacts to assign roles, build role collections, and then assign those role collections to business users or user groups. This allows them to control the permissions that the users have in the deployed applications.

For business users, there's a [default identity provider](default-identity-provider-d6a8db7.md). We expect that you have your own user base. We recommend that you configure the Identity Authentication service as the identity provider and connect Identity Authentication to your own corporate identity provider.

**Related Information**  


[161f8f0cfac64c4fa2d973bc5f08a894.md](establish-trust-and-federation-between-uaa-and-identity-authentication-161f8f0.md)

[7c6aa87459764b179aeccadccd4f91f3.md\#loio7c6aa87459764b179aeccadccd4f91f3](manually-establish-trust-and-federation-between-uaa-and-identity-authentication-7c6aa87.md#loio7c6aa87459764b179aeccadccd4f91f3)

[2ce3938c66d94479848bff3090999027.md\#loio2ce3938c66d94479848bff3090999027](establish-trust-and-federation-with-uaa-using-any-saml-identity-provider-2ce3938.md#loio2ce3938c66d94479848bff3090999027)

[b8c0aac0e86944cf984b672dea2f38d0.md](provide-logon-link-help-to-identity-provider-for-business-users-b8c0aac.md)

