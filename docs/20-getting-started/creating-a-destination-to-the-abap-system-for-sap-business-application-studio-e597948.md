<!-- loioe597948462fe45c98c10269bbe3603d6 -->

# Creating a Destination to the ABAP System for SAP Business Application Studio

Learn how to set up a destination in the same Cloud Foundry subaccount in which you have subscribed to SAP Business Application Studio to establish communication between the ABAP environment and SAP Business Application Studio.



<a name="loioe597948462fe45c98c10269bbe3603d6__steps_fn5_mv2_mmb"/>

## Procedure

1.  Log on to the SAP BTP cockpit as administrator.

2.  From your global account, navigate to your Cloud Foundry subaccount.

3.  In the navigation area, choose *Destinations*.

4.  Choose *New Destination*.

5.  Enter the following data:


    <table>
    <tr>
    <th valign="top">

    Field


    
    </th>
    <th valign="top">

    User Input


    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
        *Name*


    
    </td>
    <td valign="top">
    
        Enter a name for the destination, for example, `SAP_Business_Application_Studio`.


    
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
    
        *Description*


    
    </td>
    <td valign="top">
    
         


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        *URL*


    
    </td>
    <td valign="top">
    
        Enter the URL of the ABAP system that you copied from the `<url>` element in the service key \(see [Creating a Service Key for the ABAP System](creating-a-service-key-for-the-abap-system-7af8259.md)\).


    
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
    
        *OAuth2UserTokenExchange​*


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        *Client ID*


    
    </td>
    <td valign="top">
    
        Enter the content of the `<clientID>` element that you copied from the `uaa` section of the service key \(see [Creating a Service Key for the ABAP System](creating-a-service-key-for-the-abap-system-7af8259.md)\).


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        *Client Secret*


    
    </td>
    <td valign="top">
    
        Enter the content of the `<clientsecret>` element that you copied from the `uaa` section of the service key \(see [Creating a Service Key for the ABAP System](creating-a-service-key-for-the-abap-system-7af8259.md)\).


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        *Token Service URL Type*


    
    </td>
    <td valign="top">
    
        Choose *Dedicated*.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        *Token Service URL*


    
    </td>
    <td valign="top">
    
        Enter `<uaa-url>/oauth/token`, where `<uaa-url>` is the content of the `<url>` element that you copied from the `uaa` section of the service key \(see [Creating a Service Key for the ABAP System](creating-a-service-key-for-the-abap-system-7af8259.md)\).


    
    </td>
    </tr>
    </table>
    
6.  Choose *New Property* and add the following properties:


    <table>
    <tr>
    <th valign="top">

    Property


    
    </th>
    <th valign="top">

    Value


    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
        *HTML5.DynamicDestination*


    
    </td>
    <td valign="top">
    
        `true`


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        *HTML5.Timeout*​


    
    </td>
    <td valign="top">
    
        `60000`


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        *WebIDEEnabled*


    
    </td>
    <td valign="top">
    
        `true`


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        *WebIDEUsage*


    
    </td>
    <td valign="top">
    
        `odata_abap,dev_abap,abap_cloud`


    
    </td>
    </tr>
    </table>
    
7.  Make sure that the *Use default JDK truststore* checkbox is checked.

8.  Choose *Save*.


**Related Information**  


[Creating a Destination for Cross-Subaccount Communication](creating-a-destination-for-cross-subaccount-communication-7d58eba.md "Learn how to create a destination with SAML assertion authentication to establish communication between an ABAP environment system and SAP Business Application Studio when they are set up in different subaccounts.")

