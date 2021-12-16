<!-- loio6aabfe1f38de41ba9f888110109a4b7a -->

# Job Cancellation

Job cancellation details



A job can be canceled either by the system or by a user. If a job is canceled by the system, it gets the status *Failed*. If you want to cancel a job, please keep in mind that the system behavior depends on what exactly you want to cancel:

-   If you cancel a single job with the status *Scheduled*, this job will be canceled and removed from the job list.

-   If you cancel a single job with the status *In Process*, this job will be canceled, will get the status *Canceled* and will remain in the job list.

-   If you cancel a job that has the status *Scheduled* and is a part of a job series, all jobs with the status *Scheduled* will be canceled and removed from the job list. All jobs with other statuses will remain in the list and won't be canceled.

-   If you cancel a job that has the status *In Process* and is a part of a job series, a job with the status *In Process* will be canceled and will get the status *Canceled*. All other jobs of the series with other statuses will remain in the list.


To cancel a job, please select the job to be removed and choose *Cancel* from the main toolbar.

> ### Note:  
> Please note that the jobs with the status *Finished* cannot be canceled because they have already been run.

**Related Information**  


[Application Jobs](application-jobs-37e7a01.md)

