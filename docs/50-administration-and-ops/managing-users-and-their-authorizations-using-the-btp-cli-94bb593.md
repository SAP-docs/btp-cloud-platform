<!-- loio94bb5935d4b64cff945c181fffa85282 -->

# Managing Users and Their Authorizations Using the btp CLI

User authorizations are managed by assigning role collections to users \(for example, Subaccount Administrator\). Use the SAP BTP command-line interface \(btp CLI\) to manage roles and role collections, and to assign role collections to users.

> ### Tip:  
> All of these commands can be executed in the global account, a directory, or in a subaccount. To choose the level, use the `btp target` command. See [Set a Target for Subsequent Commands with btp target](set-a-target-for-subsequent-commands-with-btp-target-720645a.md).



<a name="loio94bb5935d4b64cff945c181fffa85282__section_l1j_mgj_rhb"/>

## Managing Users and Assigning Role Collections

Role collections are user-related authorizations that allow access to resources and services. You give users permissions by assigning role collections to them. All users in the global accounts, directories, and subaccounts are stored in identity providers, either in the default or in a custom identity provider. When the first role collection assignment to a user happens, SAP BTP creates a copy of this user in the global account, directory, or subaccount. This copy of the user is called shadow user.

When you do the first role collection assignment to a user through the btp CLI, such a shadow user is created by default. If you want to prevent this, you need to pass the `--create-user-if-missing` parameter with value `false`.

See [Role Collections and Roles in Global Accounts, Directories, and Subaccounts](../10-concepts/role-collections-and-roles-in-global-accounts-directories-and-subaccounts-0039cf0.md) and [User and Member Management](../10-concepts/user-and-member-management-cc1c676.md).


<table>
<tr>
<th valign="top">

Task

</th>
<th valign="top">

Run the command ...

</th>
<th valign="top">

Command help

</th>
</tr>
<tr>
<td valign="top">

List users

</td>
<td valign="top">

`btp list security/user`

</td>
<td valign="top">

[btp list security/user](https://help.sap.com/docs/BTP/btp-cli/btp-list-security-user.html)

</td>
</tr>
<tr>
<td valign="top">

Get details about a specific user, including role collections

</td>
<td valign="top">

`btp get security/user` 

</td>
<td valign="top">

[btp get security/user](https://help.sap.com/docs/BTP/btp-cli/btp-get-security-user.html)

</td>
</tr>
<tr>
<td valign="top">

Delete a user

</td>
<td valign="top">

`btp delete security/user`

</td>
<td valign="top">

[btp delete security/user](https://help.sap.com/docs/BTP/btp-cli/btp-delete-security-user.html)

</td>
</tr>
<tr>
<td valign="top">

Assign a role collection to a user, user group, or to an attribute

</td>
<td valign="top">

`btp assign security/role-collection`

</td>
<td valign="top">

[btp assign security/role-collection](https://help.sap.com/docs/BTP/btp-cli/btp-assign-security-role-collection.html)

</td>
</tr>
<tr>
<td valign="top">

Unassign a role collection from a user, user group, or from an attribute

</td>
<td valign="top">

`btp unassign security/role-collection`

</td>
<td valign="top">

[btp unassign security/role-collection](https://help.sap.com/docs/BTP/btp-cli/btp-unassign-security-role-collection.html)

</td>
</tr>
</table>



<a name="loio94bb5935d4b64cff945c181fffa85282__section_vmj_cjj_rhb"/>

## Managing Roles

A role is an instance of a role template; you can build a role based on a role template and assign the role to a role collection. See [Add Roles to Role Collections on the Application Level](add-roles-to-role-collections-on-the-application-level-7596a0b.md).


<table>
<tr>
<th valign="top">

Task

</th>
<th valign="top">

Run the command ...

</th>
<th valign="top">

Command help

</th>
</tr>
<tr>
<td valign="top">

List apps

</td>
<td valign="top">

`btp list security/app`

</td>
<td valign="top">

[btp list security/app](https://help.sap.com/docs/BTP/btp-cli/btp-list-security-app.html)

</td>
</tr>
<tr>
<td valign="top">

Get details about a specific application

</td>
<td valign="top">

`btp get security/app`

To get the ID of a specific app, run `btp list security/app`

.

</td>
<td valign="top">

[btp get security/app](https://help.sap.com/docs/BTP/btp-cli/btp-get-security-app.html)

</td>
</tr>
<tr>
<td valign="top">

List roles

</td>
<td valign="top">

`btp list security/role`

</td>
<td valign="top">

[btp list security/role](https://help.sap.com/docs/BTP/btp-cli/btp-list-security-role.html)

</td>
</tr>
<tr>
<td valign="top">

Get details about a specific role

</td>
<td valign="top">

`btp get security/role`

</td>
<td valign="top">

[btp get security/role](https://help.sap.com/docs/BTP/btp-cli/btp-get-security-role.html)

</td>
</tr>
<tr>
<td valign="top">

Create a role

</td>
<td valign="top">

`btp create security/role`

</td>
<td valign="top">

[btp create security/role](https://help.sap.com/docs/BTP/btp-cli/btp-create-security-role.html)

</td>
</tr>
<tr>
<td valign="top">

Delete a role

</td>
<td valign="top">

`btp delete security/role`

</td>
<td valign="top">

[btp delete security/role](https://help.sap.com/docs/BTP/btp-cli/btp-delete-security-role.html)

</td>
</tr>
<tr>
<td valign="top">

Add a role to a role collection

</td>
<td valign="top">

`btp add security/role`

</td>
<td valign="top">

[btp add security/role](https://help.sap.com/docs/BTP/btp-cli/btp-add-security-role.html)

</td>
</tr>
<tr>
<td valign="top">

Remove a role from a role collection

</td>
<td valign="top">

`btp remove security/role`

</td>
<td valign="top">

[btp remove security/role](https://help.sap.com/docs/BTP/btp-cli/btp-remove-security-role.html)

</td>
</tr>
</table>



<a name="loio94bb5935d4b64cff945c181fffa85282__section_cfh_h1c_rhb"/>

## Managing Role Collections

Role collections consist of roles, which, in turn, are based on role templates. Role collections are specific to account entities, that is, there are different role collections in global accounts, subaccounts, and directories. There are predefined role collections, such as *Global Account Administrator* and *Subaccount Viewer*. For more information, see [Role Collections and Roles in Global Accounts, Directories, and Subaccounts](../10-concepts/role-collections-and-roles-in-global-accounts-directories-and-subaccounts-0039cf0.md) and [Working with Role Collections](working-with-role-collections-393ea0b.md).


<table>
<tr>
<th valign="top">

Task

</th>
<th valign="top">

Run the command ...

</th>
<th valign="top">

Command help

</th>
</tr>
<tr>
<td valign="top">

List role collections

</td>
<td valign="top">

`btp list security/role-collection`

</td>
<td valign="top">

[btp list security/role-collection](https://help.sap.com/docs/BTP/btp-cli/btp-list-security-role-collection.html)

</td>
</tr>
<tr>
<td valign="top">

Get details about a specific role collection

</td>
<td valign="top">

`btp get security/role-collection`

</td>
<td valign="top">

[btp get security/role-collection](https://help.sap.com/docs/BTP/btp-cli/btp-get-security-role-collection.html)

</td>
</tr>
<tr>
<td valign="top">

Create a role collection

</td>
<td valign="top">

`btp create security/role-collection`

</td>
<td valign="top">

[btp create security/role-collection](https://help.sap.com/docs/BTP/btp-cli/btp-create-security-role-collection.html)

</td>
</tr>
<tr>
<td valign="top">

Change the description of a role collection

</td>
<td valign="top">

`btp update security/role-collection`

</td>
<td valign="top">

[btp update security/role-collection](https://help.sap.com/docs/BTP/btp-cli/btp-update-security-role-collection.html)

</td>
</tr>
<tr>
<td valign="top">

Delete a role collection

</td>
<td valign="top">

`btp delete security/role-collection`

</td>
<td valign="top">

[btp delete security/role-collection](https://help.sap.com/docs/BTP/btp-cli/btp-delete-security-role-collection.html)

</td>
</tr>
</table>

**Related Information**  


[Working with Global Accounts, Directories, and Subaccounts Using the btp CLI](working-with-global-accounts-directories-and-subaccounts-using-the-btp-cli-85a683e.md "Use the SAP BTP command line interface (btp CLI) to manage operations with global accounts, directories, and subaccounts.")

[Setting Entitlements Using the btp CLI](setting-entitlements-using-the-btp-cli-5af849c.md "Use the SAP BTP command line interface (btp CLI) to set entitlements to define the functionality or permissions available for users of global accounts, directories, and subaccounts.")

[Working with Environments Using the btp CLI](working-with-environments-using-the-btp-cli-48db155.md "Use the SAP BTP command line interface (btp CLI) to manage runtime environment instances in a subaccount. For example, enable the Cloud Foundry environment by creating a Cloud Foundry org (environment instance).")

[Working with Multitenant Applications Using the btp CLI](working-with-multitenant-applications-using-the-btp-cli-c1b0fcc.md "Use the SAP BTP command line interface (btp CLI) to manage the multitenant applications to which a subaccount is entitled to subscribe.")

[Working with External Resource Providers Using the btp CLI](working-with-external-resource-providers-using-the-btp-cli-48d7688.md "Use the SAP BTP command line interface (btp CLI) to get details, or to create or delete resource provider instances in a global account.")

[Managing Trust from SAP BTP to an SAP Cloud Identity Services Tenant](managing-trust-from-sap-btp-to-an-sap-cloud-identity-services-tenant-6140107.md "SAP BTP supports identity federation. Its concept is to reuse the user bases of identity providers. To use a custom identity provider, your global account or subaccount in SAP BTP must have a trust relationship to the identity provider you want to use.")

[Managing Signing Keys for Access Tokens](managing-signing-keys-for-access-tokens-dfca1d3.md "Use the SAP BTP command line interface (btp CLI) to manage signing keys for access tokens in the subaccount.")

[Managing Security Settings](managing-security-settings-168dd75.md "Use the SAP BTP command line interface (btp CLI) to display and update the security settings for the subaccount.")

[Managing API Credentials for Calling REST APIs of SAP Authorization and Trust Management Service](managing-api-credentials-for-calling-rest-apis-of-sap-authorization-and-trust-managemen-ce43eb5.md "Use the SAP BTP command line interface (btp CLI) to manage API credentials, which enable you to access the REST APIs of the SAP Authorization and Trust Management service.")

[Working with Resources of the SAP Service Manager Using the btp CLI](working-with-resources-of-the-sap-service-manager-using-the-btp-cli-fe6a53b.md "Use the SAP BTP command line interface to perform various operations related to your platforms, attached service brokers, service instances, and service bindings.")

[Security Administration: Managing Authentication and Authorization](security-administration-managing-authentication-and-authorization-1ff47b2.md "This section describes the tasks of administrators of SAP BTP. Administrators ensure user authentication and assign authorization information to users and user groups.")

[Set a Target for Subsequent Commands with btp target](set-a-target-for-subsequent-commands-with-btp-target-720645a.md "Set the target for command calls to a subaccount, a directory, or a global account with the btp target command.")

[Role Collections and Roles in Global Accounts, Directories, and Subaccounts](../10-concepts/role-collections-and-roles-in-global-accounts-directories-and-subaccounts-0039cf0.md "SAP BTP provides a set of role collections to set up administrator access to your global account and subaccounts.")

[btp CLI Command Reference](https://help.sap.com/docs/BTP/btp-cli/intro.html)

