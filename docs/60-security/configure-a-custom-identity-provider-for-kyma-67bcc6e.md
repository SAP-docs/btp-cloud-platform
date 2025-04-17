<!-- loio67bcc6e2d4d749659faf3ede1853f19e -->

# Configure a Custom Identity Provider for Kyma

Enable the Kyma environment with a custom identity provider \(IdP\).



<a name="loio67bcc6e2d4d749659faf3ede1853f19e__prereq_fv1_t2l_nrb"/>

## Prerequisites

-   Install [kubectl oidc-login](https://github.com/int128/kubelogin). This is also needed when you log in to Kyma dashboard, as the dashboard uses the kubeconfig file, and it requires the kubectl oidc-login tool to work.

-   If you choose to use SAP Cloud Identity Services as custom IdP, you have configured your tenant as OpenID Connect \(OIDC\) provider for your Kyma cluster. For details, see [Configure OpenID Connect Application for Authorization Code Flow](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/auth-code-configure-openid-connect-application-for-authorization-code-flow?version=Cloud).

-   Configure the Kyma dashboard URL \(`https://dashboard.kyma.cloud.sap`\) and the localhost for kubectl authentication \(`http://localhost:8000`\) as allowed callback URLs at your IdP provider, so that authenticated users can be redirected back to the Kyma application. See [Redirect URIs, Post Logout Redirect URI Rules](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/redirect-uris-post-logout-redirect-uri-rules?version=Cloud).


> ### Tip:  
> It is recommended to use SAP Cloud Identity Services tenant as a custom IdP. It allows you to use SAP Cloud Identity Services as a proxy to integrate your corporate identity provider. See [Get Your Tenant](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/get-your-tenant?version=Cloud). You could also configure SAP Cloud Identity Services to use a third-party IdP if you already have one.



## Context

When you create a new Kyma instance in the SAP BTP cockpit from the Service Marketplace, you can configure your custom OpenID Connect IdP to authenticate users in your Kyma runtime.

If you've already created your Kyma environment, you can also apply the custom IdP configuration and set up administrators during your Kyma instance update operation by providing the details as an array of strings in the respective fields.



## Procedure

1.  Go to *Services* \> *Service Marketplace* and [Creating a Kyma Instance](../50-administration-and-ops/creating-a-kyma-instance-09dd313.md).

2.  In the *Parameters* view, fill in the following information:

    -   *issuerURL* - the URL of the OpenID issuer \(use the `https` schema\)
    -   *clientID* - the client ID for the OpenID client
    -   *usernameClaim* - the name of a custom OpenID Connect claim for specifying a username
    -   *groupsClaim* - the name of a custom OpenID Connect claim for specifying user groups

        > ### Note:  
        > An identity provider token consists of fields \(claims\) that are included in it. For example:
        > 
        > ```
        > {
        > sub: "john.doe@sap.com"
        > groups: ["SAP fans", "Identity Provider", "OpenID"]
        > }
        > ```
        > 
        > When you configure `usernameClaim`, Kubernetes knows which field \(claim\) includes the user represented by a given token.
        > 
        > Similarly, when you configure `groupsClaim`, Kubernetes knows to which groups the user is assigned.

    -   *signingAlgs* - the list of allowed cryptographic algorithms used for token signing. The allowed values are defined by [RFC 7518](https://tools.ietf.org/html/rfc7518#section-3.1).
    -   *usernamePrefix* - the prefix for all usernames. If you don't provide it, username claims other than “email” are prefixed by the *issuerURL* to avoid clashes. To skip any prefixing, provide the value as `-`.
    -   *administrators* - the list of usernames meant to be administrators. Users identified with those usernames get the role *cluster-admin* during provisioning of your Kyma runtime.

    You can also provide the configuration as a JSON object:

    ```
     "oidc": {
        "issuerURL": "{issuerURL}",
        "clientID": "{clientID}",
        "usernameClaim": "sub",
        "groupsClaim": "groups",
        "signingAlgs": ["RS256"],
        "usernamePrefix": "-"
      },
      "administrators": [
        "example_1@mail.com",
        "example_2@mail.com"
      ]
    ```

    > ### Note:  
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
    >   "administrators": [
    >     "example_3@mail.com",
    >     "example_4@mail.com"
    >   ]
    > ```
    > 
    > The email addresses must be recognized by `https://kyma.accounts.ondemand.com`.

3.  Select *Create*.




<a name="loio67bcc6e2d4d749659faf3ede1853f19e__result_qzy_nsz_1pb"/>

## Results

Your Kyma environment is instantiated with a custom IdP.

**Related Information**  


[Authentication in the Kyma Environment](authentication-in-the-kyma-environment-85200d8.md "To authenticate in the Kyma environment, you can either use the default identity provider (IdP) or set up a custom identity provider.")

