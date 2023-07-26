<!-- loio10dbd460e566426bb90a9fdbe04bad1a -->

# Extended Cloud Foundry Commands of Service Fabrik

The Service Fabrik plugin provides commands that support backup and restore operations.



The various commands described in the table below are functionalities that facilitate these operations:


<table>
<tr>
<th valign="top">

Usage



</th>
<th valign="top">

Description



</th>
<th valign="top">

Common Error Scenarios



</th>
</tr>
<tr>
<td valign="top">

`cf list-backup` 



</td>
<td valign="top">

Shows a list of all the service instance backups. These backups are specific to the spaceyou are logged on to. If you have permission to access multiple spaces and need to view backups for a specific space, log on to that space in Cloud Foundry.



</td>
<td valign="top">

**Unauthorized Access:** if you do not have permission to access the space containing the service instance or the service instance itself. Verify that you have the required permission.



</td>
</tr>
<tr>
<td valign="top">

`cf list-backup` *<service\_instance\_name\>* 



</td>
<td valign="top">

Shows a list of backups that are specific to the service instance within a space.



</td>
<td valign="top">

**Unauthorized Access:** if you do not have permission to access the space containing the service instance or the service instance itself. Verify that you have the required permission.



</td>
</tr>
<tr>
<td valign="top">

`cf backup`*<backup\_id\>* 



</td>
<td valign="top">

Provides additional information about a specific backup such as the service instance name for which backup was taken, the org and the space name to which the backup belongs, the type of backup, the status of backup, the start and finish time of backup, and so on.



</td>
<td valign="top">

none



</td>
</tr>
<tr>
<td valign="top">

`cf list-backup --guid`*<service\_instance\_guid\>*



</td>
<td valign="top">

Shows the list of all backups for the given service-fabrik service instance. The argument has to be the guid of the service instance. \(Works even for a deleted instance.\)



</td>
<td valign="top">

**Unauthorized Access:** if you do not have permission to access the space containing the service instance or the service instance itself. Verify that you have the required permission.



</td>
</tr>
<tr>
<td valign="top">

`cf list-backup`*<service\_instance\_name\>* `--deleted`



</td>
<td valign="top">

Shows the list of all backups for a deleted service-fabrik service instance. \(Works only for a deleted service-instance.\)



</td>
<td valign="top">

**Unauthorized Access:** if you do not have permission to access the space containing the service instance or the service instance itself. Verify that you have the required permission.

**Deleted instance not found error:** If the deleted instance name is incorrect.

**Multiple Guid for a deleted service instance error:**When plugin encounters multiple instance Guid’s associated with the given instance name



</td>
</tr>
<tr>
<td valign="top">

`cf start-restore` *<service\_instance\_name\>* *<backup\_id\>* 



</td>
<td valign="top">

Restores a service instance from the specified instance name and backup ID. Before providing a restore command, ensure that the backup is available for the service instance. You can verify the state of the restore process using `cf restore`*<service\_instance\_name\>*.



</td>
<td valign="top">

**Unauthorized Access:** if you do not have permission to access the space containing the service instance or the service instance itself. Verify that you have the required permission.

**Another concurrent access:** if another operation is already in progress for the service instance. You might need to try again after the current operation is completed.



</td>
</tr>
<tr>
<td valign="top">

`cf abort-restore`*<service\_instance\_name\>* 



</td>
<td valign="top">

Aborts an ongoing restore operation of the specified service instance. You can verify the state of the abort process using `cf restore` *<service\_instance\_name\>*.



</td>
<td valign="top">

**No restore in progress:** if no restore operation is currently in progress for the specified service instance. The restore activity might have completed or you might not have initiated a restore.

**Unauthorized Access:** if you do not have permission to access the space containing the service instance or the service instance itself. Verify that you have the required permission.



</td>
</tr>
<tr>
<td valign="top">

`cf instance-events --delete` 



</td>
<td valign="top">

List all delete service instance events in the space.



</td>
<td valign="top">

**Unauthorized Access:** if you do not have permission to access the space containing the service instance or the service instance itself. Verify that you have the required permission.



</td>
</tr>
<tr>
<td valign="top">

`cf restore`*<service\_instance\_name\>* 



</td>
<td valign="top">

Check the progress of the last restore operation triggered on the specified instance name. Provides additional information about the restore operation such as the service instance name for which restore was taken, the org and the space name to which the instance belongs, the status of restore, the start and finish time of restore, and so on.



</td>
<td valign="top">

**No restore in progress**: if no restore operation is currently in progress for the specified service instance. The restore activity might have completed or you might not have initiated a restore.

**Unauthorized Access**: if you do not have permission to access the space containing the service instance or the service instance itself. Verify that you have the required permission.



</td>
</tr>
</table>

