<!-- loio9cad9e3967b540d3bfdf140302c1ac64 -->

# Use Foreign Scope Option for Principal Propagation with Tightly Coupled Developments

With foreign scope reference, configure the business application to accept new scopes for the service without having to modify the business application.



<a name="loio9cad9e3967b540d3bfdf140302c1ac64__steps_clw_yyc_h4b"/>

## Procedure

1.  As the service developer, add the attribute `granted-apps` to scopes you want to share with other business applications in the `scopes` section of the `xs-security.json` for this service.

    In this attribute, list the names of the applications \(`xsappname`\) you want to share the scope with.

    > ### Sample Code:  
    > ```lang-json
    > "scopes": [
    > 	{
    > 		"name"                 : "$XSAPPNAME.Read",
    > 		"description"          : "read",
    > 		"granted-apps"         : ["$XSAPPNAME(application,appa)" ] 
    > 	},	
    > 	{
    > 		"name"                 : "$XSAPPNAME.Approve",
    > 		"description"          : "approval",
    > 	}
    >            ]
    > ```

    In this example, we have defined two scopes, `Read` and `Approve`. Under `granted-apps`, we list the application names with which we want to share the `Read` scope. All apps listed here can consume this scope in their role templates.

    > ### Note:  
    > `$XSAPPNAME` is replaced at runtime with the application name. The parameters that follow `$XSAPPNAME` are the service plan for the XSUAA service and `xsappname` as defined in the `xs-security.json`. These parameters help uniquely identify other applications in the subaccount.

    You might reserve the `Editor` scope for a role template for the service. The editor role is only meant for administrators.

2.  Create the UAA service instance for service B.

    For example:

    ***cf create-service xsuaa application servb-uaa -c /servb/security/xs-security.json***

3.  In the business application, accept all foreign scope references.

    > ### Sample Code:  
    > ```
    > {
    >  "xsappname": "appa",
    >  "tenant-mode": "shared",
    >  "description": "Application ecurity descriptor for application A",
    >  "foreign-scope-references": ["$ACCEPT_GRANTED_SCOPES"],             
    >  "scopes"        : [
    >                         {
    >                           "name"                 : "$XSAPPNAME.View",
    >                           "description"          : "View data"
    >                         }
    >                       ],
    >     "role-templates": [
    >                         {
    >                           "name"                 : "View",
    >                           "description"          : "View data",
    >                           "scope-references"     : [
    >                                                         "$XSAPPNAME.View"
    >                                                    ]                                            
    >                         }
    >     ]
    > }
    > ```

    Under `foreign-scope-references`, the application security descriptor accepts any and all foreign scopes that were granted to it. You can limit the references to just those applications you want to accept. For example, `"$XSAPPNAME(application,servb).Read`

4.  Create the UAA service instance for application A.

    For example:

    ***cf create-service xsuaa application appa-uaa -c /appa/security/xs-security.json***

5.  Deploy the developments.

6.  As an adminístrator, create a role from the role template from business application A and assign the role to a user.

    Only assign the `Viewer` template from business application A to your test user and no templates from service B.

    For more information, see [Administration: Managing Authentication and Authorization](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/1ff47b2d980e43a6b2ce294352333708.html).

7.  As an end user, test business application A.

    Your test user can use the scopes delivered from the `Viewer` template to access business application A or service B directly or indirectly.


**Related Information**  


[Principal Propagation with Tightly Coupled Developments](PP_closely_coupled.md "A scenario is tightly coupled when a business application calls a service within the same subaccount in the Cloud Foundry environment. The business application calls the service with principal propagation, meaning information about the current user is carried over with the service call.")

