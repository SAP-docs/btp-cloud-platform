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

3.  You will be prompted to confirm the action.

    > ### Caution:  
    > Make sure you delete all artifacts in the system locally first as the deletion will only delete the software component remotely. Please note that this action can't be undone.




<a name="loioa982ba36da184788a133df4500b25a08__section_i3q_q23_43b"/>

## Result

The selected software component is deleted centrally.

You can no longer pull or clone the software component to a service instance.

If this software component has already been pulled to a service instance, objects are not deleted in the ABAP instances but the status of the software component and all belonging objects is changed to *read-only*. You're not able to make any changes to the dedicated structure package and the development package that is contained in there. If you want to delete the objects, you must delete them and import the deletion into other systems, before you delete the software component.



## Restoring Deleted Software Components

> ### Note:  
> Currently you can't restore software components that have been deleted.

