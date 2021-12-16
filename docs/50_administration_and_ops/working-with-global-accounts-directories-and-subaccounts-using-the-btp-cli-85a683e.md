<!-- loio85a683e48f0a4c6db807c05d20f43883 -->

# Working with Global Accounts, Directories, and Subaccounts Using the btp CLI

Use the SAP BTP command line interface \(btp CLI\) to manage operations with global accounts, directories, and subaccounts.



<a name="loio85a683e48f0a4c6db807c05d20f43883__section_utc_hhb_ckb"/>

## Working with Global Accounts

> ### Tip:  
> These global account commands are always executed in the global account you're logged in to. You don't need to pass the global account parameter, even if you've targeted a subaccount or directory. See [Set the Default Command Context](set-the-default-command-context-720645a.md).


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

For more information, see [Global Accounts](../10_concepts/account-model-8ed4a70.md#loioc165d95ee700407eb181770901caec94).



<a name="loio85a683e48f0a4c6db807c05d20f43883__section_a13_xjb_ckb"/>

## Working with Directories

Directories allow you to organize and manage your subaccounts according to your technical and business needs.

> ### Tip:  
> By default, all commands are executed in the context of the global account you're logged in to. To change this default command context to a directory, use `btp target -dir *<my-directory-id\>*`. See [Set the Default Command Context](set-the-default-command-context-720645a.md).


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

List the user-defined labels assigned to a directory



</td>
<td valign="top">

`btp list accounts/labels`



</td>
</tr>
<tr>
<td valign="top">

List the custom properties assigned to a directory

> ### Note:  
> Custom properties are deprecated. Custom properties support only single values per key and are now replaced by the string array `labels`, which supports multiple values per key. Use `btp list accounts/labels` instead.



</td>
<td valign="top">

`btp list accounts/custom-property`



</td>
</tr>
</table>

For more information, see [Directories \[Feature Set B\]](../10_concepts/account-model-8ed4a70.md#loioa92721fc75524ec09a7a7255997dbd94).



<a name="loio85a683e48f0a4c6db807c05d20f43883__section_m5c_23b_ckb"/>

## Working with Subaccounts

> ### Tip:  
> By default, all commands are executed in the context of the global account you're logged in to. To change this default command context to a subaccount, use `btp target -sa *<my-subaccount-id\>*`. See [Set the Default Command Context](set-the-default-command-context-720645a.md).


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

List the user-defined labels assigned to a subaccount



</td>
<td valign="top">

`btp list accounts/labels`



</td>
</tr>
<tr>
<td valign="top">

List the custom properties assigned to a subaccount

> ### Note:  
> Custom properties are deprecated. Custom properties support only single values per key and are now replaced by the string array `labels`, which supports multiple values per key. Use `btp list accounts/labels` instead.



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

For more information, see [Subaccounts](../10_concepts/account-model-8ed4a70.md#loio8d6e3a0fa4ab43e4a421d3ed08128afa).

**Related Information**  


[Setting Entitlements Using the btp CLI](setting-entitlements-using-the-btp-cli-5af849c.md "Use the SAP BTP command line interface (btp CLI) to set entitlements to define the functionality or permissions available for users of global accounts, directories, and subaccounts.")

[Working with Environments Using the btp CLI](working-with-environments-using-the-btp-cli-48db155.md "Use the SAP BTP command line interface (btp CLI) to manage runtime environment instances in a subaccount. For example, enable the Cloud Foundry environment by creating a Cloud Foundry org (environment instance).")

[Working with Multitenant Applications Using the btp CLI](working-with-multitenant-applications-using-the-btp-cli-c1b0fcc.md "Use the SAP BTP command line interface (btp CLI) to manage the multitenant applications to which a subaccount is entitled to subscribe.")

[Working with External Resource Providers Using the btp CLI](working-with-external-resource-providers-using-the-btp-cli-48d7688.md "Use the SAP BTP command line interface (btp CLI) to get details, or to create or delete resource provider instances in a global account.")

[Managing Users and Their Authorizations Using the btp CLI](managing-users-and-their-authorizations-using-the-btp-cli-94bb593.md "User authorizations are managed by assigning role collections to users (for example, Subaccount Administrator). Use the SAP BTP command line interface (btp CLI) to manage roles and role collections, and to assign role collections to users.")

[Working With Resources of the SAP Service Manager Using the btp CLI](working-with-resources-of-the-sap-service-manager-using-the-btp-cli-fe6a53b.md "Use the SAP BTP command line interface to perform various operations related to your platforms, attached service brokers, service instances, and service bindings.")

[Set the Default Command Context](set-the-default-command-context-720645a.md "Change the default context for all command calls to the global account, a directory, or a subaccount by using the btp target command.")

[Labels \[Feature Set B\]](../10_concepts/account-model-8ed4a70.md#loioe8663c08ead648faa673b0d63c5b478e "Labels are user-defined words or phrases that you can assign to various entities in SAP BTP to categorize them in your global account, to identify them more easily.")

