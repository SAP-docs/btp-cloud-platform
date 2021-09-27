<!-- loioc1b0fcc400384fedba325795dc10871d -->

# Working with Multitenant Applications Using the btp CLI

Use the SAP BTP command line interface \(btp CLI\) to manage the multitenant applications to which a subaccount is entitled to subscribe.


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

Get all applications to which a subaccount is entitled to subscribe



</td>
<td>

`btp list accounts/subscription`



</td>
</tr>
<tr>
<td>

Get details of a multitenant application in a subaccount



</td>
<td>

`btp get accounts/subscription`



</td>
</tr>
<tr>
<td>

Subscribe to an application from a subaccount



</td>
<td>

`btp subscribe accounts/subaccount`



</td>
</tr>
<tr>
<td>

Update the plan of an existing subscription

> ### Note:  
> You can update a subscription plan only if additional plans for the application are entitled to the subaccount you're using and if your subscription is eligible for a plan update.



</td>
<td>

`btp update accounts/subscription`



</td>
</tr>
<tr>
<td>

Unsubscribe an application from a subaccount



</td>
<td>

`btp unsubscribe accounts/subaccount`



</td>
</tr>
</table>

For more information, see [Subscribe to Multitenant Applications Using the Cockpit](Subscribe_to_Multitenant_Applications_Using_the_Cockpit_7a3e396.md).

**Parent topicColonSymbol** [Commands in the btp CLI](Commands_in_the_btp_CLI_a03a555.md "A list of all tasks and respective commands that are available in the SAP BTP command line interface (btp CLI).")

**Related Information**  


[Working with Global Accounts, Directories, and Subaccounts Using the btp CLI](Working_with_Global_Accounts,_Directories,_and_Subaccounts_Using_the_btp_CLI_85a683e.md "Use the SAP BTP command line interface (btp CLI) to manage operations with global accounts, directories, and subaccounts.")

[Setting Entitlements Using the btp CLI](Setting_Entitlements_Using_the_btp_CLI_5af849c.md "Use the SAP BTP command line interface (btp CLI) to set entitlements to define the functionality or permissions available for users of global accounts, directories, and subaccounts.")

[Working with Environments Using the btp CLI](Working_with_Environments_Using_the_btp_CLI_48db155.md "Use the SAP BTP command line interface (btp CLI) to manage runtime environment instances in a subaccount. For example, enable the Cloud Foundry environment by creating a Cloud Foundry org (environment instance).")

[Working with External Resource Providers Using the btp CLI](Working_with_External_Resource_Providers_Using_the_btp_CLI_48d7688.md "Use the SAP BTP command line interface (btp CLI) to get details, or to create or delete resource provider instances in a global account.")

[Managing Users and Their Authorizations Using the btp CLI](Managing_Users_and_Their_Authorizations_Using_the_btp_CLI_94bb593.md "User authorizations are managed by assigning role collections to users (for example, Subaccount Administrator). Use the SAP BTP command line interface (btp CLI) to manage roles and role collections, and to assign role collections to users.")

[Working With Resources of the SAP Service Manager Using the btp CLI](Working_With_Resources_of_the_SAP_Service_Manager_Using_the_btp_CLI_fe6a53b.md "Use the SAP BTP command line interface to perform various operations related to your platforms, attached service brokers, service instances, and service bindings.")

