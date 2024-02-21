<!-- loio8eb23a1130e24ef49fa689bf7aab781e -->

# Validation and Revocation of Access Tokens

To confirm that access tokens were truly issued by the SAP Authorization and Trust Management service and are still valid, applications check the tokens for validity.

Access tokens are JSON web tokens \(JWT\). When the SAP Authorization and Trust Management service issues access tokens for an application, the service sets a validity and digitally signs the token. The default validity for a token is 12 hours, but you can set the validity as part of the OAuth configuration in the application security descriptor \(`xs-security.json`\).

Applications must reject the access token in the following cases:

-   The token is no longer valid.

    The token could have expired or has been revoked.

-   The signature on the token doesn’t match.




<a name="loio8eb23a1130e24ef49fa689bf7aab781e__section_lvx_tbj_jmb"/>

## Online or Offline Validation

As an application developer, you have the design decision, whether to perform validation of the token online or offline.

In online validation, you send a request to the SAP Authorization and Trust Management service to determine that the access token is still valid and hasn’t been revoked. To check the validity, use the `introspect` endpoint of the standard Cloud Foundry API.

Your application can perform offline validation with the help of our client libraries. You must get the public key from the SAP Authorization and Trust Management service and use the key to check the validity. While validating a token offline can ensure that your application can continue to operate if the SAP Authorization and Trust Management service is unavailable, your application continues to accept revoked tokens until they reach the end of their validity. A malicious user with a revoked token still has access as long as the token is still valid.

To revoke a token, use the `revoke` endpoint of the standard Cloud Foundry API.

**Related Information**  


[Rotate Signing Keys of Access Tokens](../50-administration-and-ops/rotate-signing-keys-of-access-tokens-b279adf.md#loiob279adf3ec134b2a8611a42bff1ee9d9 "Components of the Cloud Foundry environment use the digital signature of the access tokens to verify the validity of access tokens. Periodically rotate the signing keys of access tokens.")

[Application Security Descriptor Configuration Syntax](application-security-descriptor-configuration-syntax-517895a.md "The syntax required to set the properties and values defined in the xs-security.json application security descriptor file.")

[https://docs.cloudfoundry.org/api/uaa/version/74.4.0/index.html\#introspect-token](https://docs.cloudfoundry.org/api/uaa/version/74.4.0/index.html#introspect-token)

[https://docs.cloudfoundry.org/api/uaa/version/74.4.0/index.html\#revoke-tokens](https://docs.cloudfoundry.org/api/uaa/version/74.4.0/index.html#revoke-tokens)

[XSUAA authentication and authorization service integration libraries and samples for authenticating users and services on GitHub](https://github.com/SAP/cloud-security-xsuaa-integration)

