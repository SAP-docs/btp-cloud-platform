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
        <th valign="top">

        Parameter


        
        </th>
        <th valign="top">

        Value


        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
                `Name`


        
        </td>
        <td valign="top">
        
                Enter a meaningful name.


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
                `Type`


        
        </td>
        <td valign="top">
        
                `HTTP`


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
                `Description`


        
        </td>
        <td valign="top">
        
                \(Optional\) Enter a meaningful description.


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
                `URL`


        
        </td>
        <td valign="top">
        
                <code>https://<i class="varname">&lt;my_SAP_Cloud_for_Customer_system_name&gt;</i>.crm.ondemand.com/sap/c4c/odata/v1/c4codataapi</code>


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
                `Proxy Type`


        
        </td>
        <td valign="top">
        
                `Internet`


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
                `Authentication`


        
        </td>
        <td valign="top">
        
                `OAuth2SAMLBearerAssertion`


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
                `Audience`


        
        </td>
        <td valign="top">
        
                Go to the SAP Cloud for Customer administration view, then navigate to *Configure Single Sign-On* under *General Settings* and copy the value from the *Local Service Provider* field.


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
                `Client Key`


        
        </td>
        <td valign="top">
        
                Client ID

        Paste the entry you have copied from the *Client ID* field when configuring the OAuth client. For more information, see [Configure the OAuth Client for OData Access](configure-the-oauth-client-for-odata-access-2c9c02d.md).


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
                `Token Service URL`


        
        </td>
        <td valign="top">
        
                <code>https://<i class="varname">&lt;my_SAP_Cloud_for_Customer_system_name&gt;</i>.crm.ondemand.com/sap/bc/sec/oauth2/token</code>


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
                `Token Service User`


        
        </td>
        <td valign="top">
        
                Client ID

        Paste the entry you have copied from the *Client ID* field when configuring the OAuth client. For more information, see [Configure the OAuth Client for OData Access](configure-the-oauth-client-for-odata-access-2c9c02d.md).


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
                `Token Service Password`


        
        </td>
        <td valign="top">
        
                Client secret

        Paste the entry you have copied from the *Client Secret* field when configuring the OAuth client. For more information, see [Configure the OAuth Client for OData Access](configure-the-oauth-client-for-odata-access-2c9c02d.md).


        
        </td>
        </tr>
        </table>
        
    2.  Configure the required additional property. To do so, in the *Additional Properties* panel, choose *New Property*, and enter the following property:

        > ### Note:  
        > You map the application users with the respective users in SAP Cloud for Customer using their email. Thanks to this mapping, you don't necessarily need to have a common identity provider between SAP BTP and SAP Cloud for Customer.


        <table>
        <tr>
        <th valign="top">

        Parameter


        
        </th>
        <th valign="top">

        Value


        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
                `authnContextClassRef`


        
        </td>
        <td valign="top">
        
                 `urn:none` 


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
                `nameIdFormat`


        
        </td>
        <td valign="top">
        
                 `urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress` 


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
                `scope`


        
        </td>
        <td valign="top">
        
                Scope ID entries separated by space.

        Paste the entry you have copied from the Client ID field when configuring the OAuth client. For more information, see [Configure the OAuth Client for OData Access](configure-the-oauth-client-for-odata-access-2c9c02d.md).

        Example: *UIWC:CC\_HOME*


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
                `userIdSource`


        
        </td>
        <td valign="top">
        
                email


        
        </td>
        </tr>
        </table>
        
    3.  Select the *Use default JDK truststore* checkbox.

4.  Save your entries.


**Related Information**  


[Consuming the Destination Service \(Cloud Foundry Environment\)](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/7e306250e08340f89d6c103e28840f30.html?q=destination%20service)

