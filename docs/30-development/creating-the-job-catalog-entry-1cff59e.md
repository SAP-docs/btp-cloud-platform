<!-- loio1cff59ef893a4a17a478a54b7ba27353 -->

# Creating the Job Catalog Entry

An application job catalog entry contains the information that is needed for scheduling and running an application job. The application job catalog entry contains the name of the class that implements the business logic, and the information on how selection fields are rendered in the job scheduling dialog in the app.

To create a job catalog entry, use the `ABAP Development Tools` \(ADT\) editor. For more information, see [Working with Application Job Objects](https://help.sap.com/docs/btp/sap-abap-development-user-guide/working-with-application-job-objects?version=Cloud). Alternatively, you could still also create job catalog entries and job templates via a released API. This API is called from within a console application. The console application is only required in the development system.

Job catalog entries and job templates are created with a package assignment and the objects are assigned to a transport request. You need to make sure that the package and transport request fit together \(regarding the transport layer\) and that possible naming conventions are obeyed.

The job catalog entry mainly contains the reference to the implementation class of the business logic.

> ### Example:  
> A code example of a console application that generates the minimal number of required development objects: One job catalog entry and one related job template is shown in *Creating the Job Template* \(see *Related Links* below\).

**Related Information**  


[Creating the Job Template](creating-the-job-template-1f04ad2.md "")

[Setting up the Authorizations](setting-up-the-authorizations-bb559a5.md "Some further activities in ADT and in the administrator’s launchpad are necessary to be able to schedule the job template in the Fiori app Application Jobs.")

