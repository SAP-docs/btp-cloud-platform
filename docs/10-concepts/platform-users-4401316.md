<!-- loio440131674b0147a09e696053a53832d5 -->

# Platform Users

**Platform users** are usually developers, administrators or operators who deploy, administer, and troubleshoot accounts, applications and services on SAP BTP. They’re the users that have full access and give certain permissions, for instance, at global account, directory, or subaccount level. Members only have basic access.

Platform users who have administrative permissions can view or manage the list of global accounts, subaccounts, and environments, such as Cloud Foundry orgs and spaces. Members have basic access to them using the SAP BTP cockpit, the SAP BTP command-line interface \(btp CLI\), or environment-specific CLI, such as the Cloud Foundry \(CF\) CLI.

For platform users, there's a [default identity provider](../50-administration-and-ops/default-identity-provider-d6a8db7.md). We expect that you have your own identity provider. We recommend that you configure your custom tenant of SAP Cloud Identity Services as the identity provider and connect SAP Cloud Identity Services to your own corporate identity provider.

> ### Note:  
> For China \(Shanghai\) and Government Cloud \(US\) regions, a different default identity provider is used, and you can't use SAP Cloud Identity Services as identity provider in the global account.
> 
> If you want to use two-factor authentication in the China \(Shanghai\) region, see this [blog article](https://blogs.sap.com/2021/02/22/activate-totp-two-factor-authentication-on-sap-business-technology-platform-formerly-known-as-cloud-platform-at-alibaba-cloud/) on *SAP Community*.



<a name="loio440131674b0147a09e696053a53832d5__section_bhj_b1x_jlb"/>

## Member Management

**Member management** refers to managing permissions for platform users. Members have only basic access to SAP BTP.

Member management happens at global account, directory, subaccount, and environment level. Members' permissions apply to all operations that are associated with the global account, the organization, or the space, irrespective of the tool used. Depending on the scope and the cloud management tools you're using, you manage members in different ways:


<table>
<tr>
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

You manage global account members by assigning role collections to platform users. Use the following predefined role collections:

-   Global Account Administrator
-   Global Account Viewer

Assign these role collections from the SAP BTP cockpit or the btp CLI.

See:

[Role Collections and Roles in Global Accounts, Directories, and Subaccounts](role-collections-and-roles-in-global-accounts-directories-and-subaccounts-0039cf0.md) 

[Add Members to Your Global Account](../50-administration-and-ops/add-members-to-your-global-account-4a04913.md)

[Create Users](../50-administration-and-ops/create-users-a3bc7e8.md)

</td>
<td valign="top">

You manage directory members by assigning role collections to platform users. Use the following predefined role collections:

-   Directory Administrator
-   Directory Viewer

Assign these role collections from the SAP BTP cockpit or the btp CLI.

See:

[Role Collections and Roles in Global Accounts, Directories, and Subaccounts](role-collections-and-roles-in-global-accounts-directories-and-subaccounts-0039cf0.md) 

[Create Users](../50-administration-and-ops/create-users-a3bc7e8.md)

[Manage Users in Directories](../50-administration-and-ops/manage-users-in-directories-ff4d4a4.md)

</td>
<td valign="top">

You manage subaccount members by assigning role collections to platform users.

> ### Note:  
> Neo subaccounts don’t use role collections.
> 
> For more information, see [Managing Member Authorizations in the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/a1ab5c4cc117455392cd0a512c7f890d.html "SAP BTP includes predefined platform roles that support the typical tasks performed by users when interacting with the platform. In addition, subaccount administrators can combine various scopes into a custom platform role that addresses their individual requirements.") :arrow_upper_right:.

Use the predefined role collections, such as:

-   Subaccount Administrator
-   Subaccount Viewer

Assign these role collections from the SAP BTP cockpit or the btp CLI.

See:

[Role Collections and Roles in Global Accounts, Directories, and Subaccounts](role-collections-and-roles-in-global-accounts-directories-and-subaccounts-0039cf0.md) 

[Add Members to Your Subaccount](../50-administration-and-ops/add-members-to-your-subaccount-1e1b7b6.md)

[Create Users](../50-administration-and-ops/create-users-a3bc7e8.md)

</td>
</tr>
</table>

**Member Management in the Cloud Foundry Environment**


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

Manage org members on the *Members* page at environment level in the SAP BTP cockpit or with the Cloud Foundry CLI.

A platform user added as an org member can be either an **Org Manager** or an **Org Auditor** or implicitly an **Org User**.

See:

[About Roles in the Cloud Foundry Environment](../50-administration-and-ops/about-roles-in-the-cloud-foundry-environment-0907638.md)

[https://docs.cloudfoundry.org/concepts/roles.html\#roles](https://docs.cloudfoundry.org/concepts/roles.html#roles)

[Add Org Members](../50-administration-and-ops/add-org-members-a4eeaf1.md)

</td>
<td valign="top">

Manage space members on the *Members* page at space level in the SAP BTP cockpit or with the Cloud Foundry CLI.

A platform user added as a space member can be either a **Space Manager**, **Space Developer**, **Space Auditor**, or **Space Supporter**.

See:

[About Roles in the Cloud Foundry Environment](../50-administration-and-ops/about-roles-in-the-cloud-foundry-environment-0907638.md)

[https://docs.cloudfoundry.org/concepts/roles.html\#roles](https://docs.cloudfoundry.org/concepts/roles.html#roles)

[Add Space Members](../50-administration-and-ops/add-space-members-81d0b4d.md)

</td>
</tr>
</table>

For more information on the Kyma environment, see [Assign Roles in the Kyma Environment](../60-security/assign-roles-in-the-kyma-environment-148ae38.md).

See also [About User Management in the Cloud Foundry Environment](../50-administration-and-ops/about-user-management-in-the-cloud-foundry-environment-8e6ce96.md).

