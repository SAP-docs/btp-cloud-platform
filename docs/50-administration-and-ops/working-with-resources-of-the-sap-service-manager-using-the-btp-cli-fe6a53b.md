<!-- loiofe6a53bfe48e4831b2f5ae7f06d4f07d -->

# Working With Resources of the SAP Service Manager Using the btp CLI

Use the SAP BTP command line interface to perform various operations related to your platforms, attached service brokers, service instances, and service bindings.

You can also get information about the service plans and service offerings associated with your subaccount.

For more information about the SAP Service Manager, see [SAP Service Manager](https://help.sap.com/viewer/09cc82baadc542a688176dce601398de/Cloud/en-US/3a27b85a47fc4dff99184dd5bf181e14.html).

> ### Tip:  
> All of these commands are executed in subaccounts. If you know you'll be working in a specific subaccount, we recommend using the `btp target` command to set the target to this subaccount. Then you won't have to provide the subaccount ID with every command call. See [Set a Target for Subsequent Commands with btp target](set-a-target-for-subsequent-commands-with-btp-target-720645a.md).

For detailed descriptions of all SAP Service Manager CLI commands, see [SAP Service Manager Commands for SAP BTP command line interface \[Feature Set B\]](https://help.sap.com/viewer/09cc82baadc542a688176dce601398de/Cloud/en-US/4dceb6a597274c65b255a400bb837400.html).



<a name="loiofe6a53bfe48e4831b2f5ae7f06d4f07d__section_jhm_tvz_w3b"/>

## Managing Platforms


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

List all registered platforms in the current subaccount



</td>
<td valign="top">

`btp list services/platform`



</td>
<td valign="top">

[btp list services/platform](https://help.sap.com/docs/BTP/btp-cli/btp-list-services-platform.html)



</td>
</tr>
<tr>
<td valign="top">

Get details about a specific platform registered in the current subaccount



</td>
<td valign="top">

`btp get services/platform`



</td>
<td valign="top">

[btp get services/platform](https://help.sap.com/docs/BTP/btp-cli/btp-get-services-platform.html)



</td>
</tr>
<tr>
<td valign="top">

Register a new platform in the current subaccount



</td>
<td valign="top">

`btp register services/platform`



</td>
<td valign="top">

[btp register services/platform](https://help.sap.com/docs/BTP/btp-cli/btp-register-services-platform.html)



</td>
</tr>
<tr>
<td valign="top">

Update an existing platform registered in the current subaccount



</td>
<td valign="top">

`btp update services/platform`



</td>
<td valign="top">

[btp update services/platform](https://help.sap.com/docs/BTP/btp-cli/btp-update-services-platform.html)



</td>
</tr>
<tr>
<td valign="top">

Unregister an existing platform in the current subaccount



</td>
<td valign="top">

`btp unregister services/platform`



</td>
<td valign="top">

[btp unregister services/platform](https://help.sap.com/docs/BTP/btp-cli/btp-unregister-services-platform.html)



</td>
</tr>
</table>



<a name="loiofe6a53bfe48e4831b2f5ae7f06d4f07d__section_ojr_cvz_w3b"/>

## Managing Service Brokers


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

List all registered brokers in the current subaccount



</td>
<td valign="top">

`btp list services/broker`



</td>
<td valign="top">

[btp list services/broker](https://help.sap.com/docs/BTP/btp-cli/btp-list-services-broker.html)



</td>
</tr>
<tr>
<td valign="top">

Get a specific service broker in the current subaccount



</td>
<td valign="top">

`btp get services/broker`



</td>
<td valign="top">

[btp get services/broker](https://help.sap.com/docs/BTP/btp-cli/btp-get-services-broker.html)



</td>
</tr>
<tr>
<td valign="top">

Register a new service broker in the current subaccount



</td>
<td valign="top">

`btp register services/broker`



</td>
<td valign="top">

[btp register services/broker](https://help.sap.com/docs/BTP/btp-cli/btp-register-services-broker.html)



</td>
</tr>
<tr>
<td valign="top">

Update an existing service broker in the current subaccount



</td>
<td valign="top">

`btp update services/broker`



</td>
<td valign="top">

[btp update services/broker](https://help.sap.com/docs/BTP/btp-cli/btp-update-services-broker.html)



</td>
</tr>
<tr>
<td valign="top">

Unregister an existing service broker in the current subaccount



</td>
<td valign="top">

`btp unregister services/broker`



</td>
<td valign="top">

[btp unregister services/broker](https://help.sap.com/docs/BTP/btp-cli/btp-unregister-services-broker.html)



</td>
</tr>
</table>



<a name="loiofe6a53bfe48e4831b2f5ae7f06d4f07d__section_eyl_wvz_w3b"/>

## Managing Service Instances


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

List all service instances associated with the current subaccount.



</td>
<td valign="top">

`btp list services/instance`



</td>
<td valign="top">

[btp list services/instance](https://help.sap.com/docs/BTP/btp-cli/btp-list-services-instance.html)



</td>
</tr>
<tr>
<td valign="top">

Get details about a specific service instance associated with the current subaccount.



</td>
<td valign="top">

`btp get services/instance`



</td>
<td valign="top">

[btp get services/instance](https://help.sap.com/docs/BTP/btp-cli/btp-get-services-instance.html)



</td>
</tr>
<tr>
<td valign="top">

Create a new service instance of the service you want to consume.



</td>
<td valign="top">

`btp create services/instance`



</td>
<td valign="top">

[btp create services/instance](https://help.sap.com/docs/BTP/btp-cli/btp-create-services-instance.html)



</td>
</tr>
<tr>
<td valign="top">

Delete an existing service instance.



</td>
<td valign="top">

`btp delete services/instance`



</td>
<td valign="top">

[btp delete services/instance](https://help.sap.com/docs/BTP/btp-cli/btp-delete-services-instance.html)



</td>
</tr>
</table>



<a name="loiofe6a53bfe48e4831b2f5ae7f06d4f07d__section_tym_xvz_w3b"/>

## Managing Service Bindings


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

List all service bindings associated with the current subaccount.



</td>
<td valign="top">

`btp list services/binding`



</td>
<td valign="top">

[btp list services/binding](https://help.sap.com/docs/BTP/btp-cli/btp-list-services-binding.html)



</td>
</tr>
<tr>
<td valign="top">

Get details about a specific service binding associated with the current subaccount.



</td>
<td valign="top">

`btp get services/binding`



</td>
<td valign="top">

[btp get services/binding](https://help.sap.com/docs/BTP/btp-cli/btp-get-services-binding.html)



</td>
</tr>
<tr>
<td valign="top">

Create a new binding between an existing service instance and an application.



</td>
<td valign="top">

`btp create services/binding`



</td>
<td valign="top">

[btp create services/binding](https://help.sap.com/docs/BTP/btp-cli/btp-create-services-binding.html)



</td>
</tr>
<tr>
<td valign="top">

Delete an existing binding between a service instance and an application.



</td>
<td valign="top">

`btp delete services/binding`



</td>
<td valign="top">

[btp delete services/binding](https://help.sap.com/docs/BTP/btp-cli/btp-delete-services-binding.html)



</td>
</tr>
</table>



<a name="loiofe6a53bfe48e4831b2f5ae7f06d4f07d__section_qq1_crz_hmb"/>

## Viewing Service Plans


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

List all service plans of services available for consumption that are associated with your current subaccount.



</td>
<td valign="top">

`btp list services/plan`



</td>
<td valign="top">

[btp list services/plan](https://help.sap.com/docs/BTP/btp-cli/btp-list-services-plan.html)



</td>
</tr>
<tr>
<td valign="top">

Get details about a specific service plan of a service that is available for consumption and associated with your current subaccount.



</td>
<td valign="top">

`btp get services/plan`



</td>
<td valign="top">

[btp get services/plan](https://help.sap.com/docs/BTP/btp-cli/btp-get-services-plan.html)



</td>
</tr>
</table>



<a name="loiofe6a53bfe48e4831b2f5ae7f06d4f07d__section_skh_crz_hmb"/>

## Viewing Service Offerings


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

List all service offerings associated with your current subaccount.



</td>
<td valign="top">

`btp list services/offering`



</td>
<td valign="top">

[btp list services/offering](https://help.sap.com/docs/BTP/btp-cli/btp-list-services-offering.html)



</td>
</tr>
<tr>
<td valign="top">

Get details about a specific service offering associated with your subaccount.



</td>
<td valign="top">

`btp get services/offering`



</td>
<td valign="top">

[btp get services/offering](https://help.sap.com/docs/BTP/btp-cli/btp-get-services-offering.html)



</td>
</tr>
</table>

**Related Information**  


[Working with Global Accounts, Directories, and Subaccounts Using the btp CLI](working-with-global-accounts-directories-and-subaccounts-using-the-btp-cli-85a683e.md "Use the SAP BTP command line interface (btp CLI) to manage operations with global accounts, directories, and subaccounts.")

[Setting Entitlements Using the btp CLI](setting-entitlements-using-the-btp-cli-5af849c.md "Use the SAP BTP command line interface (btp CLI) to set entitlements to define the functionality or permissions available for users of global accounts, directories, and subaccounts.")

[Working with Environments Using the btp CLI](working-with-environments-using-the-btp-cli-48db155.md "Use the SAP BTP command line interface (btp CLI) to manage runtime environment instances in a subaccount. For example, enable the Cloud Foundry environment by creating a Cloud Foundry org (environment instance).")

[Working with Multitenant Applications Using the btp CLI](working-with-multitenant-applications-using-the-btp-cli-c1b0fcc.md "Use the SAP BTP command line interface (btp CLI) to manage the multitenant applications to which a subaccount is entitled to subscribe.")

[Working with External Resource Providers Using the btp CLI](working-with-external-resource-providers-using-the-btp-cli-48d7688.md "Use the SAP BTP command line interface (btp CLI) to get details, or to create or delete resource provider instances in a global account.")

[Managing Trust from SAP BTP to an Identity Authentication Tenant](managing-trust-from-sap-btp-to-an-identity-authentication-tenant-6140107.md "SAP BTP supports identity federation. Its concept is to reuse the user bases of identity providers. To use a custom identity provider, your global account or subaccount in SAP BTP must have a trust relationship to the identity provider you want to use.")

[Managing Users and Their Authorizations Using the btp CLI](managing-users-and-their-authorizations-using-the-btp-cli-94bb593.md "User authorizations are managed by assigning role collections to users (for example, Subaccount Administrator). Use the SAP BTP command-line interface (btp CLI) to manage roles and role collections, and to assign role collections to users.")

[Managing Signing Keys for Access Tokens](managing-signing-keys-for-access-tokens-dfca1d3.md "Use the SAP BTP command line interface (btp CLI) to manage signing keys for access tokens in the subaccount.")

[Managing Security Settings](managing-security-settings-168dd75.md "Use the SAP BTP command line interface (btp CLI) to display and update the security settings for the subaccount.")

[btp CLI Command Reference](https://help.sap.com/docs/BTP/btp-cli/intro.html)

