<!-- loioaccd5b2389b04f4daf8a79b606435927 -->

# Setting Up a Global Account via the Command Line \[Feature Set B\]

Your global account is the entry point for managing the resources, landscape, and entitlements for your departments and projects in a self-service manner in SAP BTP. You can use the command-line tool **btp CLI** to set it up.



> ### Note:  
> The content in this section is only relevant for cloud management tools feature set B. For more information, see [Cloud Management Tools - Feature Set Overview](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/caf4e4e23aef4666ad8f125af393dfb2.html).



Set up your account model by creating subaccounts in your enterprise account that is running on the cloud management tools feature set B. You can create any number of subaccounts in the Cloud Foundry environment and region.



<a name="loioaccd5b2389b04f4daf8a79b606435927__section_kpf_h5n_jhb"/>

## Prerequisites

-   You have purchased an enterprise global account.

-   You have downloaded and extracted the following command-line tools:

    -   SAP BTP command line interface \(btp CLI\). See [Download and Start Using the btp CLI Client](../50-administration-and-ops/Download_and_Start_Using_the_btp_CLI_Client_8a8f17f.md)

    -   Cloud Foundry CLI \(cf CLI\). See [Download and Install the Cloud Foundry Command Line Interface](../50-administration-and-ops/Download_and_Install_the_Cloud_Foundry_Command_Line_Interface_4ef907a.md) 





<a name="loioaccd5b2389b04f4daf8a79b606435927__section_s1w_h5n_jhb"/>

## Procedure

> ### Tip:  
> In the btp CLI, you can view the command help of each command to get information about how to use the command, its syntax, and input parameters. See [Get Help](../50-administration-and-ops/Get_Help_f8fd1e5.md).


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

Log in to your global account using the URL of the btp CLI server and the subdomain of your global account.



</td>
<td valign="top">

Global account administrator or viewer



</td>
<td valign="top">

Run this command in the btp CLI:

`btp login`



</td>
<td valign="top">

See [Log in](../50-administration-and-ops/Log_in_e241b30.md).



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

See [Working with Global Accounts, Directories, and Subaccounts Using the btp CLI](../50-administration-and-ops/Working_with_Global_Accounts,_Directories,_and_Subaccounts_Using_the_btp_CLI_85a683e.md).



</td>
</tr>
<tr>
<td valign="top">

3.



</td>
<td valign="top">

Add admins to your global account.



</td>
<td valign="top">

Global account admin



</td>
<td valign="top">

Assign the role collection `Global Account Administrator` to a user by running the following command in the btp CLI:

`btp assign security/role-collection "Global Account Administrator" --to-user *<user\>* --create-user-if-missing`



</td>
<td valign="top">

See [Managing Users and Their Authorizations Using the btp CLI](../50-administration-and-ops/Managing_Users_and_Their_Authorizations_Using_the_btp_CLI_94bb593.md) and [Security Administration: Managing Authentication and Authorization](../50-administration-and-ops/Security_Administration_Managing_Authentication_and_Authorization_1ff47b2.md).



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

`btp create accounts/subaccount --display-name *<my-subaccount\>* --region *<my-region\>* --subdomain *<my-subaccount-subdomain\>* `



</td>
<td valign="top">

See [Working with Global Accounts, Directories, and Subaccounts Using the btp CLI](../50-administration-and-ops/Working_with_Global_Accounts,_Directories,_and_Subaccounts_Using_the_btp_CLI_85a683e.md) and [Relationship Between Global Accounts and Subaccounts \[Feature Set A\]](../10-concepts/Account_Model_8ed4a70.md#loioeeda449cf252418a97e0f7c9abd30b9a).



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

`btp get accounts/subaccount *<ID of new subaccount\>*`



</td>
<td valign="top">

See [Working with Global Accounts, Directories, and Subaccounts Using the btp CLI](../50-administration-and-ops/Working_with_Global_Accounts,_Directories,_and_Subaccounts_Using_the_btp_CLI_85a683e.md).



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

`btp assign security/role-collection "Subaccount Administrator" --to-user *<user\>* --create-user-if-missing`



</td>
<td valign="top">

See [Managing Users and Their Authorizations Using the btp CLI](../50-administration-and-ops/Managing_Users_and_Their_Authorizations_Using_the_btp_CLI_94bb593.md) and [Security Administration: Managing Authentication and Authorization](../50-administration-and-ops/Security_Administration_Managing_Authentication_and_Authorization_1ff47b2.md).



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

See [Setting Entitlements Using the btp CLI](../50-administration-and-ops/Setting_Entitlements_Using_the_btp_CLI_5af849c.md).



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

`btp assign accounts/entitlement --to-subaccount *<my-subaccount-id\>* --for-service *<my-service\>* --plan *<my-service-plan\>* --amount *<number\>*`

Validate with this command:

`btp list accounts/entitlement`



</td>
<td valign="top">

See [Setting Entitlements Using the btp CLI](../50-administration-and-ops/Setting_Entitlements_Using_the_btp_CLI_5af849c.md).



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

`btp list accounts/entitlement --subaccount *<my-subaccount-id\>*`



</td>
<td valign="top">

See [Setting Entitlements Using the btp CLI](../50-administration-and-ops/Setting_Entitlements_Using_the_btp_CLI_5af849c.md).



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

`btp create accounts/environment-instance --subaccount *<my-subaccount-id\>* --display-name *<my-environment\>* --environment *<cloudfoundry\>*`



</td>
<td valign="top">

See [Working with Environments Using the btp CLI](../50-administration-and-ops/Working_with_Environments_Using_the_btp_CLI_48db155.md).



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

`btp list accounts/environment-instance --subaccount *<my-subaccount-id\>*`



</td>
<td valign="top">

See [Working with Environments Using the btp CLI](../50-administration-and-ops/Working_with_Environments_Using_the_btp_CLI_48db155.md).



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

See [Create Spaces Using the Cloud Foundry Command Line Interface](../50-administration-and-ops/Create_Spaces_Using_the_Cloud_Foundry_Command_Line_Interface_a2e5e29.md).



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

`cf set-org-role *<USERNAME\>* *<ORG\>* *<ROLE\>*`

`cf set-space-role *<USERNAME\>**<ORG\>**<SPACE\>**<ROLE\>*`



</td>
<td valign="top">

See [Add Organization Members Using the Cloud Foundry Command Line Interface](../50-administration-and-ops/Add_Organization_Members_Using_the_Cloud_Foundry_Command_Line_Interface_1422a5d.md) and [Add Space Members Using the Cloud Foundry Command Line Interface](../50-administration-and-ops/Add_Space_Members_Using_the_Cloud_Foundry_Command_Line_Interface_d23ea8b.md).



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
`cf marketplace`
```



</td>
<td valign="top">

See [Using Services in the Cloud Foundry Environment](../30-development/Using_Services_in_the_Cloud_Foundry_Environment_f22029f.md).



</td>
</tr>
</table>

Using the btp CLI, you can perform additional account maintenance tasks, such as updating global account and subaccount details, deleting subaccounts, and deleting environment instances.

Subaccount members can also use the btp CLI to work with multitenant applications. See [Working with Multitenant Applications Using the btp CLI](../50-administration-and-ops/Working_with_Multitenant_Applications_Using_the_btp_CLI_c1b0fcc.md).



<a name="loioaccd5b2389b04f4daf8a79b606435927__section_vqn_j5n_jhb"/>

## Next Steps

Org/space members can create service instances, which are entitled to the subaccount, using also the `cf create-service *<allowed-service-plan\>*` command in the cf CLI. Use the cf CLI command cf services to verify that the service instances exist.

For further documentation about developer tasks, see [Development in the Cloud Foundry Environment](../30-development/Development_in_the_Cloud_Foundry_Environment_40a8f8f.md).

**Related Information**  


[Command Syntax of the btp CLI](../50-administration-and-ops/Command_Syntax_of_the_btp_CLI_69606f4.md "Each command consists of the base call btp followed by a verb (the action), a combination of group and object, and parameters.")

[Download and Start Using the btp CLI Client](../50-administration-and-ops/Download_and_Start_Using_the_btp_CLI_Client_8a8f17f.md "To use the SAP BTP command line interface (btp CLI), you need to download the client first.")

[Commands in the btp CLI](../50-administration-and-ops/Commands_in_the_btp_CLI_a03a555.md "A list of all tasks and respective commands that are available in the SAP BTP command line interface (btp CLI).")

[Cloud Management Tools — Feature Set Overview](../10-concepts/Cloud_Management_Tools_—_Feature_Set_Overview_caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

