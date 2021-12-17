<!-- loio6752c4b8435c456ebf67a97ddbbcb267 -->

# Managing Security Administrators in Your Subaccount \[Feature Set A\]

Running on the cloud management tools feature set A: When you create a subaccount, SAP BTP automatically grants your user the role for the administration of business users and their authorizations in the subaccount. Having this role, you can also add or remove other users who will then also be user and role administrators of this subaccount.

After having created a subaccount in SAP BTP, your user automatically has the administration role. This means that your user also has the *Security* tab, where you can perform security administration tasks. As a security administrator, you can manage authentication and authorization in this subaccount, such as configuring trust to identity providers, and assigning role collections to business users.

You can delegate the security administration to other users. Simply add the users as security administrators to your subaccount. SAP BTP grants the `User & Role Administrator` role to these users.

To see the `User & Role Administrator` role and all users with this role, go to your subaccount \(see [Navigate in the Cockpit](navigate-in-the-cockpit-0874895.md)\). Choose *Security* \> *Administrators*.

You can also remove the users who are not supposed to have this role.

> ### Note:  
> All users with the `User & Role Administrator` role can manage this subaccount, including the security administration tasks.

**Related Information**  


[User and Member Management](../10-concepts/user-and-member-management-cc1c676.md "On the cloud platform, member management happens at all levels from global account to space, while user management is done for deployed applications.")

[Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

