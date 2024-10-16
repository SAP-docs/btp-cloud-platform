<!-- loio2e684942eb964befa435b5ed6702824a -->

# Business Users

**Business users** use the applications that are deployed to SAP BTP. For example, the end users of SaaS apps or services, such as SAP Build Work Zone, or end users of your custom applications are business users.

Application developers \(platform users\) create and deploy application-specific security artifacts for business users, such as scopes. Administrators use these artifacts to assign roles, build role collections, and assign these role collections to business users or user groups. In this way, they control the users' permissions in the application.

For business users, there's a [default identity provider](../50-administration-and-ops/default-identity-provider-d6a8db7.md), too. We expect that you have your own identity provider. We recommend that you configure your custom tenant of SAP Cloud Identity Services as the identity provider and connect SAP Cloud Identity Services to your own corporate identity provider.



<a name="loio2e684942eb964befa435b5ed6702824a__section_bhj_b1x_jlb"/>

## User Management

**User management** refers to managing authentication and authorization for your business users.

To manage your business users:

1.  Configure trust to an application identity provider in your subaccount.

2.  Create shadow users in your subaccount for your business users in your identity provider.

    When a user accesses a resource, SAP BTP redirects the user to the identity provider for authentication. You assign authorizations to shadow users in SAP BTP.

3.  Assign role collections either directly to users or map them to user groups.

    The role collections were either delivered from the applications to which you subscribed or custom developed by your team.


To learn more about user management, see [Security Administration: Managing Authentication and Authorization](../50-administration-and-ops/security-administration-managing-authentication-and-authorization-1ff47b2.md).

