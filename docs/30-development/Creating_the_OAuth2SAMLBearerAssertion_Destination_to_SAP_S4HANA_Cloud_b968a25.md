<!-- loiob968a25fe20e4f9a8f4366d1972fc7d4 -->

# Creating the OAuth2SAMLBearerAssertion Destination to SAP S/4​HANA Cloud



## Procedure

1.  Log on to the SAP BTP cockpit as administrator.

2.  Navigate to your global account and to your ABAP subaccount.

3.  From the navigation area, choose *Destinations*.

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

    ***S4BusinessPartnerOAuth2***


    
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

    *S/4HANA Cloud Business Partner OAuth2​*


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *URL*


    
    </td>
    <td valign="top">

    *<Host name of the service URL from the communication arrangement​\>*, for example, ***https://my303291-api.s4hana.ondemand.com*** \(see [Copying the Inbound Service URL and Other Communication Details](Copying_the_Inbound_Service_URL_and_Other_Communication_Details_a14394b.md)\)


    
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

    *OAuth2SAMLBearerAssertion​*


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *Audience*


    
    </td>
    <td valign="top">

    *<SAML2 Audience from Oauth 2.0 Details\>* \(see [Copying the Inbound Service URL and Other Communication Details](Copying_the_Inbound_Service_URL_and_Other_Communication_Details_a14394b.md)\)


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *authnContextClassRef*


    
    </td>
    <td valign="top">

    ***urn:oasis:names:tc:SAML:2.0:ac:classes:X509​***


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *Client Key*


    
    </td>
    <td valign="top">

    *<Client ID from Oauth 2.0 Details\>* \(see [Copying the Inbound Service URL and Other Communication Details](Copying_the_Inbound_Service_URL_and_Other_Communication_Details_a14394b.md)\)


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *Token Service URL*


    
    </td>
    <td valign="top">

    *<Token Service URL from Oauth 2.0 Details\>* \(see [Copying the Inbound Service URL and Other Communication Details](Copying_the_Inbound_Service_URL_and_Other_Communication_Details_a14394b.md)\)


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *Token Service User*


    
    </td>
    <td valign="top">

    *<Communication user name​ from Oauth 2.0 Details\>* \(see [Copying the Inbound Service URL and Other Communication Details](Copying_the_Inbound_Service_URL_and_Other_Communication_Details_a14394b.md)\)


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    *Token Service Password​*


    
    </td>
    <td valign="top">

    *<Password of communication user\>* \(see [Creating a Communication Arrangement in SAP S/4HANA Cloud](Creating_a_Communication_Arrangement_in_SAP_S4HANA_Cloud_889fbe3.md)\)


    
    </td>
    </tr>
    </table>
    
6.  Choose *New Property* and add the following property:


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

    *nameIdFormat*​


    
    </td>
    <td valign="top">

    ***urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress***


    
    </td>
    </tr>
    </table>
    
7.  Choose *Save*.


