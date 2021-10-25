<!-- loio85a683e48f0a4c6db807c05d20f43883 -->

# Working with Global Accounts, Directories, and Subaccounts Using the btp CLI

Use the SAP BTP command line interface \(btp CLI\) to manage operations with global accounts, directories, and subaccounts.



<a name="loio85a683e48f0a4c6db807c05d20f43883__section_utc_hhb_ckb"/>

## Working with Global Accounts


<table>
<tr>
<th valign="top">

Task



</th>
<th valign="top">

Run the command...



</th>
</tr>
<tr>
<td valign="top">

Get details about a global account, and the account structure \(directories and subaccounts\) of the global account.



</td>
<td valign="top">

`btp get accounts/global-account`



</td>
</tr>
<tr>
<td valign="top">

Update the display name and/or description of a global account.



</td>
<td valign="top">

`btp update accounts/global-account`



</td>
</tr>
</table>

For more information, see [Global Accounts](../10-concepts/Account_Model_8ed4a70.md#loioc165d95ee700407eb181770901caec94).



<a name="loio85a683e48f0a4c6db807c05d20f43883__section_a13_xjb_ckb"/>

## Working with Directories

Directories allow you to organize and manage your subaccounts according to your technical and business needs.


<table>
<tr>
<th valign="top">

Task



</th>
<th valign="top">

Run the command...



</th>
</tr>
<tr>
<td valign="top">

Get details about a directory and list the subaccounts and subdirectories in the directory



</td>
<td valign="top">

`btp get accounts/directory`



</td>
</tr>
<tr>
<td valign="top">

Create a directory



</td>
<td valign="top">

`btp create accounts/directory`



</td>
</tr>
<tr>
<td valign="top">

Update a directory



</td>
<td valign="top">

`btp update accounts/directory`



</td>
</tr>
<tr>
<td valign="top">

Delete a directory



</td>
<td valign="top">

`btp delete accounts/directory`



</td>
</tr>
<tr>
<td valign="top">

Change the set of enabled features \(user and entitlement management\) for a directory



</td>
<td valign="top">

`btp enable accounts/directory`



</td>
</tr>
<tr>
<td valign="top">

List the custom properties assigned to a directory



</td>
<td valign="top">

`btp list accounts/custom-property`



</td>
</tr>
</table>

For more information, see [Directories \[Feature Set B\]](../10-concepts/Account_Model_8ed4a70.md#loioa92721fc75524ec09a7a7255997dbd94).



<a name="loio85a683e48f0a4c6db807c05d20f43883__section_m5c_23b_ckb"/>

## Working with Subaccounts


<table>
<tr>
<th valign="top">

Task



</th>
<th valign="top">

Run the command...



</th>
</tr>
<tr>
<td valign="top">

List all subaccounts in a global account



</td>
<td valign="top">

`btp list accounts/subaccount`



</td>
</tr>
<tr>
<td valign="top">

Get details about a subaccount



</td>
<td valign="top">

`btp get accounts/subaccount`



</td>
</tr>
<tr>
<td valign="top">

Create a subaccount



</td>
<td valign="top">

`btp create accounts/subaccount`



</td>
</tr>
<tr>
<td valign="top">

Update a subaccount



</td>
<td valign="top">

`btp update accounts/subaccount`



</td>
</tr>
<tr>
<td valign="top">

Delete a subaccount



</td>
<td valign="top">

`btp delete accounts/subaccount`



</td>
</tr>
<tr>
<td valign="top">

Move a subaccount



</td>
<td valign="top">

`btp move accounts/subaccount`



</td>
</tr>
<tr>
<td valign="top">

List the custom properties assigned to a subaccount



</td>
<td valign="top">

`btp list accounts/custom-property`



</td>
</tr>
<tr>
<td valign="top">

Get all available regions for global account



</td>
<td valign="top">

`btp list accounts/available-region`



</td>
</tr>
</table>

For more information, see [Subaccounts](../10-concepts/Account_Model_8ed4a70.md#loio8d6e3a0fa4ab43e4a421d3ed08128afa).

**Related Information**  


[Setting Entitlements Using the btp CLI](Setting_Entitlements_Using_the_btp_CLI_5af849c.md "Use the SAP BTP command line interface (btp CLI) to set entitlements to define the functionality or permissions available for users of global accounts, directories, and subaccounts.")

[Working with Environments Using the btp CLI](Working_with_Environments_Using_the_btp_CLI_48db155.md "Use the SAP BTP command line interface (btp CLI) to manage runtime environment instances in a subaccount. For example, enable the Cloud Foundry environment by creating a Cloud Foundry org (environment instance).")

[Working with Multitenant Applications Using the btp CLI](Working_with_Multitenant_Applications_Using_the_btp_CLI_c1b0fcc.md "Use the SAP BTP command line interface (btp CLI) to manage the multitenant applications to which a subaccount is entitled to subscribe.")

[Working with External Resource Providers Using the btp CLI](Working_with_External_Resource_Providers_Using_the_btp_CLI_48d7688.md "Use the SAP BTP command line interface (btp CLI) to get details, or to create or delete resource provider instances in a global account.")

[Managing Users and Their Authorizations Using the btp CLI](Managing_Users_and_Their_Authorizations_Using_the_btp_CLI_94bb593.md "User authorizations are managed by assigning role collections to users (for example, Subaccount Administrator). Use the SAP BTP command line interface (btp CLI) to manage roles and role collections, and to assign role collections to users.")

[Working With Resources of the SAP Service Manager Using the btp CLI](Working_With_Resources_of_the_SAP_Service_Manager_Using_the_btp_CLI_fe6a53b.md "Use the SAP BTP command line interface to perform various operations related to your platforms, attached service brokers, service instances, and service bindings.")

[Set the Default Command Context](Set_the_Default_Command_Context_720645a.md "Change the default context for all command calls to the global account, a directory, or a subaccount by using the btp target command.")

[Custom Properties \[Feature Set B\]](../10-concepts/Account_Model_8ed4a70.md#loioe8663c08ead648faa673b0d63c5b478e "Custom properties allow you to label or tag your directories and subaccounts according to your own business and technical needs. This makes organizing and filtering your directories and subaccounts easier within your global account.")

