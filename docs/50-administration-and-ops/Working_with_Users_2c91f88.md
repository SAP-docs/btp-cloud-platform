<!-- loio2c91f88e60ea4677a076212085b42d02 -->

# Working with Users

In the SAP BTP cockpit, you can see the users of your global account or subaccount, user-related identity provider information, and their authorizations. In a user's overview, you can create and delete users, and assign role collections. You can also display an overview of the role collections, where you can drill down all the way to the role, and see the application that the role is belongs to.



<a name="loio2c91f88e60ea4677a076212085b42d02__section_zly_111_2nb"/>

## Overview

All users in the global account and in the subaccount are stored in identity provers. Users in the global account of SAP BTP are stored in the default identity provider. Users in the subaccounts of SAP BTP are either stored in the default identity provider or in a custom identity provider.

SAP BTP creates a copy of the user in the global account or in the subaccount when a user-related action happens. This copy of the user is called a shadow user. Global account or subaccount administrators of SAP BTP assign role collections to shadow users. To comply with data protection and privacy regulations, administrators can be obliged to delete users who belonged to employees who left the company.

> ### Note:  
> For access tokens of subaccounts created after September 23, 2020, user IDs preserve the case that they are created in. This means that both uppercase and lowercase letters can be used. However, this does not qualify as a means to differentiate between them; for example, denise.smith@example.com and Denise.Smith@example.com are considered to be the same.
> 
> Subaccounts before this date convert the user IDs to lowercase.



<a name="loio2c91f88e60ea4677a076212085b42d02__section_vw4_bw4_qlb"/>

## Prerequisites

-   You have administration rights in this global account or subaccount. For more information, see [Security Administration: Managing Authentication and Authorization](Security_Administration_Managing_Authentication_and_Authorization_1ff47b2.md) or [Role Collections and Roles in Global Accounts, Directories, and Subaccounts \[Feature Set B\]](../10-concepts/Role_Collections_and_Roles_in_Global_Accounts,_Directories,_and_Subaccounts_Feature_Set_B_0039cf0.md).

-   The users are stored in identity providers that are connected to SAP BTP.

    -   Default identity provider. For more information, see [SAP ID Service](SAP_ID_Service_d6a8db7.md).

    -   Custom identity provider. For more information, see [Trust and Federation with Identity Providers](Trust_and_Federation_with_Identity_Providers_cb1bc8f.md).





<table>
<tr>
<th>

Use Case



</th>
<th>

Description



</th>
</tr>
<tr>
<td rowspan="2">

Enable a new hire to log on to the subaccount and have access to necessary resources.



</td>
<td>

If automatic creation of shadow users was switched off for this identity provider, shadow users aren't created automatically in the subaccount \(see the related link\). This means that the new user can't log on to the subaccount. As an administrator, create a shadow user that corresponds to the user in the identity provider and assign the necessary role collections to this user.

See [Create Users](Create_Users_a3bc7e8.md).



</td>
</tr>
<tr>
<td>

If automatic creation of shadow users was switched off for this identity provider, shadow users aren't created automatically in the subaccount \(see the related link\). Add the user group to the role collections that are necessary for this user if the user belongs to a user group in the identity provider.

See [Assign User Groups to Role Collections](Assign_User_Groups_to_Role_Collections_9562d9d.md).



</td>
</tr>
<tr>
<td>

Enable a new hire to have access to necessary resources.



</td>
<td>

A shadow user is automatically created in the subaccount. This means that the new user can log on to the subaccount, but the user doesn't have any authorizations. As an administrator, you have created new role collections or you want to use existing ones for the new hire. You grant authorizations by assigning the role collections to this user.

See [Assign Users to Role Collections](Assign_Users_to_Role_Collections_c576676.md).



</td>
</tr>
<tr>
<td rowspan="2">

Enable a new hire to log on.



</td>
<td>

If automatic creation of shadow users was switched off for this identity provider, shadow users aren't created automatically in the subaccount \(see the related link\). As an administrator, create a new shadow user in the subaccount.

See [Create Users](Create_Users_a3bc7e8.md).



</td>
</tr>
<tr>
<td>

If your subaccount uses the default trust configuration, you can also create a shadow user there.

See [Add Users from SAP ID Service for Multi-Environment Subaccounts](Add_Users_from_SAP_ID_Service_for_Multi-Environment_Subaccounts_760ab77.md).



</td>
</tr>
<tr>
<td>

Review authorizations of individual users.



</td>
<td>

You want to find out which authorizations have been granted to users. To do so, access the list of all users, find the users you want to review, and check the role collection assignments. From the user's role collection, you can drill down to the roles of the role collection. You can also assign and remove role collections.

See [Find Users and Their Role Collection Assignments](Find_Users_and_Their_Role_Collection_Assignments_870533e.md).



</td>
</tr>
<tr>
<td>

Delete users of employees who have left the company.



</td>
<td>

You want to find and delete users of employees who have left the company, but their users still exist in the system.

How to find users, see [Find Inactive Users](Find_Inactive_Users_90380a6.md).

How to delete users, see [Delete Users](Delete_Users_51000c2.md).



</td>
</tr>
<tr>
<td>

Find users who have never logged on.



</td>
<td>

You want to find users who never logged on. For example, they could be manually created shadow users with a typo in their user ID, so they don't match the user ID provided by the identity provider. They were never used, and it might make sense to delete them.

See [Delete Users](Delete_Users_51000c2.md).



</td>
</tr>
<tr>
<td rowspan="2">

Delete shadows user to comply with data protection and privacy regulations.



</td>
<td>

For data protection and privacy reasons, administrators might be legallly obliged to delete shadow users who belonged to employees who left the company. You can find and delete the shadow users in the SAP BTP cockpit.

See [Delete Users](Delete_Users_51000c2.md).



</td>
</tr>
<tr>
<td>

You can also delete the users using APIs.

See [Delete Shadow Users for Data Protection and Privacy Using APIs](../60-security/Delete_Shadow_Users_for_Data_Protection_and_Privacy_Using_APIs_eb70f16.md).



</td>
</tr>
</table>

-   **[Find Users and Their Role Collection Assignments](Find_Users_and_Their_Role_Collection_Assignments_870533e.md "You want to find the authorizations granted to specific users in your subaccount. You
		can search or sort the list of users, and view their role collection
		assignments.")**  
You want to find the authorizations granted to specific users in your subaccount. You can search or sort the list of users, and view their role collection assignments.
-   **[Find Inactive Users](Find_Inactive_Users_90380a6.md "As an administrator, you want to have an overview of the users in your subaccount, no
		matter which identity provider stores them. You want to clean them up if
		necessary.")**  
As an administrator, you want to have an overview of the users in your subaccount, no matter which identity provider stores them. You want to clean them up if necessary.
-   **[Create Users](Create_Users_a3bc7e8.md "As an administrator, you can create shadow users in your subaccount. When you create
		a shadow user, you must know and specify which identity provider stores the
		user.")**  
As an administrator, you can create shadow users in your subaccount. When you create a shadow user, you must know and specify which identity provider stores the user.
-   **[Delete Users](Delete_Users_51000c2.md "As an administrator, you can delete users from your subaccount. When you delete a user,
		you also delete the user's role collection assignments.")**  
As an administrator, you can delete users from your subaccount. When you delete a user, you also delete the user's role collection assignments.

**Related Information**  


[Switch Off Automatic Creation of Shadow Users](Switch_Off_Automatic_Creation_of_Shadow_Users_d852567.md "To switch off the creation of shadow users in the trust configuration of custom identity providers, administrators must explicitly allow users to log on. Administrators then have full control over who is allowed to log on.")

[Security Administration: Managing Authentication and Authorization](Security_Administration_Managing_Authentication_and_Authorization_1ff47b2.md "This section describes the tasks of administrators in the Cloud Foundry environment of SAP BTP. Administrators ensure user authentication and assign authorization information to users and user groups.")

[Role Collections and Roles in Global Accounts, Directories, and Subaccounts \[Feature Set B\]](../10-concepts/Role_Collections_and_Roles_in_Global_Accounts,_Directories,_and_Subaccounts_Feature_Set_B_0039cf0.md "In the cloud management tools feature set B, SAP BTP provides a set of role collections to set up administrator access to your global account and subaccounts.")

