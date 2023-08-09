<!-- loioa982ba36da184788a133df4500b25a08 -->

# How to Delete Software Components



<a name="loioa982ba36da184788a133df4500b25a08__section_j3y_vrj_m3b"/>

## Context

You want to delete a software component in order to:

-   get rid of no longer used software components.

-   get rid of software components that have been created by mistake \(e.g. a typo in the software component name\).


For every delete activity, the user is documented in a log.



<a name="loioa982ba36da184788a133df4500b25a08__section_zzs_dnk_m3b"/>

## Procedure

To delete a software component, perform the following steps:

1.  On the *Manage Software Components* screen, select a software component you want to delete.

2.  Choose *Delete* in the control panel.

3.  


<a name="loioa982ba36da184788a133df4500b25a08__section_j3z_ffl_vvb"/>

## Software component deletion in a service instance

**Types of Software Component deletion**


<table>
<tr>
<td valign="top">

1.  The software component contains no object locally in the service instance and no changes are committed to the remote repository. The remote repository, the associated structure package of the software component, and the software component itself are deleted. The deletion of the ABAP structure package and software component is executed without creating a transport request.



</td>
<td valign="top">

The software component contains objects locally and possible changes are committed to the remote repository. The remote repository is then deleted and the software component is locked. Since the software component is locked, no object changes can be released \(pushed to remote\) anymore.



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

The selected software component is deleted centrally.

You can no longer pull or clone the software component to a service instance.

If this software component has already been pulled to a service instance, objects are not deleted in the ABAP instances but the status of the software component and all belonging objects are changed to *read-only*. You're not able to make any changes to the dedicated structure package and the development package that is contained in there. If you want to delete the objects, you must delete them and import the deletion into other systems, before you delete the software component.



## Restoring Deleted Software Components

> ### Note:  
> Currently you can't restore software components that have been deleted.

