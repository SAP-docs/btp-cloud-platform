<!-- loio99dcde1a72ed4e7fb0959ead46a7fbf5 -->

# Implementing the Business Logic

Business logic is ABAP coding that you want to be run within an application job.



Usually, business logic also defines the data type and some properties of the selection fields that you get on the selection screen before you schedule an application job. In this context, the business logic is implemented in an ABAP class. The following development steps require a user with the development role.

To implement the business logic, create an ABAP class that implements a certain interface:

-   Create an ABAP class with interface `IF_APJ_RT_RUN`. Here, the selection fields are defined as public attributes of the class. See [Creating an ABAP Class with Interface IF\_APJ\_RT\_RUN](creating-an-abap-class-with-interface-if-apj-rt-run-79bd2d9.md) for more information. It's recommended to use this interface for all new developments.
-   You can still create an ABAP class with interfaces `IF_APJ_DT_EXEC_OBJECT` and `IF_APJ_RT_EXEC_OBJECT`. Here, the selection fields are defined in method `GET_PARAMETERS` of the interface `IF_APJ_DT_EXEC_OBJECT`. See [Creating an ABAP Class with Interfaces IF\_APJ\_DT\_EXEC\_OBJECT and IF\_APJ\_RT\_EXEC\_OBJECT](creating-an-abap-class-with-interfaces-if-apj-dt-exec-object-and-if-apj-rt-exec-object-767ef7b.md) for more information.

    > ### Note:  
    > Note that this is a legacy interface. Don't use it for new developments. If you use this interface, you only have limited options during the editing of the job catalog entry.


The ABAP class mentioned here is considered the main class of each application job. This class needs to be part of a customer-defined software component \(not `ZLOCAL`\) to be able to transport the class into subsequent systems.

**Related Information**  


[Creating the Job Catalog Entry](creating-the-job-catalog-entry-1cff59e.md "")

[Creating the Job Template](creating-the-job-template-1f04ad2.md "")

[Setting up the Authorizations](setting-up-the-authorizations-bb559a5.md "Some further activities in ADT and in the administrator’s launchpad are necessary to be able to schedule the job template in the Fiori app Application Jobs.")

[Application Logs](application-logs-091bec9.md "You can use the Application Logs to display and check if any errors occurred during runtime.")

