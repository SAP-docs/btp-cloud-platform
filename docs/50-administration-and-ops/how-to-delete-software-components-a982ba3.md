<!-- loioa982ba36da184788a133df4500b25a08 -->

# How to Delete Software Components



<a name="loioa982ba36da184788a133df4500b25a08__section_j3y_vrj_m3b"/>

## Context

You want to delete a software component in order to:

-   get rid of no longer used software components.

-   get rid of software components that have been created by mistake \(e.g. a typo in the software component name\).


For every delete activity, the executing business user is documented in a log.



<a name="loioa982ba36da184788a133df4500b25a08__section_zzs_dnk_m3b"/>

## Procedure

To delete a software component, perform the following steps:

1.  In the *Manage Software Components* app, search for the software component out of the list that you want to delete.

2.  Click onto the software component to be redirected to its detail page.

3.  Choose the *Delete* button in the upper right corner.

4.  You will be prompted to confirm the action and are able to choose if you want to delete only the local repository or the local repository in combination with the remote repository.




<a name="loioa982ba36da184788a133df4500b25a08__section_j3z_ffl_vvb"/>

## Software component deletion in a service instance



### Types of Software Component Deletion


<table>
<tr>
<th valign="top">

Empty Software Component

</th>
<th valign="top">

Used Software Component

</th>
</tr>
<tr>
<td valign="top">

The software component contains no object locally in the service instance and no changes are committed to the remote repository. The remote repository, the associated structure package of the software component, and the software component itself are deleted. The deletion of the ABAP structure package and software component is executed without creating a transport request.

</td>
<td valign="top">

The software component contains objects locally and possible changes are committed to the remote repository. The remote repository is then deleted and the software component is locked. Since the software component is locked, no object changes can be released \(pushed to remote\) anymore.

</td>
</tr>
</table>



### Local and Remote Deletion


<table>
<tr>
<th valign="top">

Local Deletion

</th>
<th valign="top">

Local and Remote Deletion

</th>
</tr>
<tr>
<td valign="top">

When only deleting the local representation of the software component, this means all ABAP objects including the parent structure package.

</td>
<td valign="top">

When deleting local and remote representations, local means only the current system instance.

*The software component will be remotely deleted. As a consequence, no actions can be performed anymore. Please make sure to first delete the software component locally on all system instances where it is cloned. The component cannot be deleted from the other systems after it is remotely erased. This action cannot be undone.*

</td>
</tr>
<tr>
<td valign="top">

Consequences:

You can re-clone the software component again.

> ### Caution:  
> A local deletion can be critical when database tables are deleted. The local \(not transported\) table entries contained in this table will get lost. Though this would be a possible scenario on a quality or production system. On development systems, usually, there should be no business data \(like table entries\).



</td>
<td valign="top">

This option should be performed at last, once all local deletions on other system instances have been performed.

> ### Note:  
> A distributed local deletion \(deleting local software components on other system instances than the current one\) is not possible.



</td>
</tr>
</table>



### Resulting behavior in service instances where the deleted Software Component is still imported

1.  No further Git actions, including pull, switch branch and others, are possible.
2.  Changes to SAP objects of the deleted sotware component can no longer be released.
3.  Non-released requests, in which object changes have already been recorded before the software component was deleted, must be handled specially.

    For example, you can delete the recorded object changes from the transport request. Alternatively, the transport layer of the transport request can be deleted.




<a name="loioa982ba36da184788a133df4500b25a08__section_i3q_q23_43b"/>

## Result

The selected software component is deleted centrally if the checkbox *remote deletion* was selected. Otherwise it is only a local deletion, affecting the current system instance.

> ### Caution:  
> Here, centrally means the repository visible throughout the global account is deleted.

You can no longer pull or clone the software component to a service instance.

If this software component has already been cloned to a service instance, objects are not deleted in the ABAP instances but the status of the software component and all belonging objects are changed to *read-only*. You're not able to make any changes to the dedicated structure package and the development package that is contained in there. If you want to delete the objects, you must delete them and import the deletion into other systems, before you delete the software component.



## Restoring Deleted Software Components

> ### Note:  
> Currently you cannot restore software components that have been deleted. Please also use new software component name instead of reusing previously deleted software components/ software component names.

