<!-- loio783809d7e52f4e14a45945f3f2bad751 -->

# Accessing Business Service Data

This section describes how the application router accesses the Business Service data.

To access Business Service data, the `xs-app.json` file should have a route referencing a specific `sap.cloud.service` or `sap.cloud.service.alias` via the service attribute. If an endpoint attribute is also modeled, it will be used to get the service URL; otherwise the fallback URL or URI attribute will be used.

> ### Sample Code:  
> ```
> "routes": [
>     {
>       "source": "^/odata/v2/(.*)$",
>       "target": "$1",
>       "service": "com.sap.appbasic.country",
>       "endpoint": "countryservice"
>     },
> 
> ```

In order to support JWT token exchange, the login JWT token should contain the `uaa.user` scope. This requires that the `xs-security` configuration file contain a role template that references the `uaa.user` scope.

> ### Sample Code:  
> ```
> {
>     "xsappname"   : "simple-approuter",
>     "tenant-mode" : "shared",
>     "scopes": [
>         {
>             "name": "uaa.user",
>             "description": "UAA"
>         },
>         {
>             "name": "$XSAPPNAME.simple-approuter.admin",
>             "description": "Simple approuter administrator"
>         }
>     ],
>     "role-templates": [
>         {
>             "name": "Token_Exchange",
>             "description": "UAA",
>             "scope-references": [
>                 "uaa.user"
>             ]
>         },
>         {
>             "name": "simple-approuter-admin",
>             "description": "Simple approuter administrator",
>             "scope-references": [
>                 "$XSAPPNAME.simple-approuter.admin"
>             ]
>         }
>     ]
> }
> ```

**Related Information**  


[Integration with Business Services](Integration_with_Business_Services_f6337cd.md "Application router supports integration with Business Services, which are a flavor of reuse-services.")

[Accessing Business Service UI](Accessing_Business_Service_UI_0f1f92e.md "This section provides information about accessing Business Services UIs that are stored in HTML5 Application Repository.")

