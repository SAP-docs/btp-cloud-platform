<!-- loio1cff59ef893a4a17a478a54b7ba27353 -->

# Defining the Job Catalog Entry

Instead of a respective editor in ADT, Job Catalog Entries and Job Templates need to be created via a released API. This API shall be called from within a console application. The console application is only required in the development system.

Job Catalog Entries and Job Templates are created with a package assignment and the objects are assigned to a transport request. You need to make sure that package and transport request fit together \(regarding transport layer\) and that possible naming conventions are obeyed.

The Job Catalog Entry mainly contains the reference to the implementation class of the business logic.

**Related Information**  


[Defining the Job Template](defining-the-job-template-1f04ad2.md "")

[Setting up the Authorizations](setting-up-the-authorizations-bb559a5.md "Some further activities in ADT and in the administrator’s launchpad are necessary to be able to schedule the job template in the Fiori app Application Jobs.")

[Scheduling an Application Job](../50-administration-and-ops/scheduling-an-application-job-147d689.md "Find out how to schedule an Application Job.")

