<!-- loiod69daf4f6168459b9f18c0d805a084ad -->

# Example: User Endpoint



Please find an example of a user endpoint below:

> ### Sample Code:  
> ```
> {
>   "schemas" : [
>     "urn:ietf:params:scim:schemas:core:2.0:User",
>     "urn:ietf:params:scim:schemas:extension:sap:2.0:User"
>   ],
>   "id" : "CB0000000001",
>   "externalId" : "WORKER_ID",
>   "userName" : "JOHN_DOE",
>   "name" : {
>     "formatted" : "John Doe",
>     "familyName" : "Doe",
>     "givenName" : "John"
>   },
>   "displayName" : "John Doe",
>   "emails" : [
>     {
>       "value" : "john.doe@sap.com",
>       "type" : "work",
>       "primary" : true
>     }
>   ],
>   "phoneNumbers" : [
>     {
>       "value" : "+123456789",
>       "type" : "work"
>     },
>     {
>       "value" : "+987654321",
>       "type" : "mobile"
>     }
>   ],
>   "userType" : "Employee",
>   "preferredLanguage" : "E",
>   "timezone" : "CET",
>   "active" : true,
>   "groups" : [
>     {
>       "value" : "BUGR_ZCBUSERGROUP",
>       "$ref" : "https://system.com/sap/bc/http/sap/aps_iam_api_scim/Groups/BUGR_ZCBUSERGROUP",
>       "display" : "business user group",
>       "type" : "userGroup"
>     },
>     {
>       "value" : "BROL_BUSINESSROLE1",
>       "$ref" : "https://system.com/sap/bc/http/sap/aps_iam_api_scim/Groups/BROL_BUSINESSROLE1",
>       "display" : "business role 1",
>       "type" : "authorization"
>     },
>     {
>       "value" : "BROL_BUSINESSROLE2",
>       "$ref" : "https://system.com/sap/bc/http/sap/aps_iam_api_scim/Groups/BROL_BUSINESSROLE2",
>       "display" : "business role 2",
>       "type" : "authorization"
>     }
>   ],
>   "urn:ietf:params:scim:schemas:extension:sap:2.0:User" : {
>     "userUuid" : "GLOBAL_USER_ID"
>   },
>   "meta" : {
>     "resourceType" : "User",
>     "created" : "2015-05-22T12:53:56Z",
>     "lastModified" : "2015-05-22T12:53:56Z",
>     "version" : "20150522125356",
>     "location" : "https://system.com/sap/bc/http/sap/aps_iam_api_scim/Users/CB0000000001"
>   }
> }
> 
> ```

