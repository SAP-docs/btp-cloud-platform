<!-- loio7d58ebac25164c5b8083647dd4b63d88 -->

# Creating a Destination for Cross-Subaccount Communication

Learn how to create a destination with SAML assertion authentication to establish communication between an ABAP environment system and SAP Business Application Studio when they are set up in different subaccounts.



## Procedure

1.  Log on to the SAP BTP cockpit as an administrator.

2.  From your global account, navigate to your Cloud Foundry subaccount.

3.  In the navigation area, choose *Connectivity* \> *Destinations*.

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

    Enter a name for the destination, for example ***SAP\_Business\_Application\_Studio***.


    
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

    Optionally, enter a description.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *URL*


    
    </td>
    <td valign="top">

    Enter the URL of your system by copying the *Host Name* from the *Communications Systems* app, for example ***1a354373-d200-46f6-9d5c-daab9a65d9b6.abap.eu10.hana.ondemand.com*** 


    
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

    *SAMLAssertion​*


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *Audience*


    
    </td>
    <td valign="top">

    Enter the URL of your system and add ***-web*** as follows ***1a354373-d200-46f6-9d5c-daab9a65d9b6.abap-web.eu10.hana.ondemand.com***


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *AuthnContextClassRef*


    
    </td>
    <td valign="top">

    *urn:oasis:names:tc:SAML:2.0:ac:classes:PreviousSession*


    
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

    ***true***


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *HTML5.Timeout*​


    
    </td>
    <td valign="top">

    ***60000***


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *WebIDEEnabled*


    
    </td>
    <td valign="top">

    ***true***


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *WebIDEUsage*


    
    </td>
    <td valign="top">

    ***odata\_abap,dev\_abap***


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *nameIdFormat*


    
    </td>
    <td valign="top">

    ***urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress***


    
    </td>
    </tr>
    </table>
    
7.  Make sure that the *Use default JDK truststore* checkbox is ticked.

8.  Choose *Save*.


