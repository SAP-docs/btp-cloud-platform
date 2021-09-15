<!-- loiofe6a53bfe48e4831b2f5ae7f06d4f07d -->

# Working With Resources of the SAP Service Manager Using the btp CLI

Use the SAP BTP command line interface to perform various operations related to your platforms, attached service brokers, service instances, and service bindings.

You can also get information about the service plans and service offerings associated with your subaccount.

For more information about the SAP Service Manager, see [SAP Service Manager](https://help.sap.com/viewer/521608084b7447839b1564e796ea0cdc/Internal/en-US/3a27b85a47fc4dff99184dd5bf181e14.html "SAP Service Manager service is the central registry for service brokers and platforms in SAP BTP.") :arrow_upper_right:.

> ### Tip:  
> All of these commands are executed for a specific subaccount. We recommend using the `btp target` command to set the default context to a subaccount. See [Set the Default Command Context](Set_the_Default_Command_Context_720645a.md).

For detailed descriptions of all SAP Service Manager CLI commands, see [SAP Service Manager Commands for SAP BTP command line interface \[Feature Set B\]](https://help.sap.com/viewer/09cc82baadc542a688176dce601398de/Cloud/en-US/4dceb6a597274c65b255a400bb837400.html).



<a name="loiofe6a53bfe48e4831b2f5ae7f06d4f07d__section_jhm_tvz_w3b"/>

## Managing Platforms


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

List all registered platforms in the current subaccount



</td>
<td>

`btp list services/platform`



</td>
</tr>
<tr>
<td>

Get details about a specific platform registered in the current subaccount



</td>
<td>

`btp get services/platform`



</td>
</tr>
<tr>
<td>

Register a new platform in the current subaccount



</td>
<td>

`btp register services/platform`



</td>
</tr>
<tr>
<td>

Update an existng platform registered in the current subaccount



</td>
<td>

`btp update services/platform`



</td>
</tr>
<tr>
<td>

Unregister an existing platform in the current subaccount



</td>
<td>

`btp unregister services/platform`



</td>
</tr>
</table>



<a name="loiofe6a53bfe48e4831b2f5ae7f06d4f07d__section_ojr_cvz_w3b"/>

## Managing Service Brokers


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

List all registered brokers in the current subaccount



</td>
<td>

`btp list services/broker`



</td>
</tr>
<tr>
<td>

Get a specific service broker in the current subaccount



</td>
<td>

`btp get services/broker`



</td>
</tr>
<tr>
<td>

Register a new service broker in the current subaccount



</td>
<td>

`btp register services/broker`



</td>
</tr>
<tr>
<td>

Update an existing service broker in the current subaccount



</td>
<td>

`btp update services/broker`



</td>
</tr>
<tr>
<td>

Unregister an existing service broker in the current subaccount



</td>
<td>

`btp unregister services/broker`



</td>
</tr>
</table>



<a name="loiofe6a53bfe48e4831b2f5ae7f06d4f07d__section_eyl_wvz_w3b"/>

## Managing Service Instances


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

List all service instances associated with the current subaccount.



</td>
<td>

`btp list services/instance`



</td>
</tr>
<tr>
<td>

Get details about a specific service instance associated with the current subaccount.



</td>
<td>

`btp get services/instance`



</td>
</tr>
<tr>
<td>

Create a new service instance of the service you want to consume.



</td>
<td>

`btp create services/instance`



</td>
</tr>
<tr>
<td>

Delete an existing service instance.



</td>
<td>

`btp delete services/instance`



</td>
</tr>
</table>



<a name="loiofe6a53bfe48e4831b2f5ae7f06d4f07d__section_tym_xvz_w3b"/>

## Managing Service Bindings


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

List all service bindings associated with the current subaccount.



</td>
<td>

`btp list services/binding`



</td>
</tr>
<tr>
<td>

Get details about a specific service binding associated with the current subaccount.



</td>
<td>

`btp get services/binding`



</td>
</tr>
<tr>
<td>

Create a new binding between an existing service instance and an application.



</td>
<td>

`btp create services/binding`



</td>
</tr>
<tr>
<td>

Delete an existing binding between a service instance and an application.



</td>
<td>

`btp delete services/instance`



</td>
</tr>
</table>



<a name="loiofe6a53bfe48e4831b2f5ae7f06d4f07d__section_qq1_crz_hmb"/>

## Viewing Service Plans


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

List all service plans of services available for consumption that are associated with your current subaccount.



</td>
<td>

`btp list services/plan`



</td>
</tr>
<tr>
<td>

Get details about a specific service plan of a service that is available for consumption and associated with your current subaccount.



</td>
<td>

`btp get services/plan`



</td>
</tr>
</table>



<a name="loiofe6a53bfe48e4831b2f5ae7f06d4f07d__section_skh_crz_hmb"/>

## Viewing Service Offerings


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

List all service offerings associated with your current subaccount.



</td>
<td>

`btp list services/offering`



</td>
</tr>
<tr>
<td>

Get details about a specific service offering associated with your subaccount.



</td>
<td>

`btp get services/offering`



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

[Managing Users and Their Authorizations Using the btp CLI](Managing_Users_and_Their_Authorizations_Using_the_btp_CLI_94bb593.md "User authorizations are managed by assigning role collections to users (for example, Subaccount Administrator). Use the SAP BTP command line interface (btp CLI) to manage roles and role collections, and to assign role collections to users.")

