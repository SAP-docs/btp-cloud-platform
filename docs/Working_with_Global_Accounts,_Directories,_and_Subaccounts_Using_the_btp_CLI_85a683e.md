<!-- loio85a683e48f0a4c6db807c05d20f43883 -->

# Working with Global Accounts, Directories, and Subaccounts Using the btp CLI

Use the SAP BTP command line interface \(btp CLI\) to manage operations with global accounts, directories, and subaccounts.



<a name="loio85a683e48f0a4c6db807c05d20f43883__section_utc_hhb_ckb"/>

## Working with Global Accounts


<table>
<tr>
<th>

Task



</th>
<th>

Run the command...



</th>
</tr>
<tr>
<td>

Get details about a global account, and the account structure \(directories and subaccounts\) of the global account.



</td>
<td>

`btp get accounts/global-account`



</td>
</tr>
<tr>
<td>

Update the display name and/or description of a global account.



</td>
<td>

`btp update accounts/global-account`



</td>
</tr>
</table>

For more information, see [Global Accounts](Account_Model_8ed4a70.md#loioc165d95ee700407eb181770901caec94).



<a name="loio85a683e48f0a4c6db807c05d20f43883__section_a13_xjb_ckb"/>

## Working with Directories

Directories allow you to organize and manage your subaccounts according to your technical and business needs.


<table>
<tr>
<th>

Task



</th>
<th>

Run the command...



</th>
</tr>
<tr>
<td>

Get details about a directory and list the subaccounts and subdirectories in the directory



</td>
<td>

`btp get accounts/directory`



</td>
</tr>
<tr>
<td>

Create a directory



</td>
<td>

`btp create accounts/directory`



</td>
</tr>
<tr>
<td>

Update a directory



</td>
<td>

`btp update accounts/directory`



</td>
</tr>
<tr>
<td>

Delete a directory



</td>
<td>

`btp delete accounts/directory`



</td>
</tr>
<tr>
<td>

Change the set of enabled features \(user and entitlement management\) for a directory



</td>
<td>

`btp enable accounts/directory`



</td>
</tr>
<tr>
<td>

List the custom properties assigned to a directory



</td>
<td>

`btp list accounts/custom-property`



</td>
</tr>
</table>

For more information, see [Directories \[Feature Set B\]](Account_Model_8ed4a70.md#loioa92721fc75524ec09a7a7255997dbd94).



<a name="loio85a683e48f0a4c6db807c05d20f43883__section_m5c_23b_ckb"/>

## Working with Subaccounts


<table>
<tr>
<th>

Task



</th>
<th>

Run the command...



</th>
</tr>
<tr>
<td>

List all subaccounts in a global account



</td>
<td>

`btp list accounts/subaccount`



</td>
</tr>
<tr>
<td>

Get details about a subaccount



</td>
<td>

`btp get accounts/subaccount`



</td>
</tr>
<tr>
<td>

Create a subaccount



</td>
<td>

`btp create accounts/subaccount`



</td>
</tr>
<tr>
<td>

Update a subaccount



</td>
<td>

`btp update accounts/subaccount`



</td>
</tr>
<tr>
<td>

Delete a subaccount



</td>
<td>

`btp delete accounts/subaccount`



</td>
</tr>
<tr>
<td>

Move a subaccount



</td>
<td>

`btp move accounts/subaccount`



</td>
</tr>
<tr>
<td>

List the custom properties assigned to a subaccount



</td>
<td>

`btp list accounts/custom-property`



</td>
</tr>
<tr>
<td>

Get all available regions for global account



</td>
<td>

`btp list accounts/available-region`



</td>
</tr>
</table>

For more information, see [Subaccounts](Account_Model_8ed4a70.md#loio8d6e3a0fa4ab43e4a421d3ed08128afa).

**Parent topicColonSymbol** [Commands in the btp CLI](Commands_in_the_btp_CLI_a03a555.md "A list of all tasks and respective commands that are available in the SAP BTP command line interface (btp CLI).")

**Related Information**  


[Setting Entitlements Using the btp CLI](Setting_Entitlements_Using_the_btp_CLI_5af849c.md "Use the SAP BTP command line interface (btp CLI) to set entitlements to define the functionality or permissions available for users of global accounts, directories, and subaccounts.")

[Working with Environments Using the btp CLI](Working_with_Environments_Using_the_btp_CLI_48db155.md "Use the SAP BTP command line interface (btp CLI) to manage runtime environment instances in a subaccount. For example, enable the Cloud Foundry environment by creating a Cloud Foundry org (environment instance).")

[Working with Multitenant Applications Using the btp CLI](Working_with_Multitenant_Applications_Using_the_btp_CLI_c1b0fcc.md "Use the SAP BTP command line interface (btp CLI) to manage the multitenant applications to which a subaccount is entitled to subscribe.")

[Working with External Resource Providers Using the btp CLI](Working_with_External_Resource_Providers_Using_the_btp_CLI_48d7688.md "Use the SAP BTP command line interface (btp CLI) to get details, or to create or delete resource provider instances in a global account.")

[Managing Users and Their Authorizations Using the btp CLI](Managing_Users_and_Their_Authorizations_Using_the_btp_CLI_94bb593.md "User authorizations are managed by assigning role collections to users (for example, Subaccount Administrator). Use the SAP BTP command line interface (btp CLI) to manage roles and role collections, and to assign role collections to users.")

[Working With Resources of the SAP Service Manager Using the btp CLI](Working_With_Resources_of_the_SAP_Service_Manager_Using_the_btp_CLI_fe6a53b.md "Use the SAP BTP command line interface to perform various operations related to your platforms, attached service brokers, service instances, and service bindings.")

[Set the Default Command Context](Set_the_Default_Command_Context_720645a.md "Change the default context for all command calls to the global account, a directory, or a subaccount by using the btp target command.")

[Custom Properties \[Feature Set B\]](Account_Model_8ed4a70.md#loioe8663c08ead648faa673b0d63c5b478e "Custom properties allow you to label or tag your directories and subaccounts according to your own business and technical needs. This makes organizing and filtering your directories and subaccounts easier within your global account.")

