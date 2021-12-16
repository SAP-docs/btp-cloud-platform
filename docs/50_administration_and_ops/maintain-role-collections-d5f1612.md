<!-- loiod5f1612d8230448bb6c02a7d9c8ac0d1 -->

# Maintain Role Collections

Role collections group together different roles that can be applied to the application users.

Application developers have defined application-specific role templates in the security descriptor file. The role templates contain the role definitions. You can assign the role to a role collection.

> ### Tip:  
> Application developers can even directly define role collections with default roles. For more information, see [Create Role Collections with Predefined Roles](../30_development/create-role-collections-with-predefined-roles-fe75054.md).

As an administrator of the Cloud Foundry environment of SAP BTP, you can group application roles in role collections. Typically, these role collections provide authorizations for certain types of users, for example, sales representatives.

Once you have created a role collection, you can pick the roles that apply to the typical job of a sales representative. Since the roles are application-based, you must reference the application to see which roles come with the role template of this application. You are free to add roles from multiple applications to your role collection.

Finally, you assign the role collection to the users provided by the `SAP ID service` or by your identity provider or to SAML 2.0 user groups, for example, sales representatives. For more information, see the related link.

**Related Information**  


[Working with Role Collections](working-with-role-collections-393ea0b.md "You can manage role collections by creating new ones from scratch or by copying an existing one and editing it. You can add or remove roles. You can also add or remove users or user groups to the role collections. This is the assignment or unassignment action. You can drill down all the way to the role definition or to the individual role, user, and user group, and make changes there.")

