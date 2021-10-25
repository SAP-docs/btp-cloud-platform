<!-- loio949ba003345b476e99e46b920f41632d -->

# Creating a Job Catalog Entry and a Job Template in ADT

Follow these steps to create a Job Catalog Entry and a Job Template in ADT.



<a name="loio949ba003345b476e99e46b920f41632d__steps"/>

## Procedure

1.  Implement the business logic. You need to create a class which implements certain interfaces so that it is usable in an application job. For more information, see [Implementing the Business Logic](Implementing_the_Business_Logic_99dcde1.md).

2.  Define the Job Catalog Entry. With a method of a certain framework class, you create a Job Catalog Entry which refers to the class of step 1. For more information, see [Creating the Job Catalog Entry](Creating_the_Job_Catalog_Entry_1cff59e.md).

3.  Define the Job Template. With another method of the framework class, you create a Job Template which refers to the Job Catalog Entry of step 2. For more information, see [Creating the Job Template](Creating_the_Job_Template_1f04ad2.md).


**Related Information**  


[Setting up the Authorizations](Setting_up_the_Authorizations_bb559a5.md "Some further activities in ADT and in the administrator’s launchpad are necessary to be able to schedule the job template in the Fiori app Application Jobs.")

[Scheduling an Application Job](Scheduling_an_Application_Job_147d689.md "Find out how to schedule an Application Job.")

