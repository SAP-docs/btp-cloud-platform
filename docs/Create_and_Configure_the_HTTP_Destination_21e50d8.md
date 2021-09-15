<!-- loio21e50d89d0904038b98e604c8ed85de3 -->

# Create and Configure the HTTP Destination



<a name="loio21e50d89d0904038b98e604c8ed85de3__prereq_yhj_m5w_3bb"/>

## Prerequisites

You have logged into the SAP BTP cockpit from the landing page for your subaccount.



<a name="loio21e50d89d0904038b98e604c8ed85de3__steps_vhq_fww_3bb"/>

## Procedure

1.  In the cockpit, navigate to your subaccount.

2.  Choose *Connectivity* \> *Destinations* in the navigation panel.

3.  Create an HTTP destination.

    To enable principal propagation, create an *OAuth2SAMLBearerAssertion* HTTP destination and configure its settings as follows:

    1.  Configure the basic settings:


        <table>
        <tr>
        <th>

        Parameter


        
        </th>
        <th>

        Value


        
        </th>
        </tr>
        <tr>
        <td>

        `Name`


        
        </td>
        <td>

        Enter a meaningful name.


        
        </td>
        </tr>
        <tr>
        <td>

        `Type`


        
        </td>
        <td>

        ***HTTP***


        
        </td>
        </tr>
        <tr>
        <td>

        `Description`


        
        </td>
        <td>

        \(Optional\) Enter a meaningful description.


        
        </td>
        </tr>
        <tr>
        <td>

        `URL`


        
        </td>
        <td>

        ***https://*<my\_SAP\_Cloud\_for\_Customer\_system\_name\>*.crm.ondemand.com/sap/c4c/odata/v1/c4codataapi***


        
        </td>
        </tr>
        <tr>
        <td>

        `Proxy Type`


        
        </td>
        <td>

        ***Internet***


        
        </td>
        </tr>
        <tr>
        <td>

        `Authentication`


        
        </td>
        <td>

        ***OAuth2SAMLBearerAssertion***


        
        </td>
        </tr>
        <tr>
        <td>

        `Audience`


        
        </td>
        <td>

        Go to the SAP Cloud for Customer administration view, then navigate to *Configure Single Sign-On* under *General Settings* and copy the value from the *Local Service Provider* field.


        
        </td>
        </tr>
        <tr>
        <td>

        `Client Key`


        
        </td>
        <td>

        Client ID

        Paste the entry you have copied from the *Client ID* field when configuring the OAuth client. For more information, see [Configure the OAuth Client for OData Access](Configure_the_OAuth_Client_for_OData_Access_2c9c02d.md).


        
        </td>
        </tr>
        <tr>
        <td>

        `Token Service URL`


        
        </td>
        <td>

        ***https://*<my\_SAP\_Cloud\_for\_Customer\_system\_name\>*.crm.ondemand.com/sap/bc/sec/oauth2/token***


        
        </td>
        </tr>
        <tr>
        <td>

        `Token Service User`


        
        </td>
        <td>

        Client ID

        Paste the entry you have copied from the *Client ID* field when configuring the OAuth client. For more information, see [Configure the OAuth Client for OData Access](Configure_the_OAuth_Client_for_OData_Access_2c9c02d.md).


        
        </td>
        </tr>
        <tr>
        <td>

        `Token Service Password`


        
        </td>
        <td>

        Client secret

        Paste the entry you have copied from the *Client Secret* field when configuring the OAuth client. For more information, see [Configure the OAuth Client for OData Access](Configure_the_OAuth_Client_for_OData_Access_2c9c02d.md).


        
        </td>
        </tr>
        </table>
        
    2.  Configure the required additional property. To do so, in the *Additional Properties* panel, choose *New Property*, and enter the following property:

        > ### Note:  
        > You map the application users with the respective users in SAP Cloud for Customer using their email. Thanks to this mapping, you don't necessarily need to have a common identity provider between SAP BTP and SAP Cloud for Customer.


        <table>
        <tr>
        <th>

        Parameter


        
        </th>
        <th>

        Value


        
        </th>
        </tr>
        <tr>
        <td>

        `authnContextClassRef`


        
        </td>
        <td>

         ***urn:none*** 


        
        </td>
        </tr>
        <tr>
        <td>

        `nameIdFormat`


        
        </td>
        <td>

         ***urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress*** 


        
        </td>
        </tr>
        <tr>
        <td>

        `scope`


        
        </td>
        <td>

        Scope ID entries separated by space.

        Paste the entry you have copied from the Client ID field when configuring the OAuth client. For more information, see [Configure the OAuth Client for OData Access](Configure_the_OAuth_Client_for_OData_Access_2c9c02d.md).

        Example: *UIWC:CC\_HOME*


        
        </td>
        </tr>
        <tr>
        <td>

        `userIdSource`


        
        </td>
        <td>

        email


        
        </td>
        </tr>
        </table>
        
    3.  Select the *Use default JDK truststore* checkbox.
4.  Save your entries.


**Related Information**  


[Consuming the Destination Service \(Cloud Foundry Environment\)](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/7e306250e08340f89d6c103e28840f30.html?q=destination%20service)

