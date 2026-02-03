<!-- loioc82379bc7d8c4f6b8a62581a27b443ac -->

# Effects of Using IAM Apps \(App Authorization Variants\)

When you work with IAM apps of the app authorization variant type, it affects how you use the IAM administration apps to manage IAM-related tasks and authorizations for business users.

The following apps contain features you can use to work with IAM apps:


<table>
<tr>
<th valign="top">

App

</th>
<th valign="top">

Feature

</th>
</tr>
<tr>
<td valign="top">

*Display IAM Apps* 

</td>
<td valign="top">

Display IAM apps for all supported IAM app types. Keep an overview of the assigned business roles, deprecated and non-deprecated IAM apps, their successors, and more.

</td>
</tr>
<tr>
<td valign="top">

*IAM Information System* 

</td>
<td valign="top">

Discover all the details about IAM apps, including the business roles they're assigned to, the business catalogs they're bundled in, and any restrictions defined for them. You can also find information on successor IAM apps for both deprecated and non-deprecated IAM apps. This helps with early app replacement and deprecation planning, among other things.

</td>
</tr>
<tr>
<td valign="top">

*Business Role Templates* 

</td>
<td valign="top">

The *IAM App* tab is available displaying all assigned IAM apps per business role template.

</td>
</tr>
<tr>
<td valign="top">

*Business Catalogs* 

</td>
<td valign="top">

On the *Applications* tab, you can view all assigned IAM apps if the *Supports IAM Apps* checkbox is selected in the corresponding business catalog. For business catalogs that do not support IAM apps, the tile and target mapping title is displayed.

</td>
</tr>
<tr>
<td valign="top">

*Display Restriction Types* 

</td>
<td valign="top">

On the *Used in IAM Apps* tab, you can view all IAM apps in which the corresponding restriction type is used.

</td>
</tr>
<tr>
<td valign="top">

*Manage Launchpad Pages* 

</td>
<td valign="top">

You can display all tiles referenced by transactions and available through the corresponding business roles for specific pages using the role context feature. This feature doesn't consider the activation status of IAM apps.

</td>
</tr>
<tr>
<td valign="top">

*Manage Business Role Changes After Upgrade* 

</td>
<td valign="top">

[How To View and Manage Changed IAM Apps After an Upgrade](how-to-view-and-manage-changed-iam-apps-after-an-upgrade-236d1ca.md) 

</td>
</tr>
<tr>
<td valign="top">

*Maintain Business Roles* 

</td>
<td valign="top">

[Effects on the Maintain Business Roles App](effects-on-the-maintain-business-roles-app-0361f3e.md) 

</td>
</tr>
</table>

Additionally, be aware of the following effects when working with IAM apps:

-   **Transaction Authorizations in Business Catalogs with and without IAM App Support**

    Transactions and their authorizations can be referenced in two types of business catalogs: those that support IAM apps and a small number that do not. If both types of business catalogs are assigned to a business role, the business catalog without IAM app support determines the authorizations for that business role. For these few non-migrated business catalogs, the corresponding tiles are not available on their own. However, if they are combined with migrated business catalogs that include the same transaction, the tiles become available. Still, these tiles do not appear in the app finder for the non-migrated business catalogs.

    > ### Example:  
    > Let's picture the following scenario: A transaction is assigned to both types of business catalogs and both types of business catalogs are assigned to a business role. Even if the IAM app is deactivated in the business catalog that supports IAM apps, the transaction authorizations remain included because of the business catalog that doesn't support IAM apps and their deactivation.

-   **IAM App Deactivation Limitations in Dependent Business Catalogs**

    If a business catalog that supports IAM apps has a dependent business catalog that does not support IAM apps, it is not possible to deactivate IAM apps in the dependent business catalog.

-   **Dependent IAM Apps**

    Not all business catalogs currently support IAM apps. As a result, some dependent IAM apps are not maintained for those that have already been delivered.

-   **Tiles in App Finder**

    For more information, refer to [End User](https://help.sap.com/docs/SAP_S4HANA_CLOUD/53e36b5493804bcdb3f6f14de8b487dd/e2b39fb01689420393931a9eb3f627ec.html).


**Related Information**  


[Display IAM Apps](https://help.sap.com/docs/SAP_S4HANA_CLOUD/53e36b5493804bcdb3f6f14de8b487dd/2cabad5cf4c649e5a1115f91a8f8e48c.html)

[IAM Information System](https://help.sap.com/docs/SAP_S4HANA_CLOUD/53e36b5493804bcdb3f6f14de8b487dd/82d17cfdb0f3464b9735e4ded705f71f.html)

[Business Role Templates](https://help.sap.com/docs/SAP_S4HANA_CLOUD/53e36b5493804bcdb3f6f14de8b487dd/223dfd30aac3441183eb8fb9964884ee.html)

[Business Catalogs](https://help.sap.com/docs/SAP_S4HANA_CLOUD/53e36b5493804bcdb3f6f14de8b487dd/dd0abf583e0647e5a536b878efeb5143.html)

[Display Restriction Types](https://help.sap.com/docs/SAP_S4HANA_CLOUD/53e36b5493804bcdb3f6f14de8b487dd/9203905781b441ed9359cb29803f000a.html)

[Manage Launchpad Pages](https://help.sap.com/docs/SAP_S4HANA_CLOUD/4fc8d03390c342da8a60f8ee387bca1a/8a174e235493472095c0bcec957dfee0.html)

[SAP Community Blog Post – Precise Control of Fiori App Access with the App Authorization Variants](https://community.sap.com/t5/enterprise-resource-planning-blog-posts-by-sap/precise-control-of-fiori-app-access-with-the-app-authorization-variants/ba-p/13994744)

