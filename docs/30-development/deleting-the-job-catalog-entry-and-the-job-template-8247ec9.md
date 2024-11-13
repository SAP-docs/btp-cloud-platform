<!-- loio8247ec94c50c40a1a36bd79c5cf837b0 -->

# Deleting the Job Catalog Entry and the Job Template

Find out how to delete a job catalog entry and a related job template.

To delete a job catalog entry or a job template, use the ABAP development tools for Eclipse. Right-click on the object in the *Project Explorer* and select *Delete*.

Alternatively, you could also still delete job catalog entries and job templates via a released API. For more information, see [Creating a Job Catalog Entry and a Job Template via API](creating-a-job-catalog-entry-and-a-job-template-via-api-e58737f.md).

Before you can delete a job catalog entry, you must first delete all related job templates: When you create a job catalog entry, an IAM app that is based on the job catalog entry is automatically created in the Cloud. If you have followed the steps in [Setting up the Authorizations](setting-up-the-authorizations-bb559a5.md), you should perform additional steps before deleting the job catalog entry, since otherwise, the IAM app can't automatically be deleted together with the job catalog entry:

-   Remove the business role from the business user in the Fiori app *Maintain Business Users*

-   Delete the business role in the Fiori app *Maintain Business Roles*

-   Unassign the IAM app from the IAM business catalog in ABAP development tools for Eclipse

-   Delete the IAM business catalog in ABAP development tools for Eclipse


Now, you can delete the job catalog entry.

If you only want to replace the job catalog entry \(if you want to delete it to recreate it with the same name\), it's sufficient to remove the IAM app assignment from the IAM business catalogs. After the creation of the new job catalog entry, assign the new IAM app to the IAM business catalogs.

