<!-- loio63fd9f1a140245df870dd7150ff15292 -->

# Implementing Custom Token Retrieval from SAP Authorization and Trust Management Service with mTLS

The application router and other token client libraries take care of getting tokens from the SAP Authorization and Trust Management service for you. If you build your own integration, you must handle token retrieval yourself.

> ### Note:  
> The service doesn't check for certificate revocation. To stop the service from accepting a certificate that is still valid, delete the relevant bindings or service keys. As soon as the binding is deleted, the service stops accepting the certificate.
> 
> For bindings with self-managed certificates and the `certificate-pinning` parameter set to ***false***, you can rotate the secrets without deleting bindings. Just use a new certificate with the same subject and issuer distinguished name \(DN\). The service saves the new validity date of the new certificate.
> 
> For more information, see [Parameters for Self-Managed X.509 Certificates](../50-administration-and-ops/parameters-for-self-managed-x-509-certificates-5168df6.md).

> ### Recommendation:  
> Build automation into your deployment or CI/CD pipeline. Client certificates have a relatively short lifetime. The default lifetime for certificates managed by the service is 7 days. Only by automating the process, can you ensure that credentials are rotated and distributed in a timely manner. Otherwise, you risk authentication failures from expired certificates.

When called with mTLS, the token endpoint is a little different from the standard endpoint. The path includes `authentication.cert` instead of just `authentication`.

<code>https://<i class="varname">&lt;subdomain&gt;</i>.<b>authentication.cert</b>.<i class="varname">&lt;landscape&gt;</i>/oauth/token</code>

For example:

```
https://test-me.authentication.cert.eu20.hana.ondemand.com/oauth/token
```

Use the `/.well-known/openid-configuration` endpoint to find the endpoints for your subaccount. The endpoints appear under the `mtls_endpoint_aliases` parameter.

For example: `https://test-me.authentication.eu20.hana.ondemand.com/.well-known/openid-configuration`

The following is an example of part of the JSON returned by the endpoint.

```
{
    …,
    "mtls_endpoint_aliases": {
        "token_endpoint": "https://test-me.authentication.cert.eu20.hana.ondemand.com/oauth/token",
        "authorization_endpoint": "https://test-me.authentication.cert.eu20.hana.ondemand.com/oauth/authorize"
    },
…
}
```

For X.509 authentication, the `grant_type` are as with client secret authentication:

-   For UI user flows: Authorization code

-   For API user flows: JWT bearer, refresh token, and password grant

-   For technical flows: Client credentials


> ### Note:  
> Leave out the `client_secret` parameter. The `client_id` is still required.

Finally, when building the call, include the client certificate \(public key\) and private key for signing in your request. The following syntax is for CURL:

<code>curl --cert <i class="varname">&lt;Path_Client_Cert&gt;</i> --key <i class="varname">&lt;Path_Private_Key&gt;</i> -XPOST https://<i class="varname">&lt;subdomain&gt;</i>.authentication.cert.<i class="varname">&lt;landscape&gt;</i>/oauth/token -d 'grant_type=<i class="varname">&lt;Grant_Type&gt;</i>&amp;client_id=<i class="varname">&lt;Client_ID&gt;</i>'</code>

The following is an example in CURL:

```
curl --cert x509certificate.pem --key x509privatekey.pem -XPOST https://test-me.authentication.cert.eu20.hana.ondemand.com/oauth/token -d 'grant_type=client_credentials&client_id=sb-na-edb111d1-2c22-3eca-444-869fde307ac7!a5017'
```

**Related Information**  


[Enable mTLS Authentication to SAP Authorization and Trust Management Service for Your Application](enable-mtls-authentication-to-sap-authorization-and-trust-management-service-for-your-app-aa80338.md "Enabling your application to retrieve access tokens from SAP Authorization and Trust Management service(XSUAA) over mutual transport layer security (mTLS) requires you to enable mTLS token retrieval for the service instance. Then ensure the binding includes the X.509 credentials.")

