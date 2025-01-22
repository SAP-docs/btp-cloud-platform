<!-- loio214b8f5c6db74343b339c781c64fdc85 -->

# Secure Communication for Inbound Integration

Integration scenarios from a customer system to SAP BTP ABAP environment \(inbound integration\) require secure communication.

You specify and configure the authentication method in the *Communication Arrangements* app when you select a user for inbound communication. The underlying communication scenario defines the authentication methods that are available for a communication arrangement.

Communication scenarios can offer the following types of authentication method:

-   Token-based

-   Certificate-based

-   Basic \(User ID and Password\)


Token-based authentication methods enable principal propagation, which means that the resulting sessions run in the context of a business user. In contrast, sessions using certificate-based or basic authentication run in the context of a technical communication user.



<a name="loio214b8f5c6db74343b339c781c64fdc85__section_ntc_s41_fbc"/>

## Token-Based Authentication

Token-based authentication methods are configured in the *Communication System* app, where you establish trust with the token provider and define which part of the token contains the user name for principal propagation.

> ### Note:  
> In system-to-system communication of the kind covered here, SAML and OIDC authentication flows use the bearer flow mechanism. These authentication flows differ from flows implemented in browser-based SAML 2.0 and OIDC authentication because there’s no UI or user interaction in system-to-system communication.



### OAuth-Based Authentication

When the external system authenticates to SAP BTP ABAP environment using OAuth, it presents a short-lived token to SAP BTP ABAP environmentt. This token is cryptographically signed by a trusted token provider.

To establish the trust relationship between SAP BTP ABAP environment and the token provider, you must upload the token provider’s certificate \(public key\) to your SAP BTP ABAP environment in the *Communication Systems* app.



### SAML-Based Authentication

In SAML-based authentication, the external system authenticates by passing a SAML assertion \(a cryptographically signed piece of text\) to SAP BTP ABAP environment.

For authentication to succeed, the issuer of the SAML assertion must be trusted by the SAP BTP ABAP environment. To ensure trust, you must upload the certificate \(public key\) of the SAML issuer in the *Communication Systems* app. This enables SAP BTP ABAP environment to verify the authenticity of the SAML assertion.



### OpenID Connect \(OIDC\) Authentication

OpenID Connect standardizes the way in which user information is transferred via JSON Web Token \(JWT\) during login. To ensure trust with the token provider, you must upload a document containing the provider’s metadata. This document can include the URL for fetching the OIDC provider’s private keys \(Web Keys\), allowing trust to be established automatically. Alternatively, you can configure the URL for downloading the OIDC provider’s public key manually or enter the keys directly.



<a name="loio214b8f5c6db74343b339c781c64fdc85__section_pgw_bp1_fbc"/>

## Certificate-Based Authentication

For certificate-based authentication, the client certificate \(public key\) of the external system must be uploaded to the communication user used in the communication arrangement.

Such client certificates must be signed by approved certification authorities \(CAs\).

If the certificate is signed by an untrusted CA, establishing a connection fails during the TLS handshake.

If the external system presents a certificate that is signed by a trusted CA, but doesn’t match the certificate configured in the communication arrangement, authentication fails at the application level.

A list of all root CAs approved by SAP Global Security is available in SAP Note [2801396](https://me.sap.com/notes/2801396) \(SAP Global Trust List\).



### Certificate Expiration

Every certificate is valid for a certain period. Once a certificate expires, it can’t be used for authentication anymore.

When a certificate of a root CA expires and is replaced by a new certificate, you also need to consider any certificates that were signed by the expiring CA certificate. These certificates have to be replaced by ones that signed with the new CA certificate. Remember to update your communication users accordingly.



<a name="loio214b8f5c6db74343b339c781c64fdc85__section_uht_gp1_fbc"/>

## Basic Authentication \(User ID and Password\)

To use password-based authentication, set a secure password for the communication user in the*Maintain Communication Users* app.

> ### Caution:  
> SAP highly recommends using strong authentication methods such as token- or certificate-based authentication for greater security.

**Related Information**  


[Maintain Communication Users](maintain-communication-users-eef80dd.md "You can use this app to create and edit communication users. Communication users are used by solutions to authenticate themselves to be able to post data.")

[Communication Systems](communication-systems-15663c1.md "You can use this app to create communication systems. Communication systems are created to enable the communication among different systems.")

 <?sap-ot O2O class="- topic/link " href="fab3fd449cf74c6384622b98831e989e.xml" text="" desc="" xtrc="link:3" xtrf="file:/home/builder/src/dita-all/jjq1673438782153/loio2080d0faf9d84ce6aa14caa4caa32935_en-US/src/content/localization/en-us/214b8f5c6db74343b339c781c64fdc85.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

[SAP Note 2801396](https://me.sap.com/notes/2801396 "SAP Global Trust List")

