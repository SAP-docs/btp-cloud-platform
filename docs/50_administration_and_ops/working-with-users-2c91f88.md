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

-   You have administration rights in this global account, subaccount, or directory. For more information, see [Security Administration: Managing Authentication and Authorization](security-administration-managing-authentication-and-authorization-1ff47b2.md) or [Role Collections and Roles in Global Accounts, Directories, and Subaccounts \[Feature Set B\]](../10_concepts/role-collections-and-roles-in-global-accounts-directories-and-subaccounts-feature-set-b-0039cf0.md).

-   The users are stored in identity providers that are connected to SAP BTP.

    -   Default identity provider. For more information, see [SAP ID Service](sap-id-service-d6a8db7.md).

    -   Custom identity provider. For more information, see [Trust and Federation with Identity Providers](trust-and-federation-with-identity-providers-cb1bc8f.md).






<table>
<tr>
<th valign="top">

Use Case



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top" rowspan="2">

Enable a new hire to log on to the subaccount and have access to necessary resources.



</td>
<td valign="top">

If automatic creation of shadow users was switched off for this identity provider, shadow users aren't created automatically in the subaccount \(see the related link\). This means that the new user can't log on to the subaccount. As an administrator, create a shadow user that corresponds to the user in the identity provider and assign the necessary role collections to this user.

See [Create Users](create-users-a3bc7e8.md).



</td>
</tr>
<tr>
<td valign="top">

If automatic creation of shadow users was switched off for this identity provider, shadow users aren't created automatically in the subaccount \(see the related link\). Add the user group to the role collections that are necessary for this user if the user belongs to a user group in the identity provider.

See [Assign User Groups to Role Collections](assign-user-groups-to-role-collections-9562d9d.md).



</td>
</tr>
<tr>
<td valign="top">

Enable a new hire to have access to necessary resources.



</td>
<td valign="top">

A shadow user is automatically created in the subaccount. This means that the new user can log on to the subaccount, but the user doesn't have any authorizations. As an administrator, you have created new role collections or you want to use existing ones for the new hire. You grant authorizations by assigning the role collections to this user.

See [Assign Users to Role Collections](assign-users-to-role-collections-c576676.md).



</td>
</tr>
<tr>
<td valign="top" rowspan="2">

Enable a new hire to log on.



</td>
<td valign="top">

If automatic creation of shadow users was switched off for this identity provider, shadow users aren't created automatically in the subaccount \(see the related link\). As an administrator, create a new shadow user in the subaccount.

See [Create Users](create-users-a3bc7e8.md).



</td>
</tr>
<tr>
<td valign="top">

If your subaccount uses the default trust configuration, you can also create a shadow user there.

See [Add Users from SAP ID Service for Multi-Environment Subaccounts](add-users-from-sap-id-service-for-multi-environment-subaccounts-760ab77.md).



</td>
</tr>
<tr>
<td valign="top">

Review authorizations of individual users.



</td>
<td valign="top">

You want to find out which authorizations have been granted to users. To do so, access the list of all users, find the users you want to review, and check the role collection assignments. From the user's role collection, you can drill down to the roles of the role collection. You can also assign and remove role collections.

See [Find Users and Their Role Collection Assignments](find-users-and-their-role-collection-assignments-870533e.md).



</td>
</tr>
<tr>
<td valign="top">

Delete users of employees who have left the company.



</td>
<td valign="top">

You want to find and delete users of employees who have left the company, but their users still exist in the system.

How to find users, see [Find Inactive Users](find-inactive-users-90380a6.md).

How to delete users, see [Delete Users](delete-users-51000c2.md).



</td>
</tr>
<tr>
<td valign="top">

Find users who have never logged on.



</td>
<td valign="top">

You want to find users who never logged on. For example, they could be manually created shadow users with a typo in their user ID, so they don't match the user ID provided by the identity provider. They were never used, and it might make sense to delete them.

See [Delete Users](delete-users-51000c2.md).



</td>
</tr>
<tr>
<td valign="top" rowspan="2">

Delete shadows user to comply with data protection and privacy regulations.



</td>
<td valign="top">

For data protection and privacy reasons, administrators might be legallly obliged to delete shadow users who belonged to employees who left the company. You can find and delete the shadow users in the SAP BTP cockpit.

See [Delete Users](delete-users-51000c2.md).



</td>
</tr>
<tr>
<td valign="top">

You can also delete the users using APIs.

See [Delete Shadow Users for Data Protection and Privacy Using APIs](../60_security/delete-shadow-users-for-data-protection-and-privacy-using-apis-eb70f16.md).



</td>
</tr>
</table>

**Related Information**  


[Switch Off Automatic Creation of Shadow Users](switch-off-automatic-creation-of-shadow-users-d852567.md "To switch off the creation of shadow users in the trust configuration of custom identity providers, administrators must explicitly allow users to log on. Administrators then have full control over who is allowed to log on.")

[Security Administration: Managing Authentication and Authorization](security-administration-managing-authentication-and-authorization-1ff47b2.md "This section describes the tasks of administrators in the Cloud Foundry environment of SAP BTP. Administrators ensure user authentication and assign authorization information to users and user groups.")

[Role Collections and Roles in Global Accounts, Directories, and Subaccounts \[Feature Set B\]](../10_concepts/role-collections-and-roles-in-global-accounts-directories-and-subaccounts-feature-set-b-0039cf0.md "In the cloud management tools feature set B, SAP BTP provides a set of role collections to set up administrator access to your global account and subaccounts.")

