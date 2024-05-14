<!-- loioac889df1f09245568e129eb5dd9aafd0 -->

# Example: Group Endpoint



Please find an example of a group endpoint below:

> ### Sample Code:  
> ```
> {
>   "schemas" : [
>     "urn:ietf:params:scim:schemas:core:2.0:Group",
>     "urn:ietf:params:scim:schemas:extension:sap:2.0:Group"
>   ],
>   "id" : "BROL_BUSINESSROLE1",
>   "externalId" : "BUSINESSROLE1",
>   "displayName" : "business role 1",
>   "members" : [
>     {
>       "value" : "CB0000000001",
>       "$ref" : "https://system.com/sap/bc/http/sap/aps_iam_api_scim/Users/CB0000000001",
>       "display" : "John Doe"
>     }
>   ],
>   "urn:ietf:params:scim:schemas:extension:sap:2.0:Group" : {
>     "type" : "authorization",
>     "supportedOperations" : "membership"
>   },
>   "meta" : {
>     "resourceType" : "Group",
>     "created" : "2018-12-11T19:18:05Z",
>     "lastModified" : "2021-09-08T12:38:32Z",
>     "version" : "20210908123832",
>     "location" : "https://system.com/sap/bc/http/sap/aps_iam_api_scim/Groups/BROL_BUSINESSROLE1
>   }
> }
> 
> ```

