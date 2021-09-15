<!-- loio48db1553eb18451e8f71fc56d99ede71 -->

# Working with Environments Using the btp CLI

Use the SAP BTP command line interface \(btp CLI\) to manage runtime environment instances in a subaccount. For example, enable the Cloud Foundry environment by creating a Cloud Foundry org \(environment instance\).


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

Get all available environments for a subaccount



</td>
<td>

`btp list accounts/available-environment`



</td>
</tr>
<tr>
<td>

Get details about an environment available for a subaccount



</td>
<td>

`btp get accounts/available-environment`



</td>
</tr>
<tr>
<td>

Get all environment instances of a subaccount



</td>
<td>

`btp list accounts/environment-instance`



</td>
</tr>
<tr>
<td>

Get a specific environment instance of a subaccount



</td>
<td>

`btp get accounts/environment-instance`



</td>
</tr>
<tr>
<td>

Create an environment instance in a subaccount



</td>
<td>

`btp create accounts/environment-instance`



</td>
</tr>
<tr>
<td>

Update the plan and/or configuration parameters of an environment in a subaccount



</td>
<td>

`btp update accounts/environment-instance`



</td>
</tr>
<tr>
<td>

Delete environment instances of a subaccount



</td>
<td>

`btp delete accounts/environment-instance`



</td>
</tr>
</table>

**Parent topicColonSymbol** [Commands in the btp CLI](Commands_in_the_btp_CLI_a03a555.md "A list of all tasks and respective commands that are available in the SAP BTP command line interface (btp CLI).")

**Related Information**  


[Working with Global Accounts, Directories, and Subaccounts Using the btp CLI](Working_with_Global_Accounts,_Directories,_and_Subaccounts_Using_the_btp_CLI_85a683e.md "Use the SAP BTP command line interface (btp CLI) to manage operations with global accounts, directories, and subaccounts.")

[Setting Entitlements Using the btp CLI](Setting_Entitlements_Using_the_btp_CLI_5af849c.md "Use the SAP BTP command line interface (btp CLI) to set entitlements to define the functionality or permissions available for users of global accounts, directories, and subaccounts.")

[Working with Multitenant Applications Using the btp CLI](Working_with_Multitenant_Applications_Using_the_btp_CLI_c1b0fcc.md "Use the SAP BTP command line interface (btp CLI) to manage the multitenant applications to which a subaccount is entitled to subscribe.")

[Working with External Resource Providers Using the btp CLI](Working_with_External_Resource_Providers_Using_the_btp_CLI_48d7688.md "Use the SAP BTP command line interface (btp CLI) to get details, or to create or delete resource provider instances in a global account.")

[Managing Users and Their Authorizations Using the btp CLI](Managing_Users_and_Their_Authorizations_Using_the_btp_CLI_94bb593.md "User authorizations are managed by assigning role collections to users (for example, Subaccount Administrator). Use the SAP BTP command line interface (btp CLI) to manage roles and role collections, and to assign role collections to users.")

[Working With Resources of the SAP Service Manager Using the btp CLI](Working_With_Resources_of_the_SAP_Service_Manager_Using_the_btp_CLI_fe6a53b.md "Use the SAP BTP command line interface to perform various operations related to your platforms, attached service brokers, service instances, and service bindings.")

[Org Management Using the SAP BTP Command Line Interface \(btp CLI\) \[Feature Set B\]](Org_Management_Using_the_SAP_BTP_Command_Line_Interface_(btp_CLI)_Feature_Set_B_aee40e1.md "The Cloud Foundry environment allows you to create polyglot cloud applications in Cloud Foundry. To manage the lifecycle of an org in the Cloud Foundry environment, use the accounts/environment-instance command in the btp CLI.")

