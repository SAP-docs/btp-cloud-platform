<!-- loio48d7688f166642dca0c431f55d1d141f -->

# Working with External Resource Providers Using the btp CLI

Use the SAP BTP command line interface \(btp CLI\) to get details, or to create or delete resource provider instances in a global account.

> ### Note:  
> The use of this functionality is subject to the availability of the supported non-SAP cloud vendors in your country or region.

Creating a resource provider instance allows your global account to connect to your provider account on a non-SAP cloud vendor. Through this channel, you can then consume remote service resources that you already own and which are supported by SAP BTP.


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

List all resource provider instances in a global account



</td>
<td>

`btp list accounts/resource-provider`



</td>
</tr>
<tr>
<td>

Get details about a resource provider instance



</td>
<td>

`btp get accounts/resource-provider`



</td>
</tr>
<tr>
<td>

Create a resource provider instance



</td>
<td>

`btp create accounts/resource-provider`



</td>
</tr>
<tr>
<td>

Update a resource provider instance



</td>
<td>

`btp update accounts/resource-provider`



</td>
</tr>
<tr>
<td>

Delete a resource provider instance



</td>
<td>

`btp delete accounts/resource-provider`



</td>
</tr>
</table>

For more information, see [Managing Resource Providers](Managing_Resource_Providers_e2c250d.md).

**Parent topicColonSymbol** [Commands in the btp CLI](Commands_in_the_btp_CLI_a03a555.md "A list of all tasks and respective commands that are available in the SAP BTP command line interface (btp CLI).")

**Related Information**  


[Working with Global Accounts, Directories, and Subaccounts Using the btp CLI](Working_with_Global_Accounts,_Directories,_and_Subaccounts_Using_the_btp_CLI_85a683e.md "Use the SAP BTP command line interface (btp CLI) to manage operations with global accounts, directories, and subaccounts.")

[Setting Entitlements Using the btp CLI](Setting_Entitlements_Using_the_btp_CLI_5af849c.md "Use the SAP BTP command line interface (btp CLI) to set entitlements to define the functionality or permissions available for users of global accounts, directories, and subaccounts.")

[Working with Environments Using the btp CLI](Working_with_Environments_Using_the_btp_CLI_48db155.md "Use the SAP BTP command line interface (btp CLI) to manage runtime environment instances in a subaccount. For example, enable the Cloud Foundry environment by creating a Cloud Foundry org (environment instance).")

[Working with Multitenant Applications Using the btp CLI](Working_with_Multitenant_Applications_Using_the_btp_CLI_c1b0fcc.md "Use the SAP BTP command line interface (btp CLI) to manage the multitenant applications to which a subaccount is entitled to subscribe.")

[Managing Users and Their Authorizations Using the btp CLI](Managing_Users_and_Their_Authorizations_Using_the_btp_CLI_94bb593.md "User authorizations are managed by assigning role collections to users (for example, Subaccount Administrator). Use the SAP BTP command line interface (btp CLI) to manage roles and role collections, and to assign role collections to users.")

[Working With Resources of the SAP Service Manager Using the btp CLI](Working_With_Resources_of_the_SAP_Service_Manager_Using_the_btp_CLI_fe6a53b.md "Use the SAP BTP command line interface to perform various operations related to your platforms, attached service brokers, service instances, and service bindings.")

