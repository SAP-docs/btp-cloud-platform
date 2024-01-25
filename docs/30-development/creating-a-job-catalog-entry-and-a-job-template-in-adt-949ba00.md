<!-- loio949ba003345b476e99e46b920f41632d -->

# Creating a Job Catalog Entry and a Job Template in ADT

Follow these steps to create a job catalog entry and a job template in ADT.



## Procedure

1.  Implement the business logic. You need to create a class which implements certain interfaces so that it's usable in an application job. For more information, see [Implementing the Business Logic](implementing-the-business-logic-99dcde1.md).

2.  Define the job catalog entry. With a method of a certain framework class, you create a job catalog entry which refers to the class of step 1. For more information, see [Creating the Job Catalog Entry](creating-the-job-catalog-entry-1cff59e.md).

3.  Define the job template. With another method of the framework class, you create a job template which refers to the job catalog entry of step 2. For more information, see [Creating the Job Template](creating-the-job-template-1f04ad2.md).

    For more information on how to create a job catalog entry and a job template in ADT, see [Working with Application Job Objects](https://help.sap.com/docs/abap-cloud/abap-development-tools-user-guide/working-with-application-job-objects?version=sap_btp).

    If you want to implement a simple RAP \(ABAP RESTful application programming model\) business object, see[Code Sample: How to Schedule Application Jobs from a RAP-based Business Object](https://github.com/SAP-samples/abap-platform-application-jobs). This code sample allows you to schedule a class as an application job that takes the semantic key of the selected entity as a parameter.


**Related Information**  


[Setting up the Authorizations](setting-up-the-authorizations-bb559a5.md "Some further activities in ADT and in the administrator’s launchpad are necessary to be able to schedule the job template in the Fiori app Application Jobs.")

