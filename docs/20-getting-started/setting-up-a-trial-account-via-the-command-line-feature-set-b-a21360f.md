<!-- loioa21360fa19714751a7c49c796d39ac3d -->

# Setting Up a Trial Account via the Command Line \[Feature Set B\]

If your trial account is running on the cloud management tools feature set B, you can use the command-line interfaces to set it up. For all tasks on global account and subaccount level, you use the ** SAP BTP command line interface** \(**btp CLI**\). Once you’ve created a Cloud Foundry environment instance \(a Cloud Foundry org\), you use the Cloud Foundry CLI \(cf CLI\). This procedure works without the SAP BTP cockpit \(except that you need the global account subdomain to log in, which you may have to look up in the cockpit\).



> ### Note:  
> The content in this section is only relevant for cloud management tools feature set B. For more information, see [Cloud Management Tools - Feature Set Overview](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/caf4e4e23aef4666ad8f125af393dfb2.html).



For all tasks on global account and subaccount level, you can use the **the btp CLI** instead of the SAP BTP cockpit. Once you’ve created a Cloud Foundry environment instance \(a Cloud Foundry org\), you use the Cloud Foundry CLI \(cf CLI\).



<a name="loioa21360fa19714751a7c49c796d39ac3d__section_kpf_h5n_jhb"/>

## Prerequisites

-   You have created a trial account on cloud management tools feature set B.

-   You have downloaded and extracted the following command-line tools:

    -   SAP BTP command line interface \(btp CLI\). See [Download and Start Using the btp CLI Client](../50-administration-and-ops/download-and-start-using-the-btp-cli-client-8a8f17f.md)

    -   Cloud Foundry CLI \(cf CLI\). See [Download and Install the Cloud Foundry Command Line Interface](../50-administration-and-ops/download-and-install-the-cloud-foundry-command-line-interface-4ef907a.md) 





<a name="loioa21360fa19714751a7c49c796d39ac3d__section_s1w_h5n_jhb"/>

## Procedure

> ### Tip:  
> In the btp CLI, you can view the command help of each command to get information about how to use the command, its syntax, and input parameters. See [Get Help](../50-administration-and-ops/get-help-f8fd1e5.md).


<table>
<tr>
<th valign="top">

Step No.



</th>
<th valign="top">

Task



</th>
<th valign="top">

Performed By



</th>
<th valign="top">

Do This



</th>
<th valign="top">

More Information



</th>
</tr>
<tr>
<td valign="top">

1.



</td>
<td valign="top">

Log in to your global account using the subdomain of your global account.



</td>
<td valign="top">

Global account administrator or viewer



</td>
<td valign="top">

Run this command in the btp CLI:

`btp login`



</td>
<td valign="top">

See [Log in](../50-administration-and-ops/log-in-e241b30.md).



</td>
</tr>
<tr>
<td valign="top">

2.



</td>
<td valign="top">

View details of your global account.



</td>
<td valign="top">

Global account admin or viewer



</td>
<td valign="top">

Run this command in the btp CLI:

`btp get accounts/global-account`



</td>
<td valign="top">

See [Working with Global Accounts, Directories, and Subaccounts Using the btp CLI](../50-administration-and-ops/working-with-global-accounts-directories-and-subaccounts-using-the-btp-cli-85a683e.md).



</td>
</tr>
<tr>
<td valign="top">

4.



</td>
<td valign="top">

View all the regions that are available to your global account and subaccounts.



</td>
<td valign="top">

Global account admin or viewer



</td>
<td valign="top">

Run this command in the btp CLI:

`btp list accounts/available-region`



</td>
<td valign="top">

This command also provides information about the environments and infrastructure provider of each region.



</td>
</tr>
<tr>
<td valign="top">

5.



</td>
<td valign="top">

Create subaccounts in your global account.



</td>
<td valign="top">

Global account admin



</td>
<td valign="top">

Run this command in the btp CLI:

<code>btp create accounts/subaccount --display-name <i class="varname">&lt;my-subaccount&gt;</i> --region <i class="varname">&lt;my-region&gt;</i> --subdomain <i class="varname">&lt;my-subaccount-subdomain&gt;</i> </code>



</td>
<td valign="top">

See [Working with Global Accounts, Directories, and Subaccounts Using the btp CLI](../50-administration-and-ops/working-with-global-accounts-directories-and-subaccounts-using-the-btp-cli-85a683e.md) and [Relationship Between Global Accounts and Subaccounts \[Feature Set A\]](../10-concepts/account-model-8ed4a70.md#loioeeda449cf252418a97e0f7c9abd30b9a).



</td>
</tr>
<tr>
<td valign="top">

6.



</td>
<td valign="top">

View the details of the subaccounts in your global account.



</td>
<td valign="top">

Global account admin or viewer



</td>
<td valign="top">

Run this command in the btp CLI:

<code>btp get accounts/subaccount <i class="varname">&lt;ID of new subaccount&gt;</i></code>



</td>
<td valign="top">

See [Working with Global Accounts, Directories, and Subaccounts Using the btp CLI](../50-administration-and-ops/working-with-global-accounts-directories-and-subaccounts-using-the-btp-cli-85a683e.md).



</td>
</tr>
<tr>
<td valign="top">

7.



</td>
<td valign="top">

Add admins to your subaccounts.



</td>
<td valign="top">

Subaccount admin



</td>
<td valign="top">

Assign the role collection `Subaccount Administrator` to the user by running the following command in the btp CLI:

<code>btp assign security/role-collection "Subaccount Administrator" --to-user <i class="varname">&lt;user&gt;</i> --create-user-if-missing</code>



</td>
<td valign="top">

See [Managing Users and Their Authorizations Using the btp CLI](../50-administration-and-ops/managing-users-and-their-authorizations-using-the-btp-cli-94bb593.md) and [Security Administration: Managing Authentication and Authorization](../50-administration-and-ops/security-administration-managing-authentication-and-authorization-1ff47b2.md).



</td>
</tr>
<tr>
<td valign="top">

8.



</td>
<td valign="top">

View all the services and applications that are entitled to your global account, including quota information per service plan.



</td>
<td valign="top">

Global account admin or viewer



</td>
<td valign="top">

Run this command in the btp CLI:

`btp list accounts/entitlement`



</td>
<td valign="top">

See [Setting Entitlements Using the btp CLI](../50-administration-and-ops/setting-entitlements-using-the-btp-cli-5af849c.md).



</td>
</tr>
<tr>
<td valign="top">

9.



</td>
<td valign="top">

Assign quotas to your subaccounts.



</td>
<td valign="top">

Global account admin



</td>
<td valign="top">

Run this command in the btp CLI:

<code>btp assign accounts/entitlement --to-subaccount <i class="varname">&lt;my-subaccount-id&gt;</i> --for-service <i class="varname">&lt;my-service&gt;</i> --plan <i class="varname">&lt;my-service-plan&gt;</i> --amount <i class="varname">&lt;number&gt;</i></code>

Validate with this command:

`btp list accounts/entitlement`



</td>
<td valign="top">

See [Setting Entitlements Using the btp CLI](../50-administration-and-ops/setting-entitlements-using-the-btp-cli-5af849c.md).



</td>
</tr>
<tr>
<td valign="top">

10.



</td>
<td valign="top">

View all the entitlements in your subaccounts.



</td>
<td valign="top">

Subaccount admin or viewer



</td>
<td valign="top">

Run this command in the btp CLI:

<code>btp list accounts/entitlement --subaccount <i class="varname">&lt;my-subaccount-id&gt;</i></code>



</td>
<td valign="top">

See [Setting Entitlements Using the btp CLI](../50-administration-and-ops/setting-entitlements-using-the-btp-cli-5af849c.md).



</td>
</tr>
<tr>
<td valign="top">

11.



</td>
<td valign="top">

Create a Cloud Foundry org \(environment instance\) in your subaccounts.



</td>
<td valign="top">

Subaccount admin



</td>
<td valign="top">

Run this command in the btp CLI:

<code>btp create accounts/environment-instance --subaccount <i class="varname">&lt;my-subaccount-id&gt;</i> --display-name <i class="varname">&lt;my-environment&gt;</i> --environment <i class="varname">&lt;cloudfoundry&gt;</i></code>



</td>
<td valign="top">

See [Working with Environments Using the btp CLI](../50-administration-and-ops/working-with-environments-using-the-btp-cli-48db155.md).



</td>
</tr>
<tr>
<td valign="top">

12.



</td>
<td valign="top">

View details of the environment instances in your subaccounts.



</td>
<td valign="top">

Subaccount admin or viewer



</td>
<td valign="top">

Run this command in the btp CLI:

<code>btp list accounts/environment-instance --subaccount <i class="varname">&lt;my-subaccount-id&gt;</i></code>



</td>
<td valign="top">

See [Working with Environments Using the btp CLI](../50-administration-and-ops/working-with-environments-using-the-btp-cli-48db155.md).



</td>
</tr>
<tr>
<td valign="top">

13.



</td>
<td valign="top">

Create a Cloud Foundry space.



</td>
<td valign="top">

Org manager



</td>
<td valign="top">

Run these cf CLI commands:

`cf login`

`cf create-space`



</td>
<td valign="top">

See [Create Spaces Using the Cloud Foundry Command Line Interface](../50-administration-and-ops/create-spaces-using-the-cloud-foundry-command-line-interface-a2e5e29.md).



</td>
</tr>
<tr>
<td valign="top">

14.



</td>
<td valign="top">

Add Cloud Foundry org and space members.



</td>
<td valign="top">

Org manager



</td>
<td valign="top">

Run these cf CLI commands:

<code>cf set-org-role <i class="varname">&lt;USERNAME&gt;</i> <i class="varname">&lt;ORG&gt;</i> <i class="varname">&lt;ROLE&gt;</i></code>

<code>cf set-space-role <i class="varname">&lt;USERNAME&gt;</i><i class="varname">&lt;ORG&gt;</i><i class="varname">&lt;SPACE&gt;</i><i class="varname">&lt;ROLE&gt;</i></code>



</td>
<td valign="top">

See [Add Organization Members Using the Cloud Foundry Command Line Interface](../50-administration-and-ops/add-organization-members-using-the-cloud-foundry-command-line-interface-1422a5d.md) and [Add Space Members Using the Cloud Foundry Command Line Interface](../50-administration-and-ops/add-space-members-using-the-cloud-foundry-command-line-interface-d23ea8b.md).



</td>
</tr>
<tr>
<td valign="top">

15.



</td>
<td valign="top">

Display all available services in the Cloud Foundry marketplace.



</td>
<td valign="top">

Org manager



</td>
<td valign="top">

Run this cf CLI command:

```
cf marketplace
```



</td>
<td valign="top">

See [Using Services in the Cloud Foundry Environment](../30-development/using-services-in-the-cloud-foundry-environment-f22029f.md).



</td>
</tr>
</table>

Using the btp CLI, you can perform additional account maintenance tasks, such as updating global account and subaccount details, deleting subaccounts, and deleting environment instances.

Subaccount members can also use the btp CLI to work with multitenant applications. See [Working with Multitenant Applications Using the btp CLI](../50-administration-and-ops/working-with-multitenant-applications-using-the-btp-cli-c1b0fcc.md).



<a name="loioa21360fa19714751a7c49c796d39ac3d__section_vqn_j5n_jhb"/>

## Next Steps

Org/space members can create service instances, which are entitled to the subaccount, using also the <code>cf create-service <i class="varname">&lt;allowed-service-plan&gt;</i></code> command in the cf CLI. Use the cf CLI command cf services to verify that the service instances exist.

For further documentation about developer tasks, see [Development in the Cloud Foundry Environment](../30-development/development-in-the-cloud-foundry-environment-40a8f8f.md).

**Related Information**  


[Command Syntax of the btp CLI](../50-administration-and-ops/command-syntax-of-the-btp-cli-69606f4.md "Each command consists of the base call btp followed by a verb (the action), a combination of group and object, and parameters.")

[Download and Start Using the btp CLI Client](../50-administration-and-ops/download-and-start-using-the-btp-cli-client-8a8f17f.md "To use the SAP BTP command line interface (btp CLI), you need to download the client first.")

[Commands in the btp CLI](../50-administration-and-ops/commands-in-the-btp-cli-a03a555.md "A list of all tasks and respective commands that are available in the SAP BTP command line interface (btp CLI).")

[Cloud Management Tools — Feature Set Overview](../10-concepts/cloud-management-tools-feature-set-overview-caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

