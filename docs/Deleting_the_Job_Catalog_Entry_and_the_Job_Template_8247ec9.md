<!-- loio8247ec94c50c40a1a36bd79c5cf837b0 -->

# Deleting the Job Catalog Entry and the Job Template

Find out how to delete a job catalog entry and a related job template.

To delete a job catalog entry, you must first delete the related job template. You can delete the job template using the method `DELETE_JOB_TEMPLATE_ENTRY` of the class `CL_APJ_DT_CREATE_CONTENT`.

In order to delete a job catalog entry, if you don't want to create a job catalog entry with the same name anymore and if you enabled the job scheduling via the app, you need to manually undo all actions that were performed after the creation of the job catalog entry in reverse order. Undo the actions in the following order:

-   Remove the business role from the business user in the Fiori app *Maintain Business Users*

-   Delete the business role in the Fiori app *Maintain Business Roles*

-   Unassign the IAM app from the IAM business catalog in ADT

-   Delete the IAM business catalog in ADT


Then, call the method `DELETE_JOB_CAT_ENTRY` of the class `CL_APJ_DT_CREATE_CONTENT`.

If you do want to create a job catalog entry with the same name as the job catalog entry you want to delete, it's sufficient to remove the IAM app assignment from the IAM business catalog\(s\) to which you've assigned it before. After the creation of the new job catalog entry, assign the new IAM app again to the IAM business catalog.

