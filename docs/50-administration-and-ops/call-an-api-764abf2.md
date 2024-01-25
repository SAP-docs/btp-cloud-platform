<!-- loio764abf29f7624e39ad872f86cbd08fa9 -->

# Call an API

Use the different endpoints of the SAP Authorization and Trust Management service APIs to manage users roles and other authorization configurations.



<a name="loio764abf29f7624e39ad872f86cbd08fa9__context_tls_rnj_d1c"/>

## Context

Actually, you need two separate URLs. First, you need the token URL to fetch an access token. Next, you can use the API URL to call an API.

To call an API of the SAP Authorization and Trust Management service, you need an access token. See the following example how to retrieve an access token and how to call an endpoint with a cURL request.

On the *SAP Business Accelerator Hub*, we provide a sandbox system for you to make example calls to the different APIs and their endpoints.

Use the following API URLs:

`https://api.authentication.<region>.hana.ondemand.com`

> ### Note:  
> To find the region, use a btp CLI command, for example `btp get accounts/subaccount subaccount-id`.



## Procedure

1.  Configure or program your application to request a token from the OAuth authorization server.

    In your call to the OAuth server, you send the client ID and client secret to the token URL appended with the `/oauth/token` endpoint. To illustrate the call, we use cURL in the following example.

    > ### Sample Code:  
    > ```
    > curl --request POST \
    >   --url 'https://my-subdomain.authentication.eu10.hana.ondemand.com/oauth/token' \
    >   --header 'Accept: application/json' \
    >   --data 'client_id=sb-full-access!a76125' \
    >   --data 'client_secret=<secret>' \
    >   --data 'grant_type=client_credentials' \
    >   --data 'response_type=token'
    > ```

    The authorization server returns a token along with other related information.

    > ### Output Code:  
    > ```json
    > {"access_token":"eyJhbGciOiJSUzI1N...",
    > "token_type":"bearer",
    > "expires_in":43199,
    > "scope":"xs_user.write uaa.resource xs_authorization.read
    >  xs_idp.write xs_user.read xs_idp.read xs_authorization.write",
    > "jti":"be340353ac694b4cb504c6823f938647"}
    > ```

2.  To retrieve the token, use the following URL:

    `https://<subdomain>.authentication.<region>.hana.ondemand.com`

    > ### Note:  
    > To find the subdomain of the global account, directory, and subaccount, go to the SAP BTP cockpit and display the overview in the *Account Explorer*.

    When you have a token, you can use this token to call the APIs until its validity expires. In this case, simply get a new access token.

3.  Use the value of the `access_token` property to make calls to the various API endpoints.

4.  Call the endpoint of an API.

    > ### Sample Code:  
    > In this example, we request the list of roles of from the authorization API. With the authorization header, use the access token you received in the prerequisites after the key word `bearer`.
    > 
    > ```
    > curl --request GET \
    >   --url https://api.authentication.eu10.hana.ondemand.com/sap/rest/authorization/v2/roles \
    >   --header 'Accept: application/json' \
    >   --header 'Authorization: bearer eyJhbGciOiJSUzI1N...'
    > ```




<a name="loio764abf29f7624e39ad872f86cbd08fa9__result_i22_3qv_qlb"/>

## Results

The API returns the list of roles.

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


[Authorization and Trust Management APIs on the SAP Business Accelerator Hub](https://api.sap.com/package/authtrustmgmnt?section=Artifacts)

[Implementing Custom Token Retrieval from SAP Authorization and Trust Management Service with mTLS](../30-development/implementing-custom-token-retrieval-from-sap-authorization-and-trust-management-service-w-63fd9f1.md "The application router and other token client libraries take care of getting tokens from the SAP Authorization and Trust Management service for you. If you build your own integration, you must handle token retrieval yourself.")

