<!-- loio1f04ad22db0147b99ebc476708b749b6 -->

# Creating the Job Template

An *Application Job Template* refers to an application job catalog entry and contains values for some or all selection fields. It can be thought of as a variant of an application job catalog. In the simplest case, a job template doesn't contain any values for the selection fields. In this case, the selection fields are prefilled with their initial values \(such as 0 if the selection field is of type integer\). An application job catalog entry can have more than one application job template. The job template is the entity that can be scheduled in the *Application Jobs* app. In the scheduling dialog, the selection fields appear and are prefilled with the values defined in the template. They can be overwritten by the user. Scheduling an application job template then results in an application job.

The creation of a job template follows the same technical rules as a *Job Catalog Entry* as described in [Creating the Job Catalog Entry](creating-the-job-catalog-entry-1cff59e.md). To create a job template, use the ABAP development tools for Eclipse. For more information, see [Creating Application Job Templates](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/creating-application-job-templates?version=sap_btp). Alternatively, you could still also create application job templates via a released API. For more information, see [Creating a Job Catalog Entry and a Job Template via API](creating-a-job-catalog-entry-and-a-job-template-via-api-e58737f.md).

**Related Information**  


[Setting up the Authorizations](setting-up-the-authorizations-bb559a5.md "Some further activities in ADT and in the administrator’s launchpad are necessary to be able to schedule the job template in the Fiori app Application Jobs.")

