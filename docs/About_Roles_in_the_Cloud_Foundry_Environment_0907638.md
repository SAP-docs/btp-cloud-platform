<!-- loio09076385086b4da3bd1808d5ef572862 -->

# About Roles in the Cloud Foundry Environment

Roles determine which features users can view and access, and which actions they can initiate.

Cloud Foundry includes predefined roles that are specific to the navigation level in the SAP BTP cockpit; for example, the roles at the level of the organization differ from the ones for the space. Each role comes with a set of permissions. Roles apply to all operations that are associated with the organization or the space, irrespective of the tool used \(Eclipse-based tools, SAP BTP cockpit, and cf CLI\).

The following roles can be assigned to users in the Cloud Foundry environment on SAP BTP:


<table>
<tr>
<th>

Level



</th>
<th>

Role



</th>
<th>

Role Description



</th>
</tr>
<tr>
<td rowspan="2">

Organization



</td>
<td>

Org Manager



</td>
<td rowspan="2">

See [https://docs.cloudfoundry.org/concepts/roles.html\#orgs](https://docs.cloudfoundry.org/concepts/roles.html#orgs).

> ### Note:  
> Managing members and roles for an organization takes place on the navigation level of the subaccount to which the organization is assigned.



</td>
</tr>
<tr>
<td>

Org Auditor



</td>
</tr>
<tr>
<td rowspan="3">

Space



</td>
<td>

Space Manager



</td>
<td rowspan="3">

See [https://docs.cloudfoundry.org/concepts/roles.html\#orgs](https://docs.cloudfoundry.org/concepts/roles.html#orgs).



</td>
</tr>
<tr>
<td>

Space Developer



</td>
</tr>
<tr>
<td>

Space Auditor



</td>
</tr>
</table>

**Related Information**  


[User and Member Management](User_and_Member_Management_cc1c676.md "On the cloud platform, member management happens at all levels from global account to space, while user management is done for deployed applications.")

[Add Org Members Using the Cockpit](Add_Org_Members_Using_the_Cockpit_a4eeaf1.md "You can add org members and assign roles to them at the subaccount level in the cockpit.")

[Add Organization Members Using the Cloud Foundry Command Line Interface](Add_Organization_Members_Using_the_Cloud_Foundry_Command_Line_Interface_1422a5d.md "You can use the Cloud Foundry Command Line Interface (cf CLI) to add organization members and assign roles to them.")

[Add Space Members Using the Cockpit](Add_Space_Members_Using_the_Cockpit_81d0b4d.md "You can add space members and assign roles to them at the space level in the cockpit.")

[Add Space Members Using the Cloud Foundry Command Line Interface](Add_Space_Members_Using_the_Cloud_Foundry_Command_Line_Interface_d23ea8b.md "You can use the Cloud Foundry Command Line Interface (cf CLI) to add space members and assign roles to them.")

