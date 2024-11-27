<!-- loiodfca1d3ff19240f5ad6b88bc935515f4 -->

# Managing Signing Keys for Access Tokens

Use the SAP BTP command line interface \(btp CLI\) to manage signing keys for access tokens in the subaccount.

You can create and manage signing keys for access tokens.

> ### Note:  
> The newly created key only becomes active once you enable it. The number of keys is restricted to 2 per subaccount.

When a signing key is enabled, all newly requested tokens are signed with this key and the existing signing key is disabled. It's also possible to list all signing keys, no matter whether they're enabled or disabled. You can also delete a disabled signing key.

For more information, see [**Rotate Signing Keys of Access Tokens**](https://help.sap.com/docs/CP_AUTHORIZ_TRUST_MNG/ae8e8427ecdf407790d96dad93b5f723/b279adf3ec134b2a8611a42bff1ee9d9.html).


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

Create a new signing key for access tokens

</td>
<td valign="top">

`btp create security/token-key`

</td>
<td valign="top">

[btp create security/token-key](https://help.sap.com/docs/BTP/btp-cli/btp-create-security-token-key.html)

</td>
</tr>
<tr>
<td valign="top">

Enable an existing key as signing key for access tokens

</td>
<td valign="top">

`btp enable security/token-key`

</td>
<td valign="top">

[btp enable security/token-key](https://help.sap.com/docs/BTP/btp-cli/btp-enable-security-token-key.html)

</td>
</tr>
<tr>
<td valign="top">

Delete a disabled signing key for access tokens

</td>
<td valign="top">

`btp delete security/token-key` 

</td>
<td valign="top">

[btp delete security/token-key](https://help.sap.com/docs/BTP/btp-cli/btp-delete-security-token-key.html)

</td>
</tr>
<tr>
<td valign="top">

List the existing signing keys for access tokens and indicates which key is currently enabled

</td>
<td valign="top">

`btp list security/token-key`

</td>
<td valign="top">

[btp list security/token-key](https://help.sap.com/docs/BTP/btp-cli/btp-list-security-token-key.html)

</td>
</tr>
</table>

**Related Information**  


[Working with Global Accounts, Directories, and Subaccounts Using the btp CLI](working-with-global-accounts-directories-and-subaccounts-using-the-btp-cli-85a683e.md "Use the SAP BTP command line interface (btp CLI) to manage operations with global accounts, directories, and subaccounts.")

[Setting Entitlements Using the btp CLI](setting-entitlements-using-the-btp-cli-5af849c.md "Use the SAP BTP command line interface (btp CLI) to set entitlements to define the functionality or permissions available for users of global accounts, directories, and subaccounts.")

[Working with Environments Using the btp CLI](working-with-environments-using-the-btp-cli-48db155.md "Use the SAP BTP command line interface (btp CLI) to manage runtime environment instances in a subaccount. For example, enable the Cloud Foundry environment by creating a Cloud Foundry org (environment instance).")

[Working with Multitenant Applications Using the btp CLI](working-with-multitenant-applications-using-the-btp-cli-c1b0fcc.md "Use the SAP BTP command line interface (btp CLI) to manage the multitenant applications to which a subaccount is entitled to subscribe.")

[Working with External Resource Providers Using the btp CLI](working-with-external-resource-providers-using-the-btp-cli-48d7688.md "Use the SAP BTP command line interface (btp CLI) to get details, or to create or delete resource provider instances in a global account.")

[Managing Trust from SAP BTP to an SAP Cloud Identity Services Tenant](managing-trust-from-sap-btp-to-an-sap-cloud-identity-services-tenant-6140107.md "SAP BTP supports identity federation. Its concept is to reuse the user bases of identity providers. To use a custom identity provider, your global account or subaccount in SAP BTP must have a trust relationship to the identity provider you want to use.")

[Managing Users and Their Authorizations Using the btp CLI](managing-users-and-their-authorizations-using-the-btp-cli-94bb593.md "User authorizations are managed by assigning role collections to users (for example, Subaccount Administrator). Use the SAP BTP command-line interface (btp CLI) to manage roles and role collections, and to assign role collections to users.")

[Managing Security Settings](managing-security-settings-168dd75.md "Use the SAP BTP command line interface (btp CLI) to display and update the security settings for the subaccount.")

[Managing API Credentials for Calling REST APIs of SAP Authorization and Trust Management Service](managing-api-credentials-for-calling-rest-apis-of-sap-authorization-and-trust-managemen-ce43eb5.md "Use the SAP BTP command line interface (btp CLI) to manage API credentials, which enable you to access the REST APIs of the SAP Authorization and Trust Management service.")

[Working with Resources of the SAP Service Manager Using the btp CLI](working-with-resources-of-the-sap-service-manager-using-the-btp-cli-fe6a53b.md "Use the SAP BTP command line interface to perform various operations related to your platforms, attached service brokers, service instances, and service bindings.")

