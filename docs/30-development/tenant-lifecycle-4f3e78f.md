<!-- loio4f3e78f4f753477098a493db75fd9812 -->

# Tenant Lifecycle



Each consumer tenant goes through a certain lifecycle starting from the provisioning to the deprovisioning of the tenant and possibly tenant restoration. The current lifecycle status of a tenant in the ABAP system is shown in the Landscape Portal.

![](images/Tenant_Lifecycle_dbe9a2f.png)


<table>
<tr>
<th valign="top">

**Request Type** in Landscape Portal



</th>
<th valign="top">

Changes to **Lifecycle Status**



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top" rowspan="3">

New Tenant



</td>
<td valign="top">

In Preparation



</td>
<td valign="top" rowspan="3">

The creation of a new tenant starts with status **In Preparation**. After the creation of the new tenant in the system, the registration of client and tenant in the system, and the import of initial tenant data, the tenant is **Ready**. Finally, after preparation of logon to the new tenant, technical configuration, business configuration, activation of tenant features, setup of monitoring, the tenant is finalized, and the lifecycle status is set to **Live**.



</td>
</tr>
<tr>
<td valign="top">

Ready



</td>
</tr>
<tr>
<td valign="top">

Live



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Delete Tenant



</td>
<td valign="top">

Live



</td>
<td valign="top" rowspan="3">

Tenant deletion is triggered when the consumer subscription is deleted. The deletion request changes the tenant lifecycle status from **Live** to **Torn Down**. During a retention period of 30 days, the tenant remains in status **Torn Down**, reflecting the deletion in progress. After 30 days, and if the tenant is not restored, the tenant deletion is automatically completed, and the status is changed to **Deleted**.



</td>
</tr>
<tr>
<td valign="top">

Torn Down



</td>
</tr>
<tr>
<td valign="top">

Deleted



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Restore Tenant



</td>
<td valign="top">

Live



</td>
<td valign="top" rowspan="3">

After a tenant deletion was requested by deleting the corresponding consumer subscription, the tenant can be restored in the Landscape Portal during a retention period of 30 days. Doing so, the lifecycle status is changed back from**Torn Down** during the retention period, to **Live** after the completed tenant restoration.



</td>
</tr>
<tr>
<td valign="top">

Torn Down



</td>
</tr>
<tr>
<td valign="top">

Live



</td>
</tr>
</table>

