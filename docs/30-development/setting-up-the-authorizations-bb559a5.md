<!-- loiobb559a5a4b654996a167d72273f28542 -->

# Setting up the Authorizations

Some further activities in ADT and in the administrator’s launchpad are necessary to be able to schedule the job template in the Fiori app *Application Jobs*.



1.  Create an Identity and Access Management \(IAM\) Business Catalog.

    When you create a job catalog entry and a job template as explained in [Creating a Job Catalog Entry and a Job Template in ADT](creating-a-job-catalog-entry-and-a-job-template-in-adt-949ba00.md), an object of the type **IAM App** is created automatically. It has the name **<job catalog entry name\>\_SAJC**. This IAM app contains the start authorization for all job templates that refer to this job catalog entry.

    Create an IAM business catalog via ADT:

    1.  Right-click the package where the objects are located that have already been created.
    2.  Select *New \> Other ABAP Repository Object*.
    3.  Expand *Cloud Identity and Access Management*.
    4.  Double-click *Business Catalog*.
    5.  Enter a name \(e.g. `ZTEST_MY_SIMPLE_JOBS`\) and a description.
    6.  Select *Save* and choose the appropriate transport request.
    7.  Select the tab *Apps* below.
    8.  Press *Add …* on the top right corner of the screen.
    9.  Enter the name of the IAM app mentioned in step **e** \(`ZTEST_MY_SIMPLE_JOB_SAJC`\).
    10. Select *Save*.
    11. Press *Publish Locally* on the top right corner of the screen.

2.  If the business logic performs own authorization checks, remember to add the required authorizations to a separate IAM app of type `EXT`. The following steps explain how to do this:

    1.  Right-click the package that contains the objects that have already been created.

    2.  Select *New* and then choose *Other ABAP Repository Object*.

    3.  Expand *Cloud Identity and Access Management*.

    4.  Choose *IAM App*.

    5.  Enter a name and a description. Choose *EXT - External App* as application type.

    6.  Select an appropriate transport request and click *Save*.

    7.  Select the *Authorizations* tab.

    8.  Select *Insert*. Now, you can specify an authorization object and assign values to the authorization fields.

    9.  Repeat step `h` for each authorization that is necessary to run the business logic.

    10. Add the IAM app to the business catalog that you've created as described in step 1.


3.  Create a business role.

    Open the Fiori App *Maintain Business Roles* in the Fiori Launchpad of the administrator and perform the following steps:

    1.  Click*New*.
    2.  Choose a name \(e.g. `ZTEST_MY_SIMPLE_JOBS`\) and a description.
    3.  Click on *Assigned Business Catalogs*.
    4.  Select *Add*.
    5.  Select the business catalog created in the previous step \(e.g. `ZTEST_MY_SIMPLE_JOBS`\).

        > ### Note:  
        > A business user who shall be able to schedule application jobs needs to have access to the *Application Jobs* tile. This tile is provided by the business catalog `SAP_CORE_BC_APJ_JCE`, which is contained in the business role `SAP_BR_ADMINISTRATOR`. It doesn't only provide the *Application Jobs* app, but also contains restriction types to configure the authorization on other users’ jobs and to schedule jobs for other users \(for more information, see the section *Assigning Further Authorizations* below\).
        > 
        > Add the business catalog `SAP_CORE_BC_APJ_JCE` to the business role created following the steps above, or assign it to a separate business role.

    6.  Select *Save*.

4.  Assign the business role to a user.

    For more information, see [How to Maintain Business Users](../50-administration-and-ops/how-to-maintain-business-users-db1d0b4.md).




<a name="loiobb559a5a4b654996a167d72273f28542__section_zrj_2wb_s4b"/>

## Assigning Further Authorizations

You can access only your own jobs in the *Application Jobs* app. In order to grant access to other users' objects used in the *Application Jobs* app, create a new business role assigning the business catalog `SAP_CORE_BC_APJ_JCE` to it. You can modify the provided restriction types according to your needs.

1.  Create a new business role assigning the business catalog `SAP_CORE_BC_APJ_JCE` to it. The restriction type `Job Catalog Entry/Application Job Part` contains the two fields `Application Job Catalog Entry` and `Application Job Part`.

    > ### Note:  
    > With this restriction type you'll be able to provide the necessary authorizations for certain actions on other users' application jobs, which are based on a specified job catalog entry. With this, you can display the logs of other users' jobs, which are based on this specified job catalog entry.
    > 
    > Alternatively, you can also create a display only-role using this restriction type.

2.  The business catalog `SAP_CORE_BC_APJ_JCE` has another restriction type: `Create Application Jobs for Other Users`. It has the restriction field `Application Job Catalog Entry`.

    > ### Note:  
    > With this restriction type you'll be able to grant a business user the authorization to schedule an application job for any other business user, based on the job catalog entry selected. This feature is supported by the parameter `iv_username` of the method `cl_apj_rt_api=>schedule_job`. For more information, see [Maintaining Application Jobs Using an API](maintaining-application-jobs-using-an-api-1491e6c.md).

3.  Next, define your business role with the above-mentioned restriction fields `Application Job Catalog Entry` and `Application Job Part`. To do so, select *Maintain Restrictions*. In the `Application Job Catalog Entry` field, you can choose the job catalog entries, and in the `Application Job Part` field, you can choose for which part of a job access should be granted. You can choose the values `JOB` \(Job Details\), `SPOOL` \(Result List\), and `APPLOG` \(Log\) by clicking the *Edit* icon next to the fields.

4.  Go back and select *Save*. Now, you've maintained your business role, and you can assign the role to a business user.


