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
<td valign="top" rowspan="2">

Organization



</td>
<td valign="top">

Org Manager



</td>
<td valign="top" rowspan="2">

See [https://docs.cloudfoundry.org/concepts/roles.html\#orgs](https://docs.cloudfoundry.org/concepts/roles.html#orgs).

> ### Note:  
> Managing members and roles for an organization takes place on the navigation level of the subaccount to which the organization is assigned.



</td>
</tr>
<tr>
<td valign="top">

Org Auditor



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Space



</td>
<td valign="top">

Space Manager



</td>
<td valign="top" rowspan="3">

See [https://docs.cloudfoundry.org/concepts/roles.html\#orgs](https://docs.cloudfoundry.org/concepts/roles.html#orgs).

> ### Caution:  
> The `Space Developer` role has broad rights within Cloud Foundry and, in particular, has access to the credentials used in various services and app bindings as well as other sensitive data. For more information, see [Giving Access Rights to Platform Users](https://help.sap.com/viewer/a04508c1a6b24e2fa0cbabc8b8e361ad/Internal/en-US/a03d08e4038b46d480c410395593bbd2.html "If you&apos;ve set up a staged development environment using different subaccounts or spaces, such as for development, testing, and production, we recommend that you grant the Cloud Development Team access to development subaccounts and spaces, but that you grant only the Cloud Administration Team access to the testing and production subaccounts or spaces.") :arrow_upper_right:.



</td>
</tr>
<tr>
<td valign="top">

Space Developer



</td>
</tr>
<tr>
<td valign="top">

Space Auditor



</td>
</tr>
</table>

**Related Information**  


[User and Member Management](../10-concepts/user-and-member-management-cc1c676.md "On the cloud platform, member management happens at all levels from global account to space, while user management is done for deployed applications.")

[Add Org Members Using the Cockpit](add-org-members-using-the-cockpit-a4eeaf1.md "You can add org members and assign roles to them at the subaccount level in the cockpit.")

[Add Organization Members Using the Cloud Foundry Command Line Interface](add-organization-members-using-the-cloud-foundry-command-line-interface-1422a5d.md "You can use the Cloud Foundry Command Line Interface (cf CLI) to add organization members and assign roles to them.")

[Add Space Members Using the Cockpit](add-space-members-using-the-cockpit-81d0b4d.md "You can add space members and assign roles to them at the space level in the cockpit.")

[Add Space Members Using the Cloud Foundry Command Line Interface](add-space-members-using-the-cloud-foundry-command-line-interface-d23ea8b.md "You can use the Cloud Foundry Command Line Interface (cf CLI) to add space members and assign roles to them.")

