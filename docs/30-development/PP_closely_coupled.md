<!-- loio5ad748d634254363b2f0cb2b9679ac6f -->

# Principal Propagation with Tightly Coupled Developments

A scenario is tightly coupled when a business application calls a service within the same subaccount in the Cloud Foundry environment. The business application calls the service with principal propagation, meaning information about the current user is carried over with the service call.



<a name="loio5ad748d634254363b2f0cb2b9679ac6f__context_aqj_zrb_4fb"/>

## Context

The figure that follows illustrates this scenario.

> ### Note:  
> With service, we do not mean a development that has been registered as a service with the Cloud Controller, but rather the role one application takes in relationship to another. Both developments can be applications, but one application takes on the role of a business application enabling business users to perform tasks. The other application plays the role of a service, enabling the development of the business application.
> 
> We also assume that both applications have their own application router. Having separate application routers means that the applications can define their own authorization models.

   
  
<a name="loio5ad748d634254363b2f0cb2b9679ac6f__fig_r3v_rfl_p2b"/>Two Applications, Tightly Coupled Using Principal Propagation

 ![](images/app_plan_named_user_pptx_70172fa.png "Two Applications, Tightly Coupled Using Principal Propagation") 

In this scenario, we enable the service to accept the JSON Web Token \(JWT\) of the business application. The JWT of the business application includes the scopes of both developments. When the service receives a JWT of the business application with the scopes of the service in it, the service implicitly accepts the JWT of the business application. This configuration is part of the `xs-security.json` of the UAA service instances of the two developments.



<a name="loio5ad748d634254363b2f0cb2b9679ac6f__steps_trq_csb_4fb"/>

## Procedure

1.  As the service developer, add the attribute `granted-apps` to scopes you want to share with other business applications in the `scopes` section of the `xs-security.json` for this service.

    In this attribute, list the names of the applications \(`xsappname`\) you want to share the scope with.

    > ### Sample Code:  
    > ```lang-json
    > "scopes": [
    > 	{
    > 		"name"                 : "$XSAPPNAME.Viewer",
    > 		"description"          : "View log",
    > 		"granted-apps"         : ["$XSAPPNAME(application,appa)" ] 
    > 	},	
    > 	{
    > 		"name"                 : "$XSAPPNAME.Editor",
    > 		"description"          : "view and write logs",
    > 	}
    >            ]
    > ```

    In this example, we have defined two scopes, `Viewer` and `Editor`. Under `granted-apps`, we list the application names with which we want to share the `Viewer` scope. All apps listed here can consume this scope in their role templates.

    > ### Note:  
    > `$XSAPPNAME` is replaced at runtime with the application name. The parameters that follow `$XSAPPNAME` are the service plan for the XSUAA service and `xsappname` as defined in the `xs-security.json`. These parameters help uniquely identify other applications in the subaccount.

    You might reserve the `Editor` scope for a role template for the service. The editor role is only meant for administrators.

2.  Create the UAA service instance for service B.

    For example:

    ***cf create-service xsuaa application servb-uaa -c /servb/security/xs-security.json***

3.  As the business application developer, add scope references to the scope of the service in the `role-templates` section of the `xs-security.json` in business application A.

    > ### Sample Code:  
    > ```lang-json
    > "role-templates": [
    >     {
    >         "name"             : "Viewer",
    >         "description"      : "View all data of the service",
    >         "scope-references" : [
    >                                "$XSAPPNAME.Display",
    >                                "$XSAPPNAME(application,servB).Viewer"
    >                              ]
    >     }
    >                    ]
    > ```

    Under `role-templates`, the `Viewer` template includes a reference to the `Viewer` scope of service B. This reference enables administrators to assign a single role to a user to grant authorizations for both applications.

4.  Create the UAA service instance for application A.

    For example:

    ***cf create-service xsuaa application appa-uaa -c /appa/security/xs-security.json***

5.  Deploy the developments.

6.  As an adminístrator, create a role from the role template from business application A and assign the role to a user.

    Only assign the `Viewer` template from business application A to your test user and no templates from service B.

    For more information, see [Administration: Managing Authentication and Authorization](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/1ff47b2d980e43a6b2ce294352333708.html).

7.  As an end user, test access business application A.

    Your test user can use the scopes delivered from the `Viewer` template to access business application A or service B directly or indirectly.


