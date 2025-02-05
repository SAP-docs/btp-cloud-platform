<!-- loio877d48c0fc6548b596208e1ed88fe686 -->

# Integration in BTP Apps via SAP Destination Service

In this topic you learn how to configure destinations in the SAP Destination service that shall be used by applications to consume services provided by the ABAP environment, and how to maintain corresponding communication arrangements in the ABAP environment. For instance, how to configure a destination that is used by an SAP Fiori application from the HTML5 repository that accesses an OData service of the ABAP environment.



![Integration in BTP Apps via Destination Service](images/Integration_in_BTP_Apps_via_Destination_Service_ad08be3.png)



<a name="loio877d48c0fc6548b596208e1ed88fe686__section_wl2_y5c_pcc"/>

## Choosing the Right Authentication Method

Before you start with the configuration, you need to decide on the right authentication method first. The right authentication method can be decided by answering the following questions:



### What Authentication Methods Are Supported Technically?

The authentication method needs to be supported by both parties. The following authentication methods are commonly supported by the SAP Destination service and the ABAP environment. For more information, see [Supported Protocols and Authentication Methods](https://help.sap.com/docs/abap-cloud/abap-integration-connectivity/supported-protocols-and-authentication-methods).

-   Authentication via communication user
    -   Basic authentication \(user name & password\)

    -   Client certificate authentication \(X.509 certificate\)

-   Authentication via business user \(principal propagation\)
    -   SAML Assertion authentication
    -   OAuth 2.0 SAML Bearer Assertion grant
        -   Client secret authentication \(client ID & secret\)
        -   Mutual TLS \(mTLS\) client authentication \(client ID & X.509 certificate\)



The following applies to each authentication method:

-   Basic authentication: A user name and password are sent to the ABAP environment for authentication.
-   Client certificate authentication: An X.509 certificate is used.
-   SAML assertion authentication: A SAML bearer assertion is sent.

In all three cases the credentials are directly sent to the ABAP environment. However, when using OAuth 2.0, then two endpoints are involved: the authorization server and the resource server. First, the SAP Destination service calls the token endpoint of the authorization server and provides an authorization grant to obtain an access token. To authenticate at the authorization server, a client secret or an X.509 certificate can be used. The supported authorization grant is SAML bearer assertion. Second, the client application uses the access token to authenticate at the ABAP environment to access the actual resource.



### Who Shall Be Acting?

Decide if the actions in the ABAP environment shall be executed under a communication user independent from the user of the client application, or if the actions shall be performed under an individual business user corresponding to the user of the client application \(principal propagation\).

If the service shall be processed as communication user, then choose one of the following authentication methods:

-   Basic authentication
-   Client certificate authentication

If the principal shall be propagated to the target, then use one of the following authentication methods:

-   SAML assertion authentication

-   OAuth 2.0 SAML Bearer Assertion

Although OAuth SAML 2.0 Bearer Assertion is a well-known standard and enables additional access restriction using OAuth scopes, it also has some drawbacks compared to the proprietary SAML assertion authentication method:

-   It requires a corresponding communication scenario and arrangement to provide the scope to the OAuth client.
-   Only OData services are supported.
-   It requires an additional round trip to exchange the authorization grant against an access token.
-   The configuration is much more complicated and, thus, more error prone.

If you don't have any special requirements to use the OAuth standard, then the usage of SAML assertion authentication is preferred over OAuth 2.0 SAML Bearer Assertion.



### How Strong Are the Security Requirements?

Certificate-based authentication is more secure than using a password-based authentication method: a password is a shared secret and is known by both communication partners. Certificate-based client authentication uses public key infrastructure. The private key, which is owned by the client, isn't shared with the communication partner. Moreover, a password change between the communication partners is disruptive, while a non-disruptive change can be achieved with certificate-based authentication since more than one client certificate can be assigned to a communication user.

Hence, client certificate authentication is preferred over Basic Authentication and OAuth 2.0 SAML Bearer Assertion Grant with mTLS-based OAuth client authentication is preferred over OAuth 2.0 SAML Bearer Assertion Grant with client secret authentication.

The client certificates can be provided by the application, can be uploaded to the SAP Destination service, or generated by the SAP Destination service. The ABAP environment needs to trust the certificate authority \(CA\) of the client certificate. The list of trusted root certificate authorities can be found in [SAP Note 2801396](https://me.sap.com/notes/2801396).



<a name="loio877d48c0fc6548b596208e1ed88fe686__section_szr_wxc_pcc"/>

## Configure the Destination and the Communication Arrangement

Once you have chosen the appropriate authentication method, you can continue to configure the destination, communication user, communication system, and communication arrangement accordingly:

-   Inbound communication via communication user
    -   [Configuring Basic Authentication](configuring-basic-authentication-4e1761c.md)
    -   Configuring client certificate authentication \(X.509 certificate\)

-   Inbound communication via business user
    -   [Configuring SAML Assertion Authentication](configuring-saml-assertion-authentication-247ac02.md)
    -   [Configure OAuth 2.0 SAML Bearer Assertion Grant](configure-oauth-2-0-saml-bearer-assertion-grant-5ee4735.md) 
        -   Client secret authentication \(client ID & secret\)
        -   Mutual TLS \(mTLS\) client authentication \(client ID & X.509 certificate\)



