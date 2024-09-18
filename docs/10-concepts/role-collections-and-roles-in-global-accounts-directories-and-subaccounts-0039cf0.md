<!-- loio0039cf082d3d43eba9200fe15647922a -->

# Role Collections and Roles in Global Accounts, Directories, and Subaccounts

SAP BTP provides a set of role collections to set up administrator access to your global account and subaccounts.

Role collections group authorizations for resources and services. Your administrators assign these role collections to other platform users to create new administrators. Role collections consist of individual roles. For more information on role collections, roles, see the related link.

Role collections are account-specific. Role collections that exist in the global account don’t exist in the subaccounts. Likewise, role collections in subaccounts aren’t available in the global account.

> ### Note:  
> Neo subaccounts don’t use role collections.
> 
> For more information, see [Managing Member Authorizations in the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/a1ab5c4cc117455392cd0a512c7f890d.html "SAP BTP includes predefined platform roles that support the typical tasks performed by users when interacting with the platform. In addition, subaccount administrators can combine various scopes into a custom platform role that addresses their individual requirements.") :arrow_upper_right:.



<a name="loio0039cf082d3d43eba9200fe15647922a__section_wx2_fn3_thb"/>

## Role Collections

You can use the default role collections, but you can’t change or delete them. SAP BTP provides the following administrator role collections:

-   *Global Account Administrator* 

-   *Subaccount Administrator* 

-   *Directory Administrator*

-   *Cloud Connector Administrator*

-   *Connectivity and Destination Administrator*

-   *Destination Administrator*

-   *Subaccount Service Administrator*


SAP BTP provides also viewer role collections for the global account and for subaccounts. In contrast to the administrator role collections, viewer role collections only grant read access.

-   *Global Account Viewer* 

-   *Subaccount Viewer* 

-   *Directory Viewer*




<a name="loio0039cf082d3d43eba9200fe15647922a__section_yzv_22s_cpb"/>

## Administrator Role Collections

If you assign the *Global Account Administrator* role collection to a user, this user can perform administration tasks for subaccounts, role collections, identity providers, entitlements, and regions on the level of the global account. If you assign the *Global Account Viewer* role collection, this user can view subaccounts, role collections, identity providers, entitlements, and regions on the level of the global account.

> ### Note:  
> You can also use the command-line interface \(CLI\) for SAP BTP to assign authorizations. For more information on managing authorizations, see the related link.

**Global Account Administrator Role Collection**


<table>
<tr>
<th valign="top">

Roles Included

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Global Account Admin 

</td>
<td valign="top">

Role for global account members with read-write authorizations for core commercialization operations, such as updating global accounts, setting entitlements, and creating, updating, and deleting subaccounts.

The *GlobalAccount\_Admin* role template contains this role. You find the role template in the SAP BTP Cockpit if you choose the *cis-central!*<suffix\>** application identifier.

> ### Example:  
> *cis-central!b1*



</td>
</tr>
<tr>
<td valign="top">

Global Account Usage Reporting Viewer 

</td>
<td valign="top">

Role for global account members with read-only authorizations for core commercialization operations, such as viewing global account usage information.

The *GlobalAccount\_Usage\_Reporting\_Viewer* role template provides this role. You find the role template in the SAP BTP Cockpit if you chose the *uas!*<suffix\>** application identifier

</td>
</tr>
<tr>
<td valign="top">

User and Role Administrator 

</td>
<td valign="top">

Manage authorizations, trusted identity providers, and users.

The *xsuaa\_admin* role template provides this role. You find the role template in the SAP BTP Cockpit if you choose the *xsuaa!*<suffix\>** application identifier.

> ### Example:  
> *xsuaa!tl*



</td>
</tr>
<tr>
<td valign="top">

System Landscape Administrator 

</td>
<td valign="top">

Administrative access to systems and scenario-related resources.

The *GlobalAccount\_System\_Landscape\_Administrator* role template provides this role. You find the role template in the SAP BTP Cockpit if you choose the *cmp!*<suffix\>** application identifier.

> ### Example:  
> *cmp!b7*



</td>
</tr>
</table>

If you assign the *Subaccount Administrator* role collection to a user, you grant a user administration permission for a subaccount.

**Subaccount Administrator Role Collection**


<table>
<tr>
<th valign="top">

Roles Included

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Cloud Connector Administrator 

</td>
<td valign="top">

Operate the data transmission tunnels used by the Cloud connector. 

</td>
</tr>
<tr>
<td valign="top">

Destination Administrator 

</td>
<td valign="top">

Manage destination configurations, certificates and subaccount trust via the Destination editor in the SAP BTP cockpit. 

</td>
</tr>
<tr>
<td valign="top">

Subaccount Admin 

</td>
<td valign="top">

Role for subaccount members with read-write authorizations for core commercialization operations, such as viewing subaccount entitlements, and creating and deleting environment instances. 

</td>
</tr>
<tr>
<td valign="top">

Subaccount Service Administrator 

</td>
<td valign="top">

Administrative access to service brokers and environments on a subaccount level. 

</td>
</tr>
<tr>
<td valign="top">

User and Role Administrator 

</td>
<td valign="top">

Manage authorizations, trusted identity providers, and users. 

</td>
</tr>
</table>

If you assign the *Cloud Connector Administrator* role collection to a user, you grant the user administration permissions for the Cloud Connector in a subaccount.

**Cloud Connector Administrator Role Collection**


<table>
<tr>
<th valign="top">

Roles Included

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Cloud Connector Administrator 

</td>
<td valign="top">

Operate the data transmission tunnels used by the Cloud connector. 

</td>
</tr>
</table>

If you assign the *Connectivity and Destination Administrator* role collection to a user, you grant the user administration permissions for the Cloud Connector and SAP Destination service in a subaccount.

**Connectivity and Destination Administrator Role Collection**


<table>
<tr>
<th valign="top">

Roles Included

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Cloud Connector Administrator 

</td>
<td valign="top">

Operate the data transmission tunnels used by the Cloud connector. 

</td>
</tr>
<tr>
<td valign="top">

Destination Administrator 

</td>
<td valign="top">

Manage destination configurations, certificates and subaccount trust via the Destination editor in the SAP BTP cockpit. 

</td>
</tr>
</table>

If you assign the *Destination Administrator* role collection to a user, you grant the user administration permissions for the SAP Destination service in a subaccount.

**Destination Administrator Role Collection**


<table>
<tr>
<th valign="top">

Roles Included

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Destination Administrator 

</td>
<td valign="top">

Manage destination configurations, certificates and subaccount trust via the Destination editor in the SAP BTP cockpit. 

</td>
</tr>
</table>

If you assign the *Subaccount Service Administrator* role collection to a user, you grant the user administration permissions for the Service Manager in a subaccount.

**Subaccount Service Administrator Role Collection**


<table>
<tr>
<th valign="top">

Roles Included

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Subaccount Service Administrator 

</td>
<td valign="top">

Administrative access to service brokers and environments on a subaccount level. 

</td>
</tr>
</table>



<a name="loio0039cf082d3d43eba9200fe15647922a__section_spt_g2s_cpb"/>

## Viewer Role Collections

If you assign the *Global Account Viewer* role collection to a user, you grant read access to the same information as the Global Account Administrator role collection.

**Global Account Viewer Role Collection**


<table>
<tr>
<th valign="top">

Roles Included

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Global Account Viewer 

</td>
<td valign="top">

Role for global account members with read-only authorizations for core commercialization operations, such as viewing global accounts, subaccounts, entitlements, and regions. 

</td>
</tr>
<tr>
<td valign="top">

Global Account Usage Reporting Viewer 

</td>
<td valign="top">

Role for global account members with read-only authorizations for core commercialization operations, such as viewing global account usage information. 

</td>
</tr>
<tr>
<td valign="top">

User and Role Auditor 

</td>
<td valign="top">

Read-only access for authorizations, trusted identity providers, and users. 

</td>
</tr>
<tr>
<td valign="top">

System Landscape Viewer 

</td>
<td valign="top">

Viewer access to systems and scenario-related resources. 

</td>
</tr>
</table>

If you assign the *Subaccount Viewer* role collection to a user, you restrict a user's viewer permission to the subaccounts.

**Subaccount Viewer Role Collection**


<table>
<tr>
<th valign="top">

Roles Included

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Cloud Connector Auditor 

</td>
<td valign="top">

View the data transmission tunnels used by the Cloud connector to communicate with back-end systems. 

</td>
</tr>
<tr>
<td valign="top">

Destination Viewer 

</td>
<td valign="top">

View destination configurations, certificates and subaccount trust via the Destination editor in the SAP BTP cockpit. 

</td>
</tr>
<tr>
<td valign="top">

Subaccount Service Auditor 

</td>
<td valign="top">

Read-only access to service brokers and environments on a subaccount level 

</td>
</tr>
<tr>
<td valign="top">

Subaccount Viewer 

</td>
<td valign="top">

Role for subaccount members with read-only authorizations for core commercialization operations, such as viewing subaccount entitlements, details of environment instances, and job results. 

</td>
</tr>
<tr>
<td valign="top">

User and Role Auditor 

</td>
<td valign="top">

Read-only access for authorizations, trusted identity providers, and users. 

</td>
</tr>
</table>



<a name="loio0039cf082d3d43eba9200fe15647922a__section_vmx_l2s_cpb"/>

## Directory Role Collections

The role collections *Directory Administrator* and *Directory Viewer* can be assigned during the creation of a directory. If you select the checkbox *Manage Authorizations* in the creation wizard, you can assign users the role collections during the step *Manage Authorizations*. You can't create custom role collections for directories.

The *Directory Administrator* role collection grants a user administration permission for directories.

**Directory Administrator Role Collection**


<table>
<tr>
<th valign="top">

Roles Included

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Directory Admin 

</td>
<td valign="top">

Role for directory members with read-write authorizations for core commercialization operations, such as updating directories, setting entitlements, and creating, updating, and deleting subaccounts. 

</td>
</tr>
<tr>
<td valign="top">

Directory Usage Reporting Viewer

</td>
<td valign="top">

Role for directory members with read-only authorizations for core commercialization operations, such as viewing directory usage information.

</td>
</tr>
<tr>
<td valign="top">

User and Role Administrator 

</td>
<td valign="top">

Manage authorizations, trusted identity providers, and users. 

</td>
</tr>
</table>

The *Directory Viewer* role collection grants a user read access to the same information as the Directory Administrator role collection.

**Directory Viewer Role Collection**


<table>
<tr>
<th valign="top">

Roles Included

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Directory Usage Reporting Viewer

</td>
<td valign="top">

Role for directory members with read-only authorizations for core commercialization operations, such as viewing directory usage information.

</td>
</tr>
<tr>
<td valign="top">

Directory Viewer 

</td>
<td valign="top">

Role for directory members with read-only authorizations for core commercialization operations, such as viewing directories, subaccounts, entitlements, and regions. 

</td>
</tr>
<tr>
<td valign="top">

User and Role Auditor 

</td>
<td valign="top">

Read-only access for authorizations, trusted identity providers, and users. 

</td>
</tr>
</table>



<a name="loio0039cf082d3d43eba9200fe15647922a__section_jr5_xl3_thb"/>

## Roles

Create your own role collections by using the roles of the default role collections. The roles are based on role templates, which are provided by applications. The application identifier refers to the application, which provides the role templates.

> ### Example:  
> The *GlobalAccount\_Admin* role template provides the *Global Account Admin* role. You find the role template in the cockpit if you choose the *cis-central!*<suffix\>** application identifier.
> 
> > ### Example:  
> > `cis-central!b1`

The following table provides the information about the roles that are available.

**Role Details**


<table>
<tr>
<th valign="top">

Roles

</th>
<th valign="top">

Available in

</th>
<th valign="top">

Role Templates

</th>
<th valign="top">

Application Identifier

</th>
</tr>
<tr>
<td valign="top">

Cloud Connector Administrator 

</td>
<td valign="top">

Subaccount

</td>
<td valign="top">

Cloud\_Connector\_Administrator 

</td>
<td valign="top">

connectivity!*<suffix\>* 

</td>
</tr>
<tr>
<td valign="top">

Cloud Connector Auditor 

</td>
<td valign="top">

Subaccount

</td>
<td valign="top">

Cloud\_Connector\_Auditor 

</td>
<td valign="top">

connectivity!*<suffix\>* 

</td>
</tr>
<tr>
<td valign="top">

Destination Administrator 

</td>
<td valign="top">

Subaccount

</td>
<td valign="top">

Destination\_Administrator 

</td>
<td valign="top">

destination-xsappname!*<suffix\>* 

</td>
</tr>
<tr>
<td valign="top">

Destination Viewer 

</td>
<td valign="top">

Subaccount

</td>
<td valign="top">

Destination\_Viewer 

</td>
<td valign="top">

destination-xsappname!*<suffix\>* 

</td>
</tr>
<tr>
<td valign="top">

Directory Admin 

</td>
<td valign="top">

Directory

</td>
<td valign="top">

Directory\_Viewer 

</td>
<td valign="top">

cis-central!*<suffix\>* 

</td>
</tr>
<tr>
<td valign="top">

Directory Usage Reporting Viewer

</td>
<td valign="top">

Directory

</td>
<td valign="top">

Directory\_Usage\_Reporting\_Viewer

</td>
<td valign="top">

uas!*<suffix\>* 

</td>
</tr>
<tr>
<td valign="top">

Directory Viewer 

</td>
<td valign="top">

Directory

</td>
<td valign="top">

Directory\_Admin 

</td>
<td valign="top">

cis-central!*<suffix\>* 

</td>
</tr>
<tr>
<td valign="top">

Global Account Admin 

</td>
<td valign="top">

Global account

</td>
<td valign="top">

GlobalAccount\_Admin 

</td>
<td valign="top">

cis-central!*<suffix\>* 

</td>
</tr>
<tr>
<td valign="top">

Global Account Viewer 

</td>
<td valign="top">

Global account

</td>
<td valign="top">

GlobalAccount\_Viewer 

</td>
<td valign="top">

cis-central!*<suffix\>* 

</td>
</tr>
<tr>
<td valign="top">

Global Account Usage Reporting Viewer 

</td>
<td valign="top">

Global account

</td>
<td valign="top">

GlobalAccount\_Usage\_Reporting\_Viewer 

</td>
<td valign="top">

uas!*<suffix\>*  

</td>
</tr>
<tr>
<td valign="top">

System Landscape Administrator 

</td>
<td valign="top">

Global account

</td>
<td valign="top">

GlobalAccount\_System\_Landscape\_Administrator 

</td>
<td valign="top">

cmp!*<suffix\>*  

</td>
</tr>
<tr>
<td valign="top">

System Landscape Viewer 

</td>
<td valign="top">

Global account

</td>
<td valign="top">

GlobalAccount\_System\_Landscape\_Viewer 

</td>
<td valign="top">

extension-service-cmp!*<suffix\>*  

</td>
</tr>
<tr>
<td valign="top">

Subaccount Admin 

</td>
<td valign="top">

Subaccount

</td>
<td valign="top">

Subaccount\_Admin 

</td>
<td valign="top">

cis-local!*<suffix\>* 

</td>
</tr>
<tr>
<td valign="top">

Subaccount Viewer 

</td>
<td valign="top">

Subaccount

</td>
<td valign="top">

Subaccount\_Viewer 

</td>
<td valign="top">

cis-local!*<suffix\>* 

</td>
</tr>
<tr>
<td valign="top">

Subaccount Service Administrator 

</td>
<td valign="top">

Subaccount

</td>
<td valign="top">

Subaccount\_Service\_Administrator 

</td>
<td valign="top">

service-manager!*<suffix\>* 

</td>
</tr>
<tr>
<td valign="top">

Subaccount Service Auditor 

</td>
<td valign="top">

Subaccount

</td>
<td valign="top">

Subaccount\_Service\_Auditor 

</td>
<td valign="top">

service-manager!*<suffix\>* 

</td>
</tr>
<tr>
<td valign="top">

User and Role Administrator 

</td>
<td valign="top">

Global account and subaccount

</td>
<td valign="top">

xsuaa\_admin 

</td>
<td valign="top">

xsuaa!*<suffix\>* 

</td>
</tr>
<tr>
<td valign="top">

User and Role Auditor 

</td>
<td valign="top">

Global account and subaccount

</td>
<td valign="top">

xsuaa\_auditor 

</td>
<td valign="top">

xsuaa!*<suffix\>* 

</td>
</tr>
</table>



<a name="loio0039cf082d3d43eba9200fe15647922a__section_uzw_h4t_1qb"/>

## Roles in Environments

If you've enabled environments in your subaccount, manage the roles for those environments. For more information, see:

-   [About Roles in the Cloud Foundry Environment](../50-administration-and-ops/about-roles-in-the-cloud-foundry-environment-0907638.md)

-   [Assign Roles in the Kyma Environment](../60-security/assign-roles-in-the-kyma-environment-148ae38.md)


> ### Note:  
> The ABAP environment uses the roles of the SAP BTP, Cloud Foundry Environment.

**Related Information**  


[User and Member Management](user-and-member-management-cc1c676.md "On SAP BTP, member management takes place at all levels from global account to environment, while user management is relevant for business applications.")

[Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md "As an administrator, you group application roles in role collections. You then assign role collections to application users.")

[Building Roles and Role Collections for Applications](../50-administration-and-ops/building-roles-and-role-collections-for-applications-eaa6a26.md "As an administrator, you can maintain application roles and role collections which can be used in user management.")

[Mapping Role Collections in the Subaccount](../50-administration-and-ops/mapping-role-collections-in-the-subaccount-9e1bf57.md "You've arranged roles in role collections, and now want to assign or map these role collections to business users.")

[Managing Users and Their Authorizations Using the btp CLI](../50-administration-and-ops/managing-users-and-their-authorizations-using-the-btp-cli-94bb593.md "User authorizations are managed by assigning role collections to users (for example, Subaccount Administrator). Use the SAP BTP command-line interface (btp CLI) to manage roles and role collections, and to assign role collections to users.")

