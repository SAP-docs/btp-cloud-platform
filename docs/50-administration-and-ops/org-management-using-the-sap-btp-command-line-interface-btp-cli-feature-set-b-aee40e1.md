<!-- loioaee40e1afa56445a9bd57c2621d6eaaa -->

# Org Management Using the SAP BTP Command Line Interface \(btp CLI\) \[Feature Set B\]

The Cloud Foundry environment allows you to create polyglot cloud applications in Cloud Foundry. To manage the lifecycle of an org in the Cloud Foundry environment, use the `accounts/environment-instance` command in the btp CLI.



> ### Note:  
> The content in this section is only relevant for cloud management tools feature set B. For more information, see [Cloud Management Tools - Feature Set Overview](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/caf4e4e23aef4666ad8f125af393dfb2.html).



<a name="loioaee40e1afa56445a9bd57c2621d6eaaa__section_zpm_lvh_5pb"/>

## Available Plans

To create a Cloud Foundry org in a subaccount, you use the Cloud Foundry Runtime service. The Cloud Foundry Runtime service offers the following plans for this purpose:


<table>
<tr>
<th valign="top">

Plan Name



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

`standard` 



</td>
<td valign="top">

This is an enterprise-grade plan that allows you to create an org in your Cloud Foundry environment to start developing polyglot cloud-native applications.

By default, a Cloud Foundry org that is created with this plan does not have any application runtime. To assign application runtime, the global account admin must assign the Cloud Foundry Runtime service with the `MEMORY` plan to the subaccount so that the org has memory for its applications.



</td>
</tr>
<tr>
<td valign="top">

`free` 



</td>
<td valign="top">

Use this plan to try out the Cloud Foundry environment without an additional charge before switching to the `standard` plan that supports enterprise-grade productivity.

By default, a Cloud Foundry org that is created with this plan is given a fixed application-runtime quota. There is no need to assign the Cloud Foundry Runtime service with the `MEMORY` plan to the subaccount as it will have no effect on the org quota.

For more information about the free tier model for SAP BTP and its availability, see [Using Free Service Plans](../10-concepts/using-free-service-plans-524e108.md).



</td>
</tr>
</table>

For more information, about the features that each plan offers, see [Cloud Foundry Runtime](https://discovery-center.cloud.sap/serviceCatalog/cloud-foundry-runtime) on SAP Discovery Center.



<a name="loioaee40e1afa56445a9bd57c2621d6eaaa__section_qjr_z31_5pb"/>

## Command Reference for CRUD Operations

The btp CLI offers the following environment instance command actions to manage Cloud Foundry orgs in SAP BTP:

****


<table>
<tr>
<th valign="top">

Action



</th>
<th valign="top">

Command



</th>
<th valign="top">

Description



</th>
<th valign="top">

Parameters



</th>
<th valign="top">

Additional Info



</th>
</tr>
<tr>
<td valign="top">

`list` 



</td>
<td valign="top">

<code>btp list accounts/environment-instance --subaccount <i class="varname">&lt;SUBACCOUNT_ID&gt;</i></code> 



</td>
<td valign="top">

List all the Cloud Foundry orgs and other environment instances in a subaccount.



</td>
<td valign="top">

`SUBACCOUNT_ID`: The ID of the subaccount.



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

`get` 



</td>
<td valign="top">

<code>btp get accounts/environment-instance <i class="varname">&lt;ID&gt;</i> --subaccount <i class="varname">&lt;SUBACCOUNT_ID&gt;</i></code> 



</td>
<td valign="top">

Get the details of a specific Cloud Foundry org in a subaccount.



</td>
<td valign="top">

`ID`: The ID of the environment instance to view.

`SUBACCOUNT_ID`: The ID of the subaccount.



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

`create` 



</td>
<td valign="top">

<code>btp create accounts/environment-instance --subaccount <i class="varname">&lt;SUBACCOUNT_ID&gt;</i> --display-name <i class="varname">&lt;DISPLAY_NAME&gt;</i> --service <i class="varname">&lt;SERVICE&gt;</i> --plan <i class="varname">&lt;PLAN&gt;</i> --environment cloudfoundry --parameters "{\"instance_name\":\"<i class="varname">&lt;ORG_NAME&gt;</i>\"}"</code> 



</td>
<td valign="top">

Create a Cloud Foundry org in a subaccount.



</td>
<td valign="top">

`SUBACCOUNT_ID`: The ID of the subaccount in which to create the Cloud Foundry org.

`DISPLAY_NAME`: The SAP BTP name of the environment instance.

`PLAN`: Specify either `standard` or `free` as the value.

`ORG_NAME`: The name of the org in the Cloud Foundry environment. Spaces are not allowed in the org name. Once the org is created, you cannot change its name.



</td>
<td valign="top">

For examples that show how to pass JSON parameters in the command line with different operating systems and shells, see the [Passing JSON Parameters on the Command Line](passing-json-parameters-on-the-command-line-899fe34.md).



</td>
</tr>
<tr>
<td valign="top">

`update` 



</td>
<td valign="top">

<code>btp update accounts/environment-instance <i class="varname">&lt;ID&gt;</i> --subaccount <i class="varname">&lt;SUBACCOUNT_ID&gt;</i> --plan <i class="varname">&lt;PLAN&gt;</i></code> 



</td>
<td valign="top">

Update an existing Cloud Foundry org in a subaccount.



</td>
<td valign="top">

`ID`: The ID of the environment instance to update

`SUBACCOUNT_ID`: The ID of the subaccount.

`PLAN`: Specify either `standard` or `free` as the value.



</td>
<td valign="top">

For the Cloud Foundry environment, you can use this command to change only the plan of an existing Cloud Foundry environment instance. In other words, update an org created with the `free` plan of the Cloud Foundry Runtime to the `standard` plan \(not vice versa\).

> ### Note:  
> Before updating the plan to `standard`, make sure that the `MEMORY` plan for the Cloud Foundry Runtime entitlement is assigned to your subaccount, and that you've assigned sufficient application runtime quota to cover the current workload in the subaccount.



</td>
</tr>
<tr>
<td valign="top">

`delete` 



</td>
<td valign="top">

<code>btp delete accounts/ environment-instance <i class="varname">&lt;ID&gt;</i> --subaccount <i class="varname">&lt;SUBACCOUNT_ID&gt;</i></code> 



</td>
<td valign="top">

Delete a Cloud Foundry org created in a subaccount.



</td>
<td valign="top">

`ID`: The ID of the environment instance to delete.

`SUBACCOUNT_ID`: The ID of the subaccount where the environment instance exists.



</td>
<td valign="top">

The Cloud Foundry org and all its data will be lost.



</td>
</tr>
</table>

> ### Note:  
> You can obtain the subaccount ID by running `btp list accounts/subaccount`. You can also target the subaccount using <code>btp target --subaccount <i class="varname">&lt;ID&gt;</i></code>, and then omit the `subaccount` parameter from the rest of the commands.



<a name="loioaee40e1afa56445a9bd57c2621d6eaaa__section_k2c_hj1_fyb"/>

## Adding and Removing of Org Members

You can also use the btp CLI to add or remove org members.

****


<table>
<tr>
<th valign="top">

Action



</th>
<th valign="top">

Command



</th>
<th valign="top">

Description



</th>
<th valign="top">

Parameters



</th>
<th valign="top">

Additional Info



</th>
</tr>
<tr>
<td valign="top">

`update` 



</td>
<td valign="top">

<code>btp update accounts/environment-instance <i class="varname">&lt;ID&gt;</i> --subaccount <i class="varname">&lt;SUBACCOUNT_ID&gt;</i> --plan <i class="varname">&lt;PLAN&gt;</i> --parameters "{\"usersToAdd\":[{\"id\":\"myUserID\",\"email\":\name@example.com\}]}"</code> 



</td>
<td valign="top">

Add one or more users to a Cloud Foundry org in a subaccount.



</td>
<td valign="top">

`ID`: The ID of the environment instance for which to add org members.

`SUBACCOUNT_ID`: The ID of the subaccount.

`PLAN`: Specify either `standard` or `free` as the value.



</td>
<td valign="top">

For examples that show how to pass JSON parameters in the command line with different operating systems and shells, see the [Passing JSON Parameters on the Command Line](passing-json-parameters-on-the-command-line-899fe34.md).



</td>
</tr>
<tr>
<td valign="top">

`update` 



</td>
<td valign="top">

<code>btp update accounts/environment-instance <i class="varname">&lt;ID&gt;</i> --subaccount <i class="varname">&lt;SUBACCOUNT_ID&gt;</i> --plan <i class="varname">&lt;PLAN&gt;</i> --parameters "{\"usersToRemove\":[{\"id\":\"myUserID\",\"email\":\name@example.com\}]}"</code> 



</td>
<td valign="top">

Remove one or more users from a Cloud Foundry org in a subaccount.



</td>
<td valign="top">

`ID`: The ID of the environment instance for which to remove org members.

`SUBACCOUNT_ID`: The ID of the subaccount.

`PLAN`: Specify either `standard` or `free` as the value.



</td>
<td valign="top">

 



</td>
</tr>
</table>

**Related Information**  


[Account Administration Using the SAP BTP Command Line Interface \(btp CLI\)](account-administration-using-the-sap-btp-command-line-interface-btp-cli-7c6df2d.md "Use the SAP BTP command line interface (btp CLI) for all account administration tasks, such as creating or updating subaccounts, authorization management, and working with service brokers and platforms. It is an alternative to the SAP BTP cockpit for users who like to work in a terminal or want to automate operations using scripts.")

[About Roles in the Cloud Foundry Environment](about-roles-in-the-cloud-foundry-environment-0907638.md "Roles determine which features users can view and access, and which actions they can initiate.")

[Org Administration Using the Cockpit](org-administration-using-the-cockpit-c4c25cc.md "In the Cloud Foundry enviroment, manage orgs, spaces and space quota plans using the SAP BTP cockpit.")

[Add Org Members Using the Cockpit](add-org-members-using-the-cockpit-a4eeaf1.md "Add users as org members and assign roles to grant the users access to information, such as user and quota information in a Cloud Foundry org.")

[Managing Spaces](managing-spaces-5209d55.md "Learn how to create and delete Cloud Foundry spaces, as well as how to add members to a space.")

