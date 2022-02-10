<!-- loiof60c8e724bb8496eae10ed29e896766a -->

# Retrieving Access Tokens with Mutual Transport Layer Security \(mTLS\)

Mutual Transport Layer Security \(mTLS\) is considered more secure than the combination of client ID and client secret. Unlike retrieving the access token with client ID and client secret, no secret is shared between calling application and the service instance of SAP Authorization and Trust Management service \(XSUAA\).

This configuration enables your application to retrieve or exchange access tokens from an instance of the SAP Authorization and Trust Management service with mTLS. When using TLS, the client verifies the identity of the OAuth server during their handshake. By using mTLS, the OAuth server also verifies the identity of the client. Calls to other services and applications with the access token use the standard OAuth protocols.

You, as a developer, have the option to have the service provide the X.509 certificate for the binding or service key or if you already have your own public key infrastructure \(PKI\), you can provide your own.

> ### Restriction:  
> If you use your own PKI, your certificates must be issued by certificate authorities trusted by the service.
> 
> For more information, see [Binding Parameters of SAP Authorization and Trust Management Service](../50-administration-and-ops/binding-parameters-of-sap-authorization-and-trust-management-service-3240307.md).

**Related Information**  


[Enable mTLS Authentication to SAP Authorization and Trust Management Service for Your Application](enable-mtls-authentication-to-sap-authorization-and-trust-management-service-for-your-app-aa80338.md "Enabling your application to retrieve access tokens from SAP Authorization and Trust Management service(XSUAA) over mutual transport layer security (mTLS) requires you to enable mTLS token retrieval for the service instance. Then ensure the binding includes the X.509 credentials.")

[Implementing Custom Token Retrieval from SAP Authorization and Trust Management Service with mTLS](implementing-custom-token-retrieval-from-sap-authorization-and-trust-management-service-w-63fd9f1.md "The application router and other token client libraries take care of getting tokens from the SAP Authorization and Trust Management service for you. If you build your own integration, you must handle token retrieval yourself.")

