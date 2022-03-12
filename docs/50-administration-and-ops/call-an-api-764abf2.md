<!-- loio764abf29f7624e39ad872f86cbd08fa9 -->

# Call an API

Use the different endpoints of the Authorization and Trust Management service APIs to manage users roles and other authorization configurations.



<a name="loio764abf29f7624e39ad872f86cbd08fa9__prereq_zty_2kw_qlb"/>

## Prerequisites

To call an API of the Authorization and Trust Management Service you need to obtain an access token. See [Access UAA Admin APIs](access-uaa-admin-apis-ebc9113.md) to learn how to obtain an access token. See the following example how to call an endpoint with a curl request.

> ### Tip:  
> On the API Business Hub, a sandbox system is provided for you to make example calls to the different APIs and their endpoints.



## Procedure

1.  Call the roles endpoint of the authorization API.

    > ### Sample Code:  
    > In this example, we request the list of roles of an XSUAA configuration.
    > 
    > ```
    > curl --request GET \
    >   --url https://api.authentication.eu10.hana.ondemand.com/sap/rest/authorization/v2/roles \
    >   --header 'Accept: application/json' \
    >   --header 'Authorization: bearer eyJhbGciOiJSUzI1N...' \
    >   --header 'Content-Type: application/x-www-form-urlencoded' \
    >   --header 'cache-control: no-cache'
    > ```




<a name="loio764abf29f7624e39ad872f86cbd08fa9__result_i22_3qv_qlb"/>

## Results

The client returns the list of roles.

> ### Output Code:  
> ```json
> [
>     {
>         "roleTemplateName": "Viewer",
>         "roleTemplateAppId": "myapp!t1111",
>         "name": "Viewer",
>         "attributeList": [],
>         "roleCapabilityIDList": [],
>         "description": "Default instance",
>         "scopes": [
>             {
>                 "description": "Display forecast",
>                 "name": "myapp!t1111.Tourist",
>                 "custom-granted-apps": [],
>                 "granted-apps": [],
>                 "grant-as-authority-to-apps": [],
>                 "custom-grant-as-authority-to-apps": []
>             }
>         ]
>     }
> ]
> ```

**Related Information**  


[Authorization and Trust Management APIs on the API Business Hub](https://api.sap.com/package/authtrustmgmnt?section=Artifacts)

