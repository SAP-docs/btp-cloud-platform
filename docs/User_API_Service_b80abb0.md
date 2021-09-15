<!-- loiob80abb01ef084bc098636348b1d618af -->

# User API Service

The application router exposes a user API that returns the details of the users who are logged in to the application.

The user API supports two endpoints:

-   `/currentUser` : returns all details of logged in users

-   `/attributes`: returns the main user properties


The`/currentUser` endpoint response has the following format:

> ### Sample Code:  
> ```
> ```
> {
>    "firstname": "John",
>    "lastname": "Doe",
>    "email": "john.doe@sap.com",
>    "name": "john.doe@sap.com",
>    "displayName": "John Doe (john.doe@sap.com)"
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
>    "name": "john.doe@sap.com"
> }
> ```
> 
> ```

> ### Note:  
> The `"name"` property is the user ID in the identity provider, which in many cases is also the email address.



<a name="loiob80abb01ef084bc098636348b1d618af__section_stt_pmg_p4b"/>

## Configuring the User API Service in the Routing Configuration File

The user API can be implemented by modelling an [xs-app.json route](routes_666eb55.md) using the `sap-approuter-userapi` service .

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


[routes](routes_666eb55.md "Defines all route objects, for example: source, target, and, destination.")

