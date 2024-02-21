<!-- loio171039b7300345cb81392ba058db5dd4 -->

# Maintaining Authorizations

Find out which authorizations you need to maintain in order to use the *Application Jobs* app.



<a name="loio171039b7300345cb81392ba058db5dd4__context_tdc_yty_q4b"/>

## Context

To change access to the objects of other users used in the *Application Jobs* app, create a new business role assigning the business catalog `SAP_CORE_BC_APJ_JCE` to it. You can modify the provided restriction types according to your needs.



<a name="loio171039b7300345cb81392ba058db5dd4__steps_udc_yty_q4b"/>

## Procedure

1.  Create a new business role assigning the business catalog `SAP_CORE_BC_APJ_JCE` to it. The restriction type `Job Catalog Entry/Application Job Part` contains the two fields `Application Job Catalog Entry` and `Application Job Part`. For more information, see [Maintain Business Roles](maintain-business-roles-365b0d6.md).

    > ### Note:  
    > With this restriction type, you'll be able to provide the necessary authorizations for certain actions on the application jobs of other users that are based on a specified job catalog entry. You can display the result lists of these application jobs.
    > 
    > Alternatively, you can also create a display only-role using this restriction type.

2.  Next, define your business role with the restriction fields `Application Job Catalog Entry` and `Application Job Part` mentioned above. To do so, select *Maintain Restrictions*. In the `Application Job Catalog Entry` field, you can choose the job catalog entries, and in the `Application Job Part` field, you can choose for which job part access should be granted. You can choose the values `JOB` \(Job Details\), `SPOOL` \(Result List\), and `APPLOG` \(Log\) by clicking the *Edit* icon next to the fields.

3.  If you want to have different business users for the job owner and the job user, the job owner needs the authorization to schedule the application job for the job user. In this case, the job owner needs the restriction type `Create Application Jobs for Other Users`.

4.  Go back and select *Save*. Now, you've maintained your business role, and you can assign the role to a business user. For more information on authorizations, see [3028505](https://me.sap.com/notes/3028505).

    > ### Note:  
    > The private templates of other users aren't shown in the *Application Jobs* app, even if the authorization to view these private templates was granted via `SAP_CORE_BC_APJ_TPL`. You can view the private templates of other users only in the *Application Job Templates* app. For more information, see [Application Job Templates](application-job-templates-9c930d5.md).


**Related Information**  


[Maintain Business Users](maintain-business-users-e40e710.md "You use this app to provide business users with access rights and to maintain business user settings.")

[Maintain Business Roles](maintain-business-roles-365b0d6.md)

