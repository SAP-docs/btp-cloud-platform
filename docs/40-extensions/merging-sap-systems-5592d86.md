<!-- loio5592d86cdd7244ce82655282981a16aa -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Merging SAP Systems

Merging the SAP systems allows you to reduce the duplicate systems in the list. You can merge auto-discovered SAP systems without assigned status in a target system that has already been registered.



<a name="loio5592d86cdd7244ce82655282981a16aa__prereq_mnr_rn1_w5b"/>

## Prerequisites

-   You are a global account administrator, or you are a system landscape administrator of the global account where you want to deregister or remove your SAP system. See [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).

-   You have registered the target SAP system. See [Registering and Deregistering Systems](registering-and-deregistering-systems-2ffdaff.md).




## Context

The logic of the SAP BTP cockpit enables it to discover SAP systems across your landscape and add them automatically on the *Systems* page. If you have already added these systems manually at a given point in time and you have registered them, the auto-discovered systems might create duplicate entries in the list. To avoid duplicates and streamline the list of systems, you can merge the auto-discovered SAP systems with your manually added systems. The logic automatically detects duplicates based on their URL and system type. Note that you can only merge auto-discovered SAP systems without assigned status in a target system that has already been registered. That is, you cannot merge registered auto-discovered systems.



## Procedure

1.  In the cockpit, navigate to your global account, and then choose *System Landscape* \> *Systems* .

2.  On the *Systems* page, find the auto-discovered SAP system you want to merge.

3.  Under the *Actions* column, choose the <span class="SAP-icons-V5"></span> \(Merge system\) button.

    Alternatively, you can choose the system from the list to open the *System Details* view, and then, choose the *Merge System* button on the top-right corner.

    The *Merge System* dialog opens.

4.  In the *Target System* dropdown menu, find and select the SAP system, in which you want to merge your system.

5.  Choose *Merge*.




<a name="loio5592d86cdd7244ce82655282981a16aa__result_xgx_jhw_p5b"/>

## Results

The auto-discovered system has been merged in the target system. That is, all individual properties of the system were recorded in the target system and the common properties were preserved. At the end, the duplicate \(auto-discovered\) system has been removed as a record from the list on the *Systems* page in the SAP BTP cockpit.

