<!-- loiocc1c676b43904066abb2a4838cbd0c37 -->

# User and Member Management

On SAP BTP, member management takes place at all levels from global account to environment, while user management is relevant for business applications.



<a name="loiocc1c676b43904066abb2a4838cbd0c37__section_ygb_5xw_jlb"/>

## User Accounts

A user account corresponds to a particular user in an identity provider, such as the default identity provider or a custom tenant of the Identity Authentication service.

**User accounts** enable users to log on to SAP BTP, access subaccounts, and to use services according to the permissions granted to them.

Before diving into the different user and member management concepts, it's important to understand the difference between the two types of users we’re referring to: **platform users** and **business users**.

![]()

![Platform Users and Business Users](images/user-accounts_27c8463.png)

**Related Information**  


[Working with Users](../50-administration-and-ops/working-with-users-2c91f88.md "In the SAP BTP cockpit, you can see the users of your global account or subaccount, user-related identity provider information, and their authorizations. In a user's overview, you can create and delete users, and assign role collections. You can also display an overview of the role collections, where you can drill down all the way to the role, and see the application that the role is belongs to.")

[Roles and Role Collections](../50-administration-and-ops/roles-and-role-collections-14a877c.md "Usually a role collection consists of one or multiple roles. You can use the SAP BTP cockpit to add or remove roles.")

[Attributes](../50-administration-and-ops/attributes-713f52a.md "Attributes use information that is specific to the user, for example the user's country. If the application developer in the Cloud Foundry environment of SAP BTP has created a country attribute to a role, this restricts the data a business user can see based on this attribute.")

[Trust and Federation with Identity Providers](../50-administration-and-ops/trust-and-federation-with-identity-providers-cb1bc8f.md "When setting up accounts you need to assign users. While we provide you with your first users to get you started, your organization has identity providers that you want to integrate.")

