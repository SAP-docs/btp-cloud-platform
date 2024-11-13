<!-- loio5ee4735543e3401e8af688a2931db153 -->

# Configure OAuth 2.0 SAML Bearer Assertion Grant

When using the OAuth 2.0 SAML Bearer Assertion Grant authentication method, the SAP Destination service sends a signed SAML Bearer Assertion containing information about the business user to the token endpoint of the ABAP environment to obtain an access token.



## Context

You can provide your own certificate to sign the SAML assertion or use the standard subaccount-wide signing certificate. The ABAP environment needs to trust the issuer of the SAML Bearer Assertion.

To authenticate the OAuth client as communication user at the token endpoint, a client secret \(password of the communication user\) or client certificate can be used. In the latter case, the client certificate needs to be provided by the SAP Destination service and the ABAP environment needs to trust the signing root certificate authority \(CA\). The list of trusted root certificate authorities can be found in [SAP Note 2801396](https://me.sap.com/notes/2801396).

Finally, the client application uses the access token to authenticate as a business user at the ABAP environment to access the actual resource.



## Procedure

1.  Maintain the key store for the signing certificate.

    If the SAML assertion shall not be signed by the standard subaccount-wide signing key, then either upload a key store including the signing certificate, the private key, or generate one, for instance `my-signing-keystore.p12`. For more information, see [Use Destination Certificates](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/use-destination-certificates).

2.  Download the signing certificate.

    If you use the standard subaccount-wide signing key, then download the signing certificate by choosing *Download Trust* in the SAP Destination service.

3.  Maintain the key store for the client certificate.

    If the OAuth client shall authenticate via client ID and client certificate, then either upload a key store including the client certificate, the private key, and the certificate chain to the SAP Destination service, or generate one, for instance `my-keystore.p12`. For more information, see [Use Destination Certificates](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/use-destination-certificates).

4.  Create a communication user.

    Create a communication user using the Maintain Communication Users app in your ABAP environment system. In this context the communication user represents the OAuth client. Enter the following data:


    <table>
    <tr>
    <th valign="top">

    Field
    
    </th>
    <th valign="top">

    Input
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    User Name
    
    </td>
    <td valign="top">
    
    Provide a user name, for example, `MY_OAUTH_CLIENT`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Description
    
    </td>
    <td valign="top">
    
    Provide a description.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Password
    
    </td>
    <td valign="top">
    
    If the OAuth client shall authenticate via client secret, provide a password.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Certificate
    
    </td>
    <td valign="top">
    
    If the OAuth client shall authenticate via client certificate, then upload the client certificate to the communication user. During runtime, the service is processed by the communication user that is assigned to the certificate.
    
    </td>
    </tr>
    </table>
    
5.  Create a communication system.

    Create a communication system using the Communication Systems app in your ABAP environment system. Enter the following data:

    **General Data**


    <table>
    <tr>
    <th valign="top">

    Field
    
    </th>
    <th valign="top">

    Input
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    System ID
    
    </td>
    <td valign="top">
    
    Provide a system ID, for example, `MY_COMMUNICATION_PARTNER`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    System Name
    
    </td>
    <td valign="top">
    
    Provide a system name.
    
    </td>
    </tr>
    </table>
    
    **Technical Data**


    <table>
    <tr>
    <th valign="top">

    Field
    
    </th>
    <th valign="top">

    Input
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    General – Inbound Only
    
    </td>
    <td valign="top">
    
    Yes
    
    </td>
    </tr>
    </table>
    
    **Identity Provider**


    <table>
    <tr>
    <th valign="top">

    Field
    
    </th>
    <th valign="top">

    Input
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    OAuth 2.0 Identity Provider
    
    </td>
    <td valign="top">
    
    On
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    User ID Mapping Mode
    
    </td>
    <td valign="top">
    
    Select *User Name*.

    Thereby, if the NameIdFormat is unspecified, then the value of the NameID element in the SAML assertions’ subject will be mapped to the user name.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    SAML Bearer Issuer
    
    </td>
    <td valign="top">
    
    Enter the SAML entity ID of the SAML bearer issuer, which corresponds to the common name \(the string after CN=\) of the signing certificate subject.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Signing Certificate
    
    </td>
    <td valign="top">
    
    Upload the signing certificate.
    
    </td>
    </tr>
    </table>
    
    **Users for Inbound Communication**


    <table>
    <tr>
    <th valign="top">

    Authentication Method
    
    </th>
    <th valign="top">

    User Name/Client ID
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    OAuth 2.0
    
    </td>
    <td valign="top">
    
    Add a user.

    User name of the communication user \(= OAuth client ID\), for example, `MY_OAUTH_CLIENT`
    
    </td>
    </tr>
    </table>
    
6.  Create a communication arrangement.

    Create a communication arrangement using the Communication Arrangements app in your ABAP environment system. Enter the following data:


    <table>
    <tr>
    <th valign="top">

    Field
    
    </th>
    <th valign="top">

    Input
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Scenario ID
    
    </td>
    <td valign="top">
    
    Select the scenario, for example, `Z_MY_SCENARIO`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Arrangement Name
    
    </td>
    <td valign="top">
    
    Provide a name, for example, `MY_ARRANGEMENT`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Communication System
    
    </td>
    <td valign="top">
    
    Select the communication system, for example, `MY_COMMUNICATION_PARTNER`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Inbound Communication – User Name
    
    </td>
    <td valign="top">
    
    Select the communication user, for example, `MY_OAUTH_CLIENT`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Inbound Communication – Authentication Method
    
    </td>
    <td valign="top">
    
    `OAuth 2.0`
    
    </td>
    </tr>
    </table>
    
7.  Get technical data of the own communication system.

    Open the own communication system in the Communication Systems app in your ABAP environment system. To open your own communication system, choose *Own SAP Cloud System*.

    Denote the following values:

    -   Host name, for example, `1a354373-d200-46f6-9d5c-daab9a65d9b6.abap.eu10.hana.ondemand.com` 
    -   OAuth 2.0 confidential client token service URL, for example, `https://1a354373-d200-46f6-9d5c-daab9a65d9b6.abap.eu10.hana.ondemand.com/sap/bc/sec/oauth2/token`
    -   SAML2 audience, for example, `https://1a354373-d200-46f6-9d5c-daab9a65d9b6.abap-web.eu10.hana.ondemand.com` 

8.  Create a Destination

    Create a destination using the Destinations editor in the SAP BTP cockpit. For more information, see [Using the Destination Editor in the Cockpit](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/using-destinations-editor-in-cockpit?version=Cloud). Provide the following data:


    <table>
    <tr>
    <th valign="top">

    Field
    
    </th>
    <th valign="top">

    Input
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Name
    
    </td>
    <td valign="top">
    
    Enter the name of the destination, for example `my-oauth-saml-bearer-assertion-destination`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Type
    
    </td>
    <td valign="top">
    
    HTTP
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    URL
    
    </td>
    <td valign="top">
    
    Enter `https://<hostname of the own communication system>`, for example, `https://1a354373-d200-46f6-9d5c-daab9a65d9b6.abap.eu10.hana.ondemand.com`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Proxy Type
    
    </td>
    <td valign="top">
    
    Internet
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Authentication
    
    </td>
    <td valign="top">
    
    `OAuth2SAMLBearerAssertion` 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Key Store Location
    
    </td>
    <td valign="top">
    
    If you don't use the standard signing certificate, then select the name of the corresponding key store, for example `my-signing-keystore.p12`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Key Store Password
    
    </td>
    <td valign="top">
    
    Enter the password for the keystore.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Audience
    
    </td>
    <td valign="top">
    
    Enter the SAML2 Audience from the own communication system, for example, `https://1a354373-d200-46f6-9d5c-daab9a65d9b6.abap-web.eu10.hana.ondemand.com`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    AuthnContextClassRef
    
    </td>
    <td valign="top">
    
    `urn:oasis:names:tc:SAML:2.0:ac:classes:PreviousSession`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Use mTLS for token retrieval
    
    </td>
    <td valign="top">
    
    Activate if the OAuth client shall be authenticated at the token endpoint using client certificate.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Client Key
    
    </td>
    <td valign="top">
    
    Enter the user name of the communication user \(= OAuth Client ID\), for example, `MY_OAUTH_CLIENT`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Token Service Key Store Location
    
    </td>
    <td valign="top">
    
    If the OAuth client shall be authenticated at the token endpoint using client certificate, then select the name of the corresponding key store, for example `my-keystore.p12`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Token Service Key Store Password
    
    </td>
    <td valign="top">
    
    If the OAuth client shall be authenticated at the token endpoint using client certificate, then enter the password for the key store.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Token Service URL Type
    
    </td>
    <td valign="top">
    
    Choose *Dedicated*.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Token Service URL
    
    </td>
    <td valign="top">
    
    Enter the OAuth 2.0 confidential client token service URL from the own communication system, for example, `https://1a354373-d200-46f6-9d5c-daab9a65d9b6.abap.eu10.hana.ondemand.com/sap/bc/sec/oauth2/token`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Token Service User
    
    </td>
    <td valign="top">
    
    If the OAuth client shall be authenticated at the token endpoint using client ID and secret, then enter the name of communication user, for example, `MY_OAUTH_CLIENT`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Token Service Password
    
    </td>
    <td valign="top">
    
    If the OAuth client shall be authenticated at the token endpoint using client ID and secret, then enter the password of the communication user.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    nameIdFormat
    
    </td>
    <td valign="top">
    
    Enter `urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress` if the e-mail is propagated or `urn:oasis:names:tc:SAML:1.1:nameid-format:unspecified` if the user name is propagated. See [User Propagation via SAML 2.0 Bearer Assertion Flow](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/user-propagation-via-saml-2-0-bearer-assertion-flow) for more information.
    
    </td>
    </tr>
    </table>
    

**Related Information**  


[Maintain Communication Users](maintain-communication-users-eef80dd.md "You can use this app to create and edit communication users. Communication users are used by solutions to authenticate themselves to be able to post data.")

[Communication Systems](communication-systems-15663c1.md "You can use this app to create communication systems. Communication systems are created to enable the communication among different systems.")

[Communication Arrangements](communication-arrangements-1decd8b.md)

