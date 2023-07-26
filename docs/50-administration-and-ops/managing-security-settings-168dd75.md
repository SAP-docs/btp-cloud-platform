<!-- loio168dd7528a784595b16388403cddd1a2 -->

# Managing Security Settings

Use the SAP BTP command line interface \(btp CLI\) to display and update the security settings for the subaccount.

The security settings comprise configuration settings, such as information about signing keys, URLs for cross origin resource sharing or iframing, and about bindings.

For more information, see [Configure Trusted Domains for SAP Authorization and Trust Management Service \[Feature Set B\]](configure-trusted-domains-for-sap-authorization-and-trust-management-service-feature-se-c5e9972.md) and [Configure Token Policy for SAP Authorization and Trust Management Service](configure-token-policy-for-sap-authorization-and-trust-management-service-40290a9.md).


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

Show the security settings of a subaccount



</td>
<td valign="top">

`btp list security/settings`



</td>
<td valign="top">

[https://help.sap.com/docs/BTP/btp-cli/btp-list-security-settings.html](https://help.sap.com/docs/BTP/btp-cli/btp-list-security-settings.html)



</td>
</tr>
<tr>
<td valign="top">

Update the security settings of a subaccount



</td>
<td valign="top">

`btp update security/settings`



</td>
<td valign="top">

[https://help.sap.com/docs/BTP/btp-cli/btp-update-security-settings.html](https://help.sap.com/docs/BTP/btp-cli/btp-update-security-settings.html)



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

[Working With Resources of the SAP Service Manager Using the btp CLI](working-with-resources-of-the-sap-service-manager-using-the-btp-cli-fe6a53b.md "Use the SAP BTP command line interface to perform various operations related to your platforms, attached service brokers, service instances, and service bindings.")

