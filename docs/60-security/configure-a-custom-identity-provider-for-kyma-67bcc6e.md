<!-- loio67bcc6e2d4d749659faf3ede1853f19e -->

# Configure a Custom Identity Provider for Kyma

Enable the Kyma environment with a custom identity provider \(IdP\).



<a name="loio67bcc6e2d4d749659faf3ede1853f19e__prereq_fv1_t2l_nrb"/>

## Prerequisites

-   Install [kubectl oidc-login](https://github.com/int128/kubelogin).




## Context

When you create a new instance in the SAP BTP cockpit from the Service Marketplace, you can configure your custom OpenID Connect IdP to authenticate users in your Kyma runtime.

If you've already created your Kyma environment, you can also apply the custom IdP configuration and set up administrators during your Kyma instance update operation by providing the details as an array of strings in the respective fields.

> ### Tip:  
> You can use SAP Cloud Identity Services - Identity Authentication as a custom IdP. Additionally, you can configure Identity Authentication to use a third-party IdP such as Azure Active Directory or Auth0, among others. For more information, see [Integrating the Service with Microsoft Azure AD](https://help.sap.com/docs/identity-authentication/identity-authentication/integrating-service-with-microsoft-azure-ad?version=Cloud) and [Configure Auth0 for SAP BTP, Kyma runtime](https://github.com/SAP-samples/kyma-runtime-extension-samples/tree/main/kyma-access-auth0-as-idp).



## Procedure

1.  In SAP BTP cockpit, navigate to your subaccount.

2.  Go to *Services* \> *Service Marketplace* and select *Kyma Environment*.

3.  In the dialog box, fill in the following additional configuration fields:

    -   *issuerURL* - the URL of the OpenID issuer \(use the `https` schema\)
    -   *clientID* - the client ID for the OpenID client
    -   *usernameClaim* - the name of a custom OpenID Connect claim for specifying a username
    -   *groupsClaim* - the name of a custom OpenID Connect claim for specifying user groups
    -   *signingAlgs* - the list of allowed cryptographic algorithms used for token signing. The allowed values are defined by [RFC 7518](https://tools.ietf.org/html/rfc7518#section-3.1).
    -   *usernamePrefix* - the prefix for all usernames. If you don't provide it, username claims other than “email” are prefixed by the *issuerURL* to avoid clashes. To skip any prefixing, provide the value as `-`.
    -   *administrators* - the list of usernames meant to be administrators. Users identified with those usernames get the role *cluster-admin* during provisioning of your Kyma runtime.

    > ### Note:  
    > You can also provide the configuration as a JSON object:
    > 
    > ```
    >  "oidc": {
    >     "issuerURL": "{issuerURL}",
    >     "clientID": "{clientID}",
    >     "usernameClaim": "sub",
    >     "groupsClaim": "groups",
    >     "signingAlgs": ["RS256"],
    >     "usernamePrefix": "-"
    >   },
    >   "administrators": ["user-admin1", ... ]
    > ```
    > 
    > If you want to revert to the default settings, use the following configuration:
    > 
    > ```
    >  "oidc": {
    >     "issuerURL": "https://kyma.accounts.ondemand.com",
    >     "clientID": "12b13a26-d993-4d0c-aa08-5f5852bbdff6",
    >     "groupsClaim": "groups",
    >     "signingAlgs": ["RS256"],
    >     "usernamePrefix": "-",
    >     "usernameClaim": "sub"
    >   },
    >   "administrators": ["{put usernames (emails) recognised by 'https://kyma.accounts.ondemand.com'}"]
    > ```

4.  Select *Create*.




<a name="loio67bcc6e2d4d749659faf3ede1853f19e__result_qzy_nsz_1pb"/>

## Results

Your Kyma environment is instantiated with a custom IdP.



<a name="loio67bcc6e2d4d749659faf3ede1853f19e__postreq_xjt_s3x_stb"/>

## Next Steps

> ### Caution:  
> According to Oauth2 flows, IdPs have lists of allowed callback URLs. Configure the Kyma dashboard URL \(`https://dashboard.kyma.cloud.sap`\) and the localhost for kubectl authentication \(`http://localhost:8000`\) as allowed callback URLs at your IdP provider, so that authenticated users can be redirected back to the Kyma application.

Access to Kyma is realized using the authorization code flow with PKCE. Therefore, make sure that *Allow Public Client Flows* is enabled in your Identity Authentication tenant. For more information, see [Configure OpenID Connect Application for Authorization Code Flow](https://help.sap.com/docs/IDENTITY_AUTHENTICATION/6d6d63354d1242d185ab4830fc04feb1/4a9425465cbb4a7aa7c3d86c9cabca51.html?locale=en-US&version=Cloud#next-steps), section *Next Steps*.

**Related Information**  


[Authentication and Authorization in the Kyma Environment](authentication-and-authorization-in-the-kyma-environment-85200d8.md "To authenticate in the Kyma environment, you can either use the default identity provider or set up a custom identity provider.")

[Identity Authentication: Initial Setup](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/LATEST/en-US/31af7da133874e199a7df1d42905241b.html)

