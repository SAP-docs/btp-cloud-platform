<!-- loio8e6ce969c432437dbaecedea385df8c8 -->

# About User Management in the Cloud Foundry Environment

The Cloud Foundry environment has its own store for user data within SAP BTP. Understanding the relationship between SAP BTP and the Cloud Foundry environment is useful.

All users of Cloud Foundry and SAP BTP are stored in identity providers. Both require a local copy of the users so that you can assign authorizations to those users. When a user tries to log on, the user is forwarded to the identity provider to authenticate. When you add a user as a member to an org or space, there's no check whether or not this user actually exists in the identity provider you specified.

Org members can only be added by an `Org Manager`. If you only have the `Space Manager` role, you can only add space members that are known to the org. To do that, you must first ask your `Org Manager` to add the users as org members with no roles.

> ### Note:  
> All org members implicitly have the `Org User` role.

If you’re the `Org Manager`, you already have the authorizations to add users to the org. When you add a new user as a space member, that user is added automatically as part of the org as well.



<a name="loio8e6ce969c432437dbaecedea385df8c8__section_v45_zb3_fxb"/>

## Cloud Foundry and Shadow Users

Whenever you add a user at the org or space level with the SAP BTP cockpit, SAP BTP also creates the user at the subaccount level, also known as a shadow user. When you use the SAP BTP cockpit to add a user, SAP BTP assigns at least one Cloud Foundry role to the user, namely *Org User* if you don't add any other role. SAP BTPchecks for Cloud Foundry users with a role and creates corresponding shadow users at the subaccount level if no such user exists. Creating users with the Cloud Foundry CLI or Cloud Foundry APIs doesn't add any Cloud Foundry roles by default. Once you add a role to the user, the system ensures that there's a corresponding user at the subaccount level.

> ### Remember:  
> When you delete a user at the Cloud Foundry level, SAP BTP doesn’t delete the corresponding shadow user at the subaccount level.
> 
> When you delete a user at the subaccount level, delete the user at the Cloud Foundry org and space levels, too. Otherwise, the system automatically creates the corresponding user at the subaccount level if the user has a Cloud Foundry role.

For more information about shadow users, see [Working with Users](working-with-users-2c91f88.md).

**Related Information**  


[User and Member Management](../10-concepts/user-and-member-management-cc1c676.md "On SAP BTP, user management takes place at all levels from global account to environment. There are different types of users, such as depending on their roles in the company.")

[About Roles in the Cloud Foundry Environment](about-roles-in-the-cloud-foundry-environment-0907638.md "Roles determine which features users can view and access, and which actions they can initiate.")

[Add Org Members](add-org-members-a4eeaf1.md "In the SAP BTP cockpit, add users as org members and assign roles to grant the users access to information, such as user and quota information in a Cloud Foundry org.")

[Add Organization Members Using the Cloud Foundry Command Line Interface](add-organization-members-using-the-cloud-foundry-command-line-interface-1422a5d.md "You can use the Cloud Foundry Command Line Interface (cf CLI) to add organization members and assign roles to them.")

[Add Space Members](add-space-members-81d0b4d.md "You can add space members and assign roles to them at the space level in the SAP BTP cockpit.")

[Add Space Members Using the Cloud Foundry Command Line Interface](add-space-members-using-the-cloud-foundry-command-line-interface-d23ea8b.md "You can use the Cloud Foundry Command Line Interface (cf CLI) to add space members and assign roles to them.")

