<!-- loio4e1761cecbdd47f6b93e1dfd9d254281 -->

# Configuring Basic Authentication

When using the basic authentication method, the client application provides the name of a communication user and its password to authenticate against the ABAP environment.



<a name="loio4e1761cecbdd47f6b93e1dfd9d254281__steps_gwf_rtr_pcc"/>

## Procedure

1.  Create a communication user using the Maintain Communication Users app in your ABAP environment system. Enter the following data:


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
    
    Provide a user name, for example, `MY_BASIC_AUTH_USER`.
    
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
    
    *Password* 
    
    </td>
    <td valign="top">
    
    Provide a password or generate one.
    
    </td>
    </tr>
    </table>
    
2.  Create a communication system.

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
    
    Provide a system ID, for example, `MY_COMMUNICATION PARTNER`.
    
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

    **Authentication Method** 
    
    </th>
    <th valign="top">

    **User Name/Client ID** 
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *User ID and Password* 
    
    </td>
    <td valign="top">
    
    User name of the communication user, for example, `MY_BASIC_AUTH_USER`.
    
    </td>
    </tr>
    </table>
    
3.  Create a communication arrangement.

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
    
    Select the scenario, for example,`Z_MY_SCENARIO`.
    
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
    
    Select the communication user, for example, `MY_BASIC_AUTH_USER`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Inbound Communication*: *Authentication Method* 
    
    </td>
    <td valign="top">
    
    `User ID and Password`
    
    </td>
    </tr>
    </table>
    
4.  Get technical data of the own communication system.

    Open the own communication system in the Communication Systems app in your ABAP environment system. To open your own communication system choose *Own SAP Cloud System*.

    Denote the host name, for example `1a354373-d200-46f6-9d5c-daab9a65d9b6.abap.eu10.hana.ondemand.com`.

5.  Create a destination.

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
    
    Enter the name of the destination that is used by the application, for example, `my-basic-destination`.
    
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
    
    *BasicAuthentication* 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *User*
    
    </td>
    <td valign="top">
    
    Enter the name of the communication user.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Password*
    
    </td>
    <td valign="top">
    
    Enter the password of the communication user.
    
    </td>
    </tr>
    </table>
    

**Related Information**  


[Maintain Communication Users](maintain-communication-users-eef80dd.md "You can use this app to create and edit communication users. Communication users are used by solutions to authenticate themselves to be able to post data.")

[Communication Systems](communication-systems-15663c1.md "You can use this app to create communication systems. Communication systems are created to enable the communication among different systems.")

[Communication Arrangements](communication-arrangements-1decd8b.md)

