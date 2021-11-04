<!-- loioeeb99e99924242529b9624c6478a5055 -->

# Maintaining Authorizations

Find out which authorizations you need to maintain in order to use the *Application Job Templates* app.



<a name="loioeeb99e99924242529b9624c6478a5055__MaintainingAuthorizations_context"/>

## Context

In order to grant access and authorizations to the *Application Job Templates* app, create a new business role assigning the business catalog `SAP_CORE_BC_APJ_TPL` to it.



<a name="loioeeb99e99924242529b9624c6478a5055__MaintainingAuthorizations_steps"/>

## Procedure

1.  Create a new business role assigning the business catalog `SAP_CORE_BC_APJ_TPL` to it. For more information, see *Maintain Business Roles* linked below.

2.  Next, select *Maintain Restrictions* to provide *Write*, *Read*, or *No Access* to templates using the restriction type `APPLICATION JOB TEMPLATE LAYER`.

3.  Go back to *Save* your template.

    > ### Note:  
    > You will always be able to see your own templates and the templates delivered by your software provider without having to maintain further authorizations.

    > ### Note:  
    > The possible values for the layer field are *Global*, *Shared*, and *Private*. These are described in *Application Job Templates* linked below. The restriction type *Global* is predelivered by SAP and therefore can't be edited or deleted, but you can modify the restriction types *Shared* and *Private* to your needs.


**Related Information**  


[Maintain Business Users](Maintain_Business_Users_e40e710.md "You use this app to provide business users with access rights and to maintain business user settings.")

[Maintain Business Roles](Maintain_Business_Roles_8980ad0.md "You can use this app to create and edit business roles, add business catalogs to the roles, and maintain access restrictions.")

[Application Job Templates](Application_Job_Templates_9c930d5.md)

