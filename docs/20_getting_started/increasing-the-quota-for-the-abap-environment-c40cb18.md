<!-- loioc40cb18aeaa343389036fdcdd03c41d0 -->

# Increasing the Quota for the ABAP Environment

Before you can create a service instance for the ABAP environment, you must assign some of the available quota to the subaccount for the ABAP environment.



<a name="loioc40cb18aeaa343389036fdcdd03c41d0__context_lhw_zst_q2b"/>

## Context

> ### Note:  
> If you have run the booster *Prepare an Account for ABAP Development*, you can skip this step.

If you are working in an enterprise account, you need to add quotas to the services that you purchased in your subaccount before they can appear in the service marketplace. For more information, see [Configure Entitlements and Quotas for Subaccounts](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/5ba357b4fa1e4de4b9fcc4ae771609da.html).



## Procedure

1.  Log on to the SAP BTP cockpit as administrator.

2.  Go to your global account.

3.  \[Feature Set A\]: From the navigation area, choose *Entitlements* \> *Subaccount Entitlements* and enter your subaccount.

    \[Feature Set B\]: From the navigation area, choose *Entitlements* \> *Entity Assignments*.

4.  Enter the subaccount for the ABAP environment and choose *Go*.

5.  Choose *Configure Entitlements*.

6.  Choose *Add Service Plans*.

    In the following popup, the available entitlements for this subaccount are shown.

7.  For the *ABAP environment* entitlement, select the plans *abap\_compute\_unit*, *standard*, and *hana\_compute\_unit*.

    With the selection of the *standard* service plan, you can size the ABAP runtime and the SAP HANA memory independently from each other. To be able to do your sizing, you must also select the quota plans *abap\_compute\_unit* and *hana\_compute\_unit*.

8.  Choose *Add 3 Service Plans*.

9.  On the following screen, increase the quotas in the *abap\_compute\_unit* service plan at least by 1 and in the *hana\_compute\_unit* service plan at least by 4.

    The configurable ABAP runtime comes in blocks of 16 GB ABAP server memory, also referred to as ABAP compute unit. You can choose between 1, 2, 4, 6, or 8 ABAP compute units. The configurable SAP HANA memory comes in blocks of 16 GB database memory, also referred to as HANA compute units. You can choose between 4, 8, or 16 HANA compute units.

    The minimum configuration of 1 ABAP compute unit and 4 HANA compute units is sufficient in many cases to create one service instance for the ABAP environment. If you need more resources, choose higher quotas.

10. Choose *Save*.




<a name="loioc40cb18aeaa343389036fdcdd03c41d0__result_vqt_rfb_s4b"/>

## Results

After you have assigned an entitlement for the three plans with respective quotas to your subaccount, you can create an ABAP system. This is the point where you can then decide how many 16 GB blocks of ABAP compute units and HANA compute units you want to assign to your new system \(see [Creating an ABAP System](creating-an-abap-system-50b32f1.md)\).

