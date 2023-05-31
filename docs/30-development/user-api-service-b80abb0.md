<!-- loiob80abb01ef084bc098636348b1d618af -->

# User API Service

The application router exposes a user API that returns the details of the users who are logged in to the application.

You implement the user API by modelling an [xs-app.json route](routes-666eb55.md).

The user API supports two endpoints:

-   `/currentUser` returns all details of logged in users.

-   `/attributes` returns the main user properties.


The `/currentUser` endpoint response has the following format:

> ### Sample Code:  
> ```
> ```
> {
>    "firstname": "John",
>    "lastname": "Doe",
>    "email": "john.doe@sap.com",
>    "name": "john.doe@sap.com",
>    "displayName": "John Doe (john.doe@sap.com)" (The user ID in the identity provider),
>    "scopes": ["openid","user_attributes","uaa.user"] (Only if the authentication type is “xsuaa")
> }
> ```
> 
> ```

The `/attributes` endpoint response has the following format:

> ### Sample Code:  
> ```
> ```
> {
>    "firstname": "John",
>    "lastname": "Doe",
>    "email": "john.doe@sap.com",
>    "name": "john.doe@sap.com" (The user ID in the identity provider), 
>    "scopes": ["openid","user_attributes","uaa.user"] (Only if the the authentication type is “xsuaa"),
>    < user attributes including custom attributes > (Only if the the authentication type is “xsuaa")
> }
> ```
> 
> ```

> ### Note:  
> The `"name"` property is the user ID in the identity provider, which in many cases is also the email address.

> ### Note:  
> If you specify “xsuaa” as the authentication type for the route, the following applies:
> 
> -   User scopes from the xsuaa access token are added to the response of both endpoints \(`/currentUser` and `/attributes` \).
> 
> -   User attributes from the identity provider \(IdP\) chosen for the authentication are added to the response of the `/attributes` endpoint. If a custom IdP is configured for Identity Authentication Service \(IAS\), the custom user attributes are also added to the response of the `/attributes` endpoint. For more information about the definition of custom properties in IAS, see [Configure the Default Attributes Sent to the Application](https://help.sap.com/docs/identity-authentication/identity-authentication/configure-default-attributes-sent-to-application?version=Cloud).
> 
> -   To get the user attributes from the custom IdP, add the following property to xs-security.json file of the application router: `"foreign-scope-references": ["user_attributes"]`



<a name="loiob80abb01ef084bc098636348b1d618af__section_stt_pmg_p4b"/>

## Configuring the User API Service in the Routing Configuration File

You implement the user API by modelling an [xs-app.json route](routes-666eb55.md) using the `sap-approuter-userapi` service .

The following example handles both endpoints:

> ### Sample Code:  
> ```
> {
>     "source": "^/user-api(.*)",
>     "target": "$1",
>     "service": "sap-approuter-userapi"
> }
> 
> ```

The following example uses only the `/currentUser` endpoint:

> ### Sample Code:  
> ```
> {
>     "source": "^/user-api/currentUser$",
>     "target": "/currentUser",
>     "service": "sap-approuter-userapi"
> }
> ```

**Related Information**  


[routes](routes-666eb55.md "Defines all route objects, for example: source, target, and, destination.")

