<!-- loio393ea0b222754311884123ce564779bd -->

# Working with Role Collections

As an administrator, you group application roles in role collections. You then assign role collections to application users.

Application developers have defined application-specific role templates in the security descriptor file. The role templates contain the role definitions. You can assign the role to a role collection.

> ### Tip:  
> Application developers can even directly define role collections with default roles. For more information, see [Create Role Collections with Predefined Roles](../30-development/create-role-collections-with-predefined-roles-fe75054.md).

Typically, these role collections provide authorizations for certain types of users, for example, sales representatives.

Once you have created a role collection, you can pick the roles that apply to the typical job of a sales representative. Since the roles are application-based, you must reference the application to see which roles come with the role template of this application. You are free to add roles from multiple applications to your role collection.

Finally, you assign the role collection directly to users or indirectly to attributes such as groups. For more information, see the related link.



<a name="loio393ea0b222754311884123ce564779bd__section_vw4_bw4_qlb"/>

## Prerequisites

-   Your user has administration rights in this subaccount and or global account. For more information, see [Security Administration: Managing Authentication and Authorization](security-administration-managing-authentication-and-authorization-1ff47b2.md) or [Role Collections and Roles in Global Accounts, Directories, and Subaccounts](../10-concepts/role-collections-and-roles-in-global-accounts-directories-and-subaccounts-0039cf0.md).

-   The roles defined by your application developers in the application security descriptor are available in the SAP BTP cockpit. For more information, see [Adding Authentication and Authorization](../30-development/adding-authentication-and-authorization-419ae2e.md).

-   The users are stored in identity providers that are connected to SAP BTP.

    -   Default identity provider \(`SAP ID service`\). For more information, see [Default Identity Provider](default-identity-provider-d6a8db7.md).

    -   Custom identity provider. For more information, see [User Management](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/228428f9f476449cafd841a68d75b234.html) in SAP Cloud Identity Services.



> ### Note:  
> SAP BTP provides default role collections. You can use the default role collections, but you can’t change or delete them. For this reason, the *Delete* icon of a default role collection is grayed out.



You can perform the following tasks:

-   [Define a Role Collection](define-a-role-collection-4b20383.md)

    -   [Add Roles to a Role Collection](add-roles-to-a-role-collection-e3130fb.md)

    -   [Delete Roles from a Role Collection](delete-roles-from-a-role-collection-b06be74.md)



-   [Assigning Role Collections to Users or User Groups](assigning-role-collections-to-users-or-user-groups-31532c7.md)

    -   [Assign Users to Role Collections](assign-users-to-role-collections-c576676.md)

    -   [Delete Users from Role Collections](delete-users-from-role-collections-4f8a242.md)

    -   [Assign User Groups to Role Collections](assign-user-groups-to-role-collections-9562d9d.md)

    -   [Delete User Groups from Role Collections](delete-user-groups-from-role-collections-bcc818a.md)



**Related Information**  


[Security Administration: Managing Authentication and Authorization](security-administration-managing-authentication-and-authorization-1ff47b2.md "This section describes the tasks of administrators of SAP BTP. Administrators ensure user authentication and assign authorization information to users and user groups.")

[Role Collections and Roles in Global Accounts, Directories, and Subaccounts](../10-concepts/role-collections-and-roles-in-global-accounts-directories-and-subaccounts-0039cf0.md "SAP BTP provides a set of role collections to set up administrator access to your global account and subaccounts.")

[Limits for Technical Artifacts of the SAP Authorization and Trust Management Service](../60-security/limits-for-technical-artifacts-of-the-sap-authorization-and-trust-management-service-6d3ef52.md "To improve the resiliency of the SAP Authorization and Trust Management service, we have introduced limitations on technical artifacts of the service.")

