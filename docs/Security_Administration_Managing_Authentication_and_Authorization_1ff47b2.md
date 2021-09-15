<!-- loio1ff47b2d980e43a6b2ce294352333708 -->

# Security Administration: Managing Authentication and Authorization

This section describes the tasks of administrators in the Cloud Foundry environment of SAP BTP. Administrators ensure user authentication and assign authorization information to users and user groups.

Since identity providers provide the users or user groups, you make then sure that there is a trust relationship between your subaccount and the identity provider. This is a prerequisite for authentication. Now you can manage the authorizations of the business users.

> ### Note:  
> Running on the cloud management tools feature set A: Only the administrator who created the current subaccount can use the SAP BTP cockpit to add other administrators as members. The added administrators can use all the security administration functions. This enables the administrators to manage authentication and authorization in this subaccount.



<a name="loio1ff47b2d980e43a6b2ce294352333708__section_cdg_gdj_kbb"/>

## Authentication

Identity providers provide the business users. The default platform identity provider SAP BTP is SAP ID service. If you use external identity providers, you must configure the trust relationship using the SAP BTP cockpit. The respective subaccount must have a trust relationship with the identity provider. Using the SAP BTP cockpit, you, as an administrator of the Cloud Foundry environment, establish this trust relationship.



<a name="loio1ff47b2d980e43a6b2ce294352333708__section_th2_hdj_kbb"/>

## Authorization

In the Cloud Foundry environment, application developers create and deploy application-based authorization artifacts for business users. Administrators use this information to assign roles, build role collections, and assign these collections to business users or user groups. In this way, they control the users' permissions.

<a name="loio1ff47b2d980e43a6b2ce294352333708__table_b4h_4rg_vbb"/>Setting Up Authorization Artifacts \(Administrators\)


<table>
<tr>
<th>

Task



</th>
<th>

User Role



</th>
<th>

Tool



</th>
</tr>
<tr>
<td>

Use an existing role or create a new one using role templates

[Add Roles to Role Collections on the Application Level](Add_Roles_to_Role_Collections_on_the_Application_Level_7596a0b.md)



</td>
<td>

Administrator of the Cloud Foundry environment



</td>
<td>

SAP BTP cockpit

Command line interface for SAP BTP



</td>
</tr>
<tr>
<td>

Create a role collection and assign roles to it

[Maintain Role Collections](Maintain_Role_Collections_d5f1612.md)



</td>
<td>

Administrator of the Cloud Foundry environment



</td>
<td>

SAP BTP cockpit

Command line interface for SAP BTP



</td>
</tr>
<tr>
<td>

Assign the role collections to users

[Managing Users and Their Authorizations Using the btp CLI](Managing_Users_and_Their_Authorizations_Using_the_btp_CLI_94bb593.md) or [Assigning Role Collections](Assigning_Role_Collections_9e1bf57.md)



</td>
<td>

Administrator of the Cloud Foundry environment



</td>
<td>

SAP BTP cockpit

Command line interface for SAP BTP



</td>
</tr>
<tr>
<td>

\(If you do not use `SAP ID Service`\) Assign the role collections to user groups \(cloud management tools feature set A regions\)

[Map Role Collections to User Groups](Map_Role_Collections_to_User_Groups_51acfc8.md)



</td>
<td>

Administrator of the Cloud Foundry environment



</td>
<td>

SAP BTP cockpit



</td>
</tr>
<tr>
<td>

Assign the role collection to the business users provided by an identity provider \(cloud management tools feature set A\)

[Directly Assign Role Collections to Users](Directly_Assign_Role_Collections_to_Users_a55a3fe.md)



</td>
<td>

Administrator of the Cloud Foundry environment



</td>
<td>

SAP BTP cockpit



</td>
</tr>
</table>

-   **[SAP ID Service](SAP_ID_Service_d6a8db7.md "The default platform identity provider and application identity provider of SAP BTP is SAP ID service.")**  
The default platform identity provider and application identity provider of SAP BTP is SAP ID service.
-   **[Trust and Federation with Identity Providers](Trust_and_Federation_with_Identity_Providers_cb1bc8f.md "When setting up accounts you need to assign users. While we provide you
                with your first users to get you started, your organization has its own user bases
                which you want to integrate.")**  
When setting up accounts you need to assign users. While we provide you with your first users to get you started, your organization has its own user bases which you want to integrate.
-   **[Working with Users](Working_with_Users_2c91f88.md "In the SAP BTP
		cockpit, you can see the users of your global account or subaccount, user-related identity
		provider information, and their authorizations. In a user's overview, you can create and
		delete users, and assign role collections. You can also display an overview of the role
		collections, where you can drill down all the way to the role, and see the application that
		the role is belongs to.")**  
In the SAP BTP cockpit, you can see the users of your global account or subaccount, user-related identity provider information, and their authorizations. In a user's overview, you can create and delete users, and assign role collections. You can also display an overview of the role collections, where you can drill down all the way to the role, and see the application that the role is belongs to.
-   **[Working with Role Collections](Working_with_Role_Collections_393ea0b.md "You can manage role collections by creating new ones from scratch or by copying an
		existing one and editing it. You can add or remove roles. You can also add or remove users
		or user groups to the role collections. This is the assignment or unassignment action. You
		can drill down all the way to the role definition or to the individual role, user, and user
		group, and make changes there.")**  
You can manage role collections by creating new ones from scratch or by copying an existing one and editing it. You can add or remove roles. You can also add or remove users or user groups to the role collections. This is the assignment or unassignment action. You can drill down all the way to the role definition or to the individual role, user, and user group, and make changes there.
-   **[Building Roles and Role Collections for Applications](Building_Roles_and_Role_Collections_for_Applications_eaa6a26.md "As an administrator of the Cloud
                                Foundry
		environment of SAP BTP,
		you can maintain application roles and role collections which can be used in user
		management.")**  
As an administrator of the Cloud Foundry environment of SAP BTP, you can maintain application roles and role collections which can be used in user management.
-   **[Assigning Role Collections](Assigning_Role_Collections_9e1bf57.md "You have arranged roles in role collections, and now want to assign these role
		collections to business users.")**  
You have arranged roles in role collections, and now want to assign these role collections to business users.
-   **[Managing Secrets of the SAP Authorization and Trust Management Service](Managing_Secrets_of_the_SAP_Authorization_and_Trust_Management_Service_22f4a5c.md "The SAP Authorization and Trust
                                    Management service
		maintains a number of secrets to ensure secure operation of the service. Your organization
		can have policies that require you change secrets or you may need to respond to the loss of
		a secret.")**  
The SAP Authorization and Trust Management service maintains a number of secrets to ensure secure operation of the service. Your organization can have policies that require you change secrets or you may need to respond to the loss of a secret.
-   **[Configure Trusted Domains for SAP Authorization and Trust Management Service \[Feature Set B\]](Configure_Trusted_Domains_for_SAP_Authorization_and_Trust_Management_Service_Feature_Set_B_c5e9972.md "By default, login pages of the SAP Authorization and Trust
                                    Management service (XSUAA) can’t
		be framed by other applications in different domains for security reasons.")**  
By default, login pages of the SAP Authorization and Trust Management service \(XSUAA\) can’t be framed by other applications in different domains for security reasons.
-   **[Configure Token Policy for SAP Authorization and Trust Management Service \[Feature Set B\]](Configure_Token_Policy_for_SAP_Authorization_and_Trust_Management_Service_Feature_Set_B_40290a9.md "Set the token policy for SAP Authorization and Trust
                                    Management service (XSUAA) by
		configuring the validity of the OpenID Connect (OIDC) tokens the service issues.")**  
Set the token policy for SAP Authorization and Trust Management service \(XSUAA\) by configuring the validity of the OpenID Connect \(OIDC\) tokens the service issues.

**Related Information**  


[Trust and Federation with Identity Providers](Trust_and_Federation_with_Identity_Providers_cb1bc8f.md "When setting up accounts you need to assign users. While we provide you with your first users to get you started, your organization has its own user bases which you want to integrate.")

[Monitoring and Troubleshooting](Monitoring_and_Troubleshooting_1b3e89e.md "This section provides information on troubleshooting-related activities for the SAP Authorization and Trust Management service in the Cloud Foundry environment.")

[SAP Authorization and Trust Management Service in the Cloud Foundry Environment](SAP_Authorization_and_Trust_Management_Service_in_the_Cloud_Foundry_Environment_6373bb7.md "The global account and subaccounts get their users from identity providers. Administrators make sure that users can only access their dedicated subaccount by making sure that there is a dedicated trust relationship only between the identity providers and the respective subaccounts. Developers configure and deploy application-based security artifacts containing authorizations, and administrators assign these authorizations using the SAP BTP cockpit.")

[SAP ID Service](SAP_ID_Service_d6a8db7.md "The default platform identity provider and application identity provider of SAP BTP is SAP ID service.")

