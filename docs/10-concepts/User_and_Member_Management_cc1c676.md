<!-- loiocc1c676b43904066abb2a4838cbd0c37 -->

# User and Member Management

On the cloud platform, member management happens at all levels from global account to space, while user management is done for deployed applications.



<a name="loiocc1c676b43904066abb2a4838cbd0c37__section_ygb_5xw_jlb"/>

## User Accounts

A user account corresponds to a particular user in an identity provider, such as the SAP ID service and consists, for example, of an SAP user ID \(S-user or P-user\) and password.

**User accounts** enable users to log on to SAP BTP and access subaccounts and use services according to the permissions given to them.

Before diving into the different user and member management concepts, it's important to understand the difference between the 2 types of users we’re referring to: **platform users** and **business users**.

![Platform Users and Business Users](images/user-accounts_27c8463.png)



<a name="loiocc1c676b43904066abb2a4838cbd0c37__section_c5x_cyw_jlb"/>

## Platform Users

**Platform users** are usually developers, administrators or operators who deploy, administer, and troubleshoot applications and services on SAP BTP. They’re the users that you give certain permissions for instance at global account or subaccount level, either by adding them as members with certain permissions \(feature set A\) or by assigning role collections to them \(feature set B\).

Platform users who were added as members and who have administrative permissions can view or manage the list of global accounts, subaccounts, and Cloud Foundry orgs and spaces that are available to them. Members access them using the SAP BTP Cockpit or the SAP BTP command line interface \(btp CLI\).

For platform users, the default identity provider is [SAP ID Service](../50-administration-and-ops/SAP_ID_Service_d6a8db7.md). In cloud management tools feature set A, to use subaccount members from your own user base, use your own tenant of SAP Cloud Identity Services - Identity Authentication.

> ### Note:  
> For China \(Shanghai\) region, a different default identity provider is used.
> 
> For more information, see this [blog article](https://blogs.sap.com/2021/02/22/activate-totp-two-factor-authentication-on-sap-business-technology-platform-formerly-known-as-cloud-platform-at-alibaba-cloud/) on *SAP Community*.



<a name="loiocc1c676b43904066abb2a4838cbd0c37__section_tn4_gdx_jlb"/>

## Business Users

**Business users** use the applications that are deployed to SAP BTP. For example, the end users of your deployed application or users of subscribed apps or services, such as SAP Business Application Studio or SAP Web IDE, are business users.

In the Cloud Foundry environment, application developers \(platform users\) create and deploy application-based security artifacts for business users. Administrators use these artifacts to assign roles, build role collections, and assign these role collections to business users or user groups. In this way, they control the users' permissions in the deployed application.

For business users, the identity provider can be, for example, Identity Authentication service or your own, such as Active Directory.



<a name="loiocc1c676b43904066abb2a4838cbd0c37__section_bhj_b1x_jlb"/>

## Member Management and User Management

**Member management** refers to managing permissions for platform users. You can think about it as managing the members of your team.

Member management happens at global account, directory, subaccount, org, and space level. Members' permissions apply to all operations that are associated with the global account, the organization, or the space, irrespective of the tool used. Depending on the scope and the cloud management tools feature set you're using, you manage members in different ways:


<table>
<tr>
<th valign="top">

 



</th>
<th valign="top">

Global Accounts



</th>
<th valign="top">

Directories



</th>
<th valign="top">

Subaccounts



</th>
</tr>
<tr>
<td valign="top">

Feature Set A



</td>
<td valign="top">

You add global account administrators on the *Members* page at global account level in the cockpit. All members/administrators of the lower levels \(e.g subaccounts or spaces\) are automatically global account members.

On the *Members* page at the global account level in the cockpit, all global account members can view the global account administrators.

You can only manage global account administrators using the cockpit.

See [Add Members to Your Global Account](../50-administration-and-ops/Add_Members_to_Your_Global_Account_4a04913.md).



</td>
<td valign="top">

Not available



</td>
<td valign="top">

You don't have member management at subaccount level directly.

The person who created the subaccount is automatically a security administrator of that subaccount. That person can assign additional subaccount security administrators on the *Security* \> *Administrators* page at subaccount level in the cockpit.

As a security administrator, you can manage authentication and authorization in the subaccount, such as configuring trust to identity providers, and assigning role collections to business users.

You can only manage subaccount security administrators using the cockpit.

See [Managing Security Administrators in Your Subaccount \[Feature Set A\]](../50-administration-and-ops/Managing_Security_Administrators_in_Your_Subaccount_Feature_Set_A_6752c4b.md)



</td>
</tr>
<tr>
<td valign="top">

Feature Set B



</td>
<td valign="top">

You manage global account members by assigning role collections to platform users. Use the following predefined role collections:

-   Global Account Administrator
-   Global Account Viewer

Assign these role collections from the cockpit or the sapcp CLI.

See:

 [Role Collections and Roles in Global Accounts, Directories, and Subaccounts \[Feature Set B\]](Role_Collections_and_Roles_in_Global_Accounts,_Directories,_and_Subaccounts_Feature_Set_B_0039cf0.md) 

[Add Members to Your Global Account](../50-administration-and-ops/Add_Members_to_Your_Global_Account_4a04913.md)



</td>
<td valign="top">

You manage directory members by assigning role collections to platform users. Use the following predefined role collections:

-   Directory Administrator
-   Directory Viewer

See:

 [Role Collections and Roles in Global Accounts, Directories, and Subaccounts \[Feature Set B\]](Role_Collections_and_Roles_in_Global_Accounts,_Directories,_and_Subaccounts_Feature_Set_B_0039cf0.md) 



</td>
<td valign="top">

You manage subaccount members by assigning role collections to platform users.

> ### Note:  
> Neo subaccounts don’t use role collections.
> 
> For more information, see [Managing Member Authorizations in the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/a1ab5c4cc117455392cd0a512c7f890d.html "SAP BTP includes predefined platform roles that support the typical tasks performed by users when interacting with the platform. In addition, subaccount administrators can combine various scopes into a custom platform role that addresses their individual requirements.") :arrow_upper_right:.

Use the following predefined role collections:

-   Subaccount Administrator
-   Subaccount Viewer

Assign these role collections from the SAP BTP cockpit or the sapcp CLI.

See:

 [Role Collections and Roles in Global Accounts, Directories, and Subaccounts \[Feature Set B\]](Role_Collections_and_Roles_in_Global_Accounts,_Directories,_and_Subaccounts_Feature_Set_B_0039cf0.md) 

[Add Members to Your Subaccount \[Feature Set B\]](../50-administration-and-ops/Add_Members_to_Your_Subaccount_Feature_Set_B_1e1b7b6.md)



</td>
</tr>
</table>

<a name="loiocc1c676b43904066abb2a4838cbd0c37__table_yc5_znz_klb"/>Member Management in the Cloud Foundry Environment


<table>
<tr>
<th valign="top">

Orgs



</th>
<th valign="top">

Spaces



</th>
</tr>
<tr>
<td valign="top">

Manage org members on the *Members* page at subaccount level in the cockpit or with the Cloud Foundry CLI.

A platform user added as an org member can be either an **Org Manager** or an **Org Auditor**.

See:

 [https://docs.cloudfoundry.org/concepts/roles.html\#roles](https://docs.cloudfoundry.org/concepts/roles.html#roles)

[Add Org Members Using the Cockpit](../50-administration-and-ops/Add_Org_Members_Using_the_Cockpit_a4eeaf1.md)



</td>
<td valign="top">

Manage space members on the *Members* page at space level in the cockpit or with the Cloud Foundry CLI.

A platform user added as a space member can be either a **Space Manager**, **Space Developer**, or a **Space Auditor**.

See:

 [https://docs.cloudfoundry.org/concepts/roles.html\#roles](https://docs.cloudfoundry.org/concepts/roles.html#roles)

[Add Space Members Using the Cockpit](../50-administration-and-ops/Add_Space_Members_Using_the_Cockpit_81d0b4d.md)



</td>
</tr>
</table>

**User management** refers to managing authentication and authorization for your business users. This is only done for your deployed applications.

To manage your business users:

-   Configure trust to an identity provider in your subaccount.

-   Build roles using role templates and attributes.

-   Add those roles to role collections.

-   Assign those role collections either directly to users or map them to user groups.


To learn more about user management, see [Security Administration: Managing Authentication and Authorization](../50-administration-and-ops/Security_Administration_Managing_Authentication_and_Authorization_1ff47b2.md).

**Related Information**  


[Working with Users](../50-administration-and-ops/Working_with_Users_2c91f88.md "In the SAP BTP cockpit, you can see the users of your global account or subaccount, user-related identity provider information, and their authorizations. In a user's overview, you can create and delete users, and assign role collections. You can also display an overview of the role collections, where you can drill down all the way to the role, and see the application that the role is belongs to.")

[Roles and Role Collections](../50-administration-and-ops/Roles_and_Role_Collections_14a877c.md "Usually a role collection consists of one or multiple roles. You can use the SAP BTP cockpit to add or remove roles.")

[Attributes](../50-administration-and-ops/Attributes_713f52a.md "Attributes use information that is specific to the user, for example the user's country. If the application developer in the Cloud Foundry environment of SAP BTP has created a country attribute to a role, this restricts the data a business user can see based on this attribute.")

[Trust and Federation with Identity Providers](../50-administration-and-ops/Trust_and_Federation_with_Identity_Providers_cb1bc8f.md "When setting up accounts you need to assign users. While we provide you with your first users to get you started, your organization has its own user bases which you want to integrate.")

