<!-- loiobb559a5a4b654996a167d72273f28542 -->

# Setting up the Authorizations

Some further activities in ADT and in the administrator’s launchpad are necessary to be able to schedule the job template in the Fiori app *Application Jobs*.



1.  Create an Identity and Access Management \(IAM\) Business Catalog.

    When you create a job catalog entry and a job template as explained in [Creating a Job Catalog Entry and a Job Template in ADT](Creating_a_Job_Catalog_Entry_and_a_Job_Template_in_ADT_949ba00.md), an object of the type **IAM App** is created automatically. It has the name **<job catalog entry name\>\_SAJC**.

    Create an IAM business catalog via ADT:

    1.  Right-click the package where the objects are located that have already been created.
    2.  Select *New \> Other ABAP Repository Object*.
    3.  Collapse *Cloud Identity and Access Management*.
    4.  Double-click *Business Catalog*.
    5.  Enter a name \(e.g. `ZTEST_MY_SIMPLE_JOBS`\) and a description.
    6.  Select *Save* and choose the appropriate transport request.
    7.  Select the tab *Apps* below.
    8.  Press *Add …* on the top right corner of the screen.
    9.  Enter the name of the IAM app mentioned in step **e** \(`ZTEST_MY_SIMPLE_JOB_SAJC`\).
    10. Select *Save*.
    11. Press *Publish Locally* on the top right corner of the screen.

2.  Create a business role.

    Open the Fiori App *Maintain Business Roles* in the Fiori Launchpad of the administrator and perform the following steps:

    1.  Click*New*.
    2.  Choose a name \(e.g. `ZTEST_MY_SIMPLE_JOBS`\) and a description.
    3.  Click on *Assigned Business Catalogs*.
    4.  Select *Add*.
    5.  Select the business role created in the previous step \(e.g. `ZTEST_MY_SIMPLE_JOBS`\).

        > ### Note:  
        > A business user who shall be able to schedule application jobs needs to have access to the *Application Jobs* tile. This tile was provided by the business catalog `SAP_CORE_BC_APJ`, which is contained in the business role `SAP_BR_ADMINISTRATOR`.
        > 
        > With the 2105 cloud release, the business catalog `SAP_CORE_BC_APJ` has been set to **deprecated**. Use the new business catalog `SAP_CORE_BC_APJ_JCE` instead. It doesn't only provide the *Application Jobs* app, but also contains restriction types to configure the authorization on other users’ jobs \(for more information, see the section *Assigning Further Authorizations* below\).
        > 
        > Add the business catalog `SAP_CORE_BC_APJ_JCE` to the business role created following the steps above, or assign it to a separate business role.

    6.  Select *Save*.

3.  Assign the business role to a user.

    For more information, see [How to Maintain Business Users](How_to_Maintain_Business_Users_db1d0b4.md).




<a name="loiobb559a5a4b654996a167d72273f28542__section_zrj_2wb_s4b"/>

## Assigning Further Authorizations

With the 2105 cloud release, you can access only your own jobs in the *Application Jobs* app. In order to grant access to other users' objects used in the *Application Jobs* app, create a new business role assigning the business catalog `SAP_CORE_BC_APJ_JCE` to it. You can modify the provided restriction types according to your needs.

1.  Create a new business role assigning the business catalog `SAP_CORE_BC_APJ_JCE` to it. The restriction type `Job Catalog Entry/Application Job Part` contains the two fields `Application Job Catalog Entry` and `Application Job Part`. For more information, see [Maintain Business Roles](Maintain_Business_Roles_8980ad0.md).

    > ### Note:  
    > With this restriction type you'll be able to provide the necessary authorizations for certain actions on other users' application jobs, which are based on a specified job catalog entry. With this, you can display the logs of other users' jobs, which are based on this specified job catalog entry.
    > 
    > Alternatively, you can also create a display only-role using this restriction type.

2.  Next, define your business role with the above-mentioned restriction fields `Application Job Catalog Entry` and `Application Job Part`. To do so, select *Maintain Restrictions*. In the `Application Job Catalog Entry` field, you can choose the job catalog entries, and in the `Application Job Part` field, you can choose for which part of a job access should be granted. You can choose the values `JOB` \(Job Details\), `SPOOL` \(Result List\), and `APPLOG` \(Log\) by clicking the *Edit* icon next to the fields.

3.  Go back and select *Save*. Now, you've maintained your business role, and you can assign the role to a business user.


**Related Information**  


[Scheduling an Application Job](Scheduling_an_Application_Job_147d689.md "Find out how to schedule an Application Job.")

