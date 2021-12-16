<!-- loio76ce7b2660054eb7871f3281fc715bf6 -->

# Self-Restart of Application Jobs

The self-restart of application jobs can be used to secure background jobs that are endangered to be canceled during lifecycle events of system infrastructure, such as a server restart, resource optimization, or periods of maintenance.

A lifecycle event could result in a cancellation of running application jobs. As an application job owner, you want to be prepared to avoid such an immediate job cancellation. To be so, you can make use of the new self-restart functionality provided by ABAP class `CL_APJ_SCP_TOOLS`. Using this functionality, a developer can prepare his application job implementation to terminate and reschedule the job in a controlled way. For these purposes, the class `CL_APJ_SCP_TOOLS` provides three methods:

-   `IS_RESTART_REQUIRED`

-   `SCHEDULE_ME_AGAIN`

-   `GET_OWN_RESTART_NUMBER`


.

Each implementation that can be executed as an application job should implement the following logic, as also shown in the programming example below:

-   A logic that checks every few minutes if a lifecycle event is ahead by using the method `IS_RESTART_REQUIRED`. This check should run regularly \(e.g. every 5 minutes\).

-   If the check returns the value `abap_true`, the logic should entail the following:
    1.  The execution of cleanup actions in order to ensure that the current program execution can terminate without leaving inconsistencies.
    2.  The use of the method `SCHEDULE_ME_AGAIN` as described further below.




<a name="loio76ce7b2660054eb7871f3281fc715bf6__section_d33_fcs_4qb"/>

## IS\_RESTART\_REQUIRED

The method `IS_RESTART_REQUIRED` returns `abap_true`, if an upcoming lifecycle event is 10 minutes or less ahead after the method is called. The return parameter is `RESTART_REQUIRED TYPE ABAP_BOOL`.



<a name="loio76ce7b2660054eb7871f3281fc715bf6__section_w5p_jcs_4qb"/>

## SCHEDULE\_ME\_AGAIN

The method `SCHEDULE_ME_AGAIN` creates a copy of the current application job from the current step onwards. The new job will be started as soon as background resources are available. If creating the self-restart job is successful, this will be reflected by messages in the application log.

**Import parameters:**

The import parameter `IV_FORCE_RESCHEDULE TYPE ABAP_BOOL` is optional. If the recurrence pattern of an application job is less than a day, the method `SCHEDULE_ME_AGAIN` won't affect the job, since the next job is scheduled very soon and will run regardless of the last job. With this parameter the behavior can be overruled by setting the parameter `IV_FORCE_RESCHEDULE = 'X'`.

**Export parameter:**

The export parameter is `ES_NEW_JOB TYPE CL_APJ_SCP_TOOLS=>TY_NEW_JOB_INFO`. This structure contains the name and the job ID of the self-restart job if the job could be scheduled successfully.

**Return parameter:**

The return parameter is `RV_SUCCESSFUL TYPE ABAP_BOOL`. It contains `abap_true` if scheduling the self-restart job was successful.



<a name="loio76ce7b2660054eb7871f3281fc715bf6__section_wvy_y2s_4qb"/>

## GET\_OWN\_RESTART\_NUMBER

A self-restart job may encounter the same situation as its original job: it finds out that it has created a copy of itself because a lifecycle event is ahead. This new self-restart job might again encounter the same situation, and so on. In this case, a chain of self-restart jobs appears. If an application job implementation wants to know on which position it is in such a chain, it can retrieve the number with this method. Note that the internal logic of the class `CL_APJ_SCP_TOOLS` restricts the length of a self-restart chain to 10.

The return parameter for this method is `RV_LENGTH TYPE I`. It returns the length of the self-restart chain.

**Example:**

```lang-abap
DATA: new_job TYPE cl_apj_scp_tools=>ty_new_job_info.
IF cl_apj_scp_tools=>is_restart_required( ) = abap_true.
"  if necessary, implement coding to do cleanup actions
   DATA(was_restarted) = cl_apj_scp_tools=>schedule_me_again(
                           IMPORTING
                              es_new_job = new_job ).

"  implement coding that finishes the job
ENDIF.
```

