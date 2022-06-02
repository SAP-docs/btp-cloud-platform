<!-- loio393ea0b222754311884123ce564779bd -->

# Working with Role Collections

You can manage role collections by creating new ones from scratch or by copying an existing one and editing it. You can add or remove roles. You can also add or remove users or user groups to the role collections. This is the assignment or unassignment action. You can drill down all the way to the role definition or to the individual role, user, and user group, and make changes there.



<a name="loio393ea0b222754311884123ce564779bd__section_vw4_bw4_qlb"/>

## Prerequisites

-   Your user has administration rights in this subaccount and or global account. For more information, see [Security Administration: Managing Authentication and Authorization](security-administration-managing-authentication-and-authorization-1ff47b2.md) or [Role Collections and Roles in Global Accounts, Directories, and Subaccounts \[Feature Set B\]](../10-concepts/role-collections-and-roles-in-global-accounts-directories-and-subaccounts-feature-set-b-0039cf0.md).

-   The roles defined by your application developers in the application security descriptor are available in the SAP BTP cockpit. For more information, see [Adding Authentication and Authorization](../30-development/adding-authentication-and-authorization-419ae2e.md).

-   The users are stored in identity providers that are connected to SAP BTP.

    -   Default identity provider \(`SAP ID service`\). For more information, see [Default Identity Provider](default-identity-provider-d6a8db7.md).

    -   Custom identity provider. For more information, see [User Management](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/228428f9f476449cafd841a68d75b234.html) in SAP Cloud Identity Services - Identity Authentication.



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


[Security Administration: Managing Authentication and Authorization](security-administration-managing-authentication-and-authorization-1ff47b2.md "This section describes the tasks of administrators in the Cloud Foundry environment of SAP BTP. Administrators ensure user authentication and assign authorization information to users and user groups.")

[Role Collections and Roles in Global Accounts, Directories, and Subaccounts \[Feature Set B\]](../10-concepts/role-collections-and-roles-in-global-accounts-directories-and-subaccounts-feature-set-b-0039cf0.md "In the cloud management tools feature set B, SAP BTP provides a set of role collections to set up administrator access to your global account and subaccounts.")

