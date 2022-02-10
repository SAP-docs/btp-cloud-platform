<!-- loioc1b0fcc400384fedba325795dc10871d -->

# Working with Multitenant Applications Using the btp CLI

Use the SAP BTP command line interface \(btp CLI\) to manage the multitenant applications to which a subaccount is entitled to subscribe.

> ### Tip:  
> By default, all commands are executed in the global account you're logged in to. To change this target to a subaccount, use <code>btp target -sa <i class="varname">&lt;my-subaccount-id&gt;</i></code>. See [Set a Target for Subsequent Commands with btp target](set-a-target-for-subsequent-commands-with-btp-target-720645a.md).


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

Get all applications to which a subaccount is entitled to subscribe



</td>
<td valign="top">

`btp list accounts/subscription`



</td>
</tr>
<tr>
<td valign="top">

Get details of a multitenant application in a subaccount



</td>
<td valign="top">

`btp get accounts/subscription`



</td>
</tr>
<tr>
<td valign="top">

Subscribe to an application from a subaccount



</td>
<td valign="top">

`btp subscribe accounts/subaccount`



</td>
</tr>
<tr>
<td valign="top">

Update the plan of an existing subscription

> ### Note:  
> You can update a subscription plan only if additional plans for the application are entitled to the subaccount you're using and if your subscription is eligible for a plan update.



</td>
<td valign="top">

`btp update accounts/subscription`



</td>
</tr>
<tr>
<td valign="top">

Unsubscribe an application from a subaccount



</td>
<td valign="top">

`btp unsubscribe accounts/subaccount`



</td>
</tr>
</table>

For more information, see [Subscribe to Multitenant Applications Using the Cockpit](subscribe-to-multitenant-applications-using-the-cockpit-7a3e396.md).

**Related Information**  


[Working with Global Accounts, Directories, and Subaccounts Using the btp CLI](working-with-global-accounts-directories-and-subaccounts-using-the-btp-cli-85a683e.md "Use the SAP BTP command line interface (btp CLI) to manage operations with global accounts, directories, and subaccounts.")

[Setting Entitlements Using the btp CLI](setting-entitlements-using-the-btp-cli-5af849c.md "Use the SAP BTP command line interface (btp CLI) to set entitlements to define the functionality or permissions available for users of global accounts, directories, and subaccounts.")

[Working with Environments Using the btp CLI](working-with-environments-using-the-btp-cli-48db155.md "Use the SAP BTP command line interface (btp CLI) to manage runtime environment instances in a subaccount. For example, enable the Cloud Foundry environment by creating a Cloud Foundry org (environment instance).")

[Working with External Resource Providers Using the btp CLI](working-with-external-resource-providers-using-the-btp-cli-48d7688.md "Use the SAP BTP command line interface (btp CLI) to get details, or to create or delete resource provider instances in a global account.")

[Managing Users and Their Authorizations Using the btp CLI](managing-users-and-their-authorizations-using-the-btp-cli-94bb593.md "User authorizations are managed by assigning role collections to users (for example, Subaccount Administrator). Use the SAP BTP command line interface (btp CLI) to manage roles and role collections, and to assign role collections to users.")

[Working With Resources of the SAP Service Manager Using the btp CLI](working-with-resources-of-the-sap-service-manager-using-the-btp-cli-fe6a53b.md "Use the SAP BTP command line interface to perform various operations related to your platforms, attached service brokers, service instances, and service bindings.")

