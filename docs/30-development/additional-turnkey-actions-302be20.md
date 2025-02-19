<!-- loio302be202dba447a68d4c9ffb07e720d3 -->

# Additional Turnkey Actions



## Context

In addition to creating and editing the turnkey schedule for an intelligent scenario, you can choose whether you want to cancel the running schedule or restart any failed turnkey schedule.

<a name="task_n3c_gsd_sbc"/>

<!-- task\_n3c\_gsd\_sbc -->

## Restart Turnkey Run



<a name="task_n3c_gsd_sbc__prereq_rvz_psd_sbc"/>

## Prerequisites

Ensure that the turnkey run is in *Failed* state.



<a name="task_n3c_gsd_sbc__context_cth_qsd_sbc"/>

## Context

After a turnkey operation is completed, it is possible that due to some error the turnkey run has failed. In such case, you can choose to restart the turnkey run.



<a name="task_n3c_gsd_sbc__steps_n2b_rsd_sbc"/>

## Procedure

1.  Launch the SAP Fiori launchpad.

2.  Open the Intelligent Scenario Management app.

3.  Choose any model or version that you want.

4.  Choose *Turnkey* \> *Turnkey Runs* tab.

5.  Choose the *Run ID* for which you want to restart the turnkey run.

6.  Choose *Restart*.

7.  On prompt, choose *Ok*.


<a name="task_iv5_hsd_sbc"/>

<!-- task\_iv5\_hsd\_sbc -->

## Cancel Turnkey Run



<a name="task_iv5_hsd_sbc__prereq_t2w_rsd_sbc"/>

## Prerequisites

Ensure that the turnkey run is in *Running* state.



<a name="task_iv5_hsd_sbc__context_u2w_rsd_sbc"/>

## Context

You can cancel any turnkey run that is in progress.

> ### Note:  
> Once canceled, all subsequent operations are canceled, and you can no longer continue with that turnkey run.



<a name="task_iv5_hsd_sbc__steps_fvj_qsj_sbc"/>

## Procedure

1.  Launch the SAP Fiori launchpad.

2.  Open the *Intelligent Scenario Management*app.

3.  Choose any model or version that you want.

4.  Choose *Turnkey* \> *Turnkey Runs* tab.

5.  Choose the *Run ID* for which you want to cancel the turnkey run.

6.  Choose *Cancel*.

7.  On prompt, choose *Ok*.


<a name="task_d4h_ljl_sbc"/>

<!-- task\_d4h\_ljl\_sbc -->

## Switch Off Turnkey



<a name="task_d4h_ljl_sbc__context_f4h_ljl_sbc"/>

## Context

You can choose to switch off the turnkey. Only the user who switched on the turnkey for that intelligent scenario can switch it off. However, you can grant access to another user to switch off the turnkey for an intelligent scenario. To provide access, see [Maintaining Authorizations](https://help.sap.com/docs/SAP_S4HANA_CLOUD/a630d57fc5004c6383e7a81efee7a8bb/171039b7300345cb81392ba058db5dd4.html).

