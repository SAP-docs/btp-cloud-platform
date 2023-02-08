<!-- loio6140107ac5da428a930cfefd73468628 -->

# Managing Trust from SAP BTP to an Identity Authentication Tenant

SAP BTP supports identity federation. Its concept is to reuse the user bases of identity providers. To use a custom identity provider, your global account or subaccount in SAP BTP must have a trust relationship to the identity provider you want to use.

> ### Note:  
> We recommend that you always use SAP Cloud Identity Services - Identity Authentication as a single identity provider for SAP BTP. If you use corporate identity providers, connect them to your Identity Authentication tenant, which then acts as a hub.



<a name="loio6140107ac5da428a930cfefd73468628__section_zmw_mz2_tvb"/>

## Prerequisites

-   You have a tenant of SAP Cloud Identity Services - Identity Authentication.

    For more information, see [Tenant Model and Licensing](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/93160ebd2dcb40e98aadcbb9a970f2b9.html?version=Cloud) in the documentation for Identity Authentication.

-   The Identity Authentication tenant must be associated with the same customer ID as the relevant global account of SAP BTP.

-   Make sure that the email addresses of all users in your identity provider are unique and correct.


> ### Note:  
> We recommend that you request your own Identity Authentication tenant \(see [Getting a Tenant](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/93160ebd2dcb40e98aadcbb9a970f2b9.html#getting-a-tenant)\).



<a name="loio6140107ac5da428a930cfefd73468628__section_l1j_mgj_rhb"/>

## Managing Trust Configurations

> ### Tip:  
> All of these commands can be executed in the global account or in a subaccount. To choose the level, use the `btp target` command. See [Set a Target for Subsequent Commands with btp target](set-a-target-for-subsequent-commands-with-btp-target-720645a.md).

To manage trust with your identity provider, use the following commands.

```
btp create security/trust --idp my-tenant --subaccount my-subaccount-id --name my-trust-configuration  --origin mytrust --description "My Trust Configuration"
```

See [Trust and Federation with Identity Providers](trust-and-federation-with-identity-providers-cb1bc8f.md).


<table>
<tr>
<th valign="top">

Task



</th>
<th valign="top">

Run the command...



</th>
<th valign="top">

Command help



</th>
</tr>
<tr>
<td valign="top">

List all trust configurations that are configured for your global account or subaccount



</td>
<td valign="top">

`btp list security/trust`



</td>
<td valign="top">

[btp list security/trust](https://help.sap.com/docs/BTP/btp-cli/btp-list-security-trust.html)



</td>
</tr>
<tr>
<td valign="top">

Get details about a trust configuration



</td>
<td valign="top">

`btp get security/trust` 



</td>
<td valign="top">

[btp get security/trust](https://help.sap.com/docs/BTP/btp-cli/btp-get-security-trust.html)



</td>
</tr>
<tr>
<td valign="top">

Establish trust from a global account or subaccount to an Identity Authentication tenant



</td>
<td valign="top">

`btp create security/trust`



</td>
<td valign="top">

[btp create security/trust](https://help.sap.com/docs/BTP/btp-cli/btp-create-security-trust.html)



</td>
</tr>
<tr>
<td valign="top">

Update a trust configuration of a global account or subaccount



</td>
<td valign="top">

`btp update security/trust`



</td>
<td valign="top">

[btp update security/trust](https://help.sap.com/docs/BTP/btp-cli/btp-update-security-trust.html)



</td>
</tr>
<tr>
<td valign="top">

Delete a trust configuration from a global account or subaccount



</td>
<td valign="top">

`btp delete security/trust`



</td>
<td valign="top">

[btp delete security/trust](https://help.sap.com/docs/BTP/btp-cli/btp-delete-security-trust.html)



</td>
</tr>
</table>



<a name="loio6140107ac5da428a930cfefd73468628__section_vmj_cjj_rhb"/>

## Finding Available Identity Authentication Tenants


<table>
<tr>
<th valign="top">

Task



</th>
<th valign="top">

Run the command...



</th>
<th valign="top">

Command help



</th>
</tr>
<tr>
<td valign="top">

List all Identity Authentication tenants to which you can connect this global account or subaccount



</td>
<td valign="top">

`btp list security/available-idp`



</td>
<td valign="top">

[btp list security/available-ipd](https://help.sap.com/docs/BTP/btp-cli/btp-list-security-available-idp.html)



</td>
</tr>
<tr>
<td valign="top">

Get details about an Identity Authentication tenant that is available for a global account or a subaccount



</td>
<td valign="top">

`btp get security/available-idp`

To see available tenants, run `btp list security/available-idp`

.



</td>
<td valign="top">

[btp get security/available-ipd](https://help.sap.com/docs/BTP/btp-cli/btp-get-security-available-idp.html)



</td>
</tr>
</table>

**Related Information**  


[Working with Global Accounts, Directories, and Subaccounts Using the btp CLI](working-with-global-accounts-directories-and-subaccounts-using-the-btp-cli-85a683e.md "Use the SAP BTP command line interface (btp CLI) to manage operations with global accounts, directories, and subaccounts.")

[Setting Entitlements Using the btp CLI](setting-entitlements-using-the-btp-cli-5af849c.md "Use the SAP BTP command line interface (btp CLI) to set entitlements to define the functionality or permissions available for users of global accounts, directories, and subaccounts.")

[Working with Environments Using the btp CLI](working-with-environments-using-the-btp-cli-48db155.md "Use the SAP BTP command line interface (btp CLI) to manage runtime environment instances in a subaccount. For example, enable the Cloud Foundry environment by creating a Cloud Foundry org (environment instance).")

[Working with Multitenant Applications Using the btp CLI](working-with-multitenant-applications-using-the-btp-cli-c1b0fcc.md "Use the SAP BTP command line interface (btp CLI) to manage the multitenant applications to which a subaccount is entitled to subscribe.")

[Working with External Resource Providers Using the btp CLI](working-with-external-resource-providers-using-the-btp-cli-48d7688.md "Use the SAP BTP command line interface (btp CLI) to get details, or to create or delete resource provider instances in a global account.")

[Managing Users and Their Authorizations Using the btp CLI](managing-users-and-their-authorizations-using-the-btp-cli-94bb593.md "User authorizations are managed by assigning role collections to users (for example, Subaccount Administrator). Use the SAP BTP command-line interface (btp CLI) to manage roles and role collections, and to assign role collections to users.")

[Working With Resources of the SAP Service Manager Using the btp CLI](working-with-resources-of-the-sap-service-manager-using-the-btp-cli-fe6a53b.md "Use the SAP BTP command line interface to perform various operations related to your platforms, attached service brokers, service instances, and service bindings.")

