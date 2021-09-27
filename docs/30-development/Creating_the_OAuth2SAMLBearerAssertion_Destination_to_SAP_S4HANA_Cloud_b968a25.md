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
    <th>

    Field


    
    </th>
    <th>

    User Input


    
    </th>
    </tr>
    <tr>
    <td>

    ***Name***


    
    </td>
    <td>

    ***S4BusinessPartnerOAuth2***


    
    </td>
    </tr>
    <tr>
    <td>

    ** *Type* **


    
    </td>
    <td>

     *HTTP* 


    
    </td>
    </tr>
    <tr>
    <td>

    ***Description***


    
    </td>
    <td>

    *S/4HANA Cloud Business Partner OAuth2​*


    
    </td>
    </tr>
    <tr>
    <td>

    ***URL***


    
    </td>
    <td>

    *<Host name of the service URL from the communication arrangement​\>*, for example, ***https://my303291-api.s4hana.ondemand.com*** \(see [Copying the Inbound Service URL and Other Communication Details](Copying_the_Inbound_Service_URL_and_Other_Communication_Details_a14394b.md)\)


    
    </td>
    </tr>
    <tr>
    <td>

    ***Proxy Type***


    
    </td>
    <td>

    *Internet*


    
    </td>
    </tr>
    <tr>
    <td>

    ***Authentication***


    
    </td>
    <td>

    *OAuth2SAMLBearerAssertion​*


    
    </td>
    </tr>
    <tr>
    <td>

    ***Audience***


    
    </td>
    <td>

    *<SAML2 Audience from Oauth 2.0 Details\>* \(see [Copying the Inbound Service URL and Other Communication Details](Copying_the_Inbound_Service_URL_and_Other_Communication_Details_a14394b.md)\)


    
    </td>
    </tr>
    <tr>
    <td>

    ***authnContextClassRef***


    
    </td>
    <td>

    ***urn:oasis:names:tc:SAML:2.0:ac:classes:X509​***


    
    </td>
    </tr>
    <tr>
    <td>

    ***Client Key***


    
    </td>
    <td>

    *<Client ID from Oauth 2.0 Details\>* \(see [Copying the Inbound Service URL and Other Communication Details](Copying_the_Inbound_Service_URL_and_Other_Communication_Details_a14394b.md)\)


    
    </td>
    </tr>
    <tr>
    <td>

    ***Token Service URL***


    
    </td>
    <td>

    *<Token Service URL from Oauth 2.0 Details\>* \(see [Copying the Inbound Service URL and Other Communication Details](Copying_the_Inbound_Service_URL_and_Other_Communication_Details_a14394b.md)\)


    
    </td>
    </tr>
    <tr>
    <td>

    ***Token Service User***


    
    </td>
    <td>

    *<Communication user name​ from Oauth 2.0 Details\>* \(see [Copying the Inbound Service URL and Other Communication Details](Copying_the_Inbound_Service_URL_and_Other_Communication_Details_a14394b.md)\)


    
    </td>
    </tr>
    <tr>
    <td>

    ***Token Service Password​***


    
    </td>
    <td>

    *<Password of communication user\>* \(see [Creating a Communication Arrangement in SAP S/4HANA Cloud](Creating_a_Communication_Arrangement_in_SAP_S4HANA_Cloud_889fbe3.md)\)


    
    </td>
    </tr>
    </table>
    
6.  Choose *New Property* and add the following property:


    <table>
    <tr>
    <th>

    Property


    
    </th>
    <th>

    Value


    
    </th>
    </tr>
    <tr>
    <td>

    ***nameIdFormat*​**


    
    </td>
    <td>

    ***urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress​***


    
    </td>
    </tr>
    </table>
    
7.  Choose *Save*.


