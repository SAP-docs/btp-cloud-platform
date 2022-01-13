<!-- loio7aba501c88b04f85b84e64a833221868 -->

# Increasing the Quota for the Cloud Foundry Runtime \(Optional\)

Check if your subaccount has a quota for the Cloud Foundry runtime and increase it, if needed.



## Context

> ### Note:  
> If you have run the booster *Prepare an Account for ABAP Development*, you can skip this step.

A quota for the Cloud Foundry runtime is optional. It's only needed for the ABAP environment if your developers want to deploy their own apps in Cloud Foundry.



<a name="loio7aba501c88b04f85b84e64a833221868__steps_y5g_xwm_g3b"/>

## Procedure

1.  Log on to the SAP BTP cockpit as Cloud Foundry administrator.

2.  Go to your global account.

3.  From the navigation area, choose *Entitlements* \> *Entity Assignments*.

4.  If there is no entry for the Cloud Foundry runtime, choose *Configure Entitlements* and *Add Service Plans*.

5.  In the following popup, proceed as follows:

    1.  Choose *Cloud Foundry Runtime*.

    2.  Under *Available Service Plans*, select the checkbox *MEMORY*.

    3.  Choose *Add 1 Service Plan*.


6.  Choose *+* to add at least 1 to the subaccount.

7.  Choose *Save*.


