<!-- loio5bb62cec33834c6eaa5b80e82b34e54a -->

# Automatically Restarting an Application Job

The automatic restart of an application job ensures continuity by resuming interrupted processes without user intervention. This allows maintaining efficiency and reducing downtime in long-running jobs, especially during planned or unplanned system interruptions.



## Context

The runtime of any process can be interrupted without programming errors being involved. Reasons are planned or unplanned failovers. In those cases, currently running transactions are rolled back and the session is ended. In particular, long-running application jobs can be affected by this. In such cases, in the past, the application job status was set to canceled by the application job runtime system. Afterwards, you had to find out the reason of the job cancellation and take appropriate action. However, when an application job stops running due to the reason mentioned above, there is no error in the job itself. There is now a new behavior for such situations.



## Business Logic for Creating an Automatic Restart

If an application job stops running due to process interruption, the system doesn't set the application job status to canceled, but the job remains active. Another server resumes processing the application job as soon as possible, starting with the job step that was interrupted. If the application job has only one step, the job will run right from the beginning again.

Please consider the following when you implement the business logic:

-   When an application job is automatically restarted, no new application job \(no copy\) is created.

-   Within your coding that runs inside the application job, you can find out if the current execution was triggered by an automatic restart. You can use the method `CL_APJ_RT_API=>GET_OWN_AUTO_RESTART_NUMBER`. The method returns an integer. If it returns 0, the current execution is the original one. If it returns 1, the current execution was triggered by an automatic restart. Since an automatically restarted job can undergo the same procedure again, the method can return values greater than 1.

-   Please implement your logic in a way that it's transactionally consistent and can be restarted at any time. Keep in mind that the system calls a rollback after the application job has stopped due to process interruption. Any database changes which your coding has not yet committed will be rolled back.

-   The automatic restart applies for application jobs that have no recurrence, and for application jobs that have a recurrence period of 5 minutes or greater. If an application job has a small recurrence period of less than 5 minutes, it's assumed that an automatic restart is not necessary, because the successor job will start shortly and resume the work. That means that periodic application jobs with a recurrence of less than 5 minutes will be set to canceled in case of a process interruption.




## Testing Job Behavior After an Automatic Restart

If you want to test if your application job behaves correctly after an automatic restart, please use the explicit restart functionality:

1.  Start your application job

2.  Cancel your application job using *Cancel* in the *Application Jobs* app or via the method `CL_APJ_RT_API=>CANCEL_JOB`.

3.  Restart your application job using *Restart* \(with the option *From Error Step*\) in the *Application Jobs* app or via the method `CL_APJ_RT_API=>RESTART_JOB`.


There is a difference between the automatic restart and the explicit restart: when an application job is automatically restarted, no new job is created. The existing job is resumed from the beginning of the step that got interrupted. When you explicitly restart an application job, a copy of the original job is created and run from the beginning of the step that was canceled before. Essentially, both restart functionalities are the same, though: the application coding that's run within an application job is stopped, and afterwards starts from the beginning. To check if the current job execution was caused by an explicit restart, you can use the method `CL_APJ_RT_API=>IS_EXPLICIT_RESTART`.

