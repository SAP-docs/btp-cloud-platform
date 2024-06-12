<!-- loio48db1553eb18451e8f71fc56d99ede71 -->

# Working with Environments Using the btp CLI

Use the SAP BTP command line interface \(btp CLI\) to manage runtime environment instances in a subaccount. For example, enable the Cloud Foundry environment by creating a Cloud Foundry org \(environment instance\).

> ### Tip:  
> By default, all commands are executed in the global account you're logged in to. To change this target to a subaccount, use <code>btp target -sa <i class="varname">&lt;my-subaccount-id&gt;</i></code>. See [Set a Target for Subsequent Commands with btp target](set-a-target-for-subsequent-commands-with-btp-target-720645a.md).


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

Get all available environments for a subaccount

</td>
<td valign="top">

`btp list accounts/available-environment`

</td>
<td valign="top">

[btp list accounts/available-environment](https://help.sap.com/docs/BTP/btp-cli/btp-list-accounts-available-environment.html)

</td>
</tr>
<tr>
<td valign="top">

Get details about an environment available for a subaccount

</td>
<td valign="top">

`btp get accounts/available-environment`

</td>
<td valign="top">

[btp get accounts/available-environment](https://help.sap.com/docs/BTP/btp-cli/btp-get-accounts-available-environment.html)

</td>
</tr>
<tr>
<td valign="top">

Get all environment instances of a subaccount

</td>
<td valign="top">

`btp list accounts/environment-instance`

</td>
<td valign="top">

[btp list accounts/environment-instance](https://help.sap.com/docs/BTP/btp-cli/btp-list-accounts-environment-instance.html)

</td>
</tr>
<tr>
<td valign="top">

Get a specific environment instance of a subaccount

</td>
<td valign="top">

`btp get accounts/environment-instance`

</td>
<td valign="top">

[btp get accounts/environment-instance](https://help.sap.com/docs/BTP/btp-cli/btp-get-accounts-environment-instance.html)

</td>
</tr>
<tr>
<td valign="top">

Create an environment instance in a subaccount

</td>
<td valign="top">

`btp create accounts/environment-instance`

</td>
<td valign="top">

[btp create accounts/environment-instance](https://help.sap.com/docs/BTP/btp-cli/btp-create-accounts-environment-instance.html)

</td>
</tr>
<tr>
<td valign="top">

Update the plan and/or configuration parameters of an environment in a subaccount

</td>
<td valign="top">

`btp update accounts/environment-instance`

</td>
<td valign="top">

[btp update accounts/environment-instance](https://help.sap.com/docs/BTP/btp-cli/btp-update-accounts-environment-instance.html)

</td>
</tr>
<tr>
<td valign="top">

Delete environment instances of a subaccount

</td>
<td valign="top">

`btp delete accounts/environment-instance`

</td>
<td valign="top">

[btp delete accounts/environment-instance](https://help.sap.com/docs/BTP/btp-cli/btp-delete-accounts-environment-instance.html)

</td>
</tr>
</table>

**Related Information**  


[Working with Global Accounts, Directories, and Subaccounts Using the btp CLI](working-with-global-accounts-directories-and-subaccounts-using-the-btp-cli-85a683e.md "Use the SAP BTP command line interface (btp CLI) to manage operations with global accounts, directories, and subaccounts.")

[Setting Entitlements Using the btp CLI](setting-entitlements-using-the-btp-cli-5af849c.md "Use the SAP BTP command line interface (btp CLI) to set entitlements to define the functionality or permissions available for users of global accounts, directories, and subaccounts.")

[Working with Multitenant Applications Using the btp CLI](working-with-multitenant-applications-using-the-btp-cli-c1b0fcc.md "Use the SAP BTP command line interface (btp CLI) to manage the multitenant applications to which a subaccount is entitled to subscribe.")

[Working with External Resource Providers Using the btp CLI](working-with-external-resource-providers-using-the-btp-cli-48d7688.md "Use the SAP BTP command line interface (btp CLI) to get details, or to create or delete resource provider instances in a global account.")

[Managing Trust from SAP BTP to an SAP Cloud Identity Services Tenant](managing-trust-from-sap-btp-to-an-sap-cloud-identity-services-tenant-6140107.md "SAP BTP supports identity federation. Its concept is to reuse the user bases of identity providers. To use a custom identity provider, your global account or subaccount in SAP BTP must have a trust relationship to the identity provider you want to use.")

[Managing Users and Their Authorizations Using the btp CLI](managing-users-and-their-authorizations-using-the-btp-cli-94bb593.md "User authorizations are managed by assigning role collections to users (for example, Subaccount Administrator). Use the SAP BTP command-line interface (btp CLI) to manage roles and role collections, and to assign role collections to users.")

[Managing Signing Keys for Access Tokens](managing-signing-keys-for-access-tokens-dfca1d3.md "Use the SAP BTP command line interface (btp CLI) to manage signing keys for access tokens in the subaccount.")

[Managing Security Settings](managing-security-settings-168dd75.md "Use the SAP BTP command line interface (btp CLI) to display and update the security settings for the subaccount.")

[Managing API Credentials for Calling REST APIs of SAP Authorization and Trust Management Service](managing-api-credentials-for-calling-rest-apis-of-sap-authorization-and-trust-managemen-ce43eb5.md "Use the SAP BTP command line interface (btp CLI) to manage API credentials, which enable you to access the REST APIs of the SAP Authorization and Trust Management service.")

[Working with Resources of the SAP Service Manager Using the btp CLI](working-with-resources-of-the-sap-service-manager-using-the-btp-cli-fe6a53b.md "Use the SAP BTP command line interface to perform various operations related to your platforms, attached service brokers, service instances, and service bindings.")

[Org Management Using the SAP BTP Command Line Interface \(btp CLI\) \[Feature Set B\]](org-management-using-the-sap-btp-command-line-interface-btp-cli-feature-set-b-aee40e1.md "The Cloud Foundry environment allows you to create polyglot cloud applications in Cloud Foundry. To manage the lifecycle of an org in the Cloud Foundry environment, use the accounts/environment-instance command in the btp CLI.")

[btp CLI Command Reference](https://help.sap.com/docs/BTP/btp-cli/intro.html)

