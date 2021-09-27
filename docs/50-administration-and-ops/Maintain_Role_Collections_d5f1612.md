<!-- loiod5f1612d8230448bb6c02a7d9c8ac0d1 -->

# Maintain Role Collections

Role collections group together different roles that can be applied to the application users.

Application developers have defined application-specific role templates in the security descriptor file. The role templates contain the role definitions. You can assign the role to a role collection.

> ### Tip:  
> Application developers can even directly define role collections with default roles. For more information, see [Create Role Collections with Predefined Roles](../30-development/Create_Role_Collections_with_Predefined_Roles_fe75054.md).

As an administrator of the Cloud Foundry environment of SAP BTP, you can group application roles in role collections. Typically, these role collections provide authorizations for certain types of users, for example, sales representatives.

Once you have created a role collection, you can pick the roles that apply to the typical job of a sales representative. Since the roles are application-based, you must reference the application to see which roles come with the role template of this application. You are free to add roles from multiple applications to your role collection.

Finally, you assign the role collection to the users provided by the `SAP ID service` or by your identity provider or to SAML 2.0 user groups, for example, sales representatives. For more information, see the related link.

-   **[Managing SAML 2.0 Identity Provider](Managing_SAML_2.0_Identity_Provider_8e0038c.md "If you want to use assertion attributes, set up SAML trust to configure the SAML
		identity providers (IDP) for runtime of the Cloud
                                Foundry
		environment. You must perform this step if you want your applications to use SAML assertions
		as the logon authentication method.")**  
If you want to use assertion attributes, set up SAML trust to configure the SAML identity providers \(IDP\) for runtime of the Cloud Foundry environment. You must perform this step if you want your applications to use SAML assertions as the logon authentication method.

**Related Information**  


[Working with Role Collections](Working_with_Role_Collections_393ea0b.md "You can manage role collections by creating new ones from scratch or by copying an existing one and editing it. You can add or remove roles. You can also add or remove users or user groups to the role collections. This is the assignment or unassignment action. You can drill down all the way to the role definition or to the individual role, user, and user group, and make changes there.")

