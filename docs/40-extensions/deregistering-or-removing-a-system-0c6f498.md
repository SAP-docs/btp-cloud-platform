<!-- loio0c6f4988f9154a96b399ce9b9a2fd5a1 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Deregistering or Removing a System

When you no longer need the system to be paired with your global account, you can deregister or remove it depending on its status.



<a name="loio0c6f4988f9154a96b399ce9b9a2fd5a1__prereq_l4m_s5b_fhb"/>

## Prerequisites

-   You are a global account administrator, or you are a system landscape administrator of the global account where you want to deregister or remove your system. See [Working with Role Collections](../50-administration-and-ops/working-with-role-collections-393ea0b.md).

-   You have added your system as a record to the list on the **Systems** page. See [Registering and Deregistering Systems](registering-and-deregistering-systems-2ffdaff.md).




## Context

> ### Note:  
> The content in this section is not relevant for China \(Shanghai\) and Government Cloud \(US\) regions.

Deregistering an SAP or third-party system means that the connectivity between this system and the global account is disabled and extension scenarios cannot be established, while removing a system means that this system is no longer part of the system landscape list. You can deregister or remove a system from the *Actions* column, or from the *System Details* page that you access when selecting the system from the system landscape list.

The deregistration and the removal processes have the following states displayed in the cockpit:

-   *Deregistering* - a deregistration process has started. As a result, the connectivity between the SAP or third-party system and SAP BTP is disabled and extension scenarios cannot be established. The system remains in the system landscape list and you can register it again later on.

    Once a system is registered, you can deregister it only after removing it from all entitlement configurations and formations it takes part in.

-   *Error while Deregistering* - the deregistration has failed. Try to deregister the system again. If the problem persists, you have to report a case in one of the components mentioned below.
-   *Removing* - a system removal process has started in the SAP BTP cockpit. As a result, the SAP or third-party system is deregistered, and then, it is removed from the system landscape list completely. To register the system again, first, you must add it to the list anew, and then, initiate the registration procedure.

    Once a system is registered, you can only remove it if you first deregister it.

-   *Error while Removing* - the system removal has failed. Try to deregister the system again. If the problem persists, you have to report a case in one of the components mentioned below.

> ### Note:  
> If the deregistration, or removal errors persist, report a case in one of the following components depending on the system type:
> 
> -   SAP SuccessFactors - `BC-NEO-EXT-SF`
> 
> -   SAP S/4HANA Cloud - `BC-NEO-EXT-S4C`
> 
> -   All other system types - `BC-CP-MP`



## Procedure

1.  In the cockpit, navigate to your global account, and then choose *System Landscape* \> *Systems* .

2.  On the *Systems* page, select the SAP or third-party system you want to deregister or remove.

    -   To deregister a system, choose <span class="SAP-icons-V5"></span> \(Deregister system\) from the *Actions* column, or choose *Deregister System* from the *System Details* page that you access when selecting the system from the system landscape list.

        You can deregister only registered systems.

        > ### Note:  
        > If your system is of type SAP S/4HANA Cloud, SAP SuccessFactors, or part of the SAP Customer Experience portfolio and you deregister this system, you can register back the same system's tenant and not a different one.

    -   To remove a system, choose :wastebasket: from the *Actions* column, or choose *Remove System* from the *System Details* page that you access when selecting the system from the system landscape list.

        Before removing a system from the list, first you have to check all configurations that this system is part of, such as entitlements and formations. Then, you have to deregister it and after that you will be able to remove it from the *Systems* page. If you try to remove a system before deregistering it, a dialog will appear and will ask you to deregister the system first.

        > ### Note:  
        > You can only remove manually added systems. Depending on their discovery mode the systems that are added to the list either are *Manually added* \(registered manually by following the procedure in the prerequisites\), or *Auto-discovered* \(added to the list automatically, based on information of the existing system landscape\), or part of the *Subaccount/<my-subaccount\>* \(automatically added, based on the information of the SAP BTP subaccount\).
        > 
        > You cannot remove *Auto-discovered* systems from the list.





<a name="loio0c6f4988f9154a96b399ce9b9a2fd5a1__result_xgx_jhw_p5b"/>

## Results

The system has been deregistered or removed as a record from the list on the *Systems* page in the SAP BTP cockpit.

