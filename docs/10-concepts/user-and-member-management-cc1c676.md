<!-- loiocc1c676b43904066abb2a4838cbd0c37 -->

# User and Member Management

On SAP BTP, user management takes place at all levels from global account to environment. There are different types of users, such as depending on their roles in the company.



<a name="loiocc1c676b43904066abb2a4838cbd0c37__section_ygb_5xw_jlb"/>

## User Accounts

A user account corresponds to a particular user in an identity provider. The user is always stored in an external identity provider, such as a custom tenant of SAP Cloud Identity Services - Identity Authentication or the default identity provider.

**User accounts** enable users to log on to SAP BTP, access subaccounts, and to use applications according to the permissions granted to them.

> ### Note:  
> A user name alone doesn't determine a concrete user account with associated authorizations, as you can have users with the same user name in different identity providers. Accessible data and allowed operations also depend on the identity provider. The concrete user is identified by the combination of user name and identity provider.
> 
> > ### Example:  
> > There are two users with the same user name, which is the email address here. The two users with different identity providers have different authorizations and can access different applications.
> > 
> > -   julia.moore@acme.com from the custom identity provider has authorizations to access her favorite industrial applications. She needs the logon with the custom identity provider for her actual work.
> > 
> > -   julia.moore@acme.com from the default identity provider has no authorizations.

Before diving into the different user and member management concepts, it's important to understand the difference between the two types of users we’re referring to: **platform users** and **business users**.

![Platform Users and Business Users](images/user-accounts_27c8463.png)

For more information, see [Platform Users](platform-users-4401316.md) and [Business Users](business-users-2e68494.md).

**Related Information**  


[Working with Users](../50-administration-and-ops/working-with-users-2c91f88.md "In the SAP BTP cockpit, you can see the users of your global account or subaccount, user-related identity provider information, and their authorizations. In a user's overview, you can create and delete users, and assign role collections. You can also display an overview of the role collections, where you can drill down all the way to the role, and see the application that the role belongs to.")

[Roles and Role Collections](../50-administration-and-ops/roles-and-role-collections-14a877c.md "Usually a role collection consists of one or multiple roles. You can use the SAP BTP cockpit to add or remove roles.")

[Attributes](../50-administration-and-ops/attributes-713f52a.md "Attributes use information that is specific to the user, for example the user's country. If the application developer in the Cloud Foundry environment of SAP BTP has created a country attribute to a role, this restricts the data a business user can see based on this attribute.")

[Trust and Federation with Identity Providers](../50-administration-and-ops/trust-and-federation-with-identity-providers-cb1bc8f.md "")

