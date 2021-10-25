<!-- loio31532c77bd61421e9d40d100fd75ef52 -->

# Assigning Role Collections to Users or User Groups

You can assign role collections to users and user groups.



<a name="loio31532c77bd61421e9d40d100fd75ef52__section_vw4_bw4_qlb"/>

## Prerequisites

-   You have administration rights in this subaccount or global account. For more information, see [Security Administration: Managing Authentication and Authorization](Security_Administration_Managing_Authentication_and_Authorization_1ff47b2.md) or [Role Collections and Roles in Global Accounts, Directories, and Subaccounts \[Feature Set B\]](../10-concepts/Role_Collections_and_Roles_in_Global_Accounts,_Directories,_and_Subaccounts_Feature_Set_B_0039cf0.md).

-   The roles defined by your application developers in the application security descriptor are available in the SAP BTP cockpit. For more information, see [Adding Authentication and Authorization](../30-development/Adding_Authentication_and_Authorization_419ae2e.md).

-   The users are stored in identity providers that are connected to SAP BTP.

    -   Default identity provider \(`SAP ID service`\). For more information, see [SAP ID Service](SAP_ID_Service_d6a8db7.md).

    -   Custom identity provider. For more information, see [User Management](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/228428f9f476449cafd841a68d75b234.html) in SAP Cloud Identity Services - Identity Authentication.





You perform the following tasks to assign role collections to users and user groups stored by identity providers. The identity providers are connected to SAP BTP using trust configurations.

> ### Note:  
> Custom identity providers can provide user groups and users whereas default identity providers can only provide individual users.

-   [Assign Users to Role Collections](Assign_Users_to_Role_Collections_c576676.md)

-   [Delete Users from Role Collections](Delete_Users_from_Role_Collections_4f8a242.md)

-   [Assign User Groups to Role Collections](Assign_User_Groups_to_Role_Collections_9562d9d.md)

-   [Delete User Groups from Role Collections](Delete_User_Groups_from_Role_Collections_bcc818a.md)


