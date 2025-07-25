<!-- loioa817aef3b51d4b0fbc4907e7adcfacd7 -->

# How to Lock Unused Business Users

Lock inactive business users



<a name="loioa817aef3b51d4b0fbc4907e7adcfacd7__HowToLockUnusedBusinessUsers_context"/>

## Context

You can schedule a job to automatically lock business users who haven't logged on for a certain number of days.

> ### Note:  
> To schedule this job, you can either use the*Application Jobs* app as described below or you can add the *Schedule Lock for Unused Business Users* tile your SAP Fiori Launchpad using *Edit Homepage* if you want to access the repective scheduling screen directly.



<a name="loioa817aef3b51d4b0fbc4907e7adcfacd7__HowToLockUnusedBusinessUsers_steps"/>

## Procedure

1.  Open the *Application Jobs* app.

2.  Under *Job Templates*, select *Lock Unused Business Users* and click *Step 2*.

3.  Define the recurrence pattern of your job and click *Step 3*.

4.  Under *Parameters*, enter the required number of days since the last logon you want to use for the automatic lock.

5.  Add the business users you want to exclude.

    Optional:

    Open the value help if you want to define further conditions.

    Go to the *Define Conditions* tab. Here you can define single users or whole user areas you want to exclude from the selection. You can enter multiple users at once by using copy and paste, for example to transfer users from lists.

    Please note that you can also restrict the list of users that should be processed by this job.

6.  Click *Schedule*.


