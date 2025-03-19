<!-- loio1ff47b2d980e43a6b2ce294352333708 -->

# Security Administration: Managing Authentication and Authorization

This section describes the tasks of administrators of SAP BTP. Administrators ensure user authentication and assign authorization information to users and user groups.

Since identity providers provide the users or user groups, you make then sure that there is a trust relationship between your subaccount and the identity provider. This is a prerequisite for authentication. You can manage the authorizations of the users.



<a name="loio1ff47b2d980e43a6b2ce294352333708__section_cdg_gdj_kbb"/>

## Authentication

A user account corresponds to a particular user in an identity provider. The user is always authenticated using an external identity provider. We recommend to use a custom tenant of Cloud Identity Services. You can connect Cloud Identity Services to your corporate identity provider.

SAP BTP distinguishes two types of users. Platform users are usually administrators, operator, or developers. They have full access and give permissions at global account, directory, and subaccount level. Business users use the applications deployed to SAP BTP. They are, for example, end users of SaaS apps or of custom applications.

For more information, see the related links.



<a name="loio1ff47b2d980e43a6b2ce294352333708__section_th2_hdj_kbb"/>

## Authorization

Application developers create and deploy application-based authorization artifacts for business users. Administrators use this model to manage roles, build role collections, and assign these collections to users or user groups. In this way, they control the users' permissions.

To perform the functions related to authorization artifacts, account administrators can have multiple options. Here are some of the options:

-   The SAP BTP cockpit covers all authorization functions. Its user interface offers easy-to-use and clear navigation.

-   There is also a command line option to manage most authorization artifacts. If you prefer working in a terminal or automating operations, use the SAP BTP command line interface \(btp CLI\). It's suitable for repetitive tasks.

-   Especially if you need to perform bulk operations or programmatically access the authorizations, we recommend to use the REST API for authorizations of the SAP Authorization and Trust Management service.

-   Administrators can also use the Terraform Provider for SAP BTP within Infrastructure as Code to manage some of the authorization functions.


You find the all available options and tools for managing authorizations in the account administration overview. See [Account Administration](account-administration-5d62ec8.md).

**Setting Up Authorization Artifacts \(Account Administrators\)**


<table>
<tr>
<th valign="top">

Task

</th>
<th valign="top">

Links

</th>
</tr>
<tr>
<td valign="top">

Assign the role collection to the users provided by an identity provider

</td>
<td valign="top">

[Working with Role Collections](working-with-role-collections-393ea0b.md) 

</td>
</tr>
<tr>
<td valign="top">

\(If you do use a custom identity provider\) Assign the role collections to user groups

</td>
<td valign="top">

[Map Role Collections to User Groups](map-role-collections-to-user-groups-51acfc8.md) 

</td>
</tr>
<tr>
<td valign="top">

Assign the role collections to users and user groups, manage attribute mappings

</td>
<td valign="top">

[Mapping Role Collections](mapping-role-collections-9e1bf57.md) 

</td>
</tr>
<tr>
<td valign="top">

Create a role collection and assign roles to it

</td>
<td valign="top">

[Define a Role Collection](define-a-role-collection-4b20383.md) 

</td>
</tr>
<tr>
<td valign="top">

Use an existing role or create a new one using role templates

</td>
<td valign="top">

[Add Roles to Role Collections on the Application Level](add-roles-to-role-collections-on-the-application-level-7596a0b.md) 

</td>
</tr>
</table>

> ### Note:  
> When users log on, their authorizations are stored in each user's current session. These authorizations are not dynamically updated and are removed from there only when the session is terminated. This means that, after changes of role collection assignments of a user, these changes only become effective after the user logged out and logged on again.

**Related Information**  


[Trust and Federation with Identity Providers](trust-and-federation-with-identity-providers-cb1bc8f.md "When setting up accounts you need to assign users. While we provide you with your first users from the default identity provider to get you started, your organization has identity providers that you want to integrate.")

[Monitoring and Troubleshooting](../60-security/monitoring-and-troubleshooting-1b3e89e.md "This section provides information on troubleshooting-related activities for the SAP Authorization and Trust Management service in the Cloud Foundry environment.")

[SAP Authorization and Trust Management Service](../60-security/sap-authorization-and-trust-management-service-6373bb7.md "The global account and subaccounts get their users from identity providers. Administrators make sure that users can only access their dedicated subaccount by making sure that there is a dedicated trust relationship only between the identity providers and the respective subaccounts. Developers configure and deploy application-based security artifacts containing authorizations, and administrators assign these authorizations using the SAP BTP cockpit.")

[Default Identity Provider](default-identity-provider-d6a8db7.md "SAP ID service is the default identity provider for both platform users and business users (in applications) at SAP BTP. You can start using it without further configuration.")

[User and Member Management](../10-concepts/user-and-member-management-cc1c676.md "On SAP BTP, user management takes place at all levels from global account to environment. There are different types of users, such as depending on their roles in the company.")

