<!-- loio61d2d0830f0c45feb4721614bbfee033 -->

# Restart Job Chains

Find out how to restart job chains.



When an application job or a chain of application jobs consisting of one or more steps has the status *Failed*, *Canceled* or *User Error*, you can restart it. To do so, select the job and choose one of the following options from the drop-down menu:

-   From Error Step: All steps before the error step will be skipped and all other steps \(including the error step\) will be executed.

-   After Error Step. All steps before the error step including the error step will be skipped and all other steps after the error step will be executed. This option is not available for single step jobs.


The new job will be executed immediately with the original job user.

> ### Note:  
> You can't change the starting or application parameters.

**Related Information**  


[Application Jobs](application-jobs-37e7a01.md)

