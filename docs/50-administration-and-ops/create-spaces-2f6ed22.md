<!-- loio2f6ed22ccf424dae84345f4500c2d8ea -->

# Create Spaces

Create spaces in your Cloud Foundry organization using the SAP BTP cockpit.



<a name="loio2f6ed22ccf424dae84345f4500c2d8ea__prereq_yys_bjm_qz"/>

## Prerequisites

You have a Cloud Foundry organization in your subaccount, and you have the Org Manager role in that organization.

See [Create Orgs](create-orgs-a9b1f54.md) and [About Roles in the Cloud Foundry Environment](about-roles-in-the-cloud-foundry-environment-0907638.md).



<a name="loio2f6ed22ccf424dae84345f4500c2d8ea__context_z1d_tgw_fbc"/>

## Context

There are two ways to create a space in the cockpit. The main one is to do it from the *Spaces* page in your subaccount. The second one is from the *Overview* page of your subaccount. You can choose either one of them.

**Procedure**


<table>
<tr>
<th valign="top">

Create a Space From the Spaces Page

</th>
<th valign="top">

Create a Space From the Subaccount Overview Page

</th>
</tr>
<tr>
<td valign="top">

1.  Navigate to the subaccount that contains the Cloud Foundry organization in which you'd like to create a space.
2.  Navigate to the *Cloud Foundry* \> *Spaces* page.
3.  Choose *Create Space* from the top right hand-side corner of that page.
4.  Enter a space name and choose the space roles you want to assign to yourself.
5.  Then, choose *Save*.



</td>
<td valign="top">

1.  Navigate to the subaccount that contains the Cloud Foundry organization in which you'd like to create a space.
2.  On the subaccount *Overview* page, you have a *Spaces* table. Choose *Create Space* from the top right hand-side corner of that table.
3.  Enter a space name and choose the space roles you want to assign to yourself.
4.  Then, choose *Save*.



</td>
</tr>
</table>



<a name="loio2f6ed22ccf424dae84345f4500c2d8ea__postreq_mys_qqm_qz"/>

## Next Steps

You can assign space quotas to spaces. See [Managing Space Quotas](managing-space-quotas-4e5f0ee.md).

This is an optional step. If you don't assign any space quota, the space you've just created will use the consumption limits of the org quota.

**Related Information**  


[Create Spaces Using the Cloud Foundry Command Line Interface](create-spaces-using-the-cloud-foundry-command-line-interface-a2e5e29.md "Use the cf create-space command to create spaces in your Cloud Foundry organization using the Cloud Foundry Command Line Interface (cf CLI).")

