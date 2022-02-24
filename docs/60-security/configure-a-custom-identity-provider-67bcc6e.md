<!-- loio67bcc6e2d4d749659faf3ede1853f19e -->

# Configure a Custom Identity Provider

Enable the Kyma environment with a custom identity provider.



<a name="loio67bcc6e2d4d749659faf3ede1853f19e__prereq_fv1_t2l_nrb"/>

## Prerequisites

-   Your cluster is running Kyma version 2.0 or higher.

-   Install [kubectl oidc-login](https://github.com/int128/kubelogin).




## Context

When you create a new Kyma environment instance in the SAP BTP cockpit from the Service Marketplace, you can configure your custom OpenID Connect IdP to authenticate users in your Kyma runtime.



## Procedure

1.  Navigate to your subaccount.

2.  Go to *Services* \> *Service Marketplace* and select *Kyma Environment*.

3.  In the pop-up window, fill in the following additional configuration fields:

    -   *issuerURL* - the URL of the OpenID issuer \(use the `https` schema\)
    -   *clientID* - the client ID for the OpenID client
    -   *usernameClaim* - the name of a custom OpenID Connect claim for specifying a username
    -   *groupsClaim* - the name of a custom OpenID Connect claim for specifying user groups
    -   *signingAlgs* - the list of allowed cryptographic algorithms used for token signing. The allowed values are defined by [RFC 7518](https://tools.ietf.org/html/rfc7518#section-3.1).
    -   *usernamePrefix* - the prefix for all usernames. If you don't provide it, username claims other than 'email' are prefixed by the *issuerURL* to avoid clashes. To skip any prefixing, provide the value as *"-"*.
    -   *administrators* - the list of usernames meant to be administrators. Users identified with those usernames will be granted the *cluster-admin* role during provisioning of your Kyma runtime.

    You can also provide the configuration as a JSON object:

    ```
     "oidc": {
        "issuerURL": "{issuerURL}",
        "clientID": "{clientID}",
        "usernameClaim": "email",
        "groupsClaim": "groups",
        "signingAlgs": ["RS256"],
        "usernamePrefix": "-"
      }
      "administrators": ["user-admin1", ... ]
    ```

4.  Select *Create*.




<a name="loio67bcc6e2d4d749659faf3ede1853f19e__result_qzy_nsz_1pb"/>

## Results

Your Kyma environment will be instantiated with a custom IdP.

> ### Caution:  
> According to Oauth2 flows, IdPs have lists of allowed callback URLs. Configure the Kyma Console/Dashboard URL \(`https://dashboard.kyma.cloud.sap/`\) and the localhost for kubectl authentication \(`http://localhost:8000`\) as allowed callback URLs at your IdP provider so that authenticated users could be redirected back to the Kyma application.

> ### Note:  
> You can also apply the custom IdP configuration and set up administrators during your Kyma instance update operation by providing the details as an array of strings in the respective fields.

**Related Information**  


[Authentication and Authorization in the Kyma Environment](authentication-and-authorization-in-the-kyma-environment-85200d8.md "Kyma allows you to use the default or a custom Identity Provider to authenticate in the Kyma environment.")



[Identity Authentication: Initial Setup](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/LATEST/en-US/31af7da133874e199a7df1d42905241b.html)

