<!-- loio94bb5935d4b64cff945c181fffa85282 -->

# Managing Users and Their Authorizations Using the btp CLI

User authorizations are managed by assigning role collections to users \(for example, Subaccount Administrator\). Use the SAP BTP command line interface \(btp CLI\) to manage roles and role collections, and to assign role collections to users.

> ### Tip:  
> All of these commands can be executed in the global account, a directory, or in a subaccount. You can set one of these as the default context using the `btp target` command. See [Set the Default Command Context](Set_the_Default_Command_Context_720645a.md).



<a name="loio94bb5935d4b64cff945c181fffa85282__section_l1j_mgj_rhb"/>

## Managing Users and Assigning Role Collections

Role collections are user-related authorizations that restrict access to resources and services based on defined user permissions. You give user permissions by assigning role collections to them. For example, after creating a subaccount, assign the role collection "Subaccount Administrator" to a user. You can also display users and their authorizations. See [Role Collections and Roles in Global Accounts, Directories, and Subaccounts \[Feature Set B\]](Role_Collections_and_Roles_in_Global_Accounts,_Directories,_and_Subaccounts_Feature_Set_B_0039cf0.md).


<table>
<tr>
<th>

Task



</th>
<th>

Run the command ...



</th>
</tr>
<tr>
<td>

List all users



</td>
<td>

`btp list security/user`



</td>
</tr>
<tr>
<td>

Get details about a specific user, including role collections



</td>
<td>

`btp get security/user` 



</td>
</tr>
<tr>
<td>

Delete a user



</td>
<td>

`btp delete security/user`



</td>
</tr>
<tr>
<td>

Assign a role collection to a user



</td>
<td>

 `btp assign security/role-collection` 



</td>
</tr>
<tr>
<td>

Unassign a role collection from a user



</td>
<td>

`btp unassign security/role-collection`



</td>
</tr>
</table>



<a name="loio94bb5935d4b64cff945c181fffa85282__section_vmj_cjj_rhb"/>

## Managing Roles

A role is an instance of a role template; you can build a role based on a role template and assign the role to a role collection. See [Add Roles to Role Collections on the Application Level](Add_Roles_to_Role_Collections_on_the_Application_Level_7596a0b.md).


<table>
<tr>
<th>

Task



</th>
<th>

Run the command ...



</th>
</tr>
<tr>
<td>

List all apps of the global account



</td>
<td>

`btp list security/app`



</td>
</tr>
<tr>
<td>

Get details about a specific application



</td>
<td>

`btp get security/app`



</td>
</tr>
<tr>
<td>

List all role templates of an application



</td>
<td>

`btp list security/role-template`



</td>
</tr>
<tr>
<td>

List all roles



</td>
<td>

`btp list security/role`



</td>
</tr>
<tr>
<td>

List all roles of a specific application



</td>
<td>

`btp list security/role`



</td>
</tr>
<tr>
<td>

Get details about a specific role



</td>
<td>

`btp get security/role`



</td>
</tr>
<tr>
<td>

Create a role



</td>
<td>

`btp create security/role`



</td>
</tr>
<tr>
<td>

Delete a role



</td>
<td>

`btp delete security/role`



</td>
</tr>
<tr>
<td>

Add a role to a role collection



</td>
<td>

`btp add security/role`



</td>
</tr>
<tr>
<td>

Remove a role from a role collection



</td>
<td>

`btp remove security/role`



</td>
</tr>
</table>



<a name="loio94bb5935d4b64cff945c181fffa85282__section_cfh_h1c_rhb"/>

## Managing Role Collections

Role collections are user-related authorizations that restrict access to resources and services based on defined user permissions. They consist of individual roles, which, in turn, are based on role templates. There are four predefined role collections: Global Account Administrator, Subaccount Administrator, Global Account Viewer, and Subaccount Viewer. For more information, see [Building Roles and Role Collections for Applications](Building_Roles_and_Role_Collections_for_Applications_eaa6a26.md).


<table>
<tr>
<th>

Task



</th>
<th>

Run the command ...



</th>
</tr>
<tr>
<td>

List all role collections



</td>
<td>

`btp list security/role-collection`



</td>
</tr>
<tr>
<td>

Get details about a specific role collection



</td>
<td>

`btp get security/role-collection`



</td>
</tr>
<tr>
<td>

Create a role collection



</td>
<td>

`btp create security/role-collection`



</td>
</tr>
<tr>
<td>

Change the description of a role collection



</td>
<td>

`btp update security/role-collection`



</td>
</tr>
<tr>
<td>

Delete a role collection



</td>
<td>

`btp delete security/role-collection`



</td>
</tr>
</table>

**Parent topicColonSymbol** [Commands in the btp CLI](Commands_in_the_btp_CLI_a03a555.md "A list of all tasks and respective commands that are available in the SAP BTP command line interface (btp CLI).")

**Related Information**  


[Working with Global Accounts, Directories, and Subaccounts Using the btp CLI](Working_with_Global_Accounts,_Directories,_and_Subaccounts_Using_the_btp_CLI_85a683e.md "Use the SAP BTP command line interface (btp CLI) to manage operations with global accounts, directories, and subaccounts.")

[Setting Entitlements Using the btp CLI](Setting_Entitlements_Using_the_btp_CLI_5af849c.md "Use the SAP BTP command line interface (btp CLI) to set entitlements to define the functionality or permissions available for users of global accounts, directories, and subaccounts.")

[Working with Environments Using the btp CLI](Working_with_Environments_Using_the_btp_CLI_48db155.md "Use the SAP BTP command line interface (btp CLI) to manage runtime environment instances in a subaccount. For example, enable the Cloud Foundry environment by creating a Cloud Foundry org (environment instance).")

[Working with Multitenant Applications Using the btp CLI](Working_with_Multitenant_Applications_Using_the_btp_CLI_c1b0fcc.md "Use the SAP BTP command line interface (btp CLI) to manage the multitenant applications to which a subaccount is entitled to subscribe.")

[Working with External Resource Providers Using the btp CLI](Working_with_External_Resource_Providers_Using_the_btp_CLI_48d7688.md "Use the SAP BTP command line interface (btp CLI) to get details, or to create or delete resource provider instances in a global account.")

[Working With Resources of the SAP Service Manager Using the btp CLI](Working_With_Resources_of_the_SAP_Service_Manager_Using_the_btp_CLI_fe6a53b.md "Use the SAP BTP command line interface to perform various operations related to your platforms, attached service brokers, service instances, and service bindings.")

[Security Administration: Managing Authentication and Authorization](Security_Administration_Managing_Authentication_and_Authorization_1ff47b2.md "This section describes the tasks of administrators in the Cloud Foundry environment of SAP BTP. Administrators ensure user authentication and assign authorization information to users and user groups.")

[Set the Default Command Context](Set_the_Default_Command_Context_720645a.md "Change the default context for all command calls to the global account, a directory, or a subaccount by using the btp target command.")

[Role Collections and Roles in Global Accounts, Directories, and Subaccounts \[Feature Set B\]](Role_Collections_and_Roles_in_Global_Accounts,_Directories,_and_Subaccounts_Feature_Set_B_0039cf0.md "In the cloud management tools feature set B, SAP BTP provides a set of role collections to set up administrator access to your global account and subaccounts.")

