<!-- loio247ac0228f304d4bbccb2b87c260efc3 -->

# Configuring SAML Assertion Authentication

When using the SAML assertion authentication method, the client application sends a signed SAML bearer assertion containing information about the business user to authenticate against the ABAP environment.



## Context

You can provide your own certificate to sign the SAML assertion or use the standard subaccount-wide signing certificate. The ABAP environment needs to trust the issuer of the SAML bearer assertion.



## Procedure

1.  Maintain the key store for the signing certificate.

    If the SAML assertion shall not be signed by the standard subaccount-wide signing certificate, then either upload a key store including the signing certificate, the private key, and the certificate chain, or generate one, for instance `my-signing-keystore.p12`. For more information, see [Use Destination Certificates](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/use-destination-certificates).

2.  Download the signing certificate.

    If you use the standard subaccount-wide signing key, then download the signing certificate by choosing *Download Trust* in the SAP Destination editor.

3.  Get data of the own communication system.

    Open the own communication system in the Communication Systems app in your ABAP environment system. To open your own communication system, choose *Own SAP Cloud System*.

    Denote the following values:

    -   Host Name, for example, `1a354373-d200-46f6-9d5c-daab9a65d9b6.abap.eu10.hana.ondemand.com`
    -   SAML2 Audience, for example, `https://1a354373-d200-46f6-9d5c-daab9a65d9b6.abap-web.eu10.hana.ondemand.com`

4.  Create a destination.

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
    
    *Name*
    
    </td>
    <td valign="top">
    
    Enter the name of the destination, for example, `my-SAML-assertion-destination`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Type*
    
    </td>
    <td valign="top">
    
    *HTTP*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *URL*
    
    </td>
    <td valign="top">
    
    Enter `https://<hostname of the own communication system>`, for example, `https://1a354373-d200-46f6-9d5c-daab9a65d9b6.abap.eu10.hana.ondemand.com>`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Proxy Type*
    
    </td>
    <td valign="top">
    
    *Internet*
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Authentication*
    
    </td>
    <td valign="top">
    
    *SAMLAssertion*​
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Key Store Location*
    
    </td>
    <td valign="top">
    
    If you don't use the standard signing certificate, then select the name of the corresponding key store, for instance `my-signing-keystore.p12`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Key Store Password*
    
    </td>
    <td valign="top">
    
    If you don't use the standard signing certificate, provide the password for the keystore.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Audience*
    
    </td>
    <td valign="top">
    
    Enter the OAuth 2.0 SAML2 Audience from the own communication system, for example, `https://1a354373-d200-46f6-9d5c-daab9a65d9b6.abap-web.eu10.hana.ondemand.com`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *AuthnContextClassRef*
    
    </td>
    <td valign="top">
    
    `urn:oasis:names:tc:SAML:2.0:ac:classes:PreviousSession`
    
    </td>
    </tr>
    </table>
    
    Enter the following additional properties:

    **Additional Properties**


    <table>
    <tr>
    <th valign="top">

    Property
    
    </th>
    <th valign="top">

    Input
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `nameIdFormat`
    
    </td>
    <td valign="top">
    
    Enter `urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress` if the e-mail is propagated or `urn:oasis:names:tc:SAML:1.1:nameid-format:unspecified` if the user name is propagated. For more information, see [User Propagation via SAML 2.0 Bearer Assertion Flow](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/user-propagation-via-saml-2-0-bearer-assertion-flow).
    
    </td>
    </tr>
    </table>
    
5.  Create a communication user.

    For this authentication method, a communication user isn't needed since it is solely based on the trust relationship to the issuer of the SAML assertion – which is configured in the communication system.

6.  Create a communication system.

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
    
    *System ID*
    
    </td>
    <td valign="top">
    
    Provide a system ID, for example, `MY_COMMUNICATION_PARTNER`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *System Name*
    
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
    
    *General*: *Inbound Only*
    
    </td>
    <td valign="top">
    
    Activate
    
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
    
    *SAML Bearer Assertion Provider*
    
    </td>
    <td valign="top">
    
    Activate
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *User ID Mapping Mode*
    
    </td>
    <td valign="top">
    
    Select *User Name*.

    If the `NameIdFormat` is unspecified, then the value of the `NameID` element in the SAML assertions' subject is mapped to the user name.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *SAML Bearer Issuer*
    
    </td>
    <td valign="top">
    
    Enter the SAML entity ID of the SAML bearer issuer, which corresponds to the common name \(the string after `CN=`\) of the signing certificate subject.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Upload Signing Certificate*
    
    </td>
    <td valign="top">
    
    Upload the signing certificate.
    
    </td>
    </tr>
    </table>
    
7.  Create a communication arrangement.

    For this authentication method, a communication arrangement isn't needed since it's solely based on the trust relationship to the issuer of the SAML assertion – which is configured in the communication system.


**Related Information**  


[Maintain Communication Users](maintain-communication-users-eef80dd.md "You can use this app to create and edit communication users. Communication users are used by solutions to authenticate themselves to be able to post data.")

[Communication Systems](communication-systems-15663c1.md "You can use this app to create communication systems. Communication systems are created to enable the communication among different systems.")

[Communication Arrangements](communication-arrangements-1decd8b.md)

