<!-- loio1c460b218664442caf28d34348284fdb -->

# Editing Job Users

Find out how to change the user of your application job, or delete your job.



<a name="loio1c460b218664442caf28d34348284fdb__section_mfh_nnb_55b"/>

## Prerequisite

Before changing the user of a job, ensure that the target user has the correct authorizations to run the job. Otherwise, the job will fail.

To be able to see the app, make sure that the target user is assigned to a business role that has the business catalog `SAP_CORE_BC_APJ_USR_PC` included.



<a name="loio1c460b218664442caf28d34348284fdb__section_kww_jhv_fsb"/>

## Procedure

1.  Open the *Maintain Job Users* app.

2.  Select the scheduled jobs that you want to work with, and choose one of the following actions:

    -   *Change Job Owner* to change the owner of your application job

    -   *Change Job User* to change the business user of your application job

    -   *Change Job Owner and User* to change both the owner and the user of your application job

    -   *Delete* to delete your application job


    When clicking on an application job, you'll be navigated to the *Details* page of the *Application Jobs* app.

3.  If you've decided to change the owner or the user of your application job, or if you want to change both, a dialog opens. Enter the new job owner and user by selecting them from the value help. Mind that in case of a job user change, you can only select users that have the appropriate start authorization for a job. Job owners don't need this authorization, but they need the restriction type `Create Application Jobs for Other Users` instead. For more information, see **Maintaining Authorizations** of the *Application Jobs* documentation. App-specific authorizations are not checked. You can choose to only display these users by filtering for *Only Valid*.

    > ### Note:  
    > If a job owner is a communication user, the owner can't be changed, since the connection to the corresponding communication arrangement of the type `SAP_COM_0064` would be broken.

4.  You can change multiple application job owners and users at the same time. To do this, select all users you want to change and choose *Change Job Owner and User*. If the job owner differs from the job user, the job owner must have the appropriate authorization given by the restriction type `Create Application Jobs for Other Users` of business catalog `SAP_CORE_BC_APJ_JCE`.

5.  You can choose to display the change history of your application job by selecting *Change History*. All changes that were made to the owner and user in the past are shown in the change history. The change history shows the user type, and the new and old user IDs. You can view who changed the user, and when it was changed. The type of change is shown, too.

6.  You can delete multiple application jobs at the same time. To do this, select all jobs you want to delete and choose *Delete*.


You've now maintained your job user.

**Related Information**  


[Application Jobs](application-jobs-37e7a01.md)

 <?sap-ot O2O class="- topic/link " href="171039b7300345cb81392ba058db5dd4.xml" text="" desc="" xtrc="link:2" xtrf="file:/home/builder/src/dita-all/jjq1673438782153/loio2080d0faf9d84ce6aa14caa4caa32935_en-US/src/content/localization/en-us/1c460b218664442caf28d34348284fdb.xml" ?> 

