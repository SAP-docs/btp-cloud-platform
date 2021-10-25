<!-- loioc8248745dde24afb91479361de336111 -->

# Managing Entitlements and Quotas Using the Cockpit

When you purchase an enterprise account, you are entitled to use a specific set of resources, such as the amount of memory that can be allocated to your applications.

An entitlement equals your right to provision and consume a resource. A quota represents the numeric quantity that defines the maximum allowed consumption of that resource.

Entitlements and quotas are managed at the global account level, distributed to subaccounts, and consumed by the subaccounts. When quota is freed at the subaccount level, it becomes available again at the global account level.

> ### Note:  
> Only global account administrators can configure entitlements and quotas for subaccounts.

There are two places in the SAP BTP cockpit where you can view and configure entitlements and quotas for subaccounts - at global account level and at subaccount level. Depending on your permissions, you may only have access to one of these pages. You can find more details below:

<a name="loioc8248745dde24afb91479361de336111__table_yhl_1dx_1jb"/>Entitlements Pages \[Feature Set A\]


<table>
<tr>
<th valign="top">

Page in cockpit



</th>
<th valign="top">

Navigation Level



</th>
<th valign="top">

Visible to



</th>
<th valign="top">

Permissions



</th>
</tr>
<tr>
<td valign="top">

*Entitlements* \> *Subaccount Assignments*



</td>
<td valign="top">

Global account level



</td>
<td valign="top">

Global account administrators only



</td>
<td valign="top">

-   View & Edit - Global account administrators



</td>
</tr>
<tr>
<td valign="top">

*Entitlements* \> *Service Assignments*



</td>
<td valign="top">

Global account level



</td>
<td valign="top">

Global account administrators only



</td>
<td valign="top">

-   View - Global account administrators \(you cannot make changes to entitlements or quota assignments from this page\)



</td>
</tr>
<tr>
<td valign="top">

*Entitlements*



</td>
<td valign="top">

Subaccount level



</td>
<td valign="top">

Subaccount members \(regardless of whether they are also global account administrators or not\)



</td>
<td valign="top">

-   View - Subaccount members who are not global account administrators
-   View & Edit - Global account administrators who are also subaccount members



</td>
</tr>
</table>

<a name="loioc8248745dde24afb91479361de336111__table_vl5_mdx_1jb"/>Entitlements Pages \[Feature Set B\]


<table>
<tr>
<th valign="top">

Page in cockpit



</th>
<th valign="top">

Navigation Level



</th>
<th valign="top">

Visible to



</th>
<th valign="top">

Permissions



</th>
</tr>
<tr>
<td valign="top">

*Entitlements* \> *Entity Assignments*



</td>
<td valign="top">

Global account level



</td>
<td valign="top">

Global account administrators only



</td>
<td valign="top">

-   View & Edit - Global account administrators



</td>
</tr>
<tr>
<td valign="top">

*Entitlements* \> *Service Assignments*



</td>
<td valign="top">

Global account level



</td>
<td valign="top">

Global account administrators only



</td>
<td valign="top">

-   View - Global account administrators \(you cannot make changes to entitlements or quota assignments from this page\)



</td>
</tr>
<tr>
<td valign="top">

*Entitlements*



</td>
<td valign="top">

Subaccount level



</td>
<td valign="top">

Subaccount members \(regardless of whether they are also global account administrators or not\)



</td>
<td valign="top">

-   View - Subaccount members who are not global account administrators
-   View & Edit - Global account administrators who are also subaccount members



</td>
</tr>
</table>

You can also assign entitlements to directories, see [Configure Entitlements and Quotas for Directories \[Feature Set B\]](Configure_Entitlements_and_Quotas_for_Directories_Feature_Set_B_37f8871.md).

> ### Note:  
> -   \[Feature Set B\] To subscribe to a multitenant application, you must first assign it as an entitlement to the specific subaccount. If you remove a subaccount’s entitlement to a multitenant application, any subscriptions to it from that subaccount will stop working.
> 
> -   \[Feature Set B\] Before a subaccount admin can enable a quota-based environment, such as Kyma, the subaccount admin must first assign the environment as an entitlement to the subaccount. Other non-quota-based environments, such as Cloud Foundry, are available by default to all subaccounts, and therefore are not available as entitlements.

In the Cloud Foundry environment, you can further distribute the quotas that are allocated to a subaccount. This is done by creating space quota plans and assigning them to the spaces. For more information on space quota plans in the Cloud Foundry environment, see:

-   [Managing Space Quota Plans](Managing_Space_Quota_Plans_4e5f0ee.md)
-   [https://docs.cloudfoundry.org/adminguide/quota-plans.html](https://docs.cloudfoundry.org/adminguide/quota-plans.html)

> ### Tip:  
> Optionally, you can configure entitlements and quotas for supported services that you own or subscribe to from supported non-SAP cloud vendors. These services can be consumed in SAP BTP in your subaccounts alongside your self-developed services and those provided by SAP. This functionality requires first setting up a resource provider instance for your provider account in the cockpit. For more information, see [Managing Resource Providers](Managing_Resource_Providers_e2c250d.md).

> ### Note:  
> -   In global accounts that use the consumption-based commercial model, SAP BTP, Cloud Foundry Runtime is not listed in the *Entitlements* pages in the SAP BTP cockpit. A quota limit of 50 GB of Cloud Foundry Runtime memory is assigned by default to every subaccount.
> -   If you need to increase this limit, report an incident to [SAP support](https://support.sap.com) on the BC-NEO-CIS component. This also applies to other services that have a technical quota limit.

**Related Information**  


[Entitlements and Quotas](../10-concepts/Entitlements_and_Quotas_00aa2c2.md "When you purchase an enterprise account, you’re entitled to use a specific set of resources, such as the amount of memory that can be allocated to your applications.")

[Configure Entitlements and Quotas for Subaccounts](Configure_Entitlements_and_Quotas_for_Subaccounts_5ba357b.md "Assign entitlements to subaccounts by adding service plans and distribute the quotas available in your global account to your subaccounts using the SAP BTP cockpit.")

[Configure Entitlements and Quotas for Directories \[Feature Set B\]](Configure_Entitlements_and_Quotas_for_Directories_Feature_Set_B_37f8871.md "Assign entitlements to directories by adding service plans and distribute the quotas available in your global account to your directories using the SAP BTP cockpit.")

[Create Space Quota Plans](Create_Space_Quota_Plans_b13c4a2.md "You can use the cockpit to create space quota plans.")

[Create Space Quota Plans Using the Cloud Foundry Command Line Interface](Create_Space_Quota_Plans_Using_the_Cloud_Foundry_Command_Line_Interface_504fde9.md "You can use the Cloud Foundry Command Line Interface to create space quota plans.")

[Cloud Management Tools — Feature Set Overview](../10-concepts/Cloud_Management_Tools_—_Feature_Set_Overview_caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

[**Tutorial**: Manage Entitlements on SAP BTP Trial](https://developers.sap.com/tutorials/cp-trial-entitlements.html)

[**Troubleshooting**: Entitlement and Quota Problems](https://ga.support.sap.com/dtp/viewer/index.html#/tree/2065/actions/26547:27066)

