<!-- loio09076385086b4da3bd1808d5ef572862 -->

# About Roles in the Cloud Foundry Environment

Roles determine which features users can view and access, and which actions they can initiate.

Cloud Foundry includes predefined roles that are specific to the navigation level in the SAP BTP cockpit; for example, the roles at the level of the organization differ from the ones for the space. Each role comes with a set of permissions. Roles apply to all operations that are associated with the organization or the space, irrespective of the tool used \(Eclipse-based tools, SAP BTP cockpit, and cf CLI\).

The following roles can be assigned to users in the Cloud Foundry environment on SAP BTP:


<table>
<tr>
<th valign="top">

Level



</th>
<th valign="top">

Role



</th>
<th valign="top">

Role Description



</th>
</tr>
<tr>
<td valign="top" rowspan="3">

Organization



</td>
<td valign="top">

Org Manager



</td>
<td valign="top">

Manages the organization.



</td>
</tr>
<tr>
<td valign="top">

Org Auditor



</td>
<td valign="top">

Provides read-only access to user information and org quota usage information.



</td>
</tr>
<tr>
<td valign="top">

Org User



</td>
<td valign="top">

Provides read-only access to the list of other organization users and their roles.

> ### Note:  
> When creating a space member, the Org User role is always one of the assigned organization roles. When creating an organization member, you can choose one or more of the following roles:
> 
> -   Org Manager
> 
> -   Org User
> 
> -   Org Auditor



</td>
</tr>
<tr>
<td valign="top" rowspan="4">

Space



</td>
<td valign="top">

Space Manager



</td>
<td valign="top">

Manages a space within an organization.



</td>
</tr>
<tr>
<td valign="top">

Space Developer



</td>
<td valign="top">

Manages applications, services, and space-scoped service brokers in a space.

> ### Caution:  
> The Space Developer role has broad rights within Cloud Foundry and, in particular, has access to the credentials used in various services and app bindings as well as other sensitive data. For more information, see [Giving Access Rights to Platform Users](https://help.sap.com/viewer/df50977d8bfa4c9a8a063ddb37113c43/Cloud/en-US/a03d08e4038b46d480c410395593bbd2.html "If you&apos;ve set up a staged development environment using different subaccounts or spaces, such as for development, testing, and production, we recommend that you grant the Cloud Development Team access to development subaccounts and spaces, but that you grant only the Platform Engineering Team access to the testing and production subaccounts or spaces.") :arrow_upper_right:.



</td>
</tr>
<tr>
<td valign="top">

Space Auditor



</td>
<td valign="top">

Provides read-only access to a space.



</td>
</tr>
<tr>
<td valign="top">

Space Supporter



</td>
<td valign="top">

Allows you to troubleshoot and debug applications and service bindings in a space.

> ### Note:  
> To add the Space Supporter role using the `set-space-role` command, you need to have installed version 8 of the Cloud Foundry Command Line Interface \(cf CLI\). See [https://docs.cloudfoundry.org/cf-cli/install-go-cli.html](https://docs.cloudfoundry.org/cf-cli/install-go-cli.html).



</td>
</tr>
</table>

> ### Note:  
> Managing members and roles for an organization takes place on the navigation level of the subaccount to which the organization is assigned.

For more information about organization and space roles in Cloud Foundry, see [https://docs.cloudfoundry.org/concepts/roles.html](https://docs.cloudfoundry.org/concepts/roles.html).

**Related Information**  


[About User Management in the Cloud Foundry Environment](about-user-management-in-the-cloud-foundry-environment-8e6ce96.md "The Cloud Foundry environment has its own store for user data within SAP BTP. Understanding the relationship between SAP BTP and the Cloud Foundry environment is useful.")

[Add Org Members Using the Cockpit](add-org-members-using-the-cockpit-a4eeaf1.md "Add users as org members and assign roles to grant the users access to information, such as user and quota information in a Cloud Foundry org.")

[Add Organization Members Using the Cloud Foundry Command Line Interface](add-organization-members-using-the-cloud-foundry-command-line-interface-1422a5d.md "You can use the Cloud Foundry Command Line Interface (cf CLI) to add organization members and assign roles to them.")

[Add Space Members Using the Cockpit](add-space-members-using-the-cockpit-81d0b4d.md "You can add space members and assign roles to them at the space level in the cockpit.")

[Add Space Members Using the Cloud Foundry Command Line Interface](add-space-members-using-the-cloud-foundry-command-line-interface-d23ea8b.md "You can use the Cloud Foundry Command Line Interface (cf CLI) to add space members and assign roles to them.")

