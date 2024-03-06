<!-- loio1ff47b2d980e43a6b2ce294352333708 -->

# Security Administration: Managing Authentication and Authorization

This section describes the tasks of administrators in the Cloud Foundry environment of SAP BTP. Administrators ensure user authentication and assign authorization information to users and user groups.

Since identity providers provide the users or user groups, you make then sure that there is a trust relationship between your subaccount and the identity provider. This is a prerequisite for authentication. Now you can manage the authorizations of the business users.

> ### Note:  
> Running on the cloud management tools feature set A: Only the administrator who created the current subaccount can use the SAP BTP cockpit to add other administrators as members. The added administrators can use all the security administration functions. This enables the administrators to manage authentication and authorization in this subaccount.



<a name="loio1ff47b2d980e43a6b2ce294352333708__section_cdg_gdj_kbb"/>

## Authentication

Identity providers provide the business users. The default platform identity provider for SAP BTP is SAP ID service. If you use external identity providers, you must configure the trust relationship using the SAP BTP cockpit. The respective subaccount must have a trust relationship with the identity provider. Using the SAP BTP cockpit, you, as an administrator of the Cloud Foundry environment, establish this trust relationship.



<a name="loio1ff47b2d980e43a6b2ce294352333708__section_th2_hdj_kbb"/>

## Authorization

In the Cloud Foundry environment, application developers create and deploy application-based authorization artifacts for business users. Administrators use this information to assign roles, build role collections, and assign these collections to business users or user groups. In this way, they control the users' permissions.

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

Use an existing role or create a new one using role templates

[Add Roles to Role Collections on the Application Level](add-roles-to-role-collections-on-the-application-level-7596a0b.md)

</td>
<td valign="top">

Administrator of the Cloud Foundry environment

</td>
<td valign="top">

SAP BTP cockpit

Command line interface for SAP BTP

</td>
</tr>
<tr>
<td valign="top">

Create a role collection and assign roles to it

[Define a Role Collection](define-a-role-collection-4b20383.md)

</td>
<td valign="top">

Administrator of the Cloud Foundry environment

</td>
<td valign="top">

SAP BTP cockpit

Command line interface for SAP BTP

</td>
</tr>
<tr>
<td valign="top">

Assign the role collections to users and user groups, manage attribute mappings

[Managing Users and Their Authorizations Using the btp CLI](managing-users-and-their-authorizations-using-the-btp-cli-94bb593.md) or [Mapping Role Collections in the Subaccount](mapping-role-collections-in-the-subaccount-9e1bf57.md)

</td>
<td valign="top">

Administrator of the Cloud Foundry environment

</td>
<td valign="top">

SAP BTP cockpit

Command line interface for SAP BTP

</td>
</tr>
<tr>
<td valign="top">

\(If you do not use `SAP ID Service`\) Assign the role collections to user groups \(cloud management tools feature set A regions\)

[Map Role Collections to User Groups](map-role-collections-to-user-groups-51acfc8.md)

</td>
<td valign="top">

Administrator of the Cloud Foundry environment

</td>
<td valign="top">

SAP BTP cockpit

</td>
</tr>
<tr>
<td valign="top">

Assign the role collection to the business users provided by an identity provider

[Working with Role Collections](working-with-role-collections-393ea0b.md)

</td>
<td valign="top">

Administrator of the Cloud Foundry environment

</td>
<td valign="top">

SAP BTP cockpit

Command line interface for SAP BTP

</td>
</tr>
</table>

> ### Note:  
> When users log on, their authorizations are stored in each user's current browser session. These authorizations are not dynamically updated and are removed from there only if the session is terminated or invalidated. This means that if you assign a role collection to a user, only the authorizations that are in their current token, apply. The user must log out and log on again to get a new token.

**Related Information**  


[Trust and Federation with Identity Providers](trust-and-federation-with-identity-providers-cb1bc8f.md "When setting up accounts you need to assign users. While we provide you with your first users to get you started, your organization has identity providers that you want to integrate.")

[Monitoring and Troubleshooting](../60-security/monitoring-and-troubleshooting-1b3e89e.md "This section provides information on troubleshooting-related activities for the SAP Authorization and Trust Management service in the Cloud Foundry environment.")

[SAP Authorization and Trust Management Service](../60-security/sap-authorization-and-trust-management-service-6373bb7.md "The global account and subaccounts get their users from identity providers. Administrators make sure that users can only access their dedicated subaccount by making sure that there is a dedicated trust relationship only between the identity providers and the respective subaccounts. Developers configure and deploy application-based security artifacts containing authorizations, and administrators assign these authorizations using the SAP BTP cockpit.")

[Default Identity Provider](default-identity-provider-d6a8db7.md "SAP ID service is the default identity provider for both platform users and business users (in applications) at SAP BTP. You can start using it without further configuration.")

