<!-- loio63fd9f1a140245df870dd7150ff15292 -->

# Retrieving Tokens with mTLS

The application router and other libraries take care of getting tokens from the SAP Authorization and Trust Management for you. If you build your own integration, you must handle tokens yourself.

> ### Note:  
> The service doesn't check for certificate revocation. The only way to revoke an X.509 secret is to rotate the secret.

> ### Recommendation:  
> Build automation into your application pipeline. Certificates have a relatively short lifetime. The default lifetime for certificates managed by the service is 7 days. Only by automating the process, can you ensure that credentials are rotated and distributed in a timely manner. Otherwise you risk authentication failures from expired certificates.

The token endpoint is a little different from the standard endpoint. The path includes `authentication.cert` instead of just `authentication`.

`https://*<subdomain\>*.**authentication.cert**.*<landscape\>*/oauth/token`

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

-   For user tokens: `authorization_code`

-   For technical flows: `client_credentials`


> ### Note:  
> Leave out the `client_secret` parameter.

Finally, when building the call, include the client certificate and public key in your request. The following syntax is for CURL:

`curl --cert *<Path\_Private\_Key\>* --key *<Path\_Public\_Key\>* -XPOST https://*<subdomain\>*.authentication.cert.*<landscape\>*/oauth/token -d 'grant_type=*<Grant\_Type\>*&client_id=*<Client\_ID\>*'`

The following is an example in CURL:

```
curl --cert x509private.pem --key x509public.pem -XPOST https://test-me.authentication.cert.eu20.hana.ondemand.com/oauth/token -d 'grant_type=client_credentials&client_id=sb-na-edb111d1-2c22-3eca-444-869fde307ac7!a5017'
```

