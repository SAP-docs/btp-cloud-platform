<!-- loio76ce7b2660054eb7871f3281fc715bf6 -->

# Self-Restart of Application Jobs

The self-restart of application jobs can be used to secure background jobs that are endangered to be canceled during lifecycle events, such as a server restart or periods of maintenance.

When a server shuts down, all running application jobs are canceled. To avoid such an immediate job cancellation, application programmers can make use of the new self-restart functionality provided by the class `CL_APJ_SCP_TOOLS`. Using this functionality, a job can terminate in a controlled way, and the processing can be resumed later on. For these purposes, the class `CL_APJ_SCP_TOOLS` provides three methods:

-   `IS_RESTART_REQUIRED`

-   `SCHEDULE_ME_AGAIN`

-   `GET_OWN_RESTART_NUMBER`


.

Each program that can be executed as an application job should implement the following logic, as also shown in the programming example further below:

-   A logic that checks every few minutes if a server restart is ahead by using the method `IS_RESTART_REQUIRED`. This check should run every 5 minutes to avoid complications.

-   If the check returns the value `abap_true`, the logic should entail the following:
    1.  The execution of cleanup actions in order to ensure that the current program execution can terminate without leaving inconsistencies.
    2.  The use of the method `SCHEDULE_ME_AGAIN` as described further below.
    3.  The termination of the job.




<a name="loio76ce7b2660054eb7871f3281fc715bf6__section_d33_fcs_4qb"/>

## IS\_RESTART\_REQUIRED

The method `IS_RESTART_REQUIRED` returns `abap_true`, if a restart of the server where the method is called from is 10 minutes or less ahead. The return parameter is `RESTART_REQUIRED TYPE ABAP_BOOL`.



<a name="loio76ce7b2660054eb7871f3281fc715bf6__section_w5p_jcs_4qb"/>

## SCHEDULE\_ME\_AGAIN

The method `SCHEDULE_ME_AGAIN` creates a copy of the current application job from the current step onwards. The start condition of the new job is 'immediate start'. If the system has only one server, the self-restart job will only start when the server is in a normal state again. If the system has several servers, and if at least one of the other servers is in normal state, the self-restart job may start immediately on one of the other servers. The method ignores jobs with a target server, because servers are considered to be volatile in the Cloud. This method works within any kind of application job. If creating the self-restart job is successful, this will be reflected by messages in the application log.

**Import parameters:**

The import parameter `IV_MIN_OFFSET TYPE I` is optional. By default, the start condition of the self-restart job is 'immediate start'. Using this parameter, you can decide to postpone the self-restart for a few minutes.

The import parameter `IV_FORCE_RESCHEDULE TYPE ABAP_BOOL` is optional. If the recurrence pattern of an application job is less than a day, the method `SCHEDULE_ME_AGAIN` won't affect the job, since the next job is scheduled very soon and will run regardless of the last job. This behavior can be overruled by setting the parameter `IV_FORCE_RESCHEDULE = 'X'`.

**Export parameter:**

The export parameter is `ES_NEW_JOB TYPE CL_APJ_SCP_TOOLS=>TY_NEW_JOB_INFO`. This structure contains the name and the job ID of the self-restart job if the job could be scheduled successfully.

**Return parameter:**

The return parameter is `RV_SUCCESSFUL TYPE ABAP_BOOL`. It contains `abap_true` if scheduling the self-restart job was successful.



<a name="loio76ce7b2660054eb7871f3281fc715bf6__section_wvy_y2s_4qb"/>

## GET\_OWN\_RESTART\_NUMBER

A self-restart job may encounter the same situation as its original job: it finds out that it has created a copy of itself because a server restart is ahead. This new self-restart job might again encounter the same situation, and so on. In this case, a chain of self-restart jobs appears. If a program wants to know on which position it is in such a chain, it can retrieve the number with this method. Note that the internal logic of the class `CL_APJ_SCP_TOOLS` restricts the length of a self-restart chain to 10.

The return parameter for this method is `RV_LENGTH TYPE I`.

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

