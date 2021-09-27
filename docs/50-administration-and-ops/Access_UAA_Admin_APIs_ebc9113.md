<!-- loioebc9113a520e495ea5fb759b9a7929f2 -->

# Access UAA Admin APIs

To enable programmatic access to the XS user authentication and authorization \(UAA\) service in your subaccount of the Cloud Foundry environment, create an XSUAA service instance under the `apiaccess` plan.



<a name="loioebc9113a520e495ea5fb759b9a7929f2__prereq_vnx_csb_fhb"/>

## Prerequisites

-   You have the role *User & Role Administrator* for the subaccount where you want to enable API access. This role ensures that you have the required scopes:

    -   `xs_authorization.read`
    -   `xs_authorization.write`
    -   `xs_idp.read`
    -   `xs_idp.write`
    -   `xs_user.read`
    -   `xs_user.write`
-   You have an org and a space where you can create a service instance.




## Context

One use case for this scenario is to use your own identity management system to integrate it with SAP BTP. The API is a RESTful API that includes access to authorization, user, group, and identity provider interfaces. The user, group, and identity provider interfaces use System for Cross-domain Identity Management \(SCIM\) protocol.

For more information about the available APIs, see [https://api.sap.com/package/authtrustmgmnt](https://api.sap.com/package/authtrustmgmnt) on *SAP API Business Hub*.



## Procedure

1.  Navigate to the space of your subaccount.

    Enter the following command:

    ***cf target -o *<org\_name\>* -s *<space\_name\>****

    For example:

    `cf target -o my-org -s DEV`

2.  In your subaccount, create a service instance of the UAA with the `apiaccess` plan.

    Enter the following command:

    ***cf create-service xsuaa apiaccess *<access\_name\>****

    For example:

    `cf create-service xsuaa apiaccess my-access`

    This command creates an entry for the OAuth client in the database of the cloud controller.

3.  Create a service key.

    Enter the following command:

    ***cf create-service-key *<access\_name\>* *<key\_name\>****

    For example:

    `cf create-service-key my-access my-access-key`

    The system writes the credentials for the OAuth client to the service key.

4.  Get the credentials for the OAuth client.

    Enter the following command:

    ***cf service-key *<access\_name\>* *<key\_name\>****

    For example:

    `cf service-key my-access my-access-key`

    The system answers similar to the following:

    > ### Output Code:  
    > ```nocode
    > Getting key my-access-key for service instance my-access as my-user...
    > 
    > {
    >  "apiurl": "https://api.authentication.eu10.hana.ondemand.com",
    >  "clientid": "aa-bb-cccc11c1-d222-333e-44f4-g5g55ggg555g!a6666",
    >  "clientsecret": "aA1B2CcCCC3dDd+ee444fFF5ggG=",
    >  "identityzone": "my-subdomain",
    >  "identityzoneid": "a11aaaa1-22b2-33c3-dd44-5555f5555f55",
    >  "sburl": "https://internal-xsuaa.authentication.eu10.hana.ondemand.com",
    >  "tenantid": "a11aaaa1-22b2-33c3-dd44-5555f5555f55",
    >  "tenantmode": "dedicated",
    >  "uaadomain": "authentication.eu10.hana.ondemand.com",
    >  "url": "https://my-subdomain.authentication.eu10.hana.ondemand.com",
    >  "verificationkey": "-----BEGIN PUBLIC KEY-----sadklfjdsaflja
    > 	...-----END PUBLIC KEY-----",
    >  "xsappname": "aa-bbbb11b1-c222-333d-44e4-f5f55fff555f!a6666"
    > }
    > ```

    With the URL, client ID, and client secret, you can get the access token. With the access token and the ***apiurl***, you have access to the API.

5.  Configure or program your application to get a token from the OAuth client.

    In your call to the OAuth client, you send the client ID and client secret, separated with a colon \(:\) and base64 encoded to the URL from the service key.

    > ### Sample Code:  
    > ```nocode
    > curl --request POST \
    >   --url https://my-subdomain.authentication.eu10.hana.ondemand.com/oauth/token \
    >   --header 'Accept: application/json' \
    >   --header 'Authorization: Basic eW91ckNsaWVudElEOnlvdXJDbGllbnRTZWNyZXQ' \
    >   --header 'cache-control: no-cache' \
    >   --data 'grant_type=client_credentials&response_type=token'
    > ```

    The client returns a token.

    > ### Output Code:  
    > ```lang-json
    > {"access_token":"eyJhbGciOiJSUzI1N...",
    > "token_type":"bearer",
    > "expires_in":43199,
    > "scope":"xs_user.write uaa.resource xs_authorization.read
    >  xs_idp.write xs_user.read xs_idp.read xs_authorization.write",
    > "jti":"be340353ac694b4cb504c6823f938647"}
    > ```

6.  Use the value of the parameter `access_token` to make calls to the various API endpoints. For an example, see [Call an API](Call_an_API_764abf2.md).


**Related Information**  


[https://docs.cloudfoundry.org/devguide/services/service-keys.html](https://docs.cloudfoundry.org/devguide/services/service-keys.html)

[SAP Note 2760424 - API Access to xsuaa Configuration Data](https://launchpad.support.sap.com/#/notes/2760424)

[https://api.sap.com](https://api.sap.com)

