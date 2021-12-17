<!-- loioeaa6a26291914b348e875a00b6beb729 -->

# Building Roles and Role Collections for Applications

As an administrator of the Cloud Foundry environment of SAP BTP, you can maintain application roles and role collections which can be used in user management.

The user roles are derived from role templates that are defined in the security description \(`xs-security.json`\) of applications that have been registered as OAuth 2.0 clients at the User Account and Authentication service during application deployment. The application security-descriptor file also contains details of the authorization scopes that are used for application access and defines any attributes that need to be applied. The roles you create can be added to role collections.

You can perform the following tasks:

-   Create and delete user roles

    User roles define authorization scopes and are based on the role templates and scopes defined in the application's security descriptor file

-   Add user roles to one or more “role collections”
-   Configure and manage role collections

> ### Tip:  
> Using the SAP BTP cockpit, you can assign the role collections to users logging on with SAML 2.0 assertions or SAP ID service.

**Related Information**  


[Add Roles to Role Collections on the Application Level](add-roles-to-role-collections-on-the-application-level-7596a0b.md "Roles are used to define the type of access granted to an application.")

[Maintain Role Collections](maintain-role-collections-d5f1612.md "Role collections group together different roles that can be applied to the application users.")

[Mapping Role Collections in the Subaccount](mapping-role-collections-in-the-subaccount-9e1bf57.md "You have arranged roles in role collections, and now want to assign or map these role collections to business users.")

[Protecting Your Application](../30-development/protecting-your-application-7c5c565.md "Developers create authorization information for business users in their environment; this information is deployed in an application and made available to administrators who complete the authorization setup and assign the authorizations to business users.")

[Working with Role Collections](working-with-role-collections-393ea0b.md "You can manage role collections by creating new ones from scratch or by copying an existing one and editing it. You can add or remove roles. You can also add or remove users or user groups to the role collections. This is the assignment or unassignment action. You can drill down all the way to the role definition or to the individual role, user, and user group, and make changes there.")

