<!-- loiof117cab6b92d438cb2a0b5204713994b -->

# Security Considerations for the SAP Authorization and Trust Management Service

Decisions you make when using or administrating the SAP Authorization and Trust Management service \(XSUAA\) can have an impact on the security of your applications. The information provided is meant to help you decide.

**Related Information**  


[Configuration Options for the SAP Authorization and Trust Management Service](configuration-options-for-the-sap-authorization-and-trust-management-service-3654087.md#loio3654087e15864b49a1bca3967a54a095 "The following configuration options enable you to manipulate the operation of the SAP Authorization and Trust Management service (XSUAA). Set these options in the application security descriptor (xs-security.json) at design time for your application.")

 <a name="loioea351dd76f8946c995145bc6a4b235f3"/>

<!-- loioea351dd76f8946c995145bc6a4b235f3 -->

## Implications of Using IFrames

By default, login pages of the SAP Authorization and Trust Management service can’t be framed by other applications for security reasons.

As the security administrator of a subaccount, you can allow the embedding of the login page of the SAP Authorization and Trust Management service in an iFrame.

To configure the trusted domains, use one of the following methods:

-   Enter trusted domains in SAP BTP cockpit.

    For more information, see [Configure Trusted Domains for SAP Authorization and Trust Management Service \[Feature Set B\]](../50-administration-and-ops/configure-trusted-domains-for-sap-authorization-and-trust-management-service-feature-se-c5e9972.md).

-   Access the Security Settings API.

    ```json
    "iframeDomains": "https://store.example.com"
    ```

    For more information, see [Security Settings API](https://api.sap.com/api/SecuritySettingsAPI/resource) on *SAP API Business Hub*.


> ### Remember:  
> To use iFrames with SAP Authorization and Trust Management service, configure the embedding of the login page of your identity provider. Not all identity providers support framing. This function only works if the identity provider supports framing and is configured, too.
> 
> To configure iFrames for SAP Cloud Identity Services - Identity Authentication, see [Configure Trusted Domains](https://help.sap.com/viewer/6d6d63354d1242d185ab4830fc04feb1/Cloud/en-US/08fa1fe816704d99a6bcab245158ebca.html) in the Identity Authentication documentation.

When configured, the SAP Authorization and Trust Management service sends a content security policy header allowing framing of the login page of the service for the domains you specified.

For more information about content security policies, see the World Wide Web Consortium \(W3C\) recommendation [Content Security Policy](https://www.w3.org/TR/CSP2/).

This configuration has several security implications like:

-   Clickjacking attacks on the login page as the URL of the login page isn’t visible.

-   JavaScript based cross site scripting vulnerabilities of older browser versions.

-   3rd party cookies are required when using different domains for authentication with the SAP Authorization and Trust Management service, the identity provider, and the application.


Ensure that no attacker can add malicious web pages or Javascript to any of the hosts allowed to frame the login page. This recommendation also includes hosts that act as reverse proxies, where an attacker can put their content on a different host behind the reverse proxy. Ensure that everything exposed by those framing hosts is safe.

 <a name="loio88b7d9d4c6ff4498b48dbc0b7be8a294"/>

<!-- loio88b7d9d4c6ff4498b48dbc0b7be8a294 -->

## Listing Allowed Redirect URIs

When developing your application, provide the list of the redirect URIs that the application needs when redirecting, for example during login or logout. Enter the list in the `redirect-uris` property of the application security descriptor \(`xs-security.json`\).

At runtime, the SAP Authorization and Trust Management service checks whether the redirect URI is listed in the property and rejects any other URIs. If your redirect isn't on this list, including wildcards, the service won't redirect users there.

The following is an example of a configuration of the `redirect-uris` property in an `xs-security.json`.

```json
"oauth2-configuration": {
  … 
  "redirect-uris": [
    "https://myapplication.cfapps.eu10-004.hana.ondemand.com",
    "https://myapplication.cfapps.eu10-004.hana.ondemand.com/my/content",
    "https://myapplication.mydomain.com",
    "https://myapplication.mydomain.com/my/content"
    ],
  …
}
```

> ### Recommendation:  
> Set the *redirect-uris* property to restrict access as much as possible.

We support explicit wildcards, namely domain relaxing and arbitrary paths. For example: `"https://*.mydomain.com/callback/**"`

> ### Caution:  
> If you use wildcards, we recommend that you make your URIs as specific as possible. By using wildcards, you open up the redirect for multiple websites. Wildcards increase the risk of redirecting to malicious websites.

> ### Note:  
> In cloud landscapes, only `localhost` is always allowed by default as a redirect URI.

**Related Information**  


[Application Security Descriptor Configuration Syntax](../30-development/application-security-descriptor-configuration-syntax-517895a.md "The syntax required to set the properties and values defined in the xs-security.json application security descriptor file.")

[Configure Redirect URLs for Browser Logout](../30-development/configure-redirect-urls-for-browser-logout-690931c.md "To avoid open redirect attacks, direct users to a safe and valid URL when they log out.")

 <a name="loio74c07afd318d46218db291ffb8c25b23"/>

<!-- loio74c07afd318d46218db291ffb8c25b23 -->

## Rotating Secrets

By default, all bindings of a service instance of the SAP Authorization and Trust Management service share a single instance secret. \(Exception: Service instances with the apiaccess plan use a secret per binding by default.\) In the application security descriptor \(`xs-security.json`\), enable individual secrets for each binding of a service instance.



We recommend this configuration so that you can rotate the secret of a binding without affecting the other bindings of the service instance. We also recommend that you rotate secrets regularly.

For more information, see [Managing Secrets of the SAP Authorization and Trust Management Service](../50-administration-and-ops/managing-secrets-of-the-sap-authorization-and-trust-management-service-22f4a5c.md).

```json
"oauth2-configuration": {
  … 
  "credential-types": ["binding-secret"],
  …
}
```

For more information about the application security descriptor, see [Application Security Descriptor Configuration Syntax](../30-development/application-security-descriptor-configuration-syntax-517895a.md).

 <a name="loioc8770b0b43084d838e475bd76eeb4715"/>

<!-- loioc8770b0b43084d838e475bd76eeb4715 -->

## Setting Token Policy

By default, SAP Authorization and Trust Management service sets the validity of tokens as shown in the following table.

> ### Remember:  
> As of September 23, 2022, we announced our intentions to change the validity values of access and refresh tokens in 2023. This change may require you to make changes in your applications or configuration.
> 
> For more information, see [Planned Restriction in the Validity of Access and Refresh Tokens](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?Valid_as_Of=2022-09-23%3A2022-09-23&locale=en-US&version=Cloud&Component=Authorization%20and%20Trust%20Management%20Service).

**Default Validity of Tokens**


<table>
<tr>
<th valign="top">

Token Type



</th>
<th valign="top">

Validity



</th>
</tr>
<tr>
<td valign="top">

Access tokens



</td>
<td valign="top">

Default: 43200 seconds \(12 hours\)



</td>
</tr>
<tr>
<td valign="top">

Refresh tokens



</td>
<td valign="top">

Default: 604800 seconds \(7 days\)



</td>
</tr>
</table>

On request, SAP Authorization and Trust Management service issues access and refresh tokens.

With a valid access token, you can access a protected resource. Once an access token expires, you can get new access tokens with a refresh token. Once the refresh token expires, you must reauthenticate and request new access and refresh tokens.

> ### Recommendation:  
> Relaxing the token policy means that users reauthenticate less. However, increasing the token validity also means that if a malicious user manages to steal a token, that malicious user has access until the token expires. Keep token validity as short as possible, but not less than 30 minutes.

To change token validity, use one of the following methods:

-   To target a specific instance of the service, change the values of the *token-validity* or *refresh-token-validity* parameters in the application security descriptor \(`xs-security.json`\).

    ```json
    "oauth2-configuration": {
      … 
      "token-validity": 1800, 
      "refresh-token-validity": 43200,
      …
    }
    ```

    > ### Note:  
    > This change applies to applications, which consume or subscribe to this instance. These values override the values set for the subaccount.

    For more information about the application security descriptor, see [Application Security Descriptor Configuration Syntax](../30-development/application-security-descriptor-configuration-syntax-517895a.md).

-   To target the subaccount in general, access the Security Settings API.

    ```json
    "tokenPolicySettings": {
      …
      "accessTokenValidity": 1800,
      "refreshTokenValidity": 43200,
      …
    }
    ```

    > ### Note:  
    > This change applies to all service instances in the subaccount that haven't set a specific value in the application security descriptor \(`xs-security.json`\).

    For more information, see [Security Settings API](https://api.sap.com/api/SecuritySettingsAPI/resource) on *SAP API Business Hub*.


 <a name="loio0b406a94f4604a4f98bbe606ef92d50d"/>

<!-- loio0b406a94f4604a4f98bbe606ef92d50d -->

## Access to REST APIs

The `apiaccess` plan provides administrator-level access to REST APIs of the SAP Authorization and Trust Management service. Ensure that only administrators have administrator access to Cloud Foundry spaces where service instances with this plan exist.

To use this service plan, create a separate Cloud Foundry space in your subaccount. Only assign administrator users the *Space Manager* and *Space Developer* roles in this space as well as the *Org Manager* role in the parent Cloud Foundry org. Use this Cloud Foundry space to create the `apiaccess` plan service instance.

Administrators are any SAP BTP cockpit users with the *User and Role Administrator* role. This role is part of the *Subaccount Administrator* role collection, but can be included in other role collections.

**Related Information**  


[About Roles in the Cloud Foundry Environment](../50-administration-and-ops/about-roles-in-the-cloud-foundry-environment-0907638.md "Roles determine which features users can view and access, and which actions they can initiate.")

[Access SAP Authorization and Trust Management Service APIs](../50-administration-and-ops/access-sap-authorization-and-trust-management-service-apis-ebc9113.md "To enable programmatic access to the SAP Authorization and Trust Management service (XSUAA) in your multi-environment subaccount, create a service instance with the apiaccess plan.")

[Default Role Collections of SAP BTP Cloud Foundry Environment \[Feature Set B\]](default-role-collections-of-sap-btp-cloud-foundry-environment-feature-set-b-a6a0072.md "The following table displays the default role collections available with cloud management tools feature set B after initially deploying your accounts. For more information, see the related links.")

 <a name="loio24c226d64f994d80879d5f2518c0d0ab"/>

<!-- loio24c226d64f994d80879d5f2518c0d0ab -->

## Training Business Users How to Handle Session Timeouts

Administrators should make business users aware of a possible security risk after single logoff. A business user might get a message saying that this user is being logged off from the application although the identity provider session was not terminated.

The reason for this message comes from a timeout mismatch between the application and the SAP Authorization and Trust Management service. The timeout of the SAP Authorization and Trust Management service is currently 30 minutes. After the timeout, the SAP Authorization and Trust Management service does not forward the logoff request to the identity provider. This situation incurs a security risk.

> ### Recommendation:  
> To remedy this security risk, advise the business users to access the application URL again, log on to the application, and log off right away, or log off directly from the identity provider.

