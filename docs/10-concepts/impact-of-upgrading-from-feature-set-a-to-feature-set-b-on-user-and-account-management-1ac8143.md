<!-- loio1ac8143b71fb46e78564ed30be757620 -->

# Impact of Upgrading from Feature Set A to Feature Set B on User and Account Management

While we have tried to make upgrading your account management feature set as simple as possible, we've had to make a few adjustments. To help you find your way, we've gathered a summary of changes you can expect in your accounts.

> ### Note:  
> For more information about the upgrade process itself, see SAP Note [3027721](https://launchpad.support.sap.com/#/notes/3027721).



<a name="loio1ac8143b71fb46e78564ed30be757620__section_n3n_2k1_54b"/>

## Reactivation of the Default Identity Provider for Applications

If you deactivated the default identity provider, SAP ID service, for business users in multi-environment subaccounts in cloud management tools feature set A, the process of upgrading to cloud management tools feature set B reactivates the default identity provider. We reactivate the default identity provider because cloud management tools feature set B also uses it for platform users.

> ### Recommendation:  
> Keep at least one user from the default identity provider in each account to still have access if there are ever issues with a custom identity provider.

Even though the default identity provider has been reactivated, the option to authenticate with the default identity provider is hidden from business users. Business users are redirected to your custom identity provider. Hiding the default identity provider ensures that the user experience for your business users remains the same. Users from the default identity provider can log on, only if the users are authorized, in other words, users with existing shadow users.

For more information about shadow users, see [Working with Users](../50-administration-and-ops/working-with-users-2c91f88.md).

> ### Note:  
> Whether the default identity provider was reactivated or not, applications that share the default identity provider, such as SAP Support Portal or your demo application in your subaccount, no longer require reauthentication, when you switch from one application to the other. This change improves the single sign-on experience.



<a name="loio1ac8143b71fb46e78564ed30be757620__section_th5_cgb_54b"/>

## Custom Identity Providers for Platform Users

In cloud management tools feature set B you're free to integrate custom identity providers for platform users. If you use custom identity providers for platform users in cloud management tools feature set A, you can't move to cloud management tools feature set B. Details about the ability to upgrade existing custom identity provider configurations for platform users from cloud management tools feature set A to cloud management tools feature set B will be covered in the future.

> ### Note:  
> This limitation doesn't apply to business users of your applications.



<a name="loio1ac8143b71fb46e78564ed30be757620__section_qft_32b_54b"/>

## Global Account Users Identified by E-Mail Address

With cloud management tools feature set B, global account users from the SAP ID service are identified by their e-mail address and not their user ID. If you've multiple user accounts that share the same e-mail address, they all get the same authorizations.



## Mapping Account Authorizations Between Feature Set A and Feature Set B

The following table lists the role collections for account administration that a user has in cloud management tools feature set B, based on the role memberships the user had in cloud management tools feature set A.

<a name="loio1ac8143b71fb46e78564ed30be757620__table_lcx_h1m_t4b"/>Account Authorization Mappings Between Feature Set A and Feature Set B


<table>
<tr>
<th valign="top">

Authorizations in Feature Set A



</th>
<th valign="top">

Authorizations in Feature Set B



</th>
<th valign="top">

More Information



</th>
</tr>
<tr>
<td valign="top">

Administrator of global account



</td>
<td valign="top">

*Global Account Administrator* in global account and *Subaccount Administrator* in multi-environment subaccounts



</td>
<td valign="top">

In cloud management tools feature set A, members of the global account have global account administrator privileges. Such users can create and manage subscriptions for subaccounts.

> ### Tip:  
> To ensure that your global account administrators still have these authorizations, these users are also assigned subaccount administrator authorizations in **all** multi-environment subaccounts of the global account. After the move, consider if your global account administrators really need subaccount administrator access to all your subaccounts.



</td>
</tr>
<tr>
<td valign="top">

Security administrator in multi-environment subaccount



</td>
<td valign="top">

*Subaccount Administrator* in multi-environment subaccount



</td>
<td valign="top">

Security administrators rely mostly on the *User & Role Administrator* role for their authorizations. In cloud management tools feature set B, these authorizations are bundled in the *Subaccount Administrator* role collection.



</td>
</tr>
</table>



<a name="loio1ac8143b71fb46e78564ed30be757620__section_mjb_tcm_t4b"/>

## Mapping Cloud Foundry Authorizations Between Feature Set A and Feature Set B

The following table lists the roles and role collections a user receives, based on the Cloud Foundry roles the user had in cloud management tools feature set A.

<a name="loio1ac8143b71fb46e78564ed30be757620__table_jgg_pvy_t4b"/>Mappings of Cloud Foundry Authorizations Between Feature Set A and Feature Set B


<table>
<tr>
<th valign="top">

Authorizations in Feature Set A



</th>
<th valign="top">

Authorizations in Feature Set B



</th>
<th valign="top">

More Information



</th>
</tr>
<tr>
<td valign="top">

*Org Manager*

*Space Manager*

*Space Developer*



</td>
<td valign="top">

*Org Manager*

*Space Manager*

*Space Developer*

> ### Note:  
> If the user doesn't already have the *Subaccount Administrator* role collection, the user receives the *Connectivity and Destination Administrator* role collection.



</td>
<td valign="top">

In cloud management tools feature set A, a user with the *Org Manager*, *Space Manager*, or *Space Developer* roles could also manage cloud connectors and destinations. To make sure that such users don't lose any authorizations, we check the users authorizations and add the required role collections.



</td>
</tr>
<tr>
<td valign="top">

*Org Auditor*

*Space Auditor*



</td>
<td valign="top">

*Org Auditor*

*Space Auditor*



</td>
<td valign="top">

No change.



</td>
</tr>
</table>



<a name="loio1ac8143b71fb46e78564ed30be757620__section_xlb_lmv_3pb"/>

## Role Collection Names

Any role collection that you created in cloud management tools feature set A with a name that is a reserved role collection name in cloud management tools feature set B, will have the suffix "\(Custom\)" appended to your role collection's name. For example, *Subaccount Administrator* will be renamed to *Subaccount Administrator \(Custom\)* after the upgrade.



<a name="loio1ac8143b71fb46e78564ed30be757620__section_o3p_yj1_54b"/>

## No Impact on Neo Subaccounts

The authorization model of Neo subaccounts remains the same in both feature sets.

