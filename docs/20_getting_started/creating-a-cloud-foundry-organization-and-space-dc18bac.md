<!-- loiodc18bac42270468d84b6c030a668e003 -->

# Creating a Cloud Foundry Organization and Space

Create a Cloud Foundry organization and Cloud Foundry space that will correspond to the instance of the ABAP environment.



<a name="loiodc18bac42270468d84b6c030a668e003__context_dkh_gbn_q2b"/>

## Context

> ### Note:  
> If you have already created an organization and space for the ABAP environment, you can skip these steps. If you have run the booster *Prepare an Account for ABAP Development*, you can also skip these steps.

For more information about creating Cloud Foundry spaces, see [Create Spaces](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/2f6ed22ccf424dae84345f4500c2d8ea.html).



## Procedure

1.  Log on to the SAP BTP cockpit in the global account for the Cloud Foundry environment as administrator.

2.  Choose the tile of the Cloud Foundry subaccount.

3.  Check whether Cloud Foundry is enabled: If it's enabled, the Cloud Foundry organization name appears as organization on the screen area *Cloud Foundry*.

4.  If Cloud Foundry is not enabled yet, proceed as follows:

    1.  Choose *Enable Cloud Foundry*.

    2.  On the *Create Cloud Foundry Organization* dialog, enter a name for the Cloud Foundry organization and choose *Create*.


5.  On the *Cloud Foundry* screen area, choose the link for spaces.

6.  If the Cloud Foundry space in the Cloud Foundry organization does not exist yet, proceed as follows:

    1.  Choose *New Space*.

    2.  On the *New Space* dialog, enter a name for the new Cloud Foundry space, for example, ***dev***, and leave the checkboxes for space manager and space developer checked.

    3.  Choose *Create*.



