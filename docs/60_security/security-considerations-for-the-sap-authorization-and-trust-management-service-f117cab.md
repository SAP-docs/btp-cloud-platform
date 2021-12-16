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

To change configure the trusted domains, use one of the following methods:

-   Enter trusted domains in SAP BTP cockpit.

    For more information, see [Configure Trusted Domains for SAP Authorization and Trust Management Service \[Feature Set B\]](../50_administration_and_ops/configure-trusted-domains-for-sap-authorization-c5e9972-md).

-   Access the Security Settings API.

    ```lang-json
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

The application security descriptor \(`xs-security.json`\) includes the *redirect-uris* parameter. This parameter contains a list of the redirect URIs that SAP BTP checks for when redirecting. If your landscape domain or custom domain isn't on this list, including wildcards, the SAP Authorization and Trust Management service won't redirect users there.

> ### Recommendation:  
> Set the *redirect-uris* parameter to restrict access as much as possible.

We support explicit wildcards, namely domain relaxing and arbitrary paths. For example: `"https://*.mydomain.com/callback/**"`

> ### Caution:  
> If you use wildcards, we recommend that you make your URIs as specific as possible. By using wildcards, you open up the redirect for multiple web sites. Wildcards increase the risk of redirecting to malicious web sites.

For more information, see [Domain Checks at Browser Login and Logout](../30_development/domain-checks-at-browser-login-and-logout-22a7d69.md).

```lang-json
"oauth2-configuration": {
  … 
  "redirect-uris": [
    "https://myapp.cfapps.eu10.hana.ondemand.com",
    "http://myapp.mydomain.com/my/content"
    ],
  …
}
```

For more information about the application security descriptor, see [Application Security Descriptor Configuration Syntax](../30_development/application-security-descriptor-configuration-syntax-517895a.md).

 <a name="loio74c07afd318d46218db291ffb8c25b23"/>

<!-- loio74c07afd318d46218db291ffb8c25b23 -->

## Rotating Secrets

By default, all bindings of a service instance of the SAP Authorization and Trust Management service share a single instance secret. \(Exception: Service instances with the apiaccess plan use a secret per binding by default.\) In the application security descriptor \(`xs-security.json`\), enable individual secrets for each binding of a service instance.



We recommend this configuration so that you can rotate the secret of a binding without affecting the other bindings of the service instance. We also recommend that you rotate secrets regularly.

For more information, see [Managing Secrets of the SAP Authorization and Trust Management Service](../50_administration_and_ops/managing-secrets-of-the-sap-authorization-and-trust-management-service-22f4a5c.md).

```lang-json
"oauth2-configuration": {
  … 
  "credential-types": ["binding-secret"],
  …
}
```

For more information about the application security descriptor, see [Application Security Descriptor Configuration Syntax](../30_development/application-security-descriptor-configuration-syntax-517895a.md).

 <a name="loioc8770b0b43084d838e475bd76eeb4715"/>

<!-- loioc8770b0b43084d838e475bd76eeb4715 -->

## Setting Token Policy

By default, SAP Authorization and Trust Management service sets the validity of tokens as shown in the following table.

<a name="loioc8770b0b43084d838e475bd76eeb4715__table_k53_g25_rqb"/>Default Validity of Tokens


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

Access and ID tokens



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

Default: 24192000 seconds \(28 days\)



</td>
</tr>
</table>

To change token validity, use one of the following methods:

-   Change the token policy in SAP BTP cockpit.

    For more information, see [Configure Token Policy for SAP Authorization and Trust Management Service \[Feature Set B\]](../50_administration_and_ops/configure-token-policy-for-sap-authorization-and-trust-management-service-feature-set-b-40290a9.md).

-   Change the values of the *token-validity* or *refresh-token-validity* parameters in the application security descriptor \(`xs-security.json`\).

    ```lang-json
    "oauth2-configuration": {
      … 
      "token-validity": 1800, 
      "refresh-token-validity": 43200,
      …
    }
    ```

    For more information about the application security descriptor, see [Application Security Descriptor Configuration Syntax](../30_development/application-security-descriptor-configuration-syntax-517895a.md).

-   Access the Security Settings API.

    ```lang-json
    "tokenPolicySettings": {
      …
      "accessTokenValidity": 1800,
      "refreshTokenValidity": 43200,
      …
    }
    ```

    For more information, see [Security Settings API](https://api.sap.com/api/SecuritySettingsAPI/resource) on *SAP API Business Hub*.


