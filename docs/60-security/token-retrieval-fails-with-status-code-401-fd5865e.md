<!-- loiofd5865e124ab411790cacc0e72df2852 -->

# Token Retrieval Fails With Status Code 401



## Symptom

You want to retrieve an access token from the Authorization and Trust Management service, but the request fails because of one of the following:

-   Client authentication failed
-   Bad credentials
-   Client with requested ID does not exist
-   The origin provided in *login\_hint* does not match an active Identity Provider \(IdP\) that supports resource-owner password grant flow.



## Reason and Prerequisites

The client or user authentication was not successful. This could happen if the client does not exist or if the client or user credentials are invalid.

-   In the case of client authentication failing, during the authentication, the caller provides the *client\_id* and the *client\_secret*. If these are not correct, an error occurs. This is valid for both technical \(*client\_credentials*\) and user authentication \(e.g. *authorization\_code*\).
-   Bad credentials could be the case in user flows and indicates that the user credentials \(username/password\) are incorrect.
-   If a client with the requested ID does not exist, it signifies that the source of the *clientid* value should be checked*.*

You have to determine whether the issue is related to client or user authentication.

-   For user authentication, verify whether token retrieval works for the `client_credentials` grant type.
-   If not, the issue is related to client authentication.



## Solution



### User authentication

-   Verify that the user and password combination is correct.
    -   Open a browser and log on to the IdP \(e.g. [https://accounts.sap.com](https://accounts.sap.com/)\).
    -   If the login fails, you need to use another user/password combination or you could change your password.

-   In case of a Universal ID user:
    -   Check [Log On to the Cloud Foundry Environment Using the Cloud Foundry Command Line Interface](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/7a37d66c2e7d401db4980db0cd74aa6b.html?locale=en-US&version=Cloud) and especially [SAP Note 3085908](https://launchpad.support.sap.com/#/notes/3085908). You can define a separate password for the SAP ID service user that is linked to the Universal ID user, which you need to use for all the logins that involve the SAP ID service and where you have to provide a user name and password and cannot run the \(redirected\) login flow via the web browser.




### Client authentication

Client authentication



### Secrets

-   Verify that the used secret is valid and that the corresponding binding/service key still exists.
-   Depending on the credential type of the used binding/service key, do one of the following:
    -   `instance-secret`: Ensure that the service instance of the client allows `instance-secret` in its security descriptor \(within `credential-types`\).
    -   `binding-secret`: Ensure that the service instance of the client allows `binding-secret` in its security descriptor \(within `credential-types`\).

-   If the application to which the service instance belongs was subscribed to from another subaccount, ensure that the application or service is onboarded correctly via the SAP SaaS Provisioning service.
-   If the secret contains the *\+* sign:
    -   Ensure that the secret is passed via POST body \(and not in the `Authorization` header\).
    -   If it's not possible to pass the secret via POST body, ensure that the username and password are correctly URL encoded before being passed via the header. Also, you need to set the `X-CF-ENCODED-CREDENTIALS` custom header to `true` to indicate that the Authorization and Trust Management service supports URL-encoded credentials.

-   If you've recently updated to Spring version 5.6 or newer and use a Spring client for the client credential flow:
    -   Set the `X-CF-ENCODED-CREDENTIALS` custom header to `true.`
    -   Customize the Spring client such that it does not URL-encode credentials.




### X.509

-   Verify that the certificate has been passed for authentication and that it is the correct one.
-   Ensure that the service instance of the client allows `x509` in its security descriptor \(within `credential-types`\).
-   If the application to which the service instance belongs was subscribed to from another subaccount, ensure that the application or service is onboarded correctly via the SAP SaaS Provisioning service.
-   For issues with the SSL handshake, create an incident in the [SAP Support Portal](http://help.sap.com/disclaimer?site=https://support.sap.com/home.html).



### No IdP that supports resource-owner password grant flow

-   Resource-owner password grant flow is only supported with OpenID Connect \(OIDC\) IdPs, not SAML.
-   Make sure to use the `sap.default` or `sap.custom` origin key.
-   Origin keys can be checked in the Cockpit, under **Trust Configuration**.

