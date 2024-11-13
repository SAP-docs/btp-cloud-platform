<!-- loio75a4131c783f478ca5b7e6e363ebe4c0 -->

# Configuring Client Certificate Authentication

When using the client certificate authentication method, the client application uses a client certificate to authenticate against the ABAP environment as corresponding communication user.



## Context

The client certificate can be provided by the application itself or by the SAP Destination service. The ABAP environment needs to trust the signing root certificate authority \(CA\). The list of trusted root certificate authorities can be found in [SAP Note 2801396](https://me.sap.com/notes/2801396).



## Procedure

1.  Maintain the key store.

    If the client application does not provide its own client certificate, then either upload a key store including the client certificate, the private key, and the certificate chain to the SAP Destination service, or generate one, for instance `my-keystore.p12`. For more information, see [Use Destination Certificates](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/use-destination-certificates).

2.  Get technical data of the own communication system.

    Open the own communication system in the Communication Systems app in your ABAP environment system. To open your own communication system choose *Own SAP Cloud System*.

    Denote the host name, for example, `1a354373-d200-46f6-9d5c-daab9a65d9b6.abap.eu10.hana.ondemand.com`.

3.  Create a destination.

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
    
    Enter the name of the destination that is used by the application, for example, `my-client-certificate-destination`.
    
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
    
    Enter `https://<hostname of the own communication system>`, for example, `https://1a354373-d200-46f6-9d5c-daab9a65d9b6.abap.eu10.hana.ondemand.com`.
    
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
    
    `ClientCertificateAuthentication` 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Use client provided certificate* 
    
    </td>
    <td valign="top">
    
    Activate, if the client provides the client certificate. Otherwise, deactivate.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Key Store Location*
    
    </td>
    <td valign="top">
    
    If the certificate is provided by the SAP Destinations service and not the client itself, then select the name of the corresponding key store, for instance `my-keystore.p12`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Key Store Password* 
    
    </td>
    <td valign="top">
    
    If the certificate is provided by the SAP Destinations service and not the client itself, then provide the password of the key store.
    
    </td>
    </tr>
    </table>
    
4.  Create a communication user.

    Create a communication user using the Maintain Communication Users app in your ABAP environment system. Enter the following data:


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
    
    *User Name*
    
    </td>
    <td valign="top">
    
    Provide a user name, for example, `MY_CERT _USER`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Description*
    
    </td>
    <td valign="top">
    
    Provide a description.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Certificate*
    
    </td>
    <td valign="top">
    
    Upload the client certificate to the communication user. During runtime, the service will be processed by the communication user that is assigned to the certificate.
    
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
    
    *SSL Client Certificate*
    
    </td>
    <td valign="top">
    
    User name of the communication user, e.g. `MY_CERT_USER`
    
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
    
    *Scenario ID*
    
    </td>
    <td valign="top">
    
    Select the scenario, for example, `Z_MY_SCENARIO`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Arrangement Name*
    
    </td>
    <td valign="top">
    
    Provide a name, for example, `MY_ARRANGEMENT`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Communication System*
    
    </td>
    <td valign="top">
    
    Select the communication system, for example, `MY_COMMUNICATION_PARTNER`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Inbound Communication*: *User Name*
    
    </td>
    <td valign="top">
    
    Select the communication user, for example, `MY_CERT_USER`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Inbound Communication*: *Authentication Method*
    
    </td>
    <td valign="top">
    
    *SSL Client Certificate*
    
    </td>
    </tr>
    </table>
    

**Related Information**  


[Maintain Communication Users](maintain-communication-users-eef80dd.md "You can use this app to create and edit communication users. Communication users are used by solutions to authenticate themselves to be able to post data.")

[Communication Systems](communication-systems-15663c1.md "You can use this app to create communication systems. Communication systems are created to enable the communication among different systems.")

[Communication Arrangements](communication-arrangements-1decd8b.md)

