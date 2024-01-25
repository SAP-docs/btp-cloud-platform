<!-- loioce43eb5dd4884997b54cddabc45c9313 -->

# Managing API Credentials for Calling REST APIs of SAP Authorization and Trust Management Service

Use the SAP BTP command line interface \(btp CLI\) to manage API credentials, which enable you to access the REST APIs of the SAP Authorization and Trust Management service.

If you want to access the REST APIs of SAP Authorization and Trust Management service in multi-environment subaccounts, global accounts, or directories, you must provide the required API credentials. One main use case is for customers who want to provision users including their authorizations, for example into a global account or a directory. They need credentials \(with a client ID\) for provisioning of users, especially when using SAP Cloud Identity Services - Identity Provisioning.

The API credentials are only passed on when they are created. They can't be retrieved later. If lost, new credentials must be generated.

See [Application Security Descriptor Configuration Syntax](../30-development/application-security-descriptor-configuration-syntax-517895a.md) for the credential types and [SAP Business Accelerator Hub](https://api.sap.com/package/authtrustmgmnt/rest) for the APIs of the SAP Authorization and Trust Management service.


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

Create API credentials

</td>
<td valign="top">

`btp create security/api-credential`

</td>
<td valign="top">

[https://help.sap.com/docs/BTP/btp-cli/btp-create-api-credential.html](https://help.sap.com/docs/BTP/btp-cli/btp-create-api-credential.html)

</td>
</tr>
<tr>
<td valign="top">

Show all API credentials

</td>
<td valign="top">

`btp list security/api-credential`

</td>
<td valign="top">

[https://help.sap.com/docs/BTP/btp-cli/btp-list-api-credential.html](https://help.sap.com/docs/BTP/btp-cli/btp-list-api-credential.html)

</td>
</tr>
<tr>
<td valign="top">

Show details about specific API credentials

</td>
<td valign="top">

`btp get security/api-credential`

</td>
<td valign="top">

[https://help.sap.com/docs/BTP/btp-cli/btp-get-api-credential.html](https://help.sap.com/docs/BTP/btp-cli/btp-get-api-credential.html)

</td>
</tr>
<tr>
<td valign="top">

Delete API credentials

</td>
<td valign="top">

`btp delete security/api-credential`

</td>
<td valign="top">

[https://help.sap.com/docs/BTP/btp-cli/btp-delete-api-credential.html](https://help.sap.com/docs/BTP/btp-cli/btp-delete-api-credential.html)

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

[Working with Resources of the SAP Service Manager Using the btp CLI](working-with-resources-of-the-sap-service-manager-using-the-btp-cli-fe6a53b.md "Use the SAP BTP command line interface to perform various operations related to your platforms, attached service brokers, service instances, and service bindings.")

