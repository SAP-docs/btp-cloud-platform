<!-- loiocaf4e4e23aef4666ad8f125af393dfb2 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Cloud Management Tools — Feature Set Overview

Cloud management tools represent the group of technologies designed for managing SAP BTP.

We're currently renovating and adding core functionalities to SAP BTP. As part of this process, we're upgrading enterprise accounts from the existing cloud management tools feature set A to the renovated cloud management tools feature set B. We're doing this upgrade as a phased rollout, so cloud management tools feature sets A and B will coexist for some time. For more information about the account upgrade process and frequently-asked questions, see [3027721](https://launchpad.support.sap.com/#/notes/3027721).



<a name="loiocaf4e4e23aef4666ad8f125af393dfb2__section_cpt_pjv_nkb"/>

## How can I know which cloud management tools feature set I'm using?

There’s an easy way to check if you're currently using cloud management tools feature set A or B. Access the SAP BTP cockpit and choose your username from the top right-hand corner of the screen. From the menu, select <span class="SAP-icons"></span> *About* to get information about the cloud management tools feature set you're using.

![The screenshot is explained in the accompanying text.](images/About_7be640f.png)



<a name="loiocaf4e4e23aef4666ad8f125af393dfb2__section_wjh_hqj_14b"/>

## Access the SAP BTP cockpit

Feature sets A and B don't share the same cockpit. So in your feature set A cockpit, you'll only see feature set A global accounts, while in your feature set B cockpit, you'll only see your feature set B global accounts.

When using cloud management tools feature set A: Choose [https://account.eu1.hana.ondemand.com](https://account.eu1.hana.ondemand.com) to access the SAP BTP cockpit.

When using cloud management tools feature set B: Choose [https://cockpit.eu10.hana.ondemand.com/cockpit/](https://cockpit.eu10.hana.ondemand.com/cockpit/) to access the SAP BTP cockpit.



<a name="loiocaf4e4e23aef4666ad8f125af393dfb2__section_axn_hqv_nkb"/>

## What are the differences between the two cloud management tools feature sets?


<table>
<tr>
<th valign="top">

New/Changed Features and Behaviors



</th>
<th valign="top">

Feature Set A



</th>
<th valign="top">

Feature Set B



</th>
</tr>
<tr>
<td valign="top">

**Directories — NEW**



</td>
<td valign="top">

*Not applicable*



</td>
<td valign="top">

Summary:

-   Group and filter directories and subaccounts

-   Monitor usage and costs for contracts that use the consumption-based commercial model


**Directories** allow you to organize and manage your subaccounts according to your technical and business needs.

A directory can contain directories and subaccounts to create a hierarchy. Using directories to group other directories and subaccounts is optional - you can still create subaccounts directly under your global account.

See:

[Directories \[Feature Set B\]](Account_Model_8ed4a70.md#loioa92721fc75524ec09a7a7255997dbd94)

[Create a Directory \[Feature Set B\]](../50-administration-and-ops/Create_a_Directory_Feature_Set_B_b8ef1c4.md)

[Manage the Account Explorer Hierarchy \[Feature Set B\]](../50-administration-and-ops/Manage_the_Account_Explorer_Hierarchy_Feature_Set_B_2e2a5b6.md)



</td>
</tr>
<tr>
<td valign="top">

**Custom properties — NEW**



</td>
<td valign="top">

*Not applicable*



</td>
<td valign="top">

Summary:

-   Label or tag subaccounts and directories
-   Additional filtering options

Custom properties allow you to label or tag your directories and subaccounts according to your own business and technical needs. This makes organizing and filtering your directories and subaccounts easier within your global account.

You create and assign custom properties when you create or edit a directory or subaccount. Using custom properties is optional.

See [Custom Properties \[Feature Set B\]](Account_Model_8ed4a70.md#loioe8663c08ead648faa673b0d63c5b478e).



</td>
</tr>
<tr>
<td valign="top">

**APIs for SAP BTP — NEW**



</td>
<td valign="top">

*Not applicable*



</td>
<td valign="top">

Summary:

Discover and consume REST APIs to manage, build, and extend the cloud operation capabilities of SAP BTP. For example:

-   Manage global accounts, directories, and subaccounts

-   Assign entitlements for services and applications to directories and subaccounts

-   Manage the provisioning of environment instances and get information relating to provisioned services

-   Manage subaccount subscriptions to multitenant applications

-   Generate reports based on the resource and cost consumption within your accounts.


See [Account Administration Using APIs of the SAP Cloud Management Service \[Feature Set B\]](../50-administration-and-ops/Account_Administration_Using_APIs_of_the_SAP_Cloud_Management_Service_Feature_Set_B_17b6a17.md) and [Monitoring Usage Information Using APIs of the SAP Usage Data Management Service \[Feature Set B\]](../50-administration-and-ops/Monitoring_Usage_Information_Using_APIs_bf2b304.md).



</td>
</tr>
<tr>
<td valign="top">

**SAP BTP command line interface \(btp CLI\) — NEW**



</td>
<td valign="top">

*Not applicable*



</td>
<td valign="top">

Summary:

Use the btp CLI for convenient account management tasks on the command line and to automate these procedures. For example:

-   Manage global accounts, directories, and subaccounts

-   Set entitlements

-   Work with environments

-   Work with multitenant applications

-   Manage users and their authorizations


To log in to a global account, you need the CLI server URL `https://cpcli.cf.eu10.hana.ondemand.com` and the global account subdomain. Only global accounts on feature set B have global account subdomains \(see cockpit\).

See:

[Account Administration Using the SAP BTP Command Line Interface \(btp CLI\) \[Feature Set B\]](../50-administration-and-ops/Account_Administration_Using_the_SAP_BTP_Command_Line_Interface_(btp_CLI)_Feature_Set_B_7c6df2d.md)

[Commands in the btp CLI](../50-administration-and-ops/Commands_in_the_btp_CLI_a03a555.md)

[Setting Up a Global Account via the Command Line \[Feature Set B\]](../20-getting-started/Setting_Up_a_Global_Account_via_the_Command_Line_Feature_Set_B_accd5b2.md)



</td>
</tr>
<tr>
<td valign="top">

**Global account navigation — CHANGED**



</td>
<td valign="top">

Summary:

-   "Home" scope outside the global account in the cockpit
-   *Global Accounts* page in the cockpit
-   Switching between global accounts via breadcrumbs \(second element\)
-   *Overview* page is the first in the global account scope

With feature set A, your cockpit contains a number of general views **outside** of the global account scope. These include a *Global Accounts* page, where you can find all your global accounts listed as tiles, and from where you can navigate to your desired global account.

Since it has several views outside of the global account scope, your cockpit contains an additional "home" scope, which is represented by the first element in the breadcrumbs. Your global account is therefore represented by the second element in the breadcrumbs. You can also use that second element to navigate from one global account to another.

Once you're in a global account, the first page you see is the global account overview page. To navigate to a subaccount, you have to navigate to the *Subaccounts* page from the left hand-side navigation.

See [Navigate in the Cockpit](../50-administration-and-ops/Navigate_in_the_Cockpit_0874895.md)



</td>
<td valign="top">

Summary:

-   Global accounts selection dialog displayed before entering the cockpit
-   Option to set a default global account
-   "Home" scope removed from the cockpit
-   Switching between global accounts via the selection dialog or breadcrumbs \(first element\)
-   *Subaccounts* page is the first in the global account scope

With feature set B, there’s no scope beyond the global account in the cockpit anymore. Therefore, after logging on to the cockpit and before actually entering it, if you’ve more than one global account, you’re asked to choose which of the available cloud management tools feature set B global accounts you want to enter. Only feature set B global accounts are visible here. This is done via a global account selection dialog, where you also have the option to remember your selection. Doing that sets the global account you chose as default, so that next time you access the cockpit you’re automatically taken to your default global account instead of seeing the selection dialog.

As the cockpit doesn't have a "home" scope anymore, the global account becomes the outermost scope and is therefore represented by the first element in the breadcrumbs. You can still navigate from one global account to another either by using the breadcrumbs, or by choosing *Switch Global Accounts* to launch the global account selection dialog, where you can also modify or remove your default global account.

Once you're in a global account, the first page you see is the *Subaccounts* page, from where you can directly navigate to your subaccount — one less click needed. Usage and cost information for your global account is displayed in the global account's *Usage Analytics* page.

See [Navigate in the Cockpit](../50-administration-and-ops/Navigate_in_the_Cockpit_0874895.md).



</td>
</tr>
<tr>
<td valign="top">

**Entitlements — CHANGED**



</td>
<td valign="top">

Summary:

-   Only manage entitlements for services
-   Assign entitlements to subaccounts individually
-   *Service Assignments* view

With feature set A, entitlements only apply to services and you have 2 views for them: *Subaccount Assignments*, where you can assign or edit entitlements to individual subaccounts, and *Service Assignments*, which is a read-only view displaying the distribution of your available services across subaccounts.

See:

[Entitlements and Quotas](Entitlements_and_Quotas_00aa2c2.md)

[Managing Entitlements and Quotas Using the Cockpit](../50-administration-and-ops/Managing_Entitlements_and_Quotas_Using_the_Cockpit_c824874.md)

[Configure Entitlements and Quotas for Subaccounts](../50-administration-and-ops/Configure_Entitlements_and_Quotas_for_Subaccounts_5ba357b.md)



</td>
<td valign="top">

Summary:

-   Manage entitlements for both services and multitenant applications
-   Assign entitlements to subaccounts individually
-   Assign entitlements to directories
-   Auto-assign entitlements to all new subaccounts in a directory
-   One single view for your entitlements, no *Service Assignments* page

With feature set B, you manage entitlements for both services and multitenant applications. Since you have directories as a way to group your subaccounts, you can also assign entitlements to a directory and choose the option to automatically assign a certain amount of quota to each subaccount added to that directory in the future \(as long as it doesn't exceed the quota of that directory\).

This means that you can more efficiently assign quota to multiple subaccounts that should have the same entitlements.

In addition, you no longer have the *Service Assignments* view with feature set B.

See:

[Entitlements and Quotas](Entitlements_and_Quotas_00aa2c2.md)

[Managing Entitlements and Quotas Using the Cockpit](../50-administration-and-ops/Managing_Entitlements_and_Quotas_Using_the_Cockpit_c824874.md)

[Configure Entitlements and Quotas for Directories \[Feature Set B\]](../50-administration-and-ops/Configure_Entitlements_and_Quotas_for_Directories_Feature_Set_B_37f8871.md)

[Subscribe to Multitenant Applications Using the Cockpit](../50-administration-and-ops/Subscribe_to_Multitenant_Applications_Using_the_Cockpit_7a3e396.md)



</td>
</tr>
<tr>
<td valign="top">

**Global account security — CHANGED**



</td>
<td valign="top">

Summary:

-   Global account membership determines if a user is global account administrator or not.

-   Members of subaccounts have view-only access to their global accounts.


With feature set A, the *Members* tab determines which uses are global administrators. These users can assign or remove global administrator membership to other users.

See:

[User and Member Management](User_and_Member_Management_cc1c676.md)

 [Add Members to Your Global Account](../50-administration-and-ops/Add_Members_to_Your_Global_Account_4a04913.md)

[Impact of Upgrading from Feature Set A to Feature Set B on User and Account Management](Impact_of_Upgrading_from_Feature_Set_A_to_Feature_Set_B_on_User_and_Account_Management_1ac8143.md)



</td>
<td valign="top">

Summary:

-   Global account membership is determined by the assignment of a role collection.

-   Predefined role collections for global account define full and read-only access.

-   You can define your own role collections with the authorizations delivered by SAP


With feature set B, you have fine-granular authorization concept for the management of global accounts. We deliver a set of role collections for the management of global accounts. If these role collections don’t match your needs, you can configure your own role collections using the authorizations we supply. For example, you have control over which global account users can create subaccounts and which can’t.

The Authorization and Trust Management \(XSUAA\) service is responsible for access management for global accounts. This service is the same service that performs access management at the subaccount level, although it’s a different instance of the service.

In the cockpit, a new *Security* tab provides access to management functions for role collections and user assignment.

With feature set B, global account users from the SAP ID service are identified by their e-mail address and not their user ID.

See:

[User and Member Management](User_and_Member_Management_cc1c676.md)

[Role Collections and Roles in Global Accounts, Directories, and Subaccounts \[Feature Set B\]](Role_Collections_and_Roles_in_Global_Accounts,_Directories,_and_Subaccounts_Feature_Set_B_0039cf0.md)

[Default Role Collections of SAP BTP Cloud Foundry Environment \[Feature Set B\]](../60-security/Default_Role_Collections_of_SAP_BTP_Cloud_Foundry_Environment_Feature_Set_B_a6a0072.md)



</td>
</tr>
<tr>
<td valign="top">

**Subaccount security — CHANGED**



</td>
<td valign="top">

Summary:

-   Subaccount administrators are determined by assignment under security administrators.

-   Subaccount members are determined by assignment of roles in the Cloud Foundry org under the *Members* tab.


With feature set A, you define administrators in the cockpit under the *Security* tab with the *Administrators* menu item. Members of the subaccount are also members of the environments provided by the subaccount.

See:

[User and Member Management](User_and_Member_Management_cc1c676.md)

 [Managing Security Administrators in Your Subaccount \[Feature Set A\]](../50-administration-and-ops/Managing_Security_Administrators_in_Your_Subaccount_Feature_Set_A_6752c4b.md)

[Impact of Upgrading from Feature Set A to Feature Set B on User and Account Management](Impact_of_Upgrading_from_Feature_Set_A_to_Feature_Set_B_on_User_and_Account_Management_1ac8143.md)



</td>
<td valign="top">

Summary:

-   Subaccount administrators and members are determined by the assignment of role collections.

-   Predefined role collections for subaccounts define the level of access.

-   Provision subaccount members with SCIM APIs

-   Membership in subaccounts and any environments, such as the Cloud Foundry org, are controlled by separate authorizations.


With feature set B, you have a fine-granular authorization concept for the management of subaccounts. We deliver a set of role collections for the management of subaccounts. If these role collections don’t match your needs, you can configure your own role collections using the authorizations we supply.

Access to environments, such as a Cloud Foundry org, is semi-independent from subaccount membership. A subaccount member isn't necessarily a member of an environment, but a member of an environment is a member of its subaccount.

See:

[User and Member Management](User_and_Member_Management_cc1c676.md)

[Role Collections and Roles in Global Accounts, Directories, and Subaccounts \[Feature Set B\]](Role_Collections_and_Roles_in_Global_Accounts,_Directories,_and_Subaccounts_Feature_Set_B_0039cf0.md)

[Add Members to Your Subaccount \[Feature Set B\]](../50-administration-and-ops/Add_Members_to_Your_Subaccount_Feature_Set_B_1e1b7b6.md)

[Default Role Collections of SAP BTP Cloud Foundry Environment \[Feature Set B\]](../60-security/Default_Role_Collections_of_SAP_BTP_Cloud_Foundry_Environment_Feature_Set_B_a6a0072.md)



</td>
</tr>
<tr>
<td valign="top">

**Custom Identity Provider — CHANGED**



</td>
<td valign="top">

Summary:

Custom identity providers enable you to integrate platform and business users from SAP Cloud Identity Services - Identity Authentication or your own corporate identity provider.

See: [Trust and Federation with Identity Providers](../50-administration-and-ops/Trust_and_Federation_with_Identity_Providers_cb1bc8f.md)

[Impact of Upgrading from Feature Set A to Feature Set B on User and Account Management](Impact_of_Upgrading_from_Feature_Set_A_to_Feature_Set_B_on_User_and_Account_Management_1ac8143.md)



</td>
<td valign="top">

Summary:

Custom identity providers enable you to integrate business users from SAP Cloud Identity Services - Identity Authentication or your own corporate identity provider.

See: [Trust and Federation with Identity Providers](../50-administration-and-ops/Trust_and_Federation_with_Identity_Providers_cb1bc8f.md)



</td>
</tr>
<tr>
<td valign="top">

**\(Trial Only\) Automatic Setup of Trial Account — CHANGED**



</td>
<td valign="top">

*Not applicable*



</td>
<td valign="top">

Summary:

-   Your trial account is automatically set up for you after you choose *Enter Your Trial Account* from the trial homepage in the cockpit for the first time.
-   You get a global account with a subaccount called *trial*, which in turn contains an org and a space called *dev*.
-   All entitlements are assigned to the subaccount that is provisioned automatically.

With feature set B, you can access the trial homepage in the cockpit before your trial account is set up and ready to use. This means that you can launch a starter scenario or guided tour before you have the global account, subaccount, org, space and entitlements in place. You trigger the automatic creation when you first choose *Enter Your Trial Account* from the trial homepage.



</td>
</tr>
<tr>
<td valign="top">

**\(Trial Only\) Trial Account Extension - CHANGED**



</td>
<td valign="top">

*Not applicable*



</td>
<td valign="top">

Summary:

-   You cannot access an expired trial global account.
-   You can still see the counter with the remaining number of days in the same place, but you cannot extend your trial from there.
-   You extend your trial account from a dialog similar to the global account selection dialog described previously in this table under global account navigation.

With feature set B, it's not possible anymore to access expired trial global accounts. Before your trial expires you can still see the counter with the remaining number of days in the same place. However, once your trial expires and you try to access it, you will instead be prompted by a dialog asking you to extend your trial first.



</td>
</tr>
<tr>
<td valign="top">

**\(Trial Only\) Deletion of SAP BTP Trial - NEW**



</td>
<td valign="top">

*Not applicable*



</td>
<td valign="top">

Summary:

-   Possible to easily delete only your SAP BTP trial account.

With feature set B, you can delete your SAP BTP trial account. Simply navigate into your trial global account by choosing *Enter Your Trial Account* on the trial home page. Once you're on the *Subaccounts* page of your global account, you will see a new button giving you the option to delete your trial account.



</td>
</tr>
</table>

> ### Note:  
> Cloud management tools feature set B applies also to the Neo environment. For more information and details about the scope offered with the enhanced capabilities, see [Working with Cloud Management Tools Feature Set B in the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/8c963e83a42545e29d1b4277a287a01b.html "Enterprise accounts in SAP BTP that have access to cloud management tools feature set B, can also use the enhanced capabilities offered by feature set B with their subaccounts in the Neo environment.") :arrow_upper_right:.

