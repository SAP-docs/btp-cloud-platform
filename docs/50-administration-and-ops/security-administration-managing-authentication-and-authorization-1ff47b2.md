<!-- loio1ff47b2d980e43a6b2ce294352333708 -->

# Security Administration: Managing Authentication and Authorization

This section describes the tasks of administrators of SAP BTP. Administrators ensure user authentication and assign authorization information to users and user groups.

Since identity providers provide the users or user groups, you make then sure that there is a trust relationship between your subaccount and the identity provider. This is a prerequisite for authentication. You can manage the authorizations of the users.



<a name="loio1ff47b2d980e43a6b2ce294352333708__section_cdg_gdj_kbb"/>

## Authentication

Identity providers provide the users. The default platform identity provider for SAP BTP is SAP ID service. If you use external identity providers, you must configure the trust relationship.



<a name="loio1ff47b2d980e43a6b2ce294352333708__section_th2_hdj_kbb"/>

## Authorization

Application developers create and deploy application-based authorization artifacts for business users. Administrators use this model to manage roles, build role collections, and assign these collections to users or user groups. In this way, they control the users' permissions.

**Setting Up Authorization Artifacts \(Administrators\)**


<table>
<tr>
<th valign="top">

Task

</th>
<th valign="top">

User Role

</th>
<th valign="top">

Tool

</th>
</tr>
<tr>
<td valign="top">

Assign the role collection to the users provided by an identity provider

[Working with Role Collections](working-with-role-collections-393ea0b.md) or [Managing Users and Their Authorizations Using the btp CLI](managing-users-and-their-authorizations-using-the-btp-cli-94bb593.md)

</td>
<td valign="top">

Account administrator

</td>
<td valign="top">

SAP BTP cockpit

Command line interface for SAP BTP

</td>
</tr>
<tr>
<td valign="top">

\(If you do use a custom identity provider\) Assign the role collections to user groups

[Map Role Collections to User Groups](map-role-collections-to-user-groups-51acfc8.md) or [Managing Users and Their Authorizations Using the btp CLI](managing-users-and-their-authorizations-using-the-btp-cli-94bb593.md)

</td>
<td valign="top">

Account administrator

</td>
<td valign="top">

SAP BTP cockpit

Command line interface for SAP BTP

</td>
</tr>
<tr>
<td valign="top">

Assign the role collections to users and user groups, manage attribute mappings

[Mapping Role Collections in the Subaccount](mapping-role-collections-in-the-subaccount-9e1bf57.md) or [Managing Users and Their Authorizations Using the btp CLI](managing-users-and-their-authorizations-using-the-btp-cli-94bb593.md)

</td>
<td valign="top">

Account administrator

</td>
<td valign="top">

SAP BTP cockpit

Command line interface for SAP BTP

</td>
</tr>
<tr>
<td valign="top">

Create a role collection and assign roles to it

[Define a Role Collection](define-a-role-collection-4b20383.md) or [Managing Users and Their Authorizations Using the btp CLI](managing-users-and-their-authorizations-using-the-btp-cli-94bb593.md)

</td>
<td valign="top">

Account administrator

</td>
<td valign="top">

SAP BTP cockpit

Command line interface for SAP BTP

</td>
</tr>
<tr>
<td valign="top">

Use an existing role or create a new one using role templates

[Add Roles to Role Collections on the Application Level](add-roles-to-role-collections-on-the-application-level-7596a0b.md) or [Managing Users and Their Authorizations Using the btp CLI](managing-users-and-their-authorizations-using-the-btp-cli-94bb593.md)

</td>
<td valign="top">

Account administrator

</td>
<td valign="top">

SAP BTP cockpit

Command line interface for SAP BTP

</td>
</tr>
</table>

> ### Note:  
> When users log on, their authorizations are stored in each user's current session. These authorizations are not dynamically updated and are removed from there only when the session is terminated. This means that, after changes of role collection assignments of a user, these changes only become effective after the user logged out and logged on again.

**Related Information**  


[Trust and Federation with Identity Providers](trust-and-federation-with-identity-providers-cb1bc8f.md "")

[Monitoring and Troubleshooting](../60-security/monitoring-and-troubleshooting-1b3e89e.md "This section provides information on troubleshooting-related activities for the SAP Authorization and Trust Management service in the Cloud Foundry environment.")

[SAP Authorization and Trust Management Service](../60-security/sap-authorization-and-trust-management-service-6373bb7.md "The global account and subaccounts get their users from identity providers. Administrators make sure that users can only access their dedicated subaccount by making sure that there is a dedicated trust relationship only between the identity providers and the respective subaccounts. Developers configure and deploy application-based security artifacts containing authorizations, and administrators assign these authorizations using the SAP BTP cockpit.")

[Default Identity Provider](default-identity-provider-d6a8db7.md "SAP ID service is the default identity provider for both platform users and business users (in applications) at SAP BTP. You can start using it without further configuration.")

