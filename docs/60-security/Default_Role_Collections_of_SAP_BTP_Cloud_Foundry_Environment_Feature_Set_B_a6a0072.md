<!-- loioa6a00728e8c54efea8f7e60f6270b1d1 -->

# Default Role Collections of SAP BTP Cloud Foundry Environment \[Feature Set B\]

The following table displays the default role collections available with cloud management tools feature set B after initially deploying your accounts. For more information, see the related links.



<a name="loioa6a00728e8c54efea8f7e60f6270b1d1__table_fkw_vwg_5kb"/>Default Role Collections Including Roles and Role Templates


<table>
<tr>
<th>

Role Collection



</th>
<th>

Role Name



</th>
<th>

Role Template



</th>
<th>

App ID



</th>
<th>

Role Description



</th>
</tr>
<tr>
<td>

Global Account Administrator



</td>
<td>

Global Account Admin



</td>
<td>

GlobalAccount\_Admin



</td>
<td>

cis-central!*<suffix\>*



</td>
<td>

Includes read-write authorizations for updating the global account, setting entitlements, and creating, updating, and deleting subaccounts.



</td>
</tr>
<tr>
<td>

Global Account Administrator



</td>
<td>

 Global Account Usage Reporting Viewer 



</td>
<td>

 GlobalAccount\_Usage\_Reporting\_Viewer 



</td>
<td>

 uas!*<suffix\>*  



</td>
<td>

 Includes read-only authorizations for viewing global account usage information. 



</td>
</tr>
<tr>
<td>

Global Account Administrator



</td>
<td>

 User and Role Administrator 



</td>
<td>

 xsuaa\_admin 



</td>
<td>

 xsuaa!*<suffix\>* 



</td>
<td>

 Includes read-write authorizations for trusted identity providers, role collections, roles and users. 



</td>
</tr>
<tr>
<td>

Global Account Administrator



</td>
<td>

 System Landscape Administrator 



</td>
<td>

 GlobalAccount\_System\_Landscape\_Administrator 



</td>
<td>

 cmp!*<suffix\>*  



</td>
<td>

 Includes read-write authorizations for registering SAP systems and assigning SAP systems to formations. 



</td>
</tr>
<tr>
<td>

Subaccount Administrator



</td>
<td>

 Cloud Connector Administrator 



</td>
<td>

 Cloud\_Connector\_Administrator 



</td>
<td>

 connectivity!*<suffix\>* 



</td>
<td>

 Operate the data transmission tunnels used by the Cloud connector. 



</td>
</tr>
<tr>
<td>

Subaccount Administrator



</td>
<td>

 Destination Administrator 



</td>
<td>

 Destination\_Administrator 



</td>
<td>

 destination-xsappname!*<suffix\>* 



</td>
<td>

 Manage destination configurations, certificates and subaccount trust via the Destination editor in the SAP BTP cockpit. 



</td>
</tr>
<tr>
<td>

Subaccount Administrator



</td>
<td>

 Subaccount Admin 



</td>
<td>

 Subaccount\_Admin 



</td>
<td>

 cis-local!*<suffix\>* 



</td>
<td>

 Includes read-write authorizations for viewing subaccount entitlements and for creating and deleting environment instances. 



</td>
</tr>
<tr>
<td>

Subaccount Administrator



</td>
<td>

 User and Role Administrator 



</td>
<td>

 xsuaa\_admin 



</td>
<td>

 xsuaa!*<suffix\>* 



</td>
<td>

 Includes read-write authorizations for trusted identity providers, role collections, roles and users. 



</td>
</tr>
<tr>
<td>

Subaccount Administrator



</td>
<td>

 Subaccount Service Administrator 



</td>
<td>

 Subaccount\_Service\_Administrator 



</td>
<td>

 service-manager!*<suffix\>* 



</td>
<td>

 Administrative access to service brokers and environments on a subaccount level. 



</td>
</tr>
<tr>
<td>

Global Account Viewer



</td>
<td>

 Global Account Viewer 



</td>
<td>

 GlobalAccount\_Viewer 



</td>
<td>

 cis-central!*<suffix\>* 



</td>
<td>

 Includes read authorizations for viewing subaccount entitlements and for creating and deleting environment instances. 



</td>
</tr>
<tr>
<td>

Global Account Viewer



</td>
<td>

 Global Account Usage Reporting Viewer 



</td>
<td>

GlobalAccount\_Usage\_Reporting\_Viewer 



</td>
<td>

 uas!*<suffix\>*  



</td>
<td>

 Includes read-only authorizations for viewing global account usage information. 



</td>
</tr>
<tr>
<td>

Global Account Viewer



</td>
<td>

 User and Role Auditor 



</td>
<td>

 xsuaa\_auditor 



</td>
<td>

 xsuaa!*<suffix\>* 



</td>
<td>

 Includes read authorizations for trusted identity providers and users 



</td>
</tr>
<tr>
<td>

Subaccount Viewer



</td>
<td>

 Cloud Connector Auditor 



</td>
<td>

 Cloud\_Connector\_Auditor 



</td>
<td>

 connectivity!*<suffix\>* 



</td>
<td>

 View the data transmission tunnels used by the Cloud connector to communicate with back-end systems. 



</td>
</tr>
<tr>
<td>

Subaccount Viewer



</td>
<td>

 Destination Viewer 



</td>
<td>

 Destination\_Viewer 



</td>
<td>

 destination-xsappname!*<suffix\>* 



</td>
<td>

 View destination configurations, certificates and subaccount trust via the Destination editor in the SAP BTP cockpit. 



</td>
</tr>
<tr>
<td>

Subaccount Viewer



</td>
<td>

 Subaccount Viewer 



</td>
<td>

 Subaccount\_Viewer 



</td>
<td>

 cis-local!*<suffix\>* 



</td>
<td>

 Includes read authorizations for viewing subaccount entitlements and for creating and deleting environment instances. 



</td>
</tr>
<tr>
<td>

Subaccount Viewer



</td>
<td>

 User and Role Auditor 



</td>
<td>

xsuaa\_auditor 



</td>
<td>

 xsuaa!*<suffix\>* 



</td>
<td>

 Includes read authorizations for trusted identity providers and users 



</td>
</tr>
<tr>
<td>

Subaccount Viewer



</td>
<td>

Subaccount Service Auditor



</td>
<td>

Subaccount\_Service\_Auditor



</td>
<td>

service-manager!*<suffix\>*



</td>
<td>

Read-only access to service brokers and environments on a subaccount level



</td>
</tr>
<tr>
<td>

Subaccount Service Administrator



</td>
<td>

 Subaccount Service Administrator 



</td>
<td>

 Subaccount\_Service\_Administrator 



</td>
<td>

 service-manager!*<suffix\>* 



</td>
<td>

 Administrative access to service brokers and environments on a subaccount level. 



</td>
</tr>
<tr>
<td>

Cloud Connector Administrator



</td>
<td>

 Cloud Connector Administrator 



</td>
<td>

 Cloud\_Connector\_Administrator 



</td>
<td>

 connectivity!*<suffix\>* 



</td>
<td>

 Operate the data transmission tunnels used by the Cloud connector. 



</td>
</tr>
<tr>
<td>

Destination Administrator



</td>
<td>

 Destination Administrator 



</td>
<td>

 Destination\_Administrator 



</td>
<td>

 destination-xsappname!*<suffix\>* 



</td>
<td>

 Manage destination configurations, certificates and subaccount trust via the Destination editor in the SAP BTP cockpit. 



</td>
</tr>
<tr>
<td>

Connectivity and Destination Administrator



</td>
<td>

 Cloud Connector Administrator 



</td>
<td>

 Cloud\_Connector\_Administrator 



</td>
<td>

 connectivity!*<suffix\>* 



</td>
<td>

 Operate the data transmission tunnels used by the Cloud connector. 



</td>
</tr>
<tr>
<td>

Connectivity and Destination Administrator



</td>
<td>

 Destination Administrator 



</td>
<td>

 Destination\_Administrator 



</td>
<td>

 destination-xsappname!*<suffix\>* 



</td>
<td>

 Manage destination configurations, certificates and subaccount trust via the Destination editor in the SAP BTP cockpit. 



</td>
</tr>
<tr>
<td>

Directory Administrator



</td>
<td>

 Directory Admin 



</td>
<td>

 Directory\_Admin 



</td>
<td>

 cis-central!*<suffix\>* 



</td>
<td>

 Role for directory members with read-write authorizations for core commercialization operations, such as updating directories, setting entitlements, and creating, updating, and deleting subaccounts. 



</td>
</tr>
<tr>
<td>

Directory Administrator



</td>
<td>

 User and Role Administrator 



</td>
<td>

 xsuaa\_admin 



</td>
<td>

 xsuaa!*<suffix\>* 



</td>
<td>

 Includes read-write authorizations for trusted identity providers, role collections, roles and users. 



</td>
</tr>
<tr>
<td>

Directory Administrator



</td>
<td>

 Directory Usage Reporting Viewer 



</td>
<td>

 Directory\_Usage\_Reporting\_Viewer 



</td>
<td>

 uas!*<suffix\>*  



</td>
<td>

 Role for directory members with read-only authorizations for core commercialization operations, such as viewing directory usage information. 



</td>
</tr>
<tr>
<td>

Directory Viewer



</td>
<td>

 Directory Viewer 



</td>
<td>

Directory\_Viewer



</td>
<td>

cis-central!*<suffix\>*



</td>
<td>

Role for directory members with read-only authorizations for core commercialization operations, such as viewing directories, subaccounts, entitlements, and regions.



</td>
</tr>
<tr>
<td>

Directory Viewer



</td>
<td>

 User and Role Auditor 



</td>
<td>

 xsuaa\_auditor 



</td>
<td>

 xsuaa!*<suffix\>* 



</td>
<td>

 Includes read authorizations for trusted identity providers and users 



</td>
</tr>
<tr>
<td>

Directory Viewer



</td>
<td>

 Directory Usage Reporting Viewer 



</td>
<td>

 Directory\_Usage\_Reporting\_Viewer 



</td>
<td>

 uas!*<suffix\>*  



</td>
<td>

 Role for directory members with read-only authorizations for core commercialization operations, such as viewing directory usage information. 



</td>
</tr>
</table>

**Related Information**  


[Cloud Management Tools — Feature Set Overview](../10-concepts/Cloud_Management_Tools_—_Feature_Set_Overview_caf4e4e.md "Cloud management tools represent the group of technologies designed for managing SAP BTP.")

