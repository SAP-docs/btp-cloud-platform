<!-- loio46b8b85878ae4c51acbaa5f3822c777c -->

# Mutual TLS Authentication \(mTLS\) and Certificates Handling

Mutual TLS \(mTLS\) is a mutual authentication mechanism. The application router supports the use of certificates for the creation of tokens and an mTLS handshake in backend connections.

To enable the mTLS authentication for backend connections, the following prerequisites must be met:

-   The authentication service instance that is bound to the application router, Authorization and Trust Management service \(XSUAA\) or Identity Authentication \(IAS\), must provide a certificate chain and a private key in its credentials.

    If the private key isn't provided in the credentials, you can also configure the environment variables XSUAA\_PRIVATE\_KEY \(Authorization and Trust Management\) and IAS\_PRIVATE\_KEY \(Identity Authentication\) in the application router to provide the private key.

-   The destinations for the backend applications must contain either the `HTML5.ForwardAuthCertificate`s property in the configuration provided by the destination service \(see [Application Routes and Destinations](application-routes-and-destinations-3cc788e.md) \) or the `forwardAuthCertificate`s property in the destinations environment variable \(see [Environment Variables](environment-variables-ba52705.md)\).

-   In Cloud Foundry, the client certificate is propagated using the `x-forwarded-client-cert` header. To enable this, the backend URL must contain a `.cert` segment in its domain.


The application router gets the XSUAA or IAS tokens that provide the certificates chain and private key. The application router uses the certificates chain and private key from the credentials of the authentication service instance for the following:

-   The application router creates the HTTP connection to backend using the private key and a chain of intermediate and client certificates to enable the mTLS handshake. If the `FULL_CERTIFICATE_CHAIN` environment variable is enabled, the application router sends the entire chain of certificates provided in the binding of the authentication service \(XSUAA or IAS\) to the backend applications. If this environment variable is not enabled, the application router sends only the root and intermediate certificates from the chain.

-   When forwarding a request to business services, the application router uses these certificates also to create a `client_credentials` token or to exchange the login token.


